# RUDI

Universal tool manager for MCP stacks, CLI tools, runtimes, and AI coding agents.

RUDI provides a single interface to install, configure, and run Model Context Protocol (MCP) servers with Claude, Codex, Gemini, and other AI agents.

## What RUDI Does

- **Install MCP stacks** - Add tools like Slack, Notion, Google Workspace to your AI agents
- **Manage runtimes** - Install Node.js, Python, Deno, Bun without system-wide changes
- **Handle secrets** - Secure credential storage with automatic injection
- **Integrate agents** - Configure Claude, Codex, and Gemini with one command

## Getting Started

```bash
npm install -g @learnrudi/cli

# Search the registry
rudi search slack

# Install a stack
rudi install slack

# Set required secrets
rudi secrets set SLACK_BOT_TOKEN

# Integrate with Claude
rudi integrate claude
```

## The Ecosystem

| Repository | Purpose |
|------------|---------|
| [**cli**](https://github.com/learn-rudi/cli) | Command-line tool manager |
| [**registry**](https://github.com/learn-rudi/registry) | Official package registry |
| [**studio**](https://github.com/learn-rudi/studio) | Desktop application |

## Available Packages

**MCP Stacks:** slack, notion-workspace, google-workspace, google-ai, openai, whisper, video-editor, content-extractor, postgres, sqlite, and more

**Runtimes:** node, python, deno, bun, ollama

**Agents:** claude, codex, gemini, copilot

## How It Works

```
rudi install slack
     │
     ├─► Downloads stack from registry
     ├─► Installs dependencies
     └─► Creates shim in ~/.rudi/bin/

rudi secrets set SLACK_BOT_TOKEN
     │
     └─► Stores in ~/.rudi/secrets.json (mode 0600)

rudi integrate claude
     │
     └─► Updates Claude config with MCP server entry
```

## Documentation

- [CLI Documentation](https://github.com/learn-rudi/cli) - Installation and command reference
- [Registry](https://github.com/learn-rudi/registry) - Available packages and contribution guide
- [Creating Stacks](https://github.com/learn-rudi/registry#creating-a-stack) - Build your own MCP servers

## Contributing

Contributions welcome:

- **New stacks or prompts**: [registry](https://github.com/learn-rudi/registry)
- **CLI improvements**: [cli](https://github.com/learn-rudi/cli)

See CONTRIBUTING.md in each repository.

## License

MIT
