# 王之開源（Gate of Open Source）

![banner](assets/banner.png)

[繁體中文](#這是什麼) | [English](#english)

> *「你竟敢在沒有查閱寶庫的情況下開發？天下所有的開源寶物皆屬於我。」*

## 這是什麼

`/oss` — 幫你找這週有什麼新的開源工具值得用。

```
/oss → 掃你的技術棧 → 搜 GitHub + HN → 列出來問你
       → 你指哪個 → 它去讀你的代碼比對 → 告訴你值不值得
```

只報告，不安裝。「都不需要」是正常結果。

## 安裝

```bash
# Claude Code
curl -o ~/.claude/commands/oss.md https://raw.githubusercontent.com/maxihermit/gate-of-oss/main/oss.md

# Codex
mkdir -p .codex/skills/oss && curl -o .codex/skills/oss/SKILL.md https://raw.githubusercontent.com/maxihermit/gate-of-oss/main/oss.md

# Cursor
mkdir -p .cursor/rules && curl -o .cursor/rules/oss.mdc https://raw.githubusercontent.com/maxihermit/gate-of-oss/main/oss.md

# Copilot — 把 oss.md 內容追加到 .github/copilot-instructions.md
```

## 用法

```
/oss                        # 掃技術棧 → 搜 → 問你要看哪個
/oss all                    # 一次掃所有子目錄
/oss audit owner/repo       # 查一個特定套件安不安全
/oss typescript             # 只看特定語言
/oss 簡報工具                # 搜特定主題
/oss init                   # 手動設定專案資訊
```

每天自動跑：跟 AI 說 `幫我建排程，每天早上跑 /oss all`

## 怎麼運作

**兩階段：先便宜地瀏覽，你指了才花 token 深入。**

**Phase 1**（每次跑，便宜）讀 package.json / Cargo.toml → 搜 GitHub + HN → 列出來問你：

```
═══════════════════════════════════════
  my-app — React + Node.js
═══════════════════════════════════════

  AI/LLM
  ⭐ 15,234  vercel/ai — AI SDK，串流 + 重試
  ⭐  3,200  instructor-ai/instructor — 結構化輸出

  UI
  ⭐ 82,000  shadcn/ui — 可複製貼上的 UI 元件

  已排除：12 個（已在用 / 無授權 / 已封存）

有沒有感興趣的？
```

**Phase 2**（你指了才跑）去讀你的代碼，誠實比對：

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

如果你的代碼已經夠好，它會直接說：

```
  │  N — 你的代碼已經夠好，不需要這個
```

## 鑑定等級

| 等級 | 意思 |
|------|------|
| SSR | 比對過代碼，確認有用，遷移合理 |
| SR | 值得試 |
| R | 有潛力，先記著 |
| N | 有疑慮 |
| 廢鐵 | 不安全，狗都不用 |

## 隱私

- Phase 1 只讀設定檔，Phase 2 只讀你指到的 2-3 個檔案
- 不讀 .env / 密碼 / 金鑰，不傳代碼到外面
- 評估結果存 `.oss-profile.yml`，下次不重複，可隨時刪

## GITHUB_TOKEN（選用）

不設也能用（60 次/小時），設了 5,000 次/小時。

```bash
export GITHUB_TOKEN=ghp_...
```

---

## English

> *"You dare develop without consulting the treasury?"*

`/oss` — finds trending open-source projects relevant to your stack.

```
/oss → reads your tech stack → searches GitHub + HN → shows a menu
     → you pick what's interesting → it reads your code → honest verdict
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

# Copilot — append oss.md contents to .github/copilot-instructions.md
```

### Usage

```
/oss                        # Scan → search → menu → you pick → verify
/oss all                    # Scan all subdirectories
/oss audit owner/repo       # Security check a specific repo
/oss typescript             # Filter by language
/oss presentation tools     # Search a topic
/oss init                   # Set up project profile
```

### How it works

**Phase 1** (cheap, always runs): reads package.json / Cargo.toml → searches → categorized menu → "anything interesting?"

**Phase 2** (you trigger): reads your actual code for selected areas → before/after comparison → honest grade.

### Grades

| Grade | Meaning |
|-------|---------|
| SSR | Verified against your code. Worth it. |
| SR | Likely helps. Worth evaluating. |
| R | Potential. Bookmark it. |
| N | Concerns found. |
| Junk | Unsafe. Not even my dog would use it. |

### Privacy

- Phase 1: config files only. Phase 2: only files you point at (2-3 per area)
- Never reads `.env`, passwords, API keys. Never sends code externally
- Verdicts cached in `.oss-profile.yml` (deletable)

MIT License

---

*如果你笑出來了，請給一顆星星。If this made you laugh, please star it.*
