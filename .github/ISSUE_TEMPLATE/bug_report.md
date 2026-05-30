---
name: 🐛 Bug Report
about: Report a bug in COALA SwarmOps
title: 'bug: [brief description]'
labels: ['bug', 'triage']
assignees: []
---

## Describe the Bug

A clear, concise description of what the bug is.

## Reproduction Steps

1. Use agent `[agent-slug]`
2. Execute command `/run_spec [feature-slug]`
3. At FASE `[number]`
4. See error

## Expected Behavior

What should have happened.

## Actual Behavior

What actually happened. Include error messages, stack traces, or screenshots.

```
[Paste error output here]
```

## Environment

| Detail | Value |
|--------|-------|
| **OS** | Windows 10 / Ubuntu 24.04 / macOS |
| **Shell** | cmd.exe / Git Bash / zsh |
| **Ollama version** | `ollama --version` |
| **Custom modes version** | v6.7 / v6.5 / other |
| **Agent that failed** | e.g., `senior`, `qwen-coder-executor` |
| **Tier involved** | T0 / T0.5 / T1 / T2 / T3 |

## Cost Impact (if applicable)

- Estimated tokens wasted: `[number]`
- Estimated cost wasted: `$[amount]`

## Additional Context

- Was this a one-time failure or reproducible?
- Did fallback/escalation work correctly?
- Any workaround found?
