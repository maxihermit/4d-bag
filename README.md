# gilgamesh — 王之開源（Gate of Open Source）

![Gate of Open Source](assets/banner.png)

[繁體中文](#這是什麼) | [English](#english)

> *「你竟敢在沒有查閱寶庫的情況下開發？天下所有的開源寶物皆屬於我。」*

## 這是什麼

一個 AI Skill。裝好之後，你只要打 `/gilgamesh`，它就會自動去 GitHub 和 Hacker News 找最近熱門的開源專案，跟你說哪些對你正在開發的東西有用，然後幫你檢查那些專案安不安全。

**它只會給你報告，不會幫你安裝任何東西。**

## 它怎麼運作

```
你正在開發專案
      ↓
每天 GitHub 上都有新的開源工具出現
你不可能每天自己去看
      ↓
gilgamesh 幫你去看
      ↓
比對你的專案用了什麼技術、缺了什麼
      ↓
檢查安全性：授權條款、已知漏洞、有沒有人在維護
      ↓
給你鑑定結果：SSR / SR / R / N / 廢鐵
```

### 鑑定等級

| 等級 | 意思 |
|------|------|
| SSR | 直接解決你的問題，安全，馬上用 |
| SR | 值得試用 |
| R | 有潛力，再看看 |
| N | 有疑慮，先別碰 |
| 廢鐵 | 不安全，別用 |

## 安裝

### Claude Code

```bash
curl -o ~/.claude/commands/gilgamesh.md https://raw.githubusercontent.com/maxihermit/gilgamesh/main/gilgamesh.md
```

### OpenAI Codex

```bash
mkdir -p .codex/skills/gilgamesh
curl -o .codex/skills/gilgamesh/SKILL.md https://raw.githubusercontent.com/maxihermit/gilgamesh/main/gilgamesh.md
```

### Cursor

```bash
mkdir -p .cursor/rules
curl -o .cursor/rules/gilgamesh.mdc https://raw.githubusercontent.com/maxihermit/gilgamesh/main/gilgamesh.md
```

### GitHub Copilot

把 `gilgamesh.md` 的內容**追加**到 `.github/copilot-instructions.md` 的最後面（不要覆蓋原本的內容）。

### 其他平台

直接把 `gilgamesh.md` 的內容貼到對話裡。

## 怎麼用

```
/gilgamesh init                     # 第一次用：告訴它你的專案在做什麼
/gilgamesh                          # 幫你找有用的新工具
/gilgamesh all                      # 一次掃描你所有的專案
/gilgamesh audit owner/repo         # 檢查某個 repo 安不安全
/gilgamesh typescript               # 只看特定語言的
/gilgamesh 簡報工具                   # 搜特定主題
```

### 每天自動跑

在 Claude Code 裡說：

```
幫我建一個排程任務，每天早上跑 /gilgamesh all
```

每天早上自動收到報告。

## 報告長什麼樣子

```
## 你的專案：my-web-app
技術：TypeScript, React, Next.js, Prisma, Tailwind
痛點：auth 自己寫的很脆弱，沒有測試

### vercel/ai — 做 AI 功能的 SDK
⭐ 15,234 | MIT | 2 天前更新 | 156 人貢獻
SSR
為什麼推薦：你已經在用 Next.js 了，這個讓你 3 行程式碼就能做串流 AI 回應。
安全：MIT 授權，沒有已知漏洞，持續維護中。

### shadcn/ui — 基於 Radix 的 UI 元件庫
⭐ 82,000 | MIT | 今天更新 | 400+ 人貢獻
SR
為什麼推薦：你在用 Tailwind 但元件都自己刻，這個省很多時間。
安全：MIT 授權，沒有漏洞，非常活躍。
```

## 資安與隱私

- 只讀 package.json 這類設定檔，**不讀你的程式碼**
- **不讀** .env、密碼、金鑰
- **不安裝**任何東西，只給你報告
- **不會把你的程式碼傳到外面**
- 規則全寫在 `gilgamesh.md` 裡，100 行，你可以自己看完每一行

## GITHUB_TOKEN（選用）

不設也能用，但一小時只能搜 60 次。設了可以搜 5,000 次。

```bash
export GITHUB_TOKEN=ghp_...
```

---

## English

> *"You dare develop without consulting the treasury? All the world's open-source treasures belong to me."*

An AI skill that searches GitHub and Hacker News for trending open-source projects, tells you which ones are useful for your project, and checks if they're safe to use.

**It only reports. It never installs anything.**

### How it works

```
You're building a project
      ↓
New open-source tools appear on GitHub every day
You can't check them all manually
      ↓
gilgamesh searches for you
      ↓
Compares against your project's tech stack and needs
      ↓
Checks security: license, known vulnerabilities, maintenance status
      ↓
Gives you a verdict: SSR / SR / R / N / Junk
```

### Grades

| Grade | Meaning |
|-------|---------|
| SSR | Solves your problem. Safe. Use it. |
| SR | Worth trying. |
| R | Has potential. Evaluate further. |
| N | Has concerns. Wait. |
| Junk | Unsafe. Don't use it. |

### Install

#### Claude Code

```bash
curl -o ~/.claude/commands/gilgamesh.md https://raw.githubusercontent.com/maxihermit/gilgamesh/main/gilgamesh.md
```

#### OpenAI Codex

```bash
mkdir -p .codex/skills/gilgamesh
curl -o .codex/skills/gilgamesh/SKILL.md https://raw.githubusercontent.com/maxihermit/gilgamesh/main/gilgamesh.md
```

#### Cursor

```bash
mkdir -p .cursor/rules
curl -o .cursor/rules/gilgamesh.mdc https://raw.githubusercontent.com/maxihermit/gilgamesh/main/gilgamesh.md
```

#### GitHub Copilot

Append the contents of `gilgamesh.md` to your existing `.github/copilot-instructions.md`.

#### Others

Paste the contents of `gilgamesh.md` into your conversation.

### Usage

```
/gilgamesh init                     # First time: describe your project
/gilgamesh                          # Find useful new tools
/gilgamesh all                      # Scan all your projects at once
/gilgamesh audit owner/repo         # Security check a specific repo
/gilgamesh typescript               # Filter by language
/gilgamesh presentation tools       # Search specific topic
```

### Daily auto-scan

In Claude Code, say:

```
Help me create a scheduled task that runs /gilgamesh all every morning
```

### Example output

```
## Your Project: my-web-app
Tech: TypeScript, React, Next.js, Prisma, Tailwind
Pain points: auth is fragile, no proper testing

### vercel/ai — AI SDK for building AI-powered apps
⭐ 15,234 | MIT | updated 2 days ago | 156 contributors
SSR
Why: You're already using Next.js. This gives you streaming AI
responses with 3 lines of code.
Security: MIT license, no known vulnerabilities, actively maintained.

### shadcn/ui — UI components built on Radix
⭐ 82,000 | MIT | updated today | 400+ contributors
SR
Why: You're using Tailwind but building components from scratch.
This saves you hours.
Security: MIT, no vulnerabilities, very active.
```

### Security & Privacy

- Only reads config files (package.json, etc.) — never your source code
- Never reads .env, passwords, API keys
- Never installs anything
- Never sends your code anywhere
- Full prompt is in `gilgamesh.md` — 100 lines, read it yourself

### GITHUB_TOKEN (optional)

Without it: 60 GitHub API requests per hour.
With it: 5,000 per hour.

```bash
export GITHUB_TOKEN=ghp_...
```

## License

MIT

---

*如果你笑出來了，請給一顆星星。If this made you laugh, please star it.*
