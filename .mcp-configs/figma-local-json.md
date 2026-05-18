# 🚀 Antigravity Developer Runbook & Context Library

Welcome to my personal engineering knowledge base, configuration repository, and agent-context library. This repository serves as a centralized "Second Brain" to store optimized workspace settings, design-to-code configurations, boilerplate commands, and architectural blueprints for full-stack web development.

---

## 🛠️ Verified MCP Server Configurations

This section contains production-ready Model Context Protocol (MCP) snippets tested and verified to work seamlessly inside **Antigravity**.

### 🎨 Figma-to-Code Local Gateway
The following configuration initializes a local Node.js process using the `@yhy2001/figma-mcp-server` registry package. This allows the Antigravity agent to read precise structural data, coordinates, typography layout layers, and auto-layout attributes straight from a Figma canvas URL.

#### `config.json` / Workspace Settings

```json
{
  "mcpServers": {
    "figma-local": {
      "command": "npx",
      "args": [
        "-y", 
        "@yhy2001/figma-mcp-server", 
        "--stdio"
      ],
      "env": {
        "FIGMA_API_KEY": "YOUR_FIGMA_PERSONAL_ACCESS_TOKEN"
      }
    }
  }
}
```

#### 🛠️ Setup Instructions
1. Generate a **Figma Personal Access Token**:
   - Go to your Figma Account Settings.
   - Scroll down to the **Personal access tokens** section.
   - Click **Create a new personal access token**, assign read permissions, and copy the string.
2. Open the Antigravity MCP or workspace settings panel.
3. Paste the configuration block above, replacing "YOUR_FIGMA_PERSONAL_ACCESS_TOKEN" with your live secret token.
4. Restart or refresh the Antigravity agent panel to trigger initialization.

---

## 💾 Core Stack Context & Cheat Sheets

*Note: This repository is actively updated with optimized cheat sheets, CLI commands, and architectural concepts.*

### 📐 Prisma Concepts & Workflows
* **Database Acceleration:** Schema structures optimized for PostgreSQL connection pooling and high-performance querying patterns.
* **Migrations Runbook:** Commands to apply safe schema mutations across isolation tiers.

### 🦁 Nest.js Architectural Blueprint
* **CLI Quick-Reference:** Best-practice commands for generating highly modular structural layers (modules, services, controllers).
* **Clean Framework Principles:** Structuring controllers and database layers explicitly so that LLM agents can interpret project patterns without drifting from native framework standards.

---

## 🔒 Security Best Practice
> ⚠️ **CRITICAL:** Never commit real secrets, database URIs, or personal access tokens directly to git history. Keep your active configuration files inside a local, un-tracked workspace configuration file or use standard environment replacement patterns where supported. Keep this file clean as a template!
