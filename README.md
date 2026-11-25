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

Name the server `Sitecore_docs` (capital S, underscore). The skill expects the tool name `mcp__Sitecore_docs__search_sitecore_knowledge_sources`.

- **claude.ai or the Claude desktop app:** Settings, Connectors, add a custom connector with the URL above.
- **Claude Code, project file (recommended):** create a `.mcp.json` file in your project folder:
  ```json
  {
    "mcpServers": {
      "Sitecore_docs": {
        "type": "http",
        "url": "https://sitecore.mcp.kapa.ai"
      }
    }
  }
  ```
- **Claude Code, command line:**
  ```
  claude mcp add --transport http Sitecore_docs https://sitecore.mcp.kapa.ai
  ```

Add the server **before** you start the session. A server added during a session is not loaded until you start a new session. If the server asks you to sign in, run `/mcp` and follow the steps.

### 2. Install the skill

- **claude.ai:** zip the `skills/sitecoreai-exam-coach` folder and upload it under Settings, Capabilities, Skills.
- **Claude Code:** copy the `skills/sitecoreai-exam-coach` folder to `~/.claude/skills/` (all projects) or `.claude/skills/` (one project).

### 3. Check that it works

Start a new session and ask: "What is Sitecore Content Serialization in SitecoreAI?" You should get answers from doc.sitecore.com. Then say "Coach me for the SitecoreAI CMS Developer exam."

## Troubleshooting

- **The server does not show up in the Claude desktop app** after `claude mcp add`: the app may not read servers added through the command line. Use the `.mcp.json` file in your project folder, or add it under Settings, Connectors as a custom connector. Then start a new session.
- **`claude mcp list` says "Needs authentication":** run `/mcp` in a session and sign in.
- **`/mcp reconnect` says no server found:** the server was added after the session started. Start a new session.
- **Duplicate servers:** if you added the server under two names, remove the old one, for example `claude mcp remove sitecore-docs -s user`.
- **Different server name:** if you use a name other than `Sitecore_docs`, the skill may not find the tool. Rename the server, or ask Claude to load the docs search tool with ToolSearch.

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
