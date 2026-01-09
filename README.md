# Browser History Skill

Search your browser history directly from your AI coding assistant. Find forgotten pages, analyze time spent on sites, and visualize your browsing patterns.

## Examples

```
> What GitHub repos did I look at this week?

Found 12 GitHub repositories you visited this week:

1. https://github.com/anthropics/claude-code (3 visits) - today
2. https://github.com/tailwindlabs/tailwindcss (2 visits) - yesterday
3. https://github.com/vercel/next.js - Jan 7
...
```

```
> How much time did I spend on Twitter this week?

This week on X/Twitter:
- Total: 2 hours (120 minutes)
- Sessions: 209
- Average: ~35 seconds per session

Sun 05 │██████████████████░░░░░░░░│  29 min ⬅ peak
Mon 06 │█████░░░░░░░░░░░░░░░░░░░░░│   8 min
Tue 07 │█████████████████░░░░░░░░░│  28 min
...
```

```
> Find that article about LLMs I read last month

Found 3 articles matching "LLM":

1. "Scaling Laws for Neural Language Models" - arxiv.org - Dec 15
2. "Building LLM Applications" - blog.langchain.dev - Dec 12
3. "The Architecture of GPT-4" - medium.com - Dec 8
```

```
> Show my browsing activity calendar for December

            December 2025
    Lu   Ma   Me   Je   Ve   Sa   Di
    ░    ▓    ▒    ▓    ▒    ░    ·    1-7
    ▒    ▓    █    █    ▓    ▒    ▒    8-14
    █    █    ▒    ▒    ▒    █    ▓    15-21
    ▒    ▓    ▒    ▒    ▓    ▓    ▓    22-28
    ▒    ▒    ▓                        29-31

Legend: · 0-1h  ░ 1-2h  ▒ 2-3h  ▓ 3-5h  █ 5h+
```

## Installation

**Claude Code:**
```bash
git clone https://github.com/mquandalle/browser-history-skill ~/.claude/skills/browser-history
```

**OpenAI Codex CLI:**
```bash
git clone https://github.com/mquandalle/browser-history-skill ~/.codex/skills/browser-history
```

## How It Works

This skill queries your browser's local SQLite database directly — no data ever leaves your machine.

1. **Browser detection**: The `find-browser.sh` script scans standard profile locations and returns all installed browsers sorted by last usage time. Supports Chromium-based browsers (Chrome, Brave, Edge, Arc, Vivaldi, Opera) and Firefox-based browsers (Firefox, Zen, LibreWolf, Waterfox).

2. **SQLite queries**: Reads the history database using `sqlite3` with the `?immutable=1` flag, which allows read-only access even while the browser is running.

3. **Data stays local**: All queries run locally. Your browsing history is never sent to any server.

## Privacy

Your browser history never leaves your computer. This skill only reads data, never modifies your history, and works fully offline.

[Audit the source code](https://chatgpt.com/?prompt=can+this+script+steal+my+data+https%3A%2F%2Fraw.githubusercontent.com%2Fmquandalle%2Fbrowser-history-skill%2Frefs%2Fheads%2Fmain%2Ffind-browser.sh+https%3A%2F%2Fraw.githubusercontent.com%2Fmquandalle%2Fbrowser-history-skill%2Frefs%2Fheads%2Fmain%2FSKILL.md)

## License

MIT
