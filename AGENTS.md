# Strawberry App Mobile — Agent Setup

This file provides instructions for AI coding agents working in this repository.

## Atlassian Tooling Setup

### TWG CLI

The [Teamwork Graph CLI](https://developer.atlassian.com/cloud/twg-cli/) gives agents
command-line access to Atlassian data (Jira, Confluence, Bitbucket) via the
Teamwork Graph.

**Install and set up TWG CLI:**

```
Install/setup TWG using https://teamwork-graph.atlassian.com/cli/AGENTS.md
```

After setup, verify with:

```bash
twg doctor
```

### Atlassian Rovo MCP

The [Atlassian Rovo MCP server](https://support.atlassian.com/atlassian-rovo-mcp-server/docs/getting-started-with-the-atlassian-remote-mcp-server/)
connects your AI agent to Jira, Confluence, Bitbucket and more via the Model
Context Protocol.

MCP configuration files for supported editors are provided in the
[`.mcp/`](.mcp/) directory. See the [MCP Configuration](#mcp-configuration) section below.

---

## MCP Configuration

### VS Code / GitHub Copilot

Add the following to your VS Code MCP settings:

```json
{
  "servers": {
    "atlassian-mcp-server": {
      "url": "https://mcp.atlassian.com/v1/mcp/authv2",
      "type": "http"
    }
  }
}
```

A ready-to-use file is available at [`.mcp/vscode-mcp.json`](.mcp/vscode-mcp.json).

### Cursor

In Cursor → Settings → MCP, add a new server entry:

```json
"Atlassian-MCP-Server": {
  "url": "https://mcp.atlassian.com/v1/mcp/authv2"
}
```

A ready-to-use file is available at [`.mcp/cursor-mcp.json`](.mcp/cursor-mcp.json).

### Claude Desktop

Add to your Claude Desktop `mcpServers` configuration:

```json
{
  "mcpServers": {
    "Atlassian": {
      "command": "npx",
      "args": ["-y", "mcp-remote@latest", "https://mcp.atlassian.com/v1/mcp/authv2"]
    }
  }
}
```

A ready-to-use file is available at [`.mcp/claude-mcp.json`](.mcp/claude-mcp.json).

### Codex

Add to your Codex MCP configuration:

```json
"Atlassian-Rovo-MCP": {
  "command": "npx",
  "args": ["-y", "mcp-remote@latest", "https://mcp.atlassian.com/v1/mcp/authv2"]
}
```

A ready-to-use file is available at [`.mcp/codex-mcp.json`](.mcp/codex-mcp.json).

---

## Try It Out

Once connected, your AI coding agent can access Atlassian data in plain language:

- _"Find all open bugs in Strawberry App Mobile."_
- _"Create a task titled 'Redesign onboarding', high priority, assign to me."_
- _"Move EXP-6 to 'In Review' and add a comment that the PR is up."_
- _"Make 5 Jira work items from these meeting notes…"_

---

## References

- [Teamwork Graph](https://teamworkgraph.com/)
- [TWG CLI setup guide](https://developer.atlassian.com/cloud/twg-cli/getting-started/installation/)
- [Atlassian Rovo MCP — Getting Started](https://support.atlassian.com/atlassian-rovo-mcp-server/docs/getting-started-with-the-atlassian-remote-mcp-server/)
- [IDE setup guide](https://support.atlassian.com/atlassian-rovo-mcp-server/docs/setting-up-ides/)
- [Troubleshooting](https://support.atlassian.com/atlassian-rovo-mcp-server/docs/troubleshooting-and-verifying-your-setup/)
