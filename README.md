
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
  src="https://github.com/user-attachments/assets/559ae811-58f4-4dba-b91b-856cdf02f430">

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

### 1. Configure the MCP Server
Add the following to your coding agent's configuration (e.g., `claude_desktop_config.json` or your IDE's MCP settings):

```json
{
  "mcpServers": {
    "puli-viewer": {
      "command": "uvx",
      "args": ["--from", "puli-plg@latest", "puli-reviewer"],
      "env": {
        "BYO_OPENAI_API_KEY": "<your-key-if-using-byok>"
      }
    }
  }
}
```

### 2. Add Agent Rules

To ensure your agent utilizes the guardrail for every change, add our rules file to your project:

* **For Cursor:** Create a file at `.cursor/rules/puli-reviewer.md` and paste the content from [our rules template here](https://drive.google.com/file/d/1e2qbVHWiT6zAE2VYYVbXrydT8iRz1HlH/view?usp=sharing).

---

## 🛡️ Privacy & Security
We prioritize your IP security with two distinct working modes:

| Mode | How it Works | Data Privacy |
| :--- | :--- | :--- |
| **Bring Your Own Key** | Uses your own OpenAI/Anthropic API key. | **Local Only.** No code is shared with our cloud; only DB patterns are fetched. |
| **Internal Key** | Uses Puli's managed API keys. | **Zero Retention.** Code passes through our infra for processing but is never logged or stored. |
