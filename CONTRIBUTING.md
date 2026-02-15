# Contributing to Bookend

Thank you for your interest in improving Bookend! This project is a bit different from typical open source — the "code" is primarily markdown instructions that AI assistants follow. Contributions are prose, not programs.

## Ways to Contribute

- **Templates**: Improve existing templates or add new ones for different workflows
- **Examples**: Add real-world examples showing bookend in action
- **Documentation**: Improve clarity of instructions, fix typos, add diagrams
- **Patterns**: Document new patterns or anti-patterns in `references/`
- **Bug Reports**: Report issues with the skill instructions (AI misinterprets, missing edge cases)
- **Feature Requests**: Suggest new capabilities or integrations

## Getting Started

1. Fork the repository
2. Clone your fork locally
3. Create a feature branch: `git checkout -b feat/your-feature`
4. Make your changes
5. Test with Claude Code (see Testing below)
6. Commit and push
7. Open a Pull Request

## Skill Writing Guidelines

Since contributions are instructions for AI assistants, quality matters differently than in code:

- **Be unambiguous**: Write instructions that have one clear interpretation
- **Be imperative**: "Read the state file" not "You should read the state file"
- **Be specific**: "Create `state/current.md`" not "Create a state file"
- **Test with AI**: Run your changes through Claude Code and verify the AI follows them correctly
- **Keep it lean**: The SKILL.md body should stay under 3,000 words. Move detailed content to `references/`

## Markdown Style Guide

- Use ATX-style headers (`#`, `##`, `###`)
- One blank line between sections
- Use fenced code blocks with language identifiers
- Keep lines reasonable length (no hard wrap required)
- Use relative links for internal references

## Testing

There are no unit tests — the "test" is running the skill with an AI assistant:

1. Install the plugin locally (clone into `~/.claude/plugins/cache/bookend/`)
2. Start a new Claude Code session
3. Run `/setup` and verify workspace files are created correctly
4. Test morning briefing flow
5. Test checkpoint flow
6. Test end-of-day flow
7. Verify state survives a fresh session start

## Pull Request Process

1. Fill out the PR template completely
2. Ensure markdown linting passes (CI will check)
3. Describe what you changed and why
4. If modifying SKILL.md, explain how you tested with an AI assistant
5. One approval required for merge

## Community

This project follows the [Contributor Covenant](https://www.contributor-covenant.org/version/2/1/code_of_conduct/) code of conduct. Please be respectful and constructive in all interactions.
