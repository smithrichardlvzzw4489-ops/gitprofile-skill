# gitprofile-skill

给 **OpenClaw 小龙虾** 用的技能：你在聊天里丢一个 **GitHub 用户名**，它会去生成 **开发者技术画像**（对话里说明，有时还会给网页链接）。

---

## 第一步：装到小龙虾的技能目录

下面命令二选一：**有 Git** 用克隆；**没有 Git** 用 ZIP。装完建议 **重启一下 OpenClaw / 小龙虾**（或你平时开网关的方式），再聊天。

### Windows（PowerShell，整段复制执行）

```powershell
New-Item -ItemType Directory -Force -Path "$env:USERPROFILE\.openclaw\skills" | Out-Null
git clone https://github.com/smithrichardlvzzw4489-ops/gitprofile-skill.git "$env:USERPROFILE\.openclaw\skills\gitprofile-skill"
```

### Mac / Linux

```bash
mkdir -p ~/.openclaw/skills && git clone https://github.com/smithrichardlvzzw4489-ops/gitprofile-skill.git ~/.openclaw/skills/gitprofile-skill
```

### 没有 Git

1. 打开：<https://github.com/smithrichardlvzzw4489-ops/gitprofile-skill> → **Code** → **Download ZIP**  
2. 解压，文件夹**改名为** `gitprofile-skill`  
3. 放进本机的 **`OpenClaw 技能文件夹`** 里，路径要像：  
   - Windows：`C:\Users\你的用户名\.openclaw\skills\gitprofile-skill\`  
   - Mac/Linux：`~/.openclaw/skills/gitprofile-skill/`  
4. 这一层里应直接能看到仓库里的文件，**不要再多套一层文件夹**。

若你用的 OpenClaw 版本需要在设置里 **勾选 / 启用技能**，打开 **gitprofile-skill** 即可（没有这项就只靠上面目录）。

---

## 第二步：跟小龙虾说话

打开你平时跟 **小龙虾** 聊天的窗口，直接发（把 `octocat` 换成真实用户名）：

```text
帮我查一下 GitHub 用户 octocat 的技术画像
```

也可以说「查 @某某」「看看这个 GitHub 是谁」——**带上对的 GitHub 用户名**就行。

---

## 你会得到什么

- 对话里：技术方向、亮点一类的**文字总结**。  
- 有时会有一条 **网页链接**，点进去是 GITLINK 上的完整画像页。

---

## 装好了但一直不行？

把报错或截图发给 **帮你装 OpenClaw / 小龙虾的人**；不用自己改仓库里的文件。

---

[MIT](./LICENSE)
