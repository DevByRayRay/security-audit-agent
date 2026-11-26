# Full Audit Agent

A reusable, client-independent project audit skill for AI coding agents. It covers security, correctness, accessibility, and maintainability across software stacks, with optional native adapters for OpenCode, Claude Code, and GitHub Copilot.

## Portable skill

The canonical portable skill is `.agent/skills/full-project-audit/SKILL.md`. Identical copies are included in common client skill directories:

| Client / format | Skill path | How to run |
| --- | --- | --- |
| Generic agent skill | `.agent/skills/full-project-audit/` | Load the skill and ask the agent to audit the current project. |
| Codex and compatible agents | `.agents/skills/full-project-audit/` | Ask the agent to use `$full-project-audit`, or request a full audit. |
| Claude Code | `.claude/skills/full-project-audit/` | Run `/full-project-audit`. |
| GitHub Copilot | `.github/skills/full-project-audit/` | Ask Copilot to use the `full-project-audit` skill. |
| OpenCode | `.opencode/skills/full-project-audit/` | Use `/full-audit` (command and agent adapter included). |

Copy the folder for your client into the root of the project being audited. If your client does not auto-discover skills, provide the `SKILL.md` contents as its project instructions or attach the file as context. Keep the skill text in sync with the canonical `.agent` copy when adapting it.

## Native adapters

- **OpenCode:** `.opencode/command/full-audit.md` provides `/full-audit`; `.opencode/agents/project-auditor.md` sets the auditor role.
- **Claude Code:** `.claude/agents/project-auditor.md` provides an optional named agent.
- **GitHub Copilot:** `.github/agents/project-auditor.agent.md` provides an optional custom agent.

For **ChatGPT**, use a coding client with access to the project files (such as Codex) and its skill support, or provide the skill in the conversation/project instructions. The ChatGPT web conversation alone cannot inspect a local repository unless its files are made available. For **Mistral** and other clients without a compatible skill loader, paste or attach the canonical skill as the agent's task instructions; available local tools determine whether it can inspect files or run checks.

## Run an audit

In any supported client, ask for a full audit and mention project-specific scope or report preferences. For example:

```text
Run the full-project-audit skill. Focus on the API and save the report as audit-report.md.
```

In OpenCode, use `/full-audit Focus on the API and save the report as audit-report.md`.

## Safety

Static review is the default. Active runtime testing is restricted to authorized targets and, by default, an isolated local instance with disposable data and synthetic credentials. The auditor must not probe remote systems without explicit authorization, expose or reuse secrets, or perform destructive, denial-of-service, or persistence testing. See the agent and skill instructions for the full boundaries.

## License

MIT. See [LICENSE](LICENSE).
