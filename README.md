
<img align="center" width="197" height="240" alt="Puli-Icon" src="https://github.com/user-attachments/assets/f8c608c3-17d5-4274-a494-98c16b0a77c2" />

# 🛡️ The Puli Guardian MCP

<img align="right" width="350" height="600" 
  src="https://github.com/user-attachments/assets/e0d31d86-2d8a-41d3-a1ff-7a47abb87b3a">

### Puli Reviewer
is a proactive security and stability guardrail for your 
AI coding agents (Claude Code, Cursor, Antigravity, etc.). 
It prevents production breakages by confronting proposed 
code changes with a massive, real-time database of global 
incidents, edge cases, and security breaches.

**Stop production errors before they happen.**

Puli acts as a real-time bridge between your local development and global production insights. It doesn't just check syntax—it checks reality.
* **Real-time Intelligence:** Connects to a live DB of global incidents.
* **Agent Native:** Built specifically for the MCP ecosystem.
* **IP Protection:** Choose between BYOK or zero-retention cloud.

[How do I install it?](#install)

<br clear="right">

## 🚀 How it Works
<img align="right" width="450" height="750" 
  src="https://github.com/user-attachments/assets/4f0869c2-66b9-4498-8ddb-86fc0ccf7ed9">

Whenver your coding agent attempts to modify your codebase, <br>
Puli:

1.  **Analyzes the Context:**<br>
Queries the agent to understand the intent of<br>
the change.

2.  **Cross-References Failures:**<br>
Matches the code against a live-updated DB<br>
of real-world production errors and business-flow<br>
disruptions.

4.  **Stress Tests:**<br>
Forces the agent to account for specific edge<br>
cases before the code is ever committed.<br><br>
<img align="left" width="146" height="188" 
  src="https://github.com/user-attachments/assets/0a73df13-60bb-453c-bd11-c8e929dd7a7d">

<br clear="all" />

---

<a id="install"></a>
## ⚙️ Installation & Setup

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
        "PULI_API_KEY": "Your personal API key that was send to your e-mail",
        "BYO_OPENAI_API_KEY": "Optional* - <your-key-if-using-byok>",
        "BYO_GOOGLE_API_KEY": "Optional* - <your-key-if-using-byok>",
        "BYO_ANTHROPIC_API_KEY": "Optional* - <your-key-if-using-byok>"
      }
    }
  }
}
```

* Provide at lease one API key

### 2. Add Agent Rules

To ensure your agent utilizes the guardrail for every change, add our rules file to your project:

* **For Cursor:** Create a file at `.cursor/rules/puli-reviewer.md` and paste the content from [our rules template here](https://drive.google.com/file/d/1e2qbVHWiT6zAE2VYYVbXrydT8iRz1HlH/view?usp=sharing).

---

## 🛡️ Privacy & Security
We prioritize your IP security, Operations run locally on your station and no code is shared with our cloud.
**Zero Retention.** We embedd the semantical meanning of your code change in our cloud. Nothing is ever logged or stored.
We use vertex's LLM and embedding, You can provide your own GCP credentials (GOOGLE_CLOUD_PROJECT,GOOGLE_CLOUD_LOCATION) and in this case everything will run locally on your station apart from emebedded vectors needed to retreive data from our data bases.
