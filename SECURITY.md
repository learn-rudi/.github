# Security Policy

## Supported Versions

| Version | Supported          |
| ------- | ------------------ |
| 1.x.x   | Yes                |
| < 1.0   | No                 |

## Reporting a Vulnerability

If you discover a security vulnerability in RUDI, please do not open a public issue. Instead, contact the maintainers directly with:

- Description of the vulnerability
- Steps to reproduce
- Potential impact
- Suggested fix (if any)

We will respond within 48 hours and work with you on a fix.

## Security Model

### Secret Storage

RUDI stores secrets in `~/.rudi/secrets.json` with file permissions `0600` (owner read/write only). This follows the same security model used by:

- SSH (`~/.ssh/`)
- AWS CLI (`~/.aws/credentials`)
- GitHub CLI (`~/.config/gh/`)

Secrets are:
- Never written to agent configuration files
- Never exposed in process listings
- Never logged or transmitted
- Injected as environment variables only at runtime

### npm Package Installation

By default, RUDI installs npm packages with `--ignore-scripts` to prevent arbitrary code execution during installation. Users must explicitly opt-in with `--allow-scripts` for packages that require lifecycle scripts.

### Shim Isolation

Each package installs to its own isolated directory. Shims are thin wrapper scripts that:
- Set up the correct environment
- Delegate to the actual binary
- Prevent packages from interfering with each other

## Security Best Practices

### For Users

- **Keep RUDI updated** - Run `npm update -g @learnrudi/cli` regularly
- **Review packages before installing** - Check the registry for package details
- **Protect your secrets file** - Ensure `~/.rudi/secrets.json` has mode 0600
- **Use --allow-scripts sparingly** - Only enable scripts for trusted packages

### For Contributors

- **No secrets in code** - Never commit API keys, tokens, or passwords
- **Validate inputs** - Always validate user input before processing
- **Use secure libraries** - Keep dependencies updated
- **Avoid shell injection** - Use safe APIs for command execution

## Registry Security

The registry must never contain API keys, tokens, or credentials. All secrets are:

- Declared in stack manifests under `requires.secrets`
- Stored locally by users
- Injected at runtime by the RUDI CLI

## Responsible Disclosure

We appreciate security researchers who responsibly disclose vulnerabilities. Please:

1. Report directly to maintainers (not GitHub issues)
2. Give us time to fix (30 days minimum)
3. Don't publicly disclose until we release a fix
4. Provide clear reproduction steps

## Scope

This security policy covers:
- The RUDI CLI (`@learnrudi/cli`)
- The official package registry (`learn-rudi/registry`)
- Associated npm packages (`@learnrudi/*`)

Third-party MCP stacks have their own security policies.
