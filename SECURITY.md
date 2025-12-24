# Security Policy

## Reporting a Vulnerability

If you discover a security vulnerability in Prompt Stack, please do not open a public issue. Instead, email security@prompt-stack.dev with:

- Description of the vulnerability
- Steps to reproduce
- Potential impact
- Suggested fix (if any)

We will respond within 48 hours and work with you on a fix.

## Security Best Practices

### For Users

- **Keep Prompt Stack updated** - Download the latest release from [Releases](https://github.com/prompt-stack/releases)
- **Manage secrets carefully** - Secrets are stored locally; protect your `~/.prompt-stack/secrets.json`
- **Review stacks before running** - Understand what code you're executing
- **Use strong authentication** - Protect access to your API keys and credentials

### For Contributors

- **No secrets in code** - Never commit API keys, tokens, or passwords
- **Validate inputs** - Always validate user input before processing
- **Use secure libraries** - Keep dependencies updated
- **Avoid shell injection** - Use safe APIs for command execution
- **Encrypt sensitive data** - Use encryption for secrets at rest

## Security Features

### Secrets Management

- Secrets are stored locally in `~/.prompt-stack/secrets.json`
- Can be encrypted using OS keychain (macOS, Windows)
- Never sent to servers (local-first design)
- Stacks declare what secrets they need; users provide values

### Session Management

- All execution sessions are logged to local SQLite database
- Session history is stored locally, never uploaded
- Full audit trail of who ran what, when, with which inputs

### Runtime Isolation

- Stacks run with explicit runtime dependencies declared
- Lockfiles ensure reproducible execution environments
- No automatic downloads or execution of untrusted code

## Known Limitations

- **No code signing** (planned for future releases)
- **No sandboxing** for stack execution (runs with user privileges)
- **Windows support** not yet available

## Responsible Disclosure

We appreciate security researchers who responsibly disclose vulnerabilities. Please:

1. Report via email (not GitHub issues)
2. Give us time to fix (30 days minimum)
3. Don't publicly disclose until we release a fix
4. Provide clear reproduction steps

## Security Updates

Security updates are released as patches. Subscribe to releases at:

https://github.com/prompt-stack/releases

## Third-Party Security

Prompt Stack depends on several open-source projects. We keep these updated regularly. Report third-party vulnerabilities to their respective projects.

## Legal

- We do not warrant the security of Prompt Stack
- Use at your own risk
- Follow your organization's security policies

## Questions?

For security questions, email security@prompt-stack.dev
