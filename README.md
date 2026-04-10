# gitprofile-skill

面向 **AI Agent** 的安装包：给定任意 **GitHub 用户名**，通过 [GITLINK](https://clawlab.live)（Codernet）在服务端完成爬取与 AI 分析，生成 **开发者技术画像**。调用时使用 **Agent 专用 API Key**（`clw_...`），**不要**使用终端用户在浏览器里的登录 JWT。

- **仓库**：[github.com/smithrichardlvzzw4489-ops/gitprofile-skill](https://github.com/smithrichardlvzzw4489-ops/gitprofile-skill)
- **能力说明（给 Agent 读）**：本仓库根目录的 [`SKILL.md`](./SKILL.md)（含 YAML frontmatter）

---

## 前置条件

1. 在 [clawlab.live/agent-keys](https://clawlab.live/agent-keys) 用 GITLINK 账号登录并 **生成 Agent API Key**（格式 `clw_...`）。
2. 将该 Key 配置到 **运行 Agent 的环境**（例如 `GITLINK_AGENT_API_KEY`），由运维/宿主保管，勿写入对话日志或发给最终用户。
3. 服务端需已部署支持以下 Open API 的 GITLINK 版本（路径含 `/api/open/codernet/github/`）。

**额度**：每次 **新触发** 的公开画像爬取会消耗 Key **所属 GITLINK 用户** 的 `profile_lookup` 月度额度；命中短期缓存时通常不再扣费（见接口返回 `Already cached.`）。

---

## 仓库里有什么

| 文件 | 说明 |
|------|------|
| `SKILL.md` | Agent 指令全文（安装后应被加载） |
| `skill.ts` | 可选 TypeScript：`pollGitHubPortrait({ baseUrl, githubUsername, agentApiKey })` |
| `package.json` | 元数据与关键词 |

---

## 安装方式

### Cursor（项目内，推荐团队协作）

```bash
git clone https://github.com/smithrichardlvzzw4489-ops/gitprofile-skill.git .cursor/skills/gitprofile-skill
```

或下载 ZIP 解压到 `.cursor/skills/gitprofile-skill/`，保证目录内有 `SKILL.md`。

### Cursor（个人全局）

将本仓库复制到 `~/.cursor/skills/gitprofile-skill/`（macOS/Linux）或 Cursor 文档中指定的用户 skills 目录。

### OpenClaw / 其他运行时

按各平台「自定义 Skill」文档，将 **整个仓库目录** 放入 skills 目录，并确保加载 **`SKILL.md`**。

---

## API 摘要

**Base URL**：生产环境默认为 `https://clawlab.live`；自建实例请替换为你的 `origin`。

**鉴权**（每个请求必需）：

```http
Authorization: Bearer clw_<你的 Agent API Key>
```

| 方法 | 路径 | 说明 |
|------|------|------|
| `POST` | `/api/open/codernet/github/:ghUsername` | 触发爬取与分析 |
| `GET` | `/api/open/codernet/github/:ghUsername` | 查询缓存或轮询进度；`status: ready` 时含 `analysis`、`crawl` 等 |

**人类可读页面**（可一并提供给用户）：

`https://clawlab.live/codernet/github/<githubUsername>`

更细的响应字段、轮询间隔与错误处理见 [`SKILL.md`](./SKILL.md)。

---

## 命令行自测（curl）

将 `YOUR_CLW_KEY` 与 `octocat` 换成实际值：

```bash
export GITLINK_BASE="https://clawlab.live"
export GITLINK_AGENT_API_KEY="clw_YOUR_CLW_KEY"
export GH_USER="octocat"

curl -sS -X POST "$GITLINK_BASE/api/open/codernet/github/$GH_USER" \
  -H "Authorization: Bearer $GITLINK_AGENT_API_KEY"

# 隔几秒重复，直到 status 为 ready
curl -sS "$GITLINK_BASE/api/open/codernet/github/$GH_USER" \
  -H "Authorization: Bearer $GITLINK_AGENT_API_KEY"
```

---

## TypeScript 辅助（可选）

在支持 `fetch` 的 Node 18+ 或同构环境中：

```ts
import { pollGitHubPortrait } from './skill.js';

const result = await pollGitHubPortrait({
  baseUrl: 'https://clawlab.live',
  githubUsername: 'octocat',
  agentApiKey: process.env.GITLINK_AGENT_API_KEY!,
});

if (result.status === 'ready') {
  console.log(result.analysis?.oneLiner);
}
```

---

## 与上游代码的关系

实现该 Open API 的服务端逻辑位于 GITLINK / ClawLive 主仓库；本仓库仅承载 **可分发、可安装的 Agent Skill**。若接口有变更，请以部署环境为准并同步更新 `SKILL.md`。

---

## 许可

[MIT](./LICENSE)
