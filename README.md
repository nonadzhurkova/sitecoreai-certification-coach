# SitecoreAI Certification Coach

A Claude skill that coaches you for the **SitecoreAI CMS Developer** certification, one competency at a time.

It writes fresh, exam-style questions from the official Sitecore docs, runs short quizzes (single answer and select-all), explains every answer with the doc source, and recommends what to practice next.

> Unofficial. Not affiliated with or endorsed by Sitecore. It does not guarantee a pass.

## What you get

- Drills by competency, using the official weights (C1 to C9)
- Questions built from the current docs, so facts do not go stale
- Interactive quizzes in claude.ai (plain text in Claude Code)
- Feedback after each score: what you missed, a memory hook, and a next step
- Mixed sets and a 60-question mock exam split by competency weight

## Setup

### 1. Connect the Sitecore docs MCP

The skill reads the docs through this MCP server: `https://sitecore.mcp.kapa.ai`

- **claude.ai:** Settings, Connectors, add a custom connector with the URL above.
- **Claude Code:**
  ```
  claude mcp add --transport http sitecore-docs https://sitecore.mcp.kapa.ai
  ```

### 2. Install the skill

- **claude.ai:** zip the `skills/sitecoreai-exam-coach` folder and upload it under Settings, Capabilities, Skills.
- **Claude Code:** copy the `skills/sitecoreai-exam-coach` folder to `~/.claude/skills/` (all projects) or `.claude/skills/` (one project).

## How to use it

Start a chat and say, for example:

- "Coach me for the SitecoreAI CMS Developer exam."
- "Drill me on Content Modeling."
- "Run a mixed set of Pages, Serialization and Security."
- "Retry the Security set with new questions."
- "Start a 60-question mock exam."

Tell it your practice-exam score or weak topics at the start so it can focus your practice.

## How it works

1. It asks which competency you want to practice.
2. It searches the Sitecore docs for the facts first.
3. It writes a quiz of about 6 questions with randomized answer positions.
4. You answer, check, and send your score back.
5. It gives feedback and recommends the next set.

## What is not included

- No real exam questions or answer keys
- No personal data or scores
- No fixed list of facts. Everything is checked against the docs each time.

Please do not add exam content to this repo.

## Contributing

Improvements to the coaching rules, question style and accuracy rules are welcome. Open an issue or a pull request. Never include real exam questions.

## License

MIT
