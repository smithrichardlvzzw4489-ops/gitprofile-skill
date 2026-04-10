# gitprofile-skill

## 做什么

装好后，Agent 只要拿到一个 **GitHub 用户名**，就会去 [GITLINK](https://clawlab.live) 拉取公开资料并生成 **开发者技术画像**（技术栈、能力分布、一句话总结、锐评、多平台线索等），用自然语言回复用户，并给出网页版卡片链接。

## 怎么用

1. 在 [clawlab.live/agent-keys](https://clawlab.live/agent-keys) 生成 **Agent API Key**（`clw_...`），配到运行 Agent 的环境变量（例如 `GITLINK_AGENT_API_KEY`），**不要**用浏览器里的用户登录 JWT。
2. 把本仓库放进 Agent 的 skills 目录，并加载根目录的 **`SKILL.md`**（Cursor 示例：克隆到 `.cursor/skills/gitprofile-skill`）。
3. 之后用户说「查一下 @某某 的 GitHub 画像」之类即可；具体调用步骤、接口路径写在 [`SKILL.md`](./SKILL.md)。

可选：在代码里用 [`skill.ts`](./skill.ts) 的 `pollGitHubPortrait({ baseUrl, githubUsername, agentApiKey })` 轮询直到结果就绪。

## 用了之后的效果

- **对话里**：用户会收到基于结构化数据的摘要（亮点、技术标签、语言占比、能力象限、评价文字等），信息来自服务端返回的 `analysis`（及必要时 `crawl`）。
- **页面上**：可打开 `https://clawlab.live/codernet/github/<用户名>` 查看完整画像卡片。
- **额度**：新触发爬取会扣 Key **所属 GITLINK 账号**的月度画像额度；短期内已有缓存时响应更快、通常不再扣费。

---

[MIT](./LICENSE)
