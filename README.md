# 4d-bag

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

## License

MIT
