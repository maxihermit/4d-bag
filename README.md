# Gate of Open Source

![banner](assets/banner.png)

[繁體中文](#繁體中文) | [English](#english)

---

## 繁體中文

> *「你竟敢在沒有查閱寶庫的情況下開發？」*

輸入 `/oss`，替你的專案在 GitHub 物色合適的開源代碼。

```
/oss → 讀技術棧 → 搜 GitHub + HN → 列出來問你
     → 你指哪個 → 讀你的代碼比對 → 告訴你值不值得
```

只報告，不安裝。「都不需要」是正常結果。

### 安裝

```bash
# Claude Code
curl -o ~/.claude/commands/oss.md https://raw.githubusercontent.com/maxihermit/gate-of-oss/main/oss.md

# Codex
mkdir -p .codex/skills/oss && curl -o .codex/skills/oss/SKILL.md https://raw.githubusercontent.com/maxihermit/gate-of-oss/main/oss.md

# Cursor
mkdir -p .cursor/rules && curl -o .cursor/rules/oss.mdc https://raw.githubusercontent.com/maxihermit/gate-of-oss/main/oss.md

# Copilot — 追加 oss.md 內容到 .github/copilot-instructions.md
```

### 用法

```
/oss                        # 掃技術棧 → 搜 → 問你要看哪個
/oss all                    # 一次掃所有子目錄
/oss audit owner/repo       # 查特定套件安不安全
/oss typescript             # 只看特定語言
/oss 簡報工具                # 搜特定主題
/oss init                   # 手動設定專案資訊
```

自動排程：跟 AI 說 `幫我建排程，每天早上跑 /oss all`

### 兩階段

**Phase 1**（便宜）讀設定檔 → 搜 → 列出來問你：

```
═══════════════════════════════════════
  my-app — React + Node.js
═══════════════════════════════════════

  AI/LLM
  ⭐ 15,234  vercel/ai — AI SDK，串流 + 重試

  UI
  ⭐ 82,000  shadcn/ui — 可複製貼上的元件

  已排除：12 個（已在用 / 無授權 / 已封存）

有沒有感興趣的？
```

**Phase 2**（你指了才跑）讀你的代碼，誠實比對：

```
  ┌─ vercel/ai — AI SDK
  │  ⭐ 15,234  MIT  漏洞: 0
  │  SSR
  │
  │  你現在：自己寫 fetch 串 OpenAI，80 行，沒重試
  │  用了之後：useChat hook，3 行，自動重試
  │  值不值得：值得，省 80 行，遷移 30 分鐘
  └─────────────────────────────────────
```

代碼已經夠好的話：`N — 你的代碼已經夠好，不需要這個`

### 鑑定等級

| 等級 | 意思 |
|------|------|
| SSR | 比對過代碼，確認有用，遷移合理 |
| SR | 值得試 |
| R | 有潛力，先記著 |
| N | 有疑慮 |
| 廢鐵 | 不安全，狗都不用 |

### 隱私

- Phase 1 只讀設定檔，Phase 2 只讀你指到的 2-3 個檔案
- 不讀 .env / 密碼 / 金鑰，不傳代碼到外面
- 評估結果存 `.oss-profile.yml`，可隨時刪

### GITHUB_TOKEN（選用）

不設也能用（60 次/小時），設了 5,000 次。`export GITHUB_TOKEN=ghp_...`

---

## English

> *"You dare develop without consulting the treasury?"*

Type `/oss` to find useful open-source code for your project on GitHub.

```
/oss → reads tech stack → searches GitHub + HN → shows menu
     → you pick → it reads your code → honest verdict
```

Reports only. Never installs. "You don't need anything" is a valid result.

### Install

```bash
# Claude Code
curl -o ~/.claude/commands/oss.md https://raw.githubusercontent.com/maxihermit/gate-of-oss/main/oss.md

# Codex
mkdir -p .codex/skills/oss && curl -o .codex/skills/oss/SKILL.md https://raw.githubusercontent.com/maxihermit/gate-of-oss/main/oss.md

# Cursor
mkdir -p .cursor/rules && curl -o .cursor/rules/oss.mdc https://raw.githubusercontent.com/maxihermit/gate-of-oss/main/oss.md

# Copilot — append oss.md to .github/copilot-instructions.md
```

### Usage

```
/oss                        # Scan → search → menu → you pick → verify
/oss all                    # Scan all subdirectories
/oss audit owner/repo       # Security check a repo
/oss typescript             # Filter by language
/oss presentation tools     # Search a topic
/oss init                   # Set up project profile
```

Auto-schedule: tell AI `Create a scheduled task to run /oss all every morning`

### Two phases

**Phase 1** (cheap): reads config files → searches → shows categorized menu.

**Phase 2** (you trigger): reads your code for selected areas → before/after → honest grade.

### Grades

| Grade | Meaning |
|-------|---------|
| SSR | Verified against your code. Worth it. |
| SR | Worth evaluating. |
| R | Bookmark it. |
| N | Concerns found. |
| Junk | Unsafe. Not even my dog would use it. |

### Privacy

- Phase 1: config files only. Phase 2: only files you point at
- Never reads `.env`, passwords, keys. Never sends code externally
- Verdicts cached in `.oss-profile.yml` (deletable)

### GITHUB_TOKEN (optional)

Works without it (60 req/hr). With it: 5,000. `export GITHUB_TOKEN=ghp_...`

---

MIT — *如果你笑出來了，請給一顆星星。If this made you laugh, star it.*
