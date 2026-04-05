# 4d-bag (四次元百宝袋)

[English](#what-it-does) | [中文](#中文说明)

An AI skill that finds trending open-source projects and tells you which ones are worth using in your projects — with security checks. Works with Claude Code, Codex, Cursor, Copilot, or any AI assistant.

**It only reports. It never installs anything.**

## What it Does

```
You have projects in development
        ↓
Every day, new open-source tools appear on GitHub
You can't check them all manually
        ↓
4d-bag searches GitHub + Hacker News for you
        ↓
Compares against YOUR project's tech stack
        ↓
Checks security: license, CVEs, maintenance health
        ↓
Gives you a report: ADOPT / TRIAL / ASSESS / HOLD / AVOID
```

## Install

### Claude Code (recommended)

```bash
# Option 1: Global (works in all projects)
curl -o ~/.claude/commands/4d-bag.md https://raw.githubusercontent.com/YOUR_USERNAME/4d-bag/main/4d-bag.md

# Option 2: Per-project
mkdir -p .claude/commands
curl -o .claude/commands/4d-bag.md https://raw.githubusercontent.com/YOUR_USERNAME/4d-bag/main/4d-bag.md
```

Then use:
```
/4d-bag                          # scan current project
/4d-bag all                      # scan all projects
/4d-bag audit owner/repo         # security audit
/4d-bag typescript               # filter by language
/4d-bag presentation tools       # search specific topic
```

### OpenAI Codex / Cursor / Copilot / Others

Copy the contents of `4d-bag.md` into your platform's instruction file:

| Platform | Copy to |
|----------|---------|
| Codex | `AGENTS.md` in your repo |
| Cursor | `.cursorrules` in your repo |
| Copilot | `.github/copilot-instructions.md` |
| Others | Paste into the system prompt or conversation |

### Scheduled (daily auto-scan)

In Claude Code, set up a scheduled task to run `/4d-bag all` every morning. It will scan all your projects and notify you of new tools worth checking out.

## Example Output

```
## Your Project: my-web-app
Tech stack: TypeScript, React, Next.js, Prisma

### vercel/ai — AI SDK for building AI-powered apps
⭐ 15,234 | MIT | active (2 days ago) | 156 contributors
ADOPT
Why: You're already using Next.js. This gives you streaming AI responses with 3 lines of code.
Security: MIT license, no CVEs, actively maintained.

### shadcn/ui — UI components built on Radix
⭐ 82,000 | MIT | active (today) | 400+ contributors
TRIAL
Why: You're using Tailwind but building components from scratch. This saves time.
Security: MIT, no CVEs, very active.
```

## Security & Privacy

- **Only reads** package.json, requirements.txt, etc. — never your source code
- **Never reads** .env, credentials, API keys, or secrets
- **Never installs** anything — only reports findings
- **Never sends** your code to external APIs — only searches GitHub/HN/OSV
- All API calls go to public endpoints (GitHub, Hacker News, OSV.dev)
- Full prompt is in `4d-bag.md` — read it yourself, it's 90 lines

## Optional: GITHUB_TOKEN

Without it: 60 GitHub API requests/hour (enough for occasional use).
With it: 5,000/hour (needed for daily scans).

```bash
export GITHUB_TOKEN=ghp_...
```

---

## 中文说明

一个 AI Skill，自动帮你找最近热门的开源项目，对比你正在开发的所有项目，告诉你哪些值得用、哪些有安全问题。

**只看不装，不读你的源码。**

### 安装

```bash
# Claude Code
curl -o ~/.claude/commands/4d-bag.md https://raw.githubusercontent.com/maxihermit/4d-bag/main/4d-bag.md

# 其他平台（Codex / Cursor / Copilot）
# 把 4d-bag.md 的内容复制到对应的配置文件里
```

### 使用

```
/4d-bag                          # 扫描当前项目
/4d-bag all                      # 扫描所有项目
/4d-bag audit owner/repo         # 安全审计指定 repo
/4d-bag typescript               # 只看特定语言
/4d-bag 简报工具                   # 搜特定主题
```

### 它会做什么

1. 读你的 package.json 等清单文件（不读源码、不读 .env）
2. 搜 GitHub + Hacker News 热门项目
3. 评估跟你项目的相关性
4. 检查 license、已知漏洞、维护状态
5. 给出推荐：ADOPT / TRIAL / ASSESS / HOLD / AVOID

可以搭配定时任务每天自动跑。

## License

MIT
