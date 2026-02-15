# Security Policy

## Supported Versions

| Version | Supported |
|---------|-----------|
| 1.x     | Yes       |

## Reporting a Vulnerability

If you discover a security issue, please report it responsibly:

1. **Do not** open a public GitHub issue
2. Use [GitHub Security Advisories](https://github.com/rockywuest/bookend-skill/security/advisories/new) to report privately
3. Include a description of the issue and steps to reproduce

### Response Timeline

- **Acknowledgment**: Within 48 hours
- **Assessment**: Within 1 week
- **Fix**: Based on severity

## Scope

This skill instructs AI assistants to read and write files in the user's workspace (`state/`, `memory/`, `MEMORY.md`, `AGENTS.md`). Users should understand that:

- The AI assistant will create and modify files in your working directory
- State files may contain session context and decisions
- Memory files may contain summaries of your work
- No data is sent to external services — all files are local

## Best Practices

- Review `state/current.md` periodically to ensure it contains only intended information
- Add sensitive file patterns to your `.gitignore` to prevent accidental commits
- Use workspace-level permissions to control which directories the AI can access
