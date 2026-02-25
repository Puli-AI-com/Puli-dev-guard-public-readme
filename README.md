

<p align="center">
  <img width="250" height="302" alt="Puli AI" src="https://github.com/user-attachments/assets/b1e21d97-35b2-4364-b62d-62d7f663c900" />
</p>

# 🛡️ Puli Guardian MCP

### _**AI agents write code fast. Puli validates it against what actually matters.**_

## What is it?

<img align="right" width="300" height="510" 
  src="https://github.com/user-attachments/assets/e0d31d86-2d8a-41d3-a1ff-7a47abb87b3a">

is a proactive **quality** and **stability** guardrail for your <br>
AI coding agents (Claude Code, Cursor, Antigravity, etc.). <br> 
It prevents production breakages by confronting proposed <br> 
code changes with a massive, real-time knowledge layer consisted <br> 
of real-time bugs, release notes, past incidents, edge cases, regulations and security breaches. <br>

**Not a linter.** Linters check syntax and style. Puli checks whether your code will survive production.

**Stop production errors before they happen.** Puli acts as a <br> real-time bridge between your local development and global the real world. <br> It doesn't just check syntax — **it checks reality.**

[How do I install it?](#install)

<br clear="right">

## ✨ What it does
<img align="right" width="450" height="750" 
  src="https://github.com/user-attachments/assets/b20008e8-b2f3-494a-95bf-ad74344f6456">

Whenver your coding agent finishes a coding session, <br>
Puli receives from the agent the code changes and their meanning and

1. **Analyzes the Context:**<br>
Understand the intent of the change <br>
and the underlying architecture and technology stack<br>

2.  **Query data:**<br>
Query the data layer for real-world real-time production <br>
errors and relevant chaos patterns<br>

3.  **Reality check:**<br>
Comfronts the code with the most relevant and updated <br>
information and forces the agent to account for <br>
any issues found, making sure they are fixed before <br>
the code is ever committed.<br><br>

<br clear="all" />

<br>
<br>

## 🚀 How it Works

### Context Diagram

<p align="center">
<img width="740" height="420" alt="Screenshot 2026-02-25 at 22 16 21" src="https://github.com/user-attachments/assets/e989ebee-c4bf-42e5-96fb-0c9aa5f6a57a" />
</p>

### What Puli validates against

| Layer | What it covers | Sources |
|---|---|---|
| **Chaos patterns** | Silent errors, race conditions, hardcoded fragility | Public incident databases, community catalogs |
| **Coding best practices** | Anti-patterns, error handling, structural issues | Stack Overflow, AWS, Azure, GCP docs |
| **AI framework knowledge** | Outdated API calls, deprecated methods | LangChain, LangGraph, latest library docs |
| **Production incidents** | Patterns that caused real outages | Engineering blogs, Hacker News, postmortem repos |
| **Regulations** | Data handling, privacy, audit trail violations | GDPR, SOC 2 |
| **Security weaknesses** | CWEs and vulnerability patterns | CWE database, CVE databases |

And many more..

The data layer *updates continuously*. Your agent validates against what's happening in the real world right now — not a static rule set from 6 months ago.

<a id="install"></a>
## ⚙️ Installation & Setup (2 minutes)

### 1. Install dependencies
Make sure that uvx is installed on your station

### 2. Configure the MCP Server
Add the following to your coding agent's configuration (e.g., `claude_desktop_config.json` or your IDE's MCP settings):

```json
{
  "mcpServers": {
    "puli-viewer": {
      "command": "uvx",
      "args": ["--from", "puli-mcp-server@latest", "puli-reviewer"],
      "env": {
        "BYO_OPENAI_API_KEY": "Optional* - <your-key-if-using-byok>",
        "BYO_GOOGLE_API_KEY": "Optional* - <your-key-if-using-byok>",
        "BYO_ANTHROPIC_API_KEY": "Optional* - <your-key-if-using-byok>"
      }
    }
  }
}
```

* Provide at lease one API key or use our infrastructure

### 2. Add Agent Rules

So your agent actually uses Puli on every change, add the rules file to your project:

* **For Cursor:** Create a file at `.cursor/rules/puli-reviewer.mdc` and paste the content from [our rules template here](https://drive.google.com/file/d/10mXrsaERDonnUIefV4GQ1hEXhJbZboZ6/view?usp=sharing).
* **For Claude-code:** Create a file at `.claude/rules/puli-reviewer.md` and paste the content from [our rules template here](https://drive.google.com/file/d/10mXrsaERDonnUIefV4GQ1hEXhJbZboZ6/view?usp=sharing).

That's it. Next time your agent writes code, Puli validates it against real-world failure patterns before it lands.

## Examples:
<p align="center">
<img width="975" height="484" alt="Screenshot 2026-02-26 at 0 12 43" src="https://github.com/user-attachments/assets/30ae516b-9ce1-4a09-99be-51f9a0dbf670" />
</p>

<p align="center">
<img width="780" height="222" alt="Screenshot 2026-02-26 at 0 14 34" src="https://github.com/user-attachments/assets/3439dd06-6893-4eba-b0bc-cb35f54547f0" />
</p>

<p align="center">
<img width="621" height="500" alt="Screenshot 2026-02-26 at 0 16 40" src="https://github.com/user-attachments/assets/3ced347e-ba6b-4f52-9eab-f361a7c3c4fd" />
</p>

## 🛡️ Privacy & Security
**We prioritize your IP security**! Operations run locally on your station. no code is shared with our cloud.<br>
**Zero Retention.** We embedd the semantical meanning of your code change in our cloud. Nothing is ever logged or stored.<br>
We use vertex's LLM and embedding, You can provide your own GCP credentials (set GOOGLE_CLOUD_PROJECT, GOOGLE_CLOUD_LOCATION env vars for the MCP server)
in this case **everything** will run locally on your station apart from the data layer query using emebedded vectors <br>

## Feedback

This is early. We're actively expanding the knowledge layer and would genuinely love feedback:

- What failure patterns are your AI agents producing that we should be catching?
- What agents/IDEs should we support next?
- What broke in production that you wish had been caught earlier?

[Open an issue](https://github.com/Puli-AI-com/Puli-dev-guard-public-readme/issues) or [start a discussion](https://github.com/Puli-AI-com/Puli-dev-guard-public-readme/discussions).

<br>

---

<p align="center">
  <strong>Your AI agent doesn't know what broke production last week. Puli does.</strong>
</p>
