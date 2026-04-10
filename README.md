# gitprofile-skill

用 **GitHub 用户名** 自动生成 **开发者技术画像**：在对话里看总结，需要时打开网页看完整卡片。

---

## 第一步：安装（复制粘贴命令）

先打开 **终端**，进入你要用 Cursor 写的**项目根目录**（就是有代码的那个文件夹），再执行下面**其中一种**。

### 有 Git（Windows PowerShell）

```powershell
New-Item -ItemType Directory -Force -Path ".cursor\skills" | Out-Null
git clone https://github.com/smithrichardlvzzw4489-ops/gitprofile-skill.git .cursor\skills\gitprofile-skill
```

### 有 Git（Mac / Linux）

```bash
mkdir -p .cursor/skills && git clone https://github.com/smithrichardlvzzw4489-ops/gitprofile-skill.git .cursor/skills/gitprofile-skill
```

### 没有 Git

1. 浏览器打开：<https://github.com/smithrichardlvzzw4489-ops/gitprofile-skill>  
2. 点绿色 **Code** → **Download ZIP**，下载并解压。  
3. 把解压出来的文件夹**改名为** `gitprofile-skill`。  
4. 在项目里新建文件夹 `.cursor`，再在 `.cursor` 里新建 `skills`，把 `gitprofile-skill` **整个**拖进去。  
5. 最终路径要像：`你的项目/.cursor/skills/gitprofile-skill/`（这一层里直接能看到一堆文件，不要再多套一层）。

装好后**重新打开一下 Cursor** 或当前项目，让设置生效。

---

## 第二步：使用（对 AI 说话就行）

打开 Cursor 的 **Agent / 聊天**，直接说，把 `octocat` 换成你要查的账号：

```text
帮我查一下 GitHub 用户 octocat 的技术画像
```

也可以说「查 @octocat」「看看这个 GitHub 是谁」等，**只要带上正确的 GitHub 用户名**即可。

---

## 你会得到什么

- 对话里：技术方向、亮点之类的**文字总结**。  
- 有时会有一条 **GITLINK 网页链接**，点进去可以看排版好的完整画像。

---

## 装好了但一直不成功？

把终端或 Cursor 里的报错原文发给 **帮你装软件 / 配环境的人** 处理即可；你自己不用改仓库里的文件。

---

[MIT](./LICENSE)
