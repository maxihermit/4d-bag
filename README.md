# gilgamesh — Gate of Open Source（王之開源）

![Gate of Open Source](assets/banner.png)

[English](#the-gate) | [繁體中文](#繁體中文)

> *"You dare develop without consulting the treasury? All the world's open-source treasures belong to me."*

An AI skill that opens the Gate to GitHub's infinite treasury — discovers trending projects, appraises their worth to your kingdom (project), and inspects them for curses (security issues).

**The King appraises. The King never installs.**

## The Gate

```
Your kingdom is under development
        ↓
Every day, new treasures appear in the vault (GitHub)
You cannot inspect them all yourself
        ↓
Open the Gate → survey the treasury
        ↓
The Appraiser compares each treasure against your kingdom's needs
        ↓
Inspects for curses: license, CVEs, abandoned forges
        ↓
Verdict:  Noble Phantasm / Heroic Spirit / Mystic Code / Sealed / Counterfeit
          寶具級        / 英靈級       / 禮裝級      / 封印中 / 贋作
```

## Install

### Claude Code

```bash
curl -o ~/.claude/commands/gilgamesh.md https://raw.githubusercontent.com/maxihermit/gilgamesh/main/gilgamesh.md
```

Then:
```
/gilgamesh init                     # Declare your kingdom
/gilgamesh                          # Open the Gate
/gilgamesh all                      # Survey all kingdoms
/gilgamesh audit owner/repo         # Appraise a specific treasure
/gilgamesh typescript               # Filter treasury by language
/gilgamesh presentation tools       # Seek a specific class of treasure
```

### OpenAI Codex / Cursor / Copilot / Others

Copy the contents of `gilgamesh.md` into your platform's instruction file:

| Platform | Copy to |
|----------|---------|
| Codex | `AGENTS.md` |
| Cursor | `.cursorrules` |
| Copilot | `.github/copilot-instructions.md` |
| Others | Paste into conversation |

### Daily Auto-Scan

In Claude Code:

```
Help me create a scheduled task that runs /gilgamesh all every morning
```

The Gate opens at dawn. You receive a report of new treasures.

## Appraisal System

| Grade | Meaning |
|-------|---------|
| **Noble Phantasm（寶具級）** | Legendary. Directly solves your pain point. Safe. Summon it. |
| **Heroic Spirit（英靈級）** | Powerful. Worth summoning for trial. |
| **Mystic Code（禮裝級）** | Has potential. Needs further evaluation. |
| **Sealed（封印中）** | Concerns detected. Keep in the vault. |
| **Counterfeit（贋作）** | Unsafe or unsuitable. Cast it out. |

## Example Output

```
## Kingdom: my-web-app
An e-commerce fortress built on Next.js and Prisma
Arsenal: TypeScript, React, Next.js, Prisma, Tailwind
Vulnerabilities: auth is hand-forged and brittle

### vercel/ai — AI SDK for building AI-powered apps
⭐ 15,234 | MIT | active forge (2 days ago) | 156 blacksmiths
**Noble Phantasm（寶具級）**
Appraisal: Your kingdom already uses Next.js. This treasure grants streaming
AI responses with 3 lines of incantation.
Authenticity: Clean inscription (MIT), no curses (0 CVEs), active forge.

### shadcn/ui — UI components forged on Radix
⭐ 82,000 | MIT | active forge (today) | 400+ blacksmiths
**Heroic Spirit（英靈級）**
Appraisal: Your kingdom uses Tailwind but forges components from raw metal.
This treasure saves countless hours.
Authenticity: Clean inscription (MIT), no curses, heavily maintained.
```

## Security & Privacy

The King's Appraiser follows strict protocol:

- **Only reads** royal decrees (package.json, requirements.txt) — never inspects source code
- **Never reads** .env, credentials, API keys, or secret scrolls
- **Never deploys** anything — only appraises
- **Never sends** your kingdom's code to external realms — only queries the public gates (GitHub / HN / OSV)
- Full appraisal protocol is in `gilgamesh.md` — 100 lines, inspect it yourself

## Optional: GITHUB_TOKEN

Without a royal seal: 60 gate openings per hour.
With a royal seal: 5,000 per hour.

```bash
export GITHUB_TOKEN=ghp_...
```

---

## 繁體中文

> *「你竟敢在沒有查閱寶庫的情況下開發？天下所有的開源寶物皆屬於我。」*

一個 AI Skill，打開通往 GitHub 無盡寶庫的大門——發現熱門專案、鑑定它們對你的王國（專案）的價值、並檢測是否有詛咒（資安問題）。

**王只鑑定，不親自部署。**

### 安裝

```bash
curl -o ~/.claude/commands/gilgamesh.md https://raw.githubusercontent.com/maxihermit/gilgamesh/main/gilgamesh.md
```

### 使用方式

```
/gilgamesh init                     # 宣告你的王國
/gilgamesh                          # 打開寶庫之門
/gilgamesh all                      # 巡視所有王國
/gilgamesh audit owner/repo         # 鑑定特定寶物
/gilgamesh typescript               # 依語言篩選寶庫
/gilgamesh 簡報工具                   # 搜尋特定類型的寶物
```

### 鑑定等級

| 等級 | 意義 |
|------|------|
| **寶具級（Noble Phantasm）** | 傳說級寶物。直接解決你的痛點，安全可靠，立即召喚。 |
| **英靈級（Heroic Spirit）** | 強大的寶物，值得召喚試用。 |
| **禮裝級（Mystic Code）** | 有潛力，但需要進一步評估。 |
| **封印中（Sealed）** | 偵測到疑慮，先留在寶庫裡。 |
| **贋作（Counterfeit）** | 不安全或不適合。逐出寶庫。 |

### 每天自動開門

在 Claude Code 裡直接說：

```
幫我建一個排程任務，每天早上跑 /gilgamesh all
```

每天黎明開門，自動收到新寶物鑑定報告。

### 資安與隱私

- 只讀取設定檔（package.json 等），**不讀原始碼**
- **不讀** .env、密碼、金鑰等機敏檔案
- **不安裝**任何東西，只產生鑑定報告
- **不會把你的程式碼傳到外部**
- 完整鑑定規則就在 `gilgamesh.md` 裡，100 行，你可以自己審查

## License

MIT
