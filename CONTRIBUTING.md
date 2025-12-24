# Contributing to Prompt Stack

Thank you for your interest in contributing to Prompt Stack. This document outlines the process for contributing code, stacks, and prompts.

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
git clone https://github.com/your-username/prompt-stack.git
cd prompt-stack
npm install
```

### Style Guide

- Use TypeScript for new code
- Follow existing code style (use `npm run lint`)
- Write meaningful variable and function names
- Add comments for complex logic

### Commits

Use semantic commit messages:

```
feat: Add new feature
fix: Fix a bug
refactor: Reorganize code
docs: Update documentation
test: Add or update tests
chore: Maintenance tasks
```

Example:

```
feat: Add pstack secrets command

- Implement secrets set/list/remove commands
- Add encryption for stored secrets
- Update CLI documentation
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
- Valid `stack.yaml` manifest
- Prompt file with clear instructions
- Example usage with expected output
- **CRITICAL: No hardcoded secrets, API keys, passwords, or credentials**

### Security Requirements

Stacks MUST declare required secrets but NEVER include actual values:

**❌ DO NOT DO THIS:**
```yaml
secrets:
  - name: OPENAI_API_KEY
    value: sk-abc123xyz789  # NEVER include actual keys!
```

**✅ DO THIS INSTEAD:**
```yaml
secrets:
  - name: OPENAI_API_KEY
    required: true
    description: "OpenAI API key (get from https://platform.openai.com/api-keys)"
```

Users will provide their own key locally with `pstack secrets set OPENAI_API_KEY`.

### Directory Structure

```
packages/stacks/your-stack/
├── stack.yaml
├── prompt.md
├── example.input (optional)
└── example.output (optional)
```

### Stack Manifest

Minimal example:

```yaml
id: your-stack
kind: stack
name: Your Stack
version: 1.0.0
description: What this stack does

requires:
  runtimes: [node]

inputs:
  - name: input_file
    type: path
    required: true

outputs:
  - name: result
    type: string

entrypoint: process.js
```

### Submission Process

1. Create directory under `packages/stacks/`
2. Include all required files
3. Test locally: `pstack install ./packages/stacks/your-stack`
4. Open pull request with clear description

## Contributing Prompts

### Requirements

- Clear, instructive content
- Follows markdown formatting
- Includes example inputs/outputs (if applicable)
- No hardcoded values or API keys

### File Structure

```
packages/prompts/your-prompt/
└── prompt.md
```

### Submission Process

1. Create directory under `packages/prompts/`
2. Include `prompt.md` file
3. Open pull request

## Pull Request Process

1. Update relevant READMEs
2. Add tests for new functionality
3. Ensure all tests pass: `npm test`
4. Ensure code is linted: `npm run lint`
5. Write clear PR description (what, why, how)
6. Reference any related issues

### PR Description Template

```markdown
## What
Brief description of changes

## Why
Motivation for these changes

## How
Technical approach taken

## Testing
How to test these changes

## Checklist
- [ ] Tests pass
- [ ] Code is linted
- [ ] Documentation updated
- [ ] No secrets or sensitive data included
```

## Review Process

- At least one maintainer review required
- Address feedback promptly
- Be respectful of reviewer comments
- Updates may be requested before merge

## Running Tests

```bash
# All tests
npm test

# Single package
npm test -- --filter=@prompt-stack/core

# Watch mode
npm test -- --watch
```

## Linting

```bash
# Check code style
npm run lint

# Fix issues automatically
npm run lint -- --fix
```

## Building

```bash
# Build all packages
npm run build

# Build single package
npm run build -- --filter=@prompt-stack/core
```

## Questions?

- Open an issue for bugs
- Start a discussion for questions
- Check existing issues before opening new ones

## License

By contributing, you agree that your contributions will be licensed under the MIT License.

## Recognition

Contributors are recognized in:

- Repository CONTRIBUTORS file
- Release notes for significant contributions
- GitHub "contributors" page

Thank you for making Prompt Stack better!
