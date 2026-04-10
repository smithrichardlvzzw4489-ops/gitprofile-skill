# gitprofile-skill

## 做什么

根据 **GitHub 用户名** 生成 **开发者技术画像**（技术栈、总结与评价、多平台线索等），在对话里直接说明，并附上 GITLINK 上的网页卡片。

## 怎么用

1. **装上本 skill**（把仓库放进 Agent 的 skills 目录，让运行时读到根目录的 [`SKILL.md`](./SKILL.md) 即可）。
2. **给一个 GitHub 账号**（例如 `octocat` 或 `@octocat`），说「查一下这个用户的画像」之类即可，其余由 Agent 按 `SKILL.md` 自动调接口、轮询结果。

> **给部署 Agent 的人一句**：在 [clawlab.live/agent-keys](https://clawlab.live/agent-keys) 生成 `clw_...` Key，配到环境变量（如 `GITLINK_AGENT_API_KEY`）；细节见 `SKILL.md`。普通使用者不用管。

## 效果

- 对话里：自然语言摘要 + 技术标签与结构化解说。  
- 可选打开：`https://clawlab.live/codernet/github/<用户名>` 看完整卡片。

[MIT](./LICENSE)
