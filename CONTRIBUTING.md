# Contributing to RUDI

Thank you for your interest in contributing to RUDI. This document outlines the process for contributing code, stacks, and prompts.

## Code of Conduct

We are committed to providing a welcoming and inclusive environment. Please be respectful of all contributors and maintainers.

## Getting Started

1. Fork the relevant repository
2. Clone your fork
3. Create a feature branch
4. Make your changes
5. Submit a pull request

## Contributing Code

### Setup

```bash
git clone https://github.com/your-username/cli.git
cd cli
pnpm install
```

### Style Guide

- Use ES modules (import/export)
- No semicolons (project convention)
- Use async/await for asynchronous code
- Add JSDoc comments for public APIs

### Commits

Use clear, descriptive commit messages:

```
Add support for Python runtime detection

- Add detect.command support in resolver
- Handle virtual environments
- Add tests for Python path resolution
```

### Testing

Write tests for new features:

```bash
npm test
```

All tests must pass before submission.

## Contributing Stacks

### Requirements

- Clear, specific purpose
- Valid `manifest.json` with required fields
- MCP server implementation in `node/src/` or `python/src/`
- No hardcoded secrets, API keys, passwords, or credentials

### Security Requirements

Stacks MUST declare required secrets but NEVER include actual values:

```json
{
  "requires": {
    "secrets": [
      {
        "name": "API_KEY",
        "required": true,
        "description": "Get yours at https://example.com/api-keys"
      }
    ]
  }
}
```

Users provide their own keys with `rudi secrets set API_KEY`.

### Directory Structure

```
catalog/stacks/your-stack/
├── manifest.json
└── node/src/index.ts (or python/src/server.py)
```

### Submission Process

1. Create directory under `catalog/stacks/`
2. Include all required files
3. Test locally with the RUDI CLI
4. Open pull request with clear description

## Contributing Prompts

### Requirements

- Clear, instructive content
- YAML frontmatter with metadata
- Example inputs/outputs (if applicable)

### File Structure

```
catalog/prompts/your-prompt.md
```

### Submission Process

1. Create file under `catalog/prompts/`
2. Include YAML frontmatter
3. Open pull request

## Pull Request Process

1. Update relevant documentation
2. Add tests for new functionality
3. Ensure all tests pass
4. Write clear PR description (what, why, how)
5. Reference any related issues

## Review Process

- At least one maintainer review required
- Address feedback promptly
- Updates may be requested before merge

## Questions?

- Open an issue for bugs
- Start a discussion for questions
- Check existing issues before opening new ones

## License

By contributing, you agree that your contributions will be licensed under the MIT License.
