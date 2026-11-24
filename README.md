# AI Certificates MCP server

[![AI Certificates MCP connector](https://glama.ai/mcp/connectors/study.aicertificates/practice-exams/badges/score.svg)](https://glama.ai/mcp/connectors/study.aicertificates/practice-exams)

Practice questions for the Anthropic Claude certifications, served over MCP. Quiz yourself from Claude, Claude Code, Cursor, VS Code or any MCP client.

**The assistant never sees the answer key.** `get_practice_question` returns the question and options with no answer field at all. The key is withheld at the data layer, not by a prompt instruction, so the assistant can't leak it or be argued into a wrong one. You commit to an answer first, and `check_answer` then grades it and explains every option, including the ones you didn't pick.

- **Endpoint:** `https://aicertificates.study/api/mcp` (Streamable HTTP, free, no account, nothing recorded)
- **Website:** [aicertificates.study/mcp](https://aicertificates.study/mcp)
- **Registry:** `study.aicertificates/practice-exams` in the [Official MCP Registry](https://registry.modelcontextprotocol.io/v0/servers?search=aicertificates)

## Exams covered

| Code | Certification |
| --- | --- |
| CCAR-P | Claude Certified Architect – Professional |
| CCAR-F | Claude Certified Architect – Foundations |
| CCDV-P | Claude Certified Developer – Professional |
| CCDV-F | Claude Certified Developer – Foundations |
| CCAO-F | Claude Certified Associate – Foundations |

Where Anthropic has announced a new exam version (December 7, 2026), both versions are available.

## Tools

| Tool | What it does |
| --- | --- |
| `list_exams` | Exam codes, item counts and the domain list with published weights |
| `get_practice_question` | One original practice question with options and no answer key |
| `check_answer` | Grades your choice and explains every option |
| `my_progress` | Signed-in users: results by exam domain, weakest first |
| `open_study` | Opens the study page for an exam, domain or sub-objective |

## Connect

**Claude Code**

```bash
claude mcp add --transport http ai-certificates https://aicertificates.study/api/mcp
```

**Claude (web and desktop):** Settings, Connectors, Add custom connector, then paste `https://aicertificates.study/api/mcp`.

**Any client with a JSON config** (Cursor, VS Code, and others):

```json
{
  "mcpServers": {
    "ai-certificates": {
      "type": "http",
      "url": "https://aicertificates.study/api/mcp"
    }
  }
}
```

Then ask: *"Quiz me on CCAR-P, one question at a time."*

## About

Written by Matthew Hartman, who passed CCAR-P with 965/1000. Original questions, blind-checked by separate AI solvers before release.

Unofficial study material. Not affiliated with, authorized by or endorsed by Anthropic. "Claude" and the certification names are Anthropic's marks.
