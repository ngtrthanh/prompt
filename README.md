# prompt

Curated Claude prompts for code quality.

| Item | Where | Use |
|---|---|---|
| `CLAUDE.md` | this repo | Baseline rules — copy into each repo |
| `/code-review` | plugin `code-review` | PR review, 5 parallel agents, confidence-filtered |
| `/pr-review-toolkit:review-pr` | plugin `pr-review-toolkit` | silent-failure-hunter, pr-test-analyzer, type-design-analyzer, code-simplifier, comment-analyzer |
| `/feature-dev` | plugin `feature-dev` | 7-phase feature flow: explore → architect → review |
| security hook | plugin `security-guidance` | Warns on injection, XSS, eval, pickle, os.system on edit |
| `/hookify` | plugin `hookify` | Turn repeated mistakes into blocking hooks |
| `/commit` | plugin `commit-commands` | Commit / commit-push-pr |
| `webapp-testing` | `skills/` (Apache-2.0) | Playwright testing of local web apps |
| `frontend-design` | `skills/` (Apache-2.0) | Non-generic UI guidance |

## Install plugins (Claude Code)

```
/plugin marketplace add anthropics/claude-code
/plugin install code-review@claude-code-plugins
/plugin install pr-review-toolkit@claude-code-plugins
/plugin install feature-dev@claude-code-plugins
/plugin install security-guidance@claude-code-plugins
/plugin install hookify@claude-code-plugins
/plugin install commit-commands@claude-code-plugins
```

Plugin prompts are not copied here: `anthropics/claude-code` is "All rights reserved".

## Install skills

```
cp -r skills/* ~/.claude/skills/
```

## Sources
- [Claude prompting best practices](https://platform.claude.com/docs/en/build-with-claude/prompt-engineering/claude-prompting-best-practices)
- [anthropics/claude-code/plugins](https://github.com/anthropics/claude-code/tree/main/plugins)
- [anthropics/skills](https://github.com/anthropics/skills)
