# 王之開源（Gate of Open Source）

![Gate of Open Source](assets/banner.png)

[繁體中文](#這是什麼) | [English](#english)

> *「你竟敢在沒有查閱寶庫的情況下開發？天下所有的開源寶物皆屬於我。」*

## 這是什麼

一個 AI Skill。裝好之後，你只要打 `/oss`，它就會自動去 GitHub 和 Hacker News 找最近熱門的開源專案，跟你說哪些對你正在開發的東西有用，然後幫你檢查那些專案安不安全。

**它只會給你報告，不會幫你安裝任何東西。**

## 它怎麼運作

```
你正在開發專案
      ↓
每天 GitHub 上都有新的開源工具出現
你不可能每天自己去看
      ↓
/oss 幫你去看
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
curl -o ~/.claude/commands/oss.md https://raw.githubusercontent.com/maxihermit/oss/main/oss.md
```

### OpenAI Codex

```bash
mkdir -p .codex/skills/oss
curl -o .codex/skills/oss/SKILL.md https://raw.githubusercontent.com/maxihermit/oss/main/oss.md
```

### Cursor

```bash
mkdir -p .cursor/rules
curl -o .cursor/rules/oss.mdc https://raw.githubusercontent.com/maxihermit/oss/main/oss.md
```

### GitHub Copilot

把 `oss.md` 的內容**追加**到 `.github/copilot-instructions.md` 的最後面（不要覆蓋原本的內容）。

### 其他平台

直接把 `oss.md` 的內容貼到對話裡。

## 怎麼用

```
/oss init                     # 第一次用：告訴它你的專案在做什麼
/oss                          # 幫你找有用的新工具
/oss all                      # 一次掃描你所有的專案
/oss audit owner/repo         # 檢查某個 repo 安不安全
/oss typescript               # 只看特定語言的
/oss 簡報工具                   # 搜特定主題
```

### 每天自動跑

在 Claude Code 裡說：

```
幫我建一個排程任務，每天早上跑 /oss all
```

每天早上自動收到報告。

## 報告長什麼樣子

```
## my-web-app — 電商網站

| Repo | Stars | 等級 | 一句話 |
|------|-------|------|--------|
| vercel/ai | 15,234 | SSR | 3 行就能做串流 AI 回應 |
| shadcn/ui | 82,000 | SR | 不用再自己刻 UI 元件 |

---

### vercel/ai — 做 AI 功能的 SDK

| 項目 | 內容 |
|------|------|
| Stars | 15,234 |
| License | MIT ✓ |
| 最近更新 | 2 天前 |
| 貢獻者 | 156 人 |
| 等級 | **SSR** |

**Before → After**

| | Before | After |
|---|---|---|
| 做法 | 自己寫 fetch 串 OpenAI API | 用 AI SDK 內建的 useChat hook |
| 程式碼 | 80 行，要自己管串流和錯誤處理 | 3 行，自動處理 |
| 結果 | 串流不穩定，錯誤處理不完整 | 穩定串流，自動重試 |

**結論：** 你已經在用 Next.js，這個直接裝就能用，省 80 行程式碼。
```

## 資安與隱私

- 只讀 package.json 這類設定檔，**不讀你的程式碼**
- **不讀** .env、密碼、金鑰
- **不安裝**任何東西，只給你報告
- **不會把你的程式碼傳到外面**
- 規則全寫在 `oss.md` 裡，100 行，你可以自己看完每一行

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
/oss searches for you
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
curl -o ~/.claude/commands/oss.md https://raw.githubusercontent.com/maxihermit/oss/main/oss.md
```

#### OpenAI Codex

```bash
mkdir -p .codex/skills/oss
curl -o .codex/skills/oss/SKILL.md https://raw.githubusercontent.com/maxihermit/oss/main/oss.md
```

#### Cursor

```bash
mkdir -p .cursor/rules
curl -o .cursor/rules/oss.mdc https://raw.githubusercontent.com/maxihermit/oss/main/oss.md
```

#### GitHub Copilot

Append the contents of `oss.md` to your existing `.github/copilot-instructions.md`.

#### Others

Paste the contents of `oss.md` into your conversation.

### Usage

```
/oss init                     # First time: describe your project
/oss                          # Find useful new tools
/oss all                      # Scan all your projects at once
/oss audit owner/repo         # Security check a specific repo
/oss typescript               # Filter by language
/oss presentation tools       # Search specific topic
```

### Daily auto-scan

In Claude Code, say:

```
Help me create a scheduled task that runs /oss all every morning
```

### Example output

```
## my-web-app — e-commerce site

| Repo | Stars | Grade | One-liner |
|------|-------|-------|-----------|
| vercel/ai | 15,234 | SSR | Streaming AI in 3 lines |
| shadcn/ui | 82,000 | SR | Stop building UI from scratch |

---

### vercel/ai — AI SDK for building AI-powered apps

| Item | Detail |
|------|--------|
| Stars | 15,234 |
| License | MIT |
| Last commit | 2 days ago |
| Contributors | 156 |
| Grade | **SSR** |

Before → After

| | Before | After |
|---|---|---|
| How | Manual fetch to OpenAI API | Built-in useChat hook |
| Code | 80 lines, manual streaming | 3 lines, automatic |
| Result | Flaky streaming, no retry | Stable, auto-retry |

**Bottom line:** You already use Next.js. Install and save 80 lines.
```

### Security & Privacy

- Only reads config files (package.json, etc.) — never your source code
- Never reads .env, passwords, API keys
- Never installs anything
- Never sends your code anywhere
- Full prompt is in `oss.md` — 100 lines, read it yourself

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
