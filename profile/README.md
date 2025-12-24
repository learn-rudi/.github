# Prompt Stack

Local-first IDE for orchestrating multiple AI models, automating complex workflows, and maintaining reproducibility.

Designed for power users who need full control over compute, data, and model selection.

## Core Capabilities

- **Multi-agent orchestration**: Run Claude, Codex, and Gemini in parallel within a single interface
- **Reproducible workflows**: Full session history, lockfiles, and audit trails for every execution
- **Local execution**: No vendor lock-in. All data stays on your machine
- **Scheduled automation**: Cron-based task scheduling with multi-step workflows
- **Terminal integration**: Shell execution with AI assistance in the same window
- **Session management**: Unified view across all AI providers and execution histories

## Getting Started

### Option 1: Command Line (Recommended for Power Users)

```bash
npm install -g @prompt-stack/cli

# Search the registry
pstack search youtube-summarizer

# Install a stack
pstack install youtube-summarizer

# Run it
pstack run youtube-summarizer --url "https://youtube.com/watch?v=..."
```

### Option 2: Desktop Application

Download Prompt Stack Studio from [Releases](https://github.com/prompt-stack/releases).

Bundles the CLI, bundled runtimes, and IDE for visual workflow design.

## The Ecosystem

| Component | Purpose | Status |
|-----------|---------|--------|
| [**cli**](https://github.com/prompt-stack/cli) | Package manager and primary interface | Production |
| [**registry**](https://github.com/prompt-stack/registry) | Community-maintained stacks and prompts | Open for contributions |
| [**runtimes**](https://github.com/prompt-stack/runtimes) | Pre-built binaries for 29+ tools and agents | Maintained |
| [**packages**](https://github.com/prompt-stack/packages) | Shared core libraries (@prompt-stack/core, @prompt-stack/runner, etc) | Maintained |
| [**releases**](https://github.com/prompt-stack/releases) | Studio installers and auto-update manifests | Current: v1.0.0-beta.8 |

## Architecture

```
┌─────────────────────────────────┐
│  Studio (Private Electron App)  │
│  IDE for visual workflows       │
└─────────────┬───────────────────┘
              │
              ▼
┌─────────────────────────────────┐
│  @prompt-stack/core             │
│  Resolver, installer, runner    │
└─────────────┬───────────────────┘
              │
              ▼
┌─────────────────────────────────┐
│  pstack CLI (npm package)       │
│  Search, install, run           │
└─────────────────────────────────┘
```

Studio and CLI share the same core libraries, ensuring consistency.

## Workflow Example

```bash
# Search for stacks that process data
pstack search "data pipeline"

# Install a stack that fetches and processes data
pstack install data-pipeline

# View what it requires
pstack info data-pipeline

# Run with inputs
pstack run data-pipeline --input '{"source":"api","format":"json"}'

# Check execution history
pstack db sessions
pstack db search "recent runs"
```

## Documentation

- [CLI Documentation](https://github.com/prompt-stack/cli) - Full command reference
- [Creating Stacks](https://github.com/prompt-stack/registry#creating-a-stack) - How to contribute
- [Supported Runtimes](https://github.com/prompt-stack/runtimes#supported-runtimes) - All 29 runtimes
- [Architecture Guide](https://github.com/prompt-stack/packages#architecture) - System design

## Contributing

Contributions are welcome in all repos:

- **New stacks or prompts**: [registry](https://github.com/prompt-stack/registry)
- **New runtimes**: [runtimes](https://github.com/prompt-stack/runtimes)
- **CLI improvements**: [cli](https://github.com/prompt-stack/cli)
- **Core libraries**: [packages](https://github.com/prompt-stack/packages)

See [CONTRIBUTING.md](./CONTRIBUTING.md) for process and guidelines.

## License

MIT License. See LICENSE file in each repository.

## Support

- Report bugs in the relevant repository
- Discuss features in [GitHub Discussions](https://github.com/prompt-stack)
- Security issues: See [SECURITY.md](./SECURITY.md)
