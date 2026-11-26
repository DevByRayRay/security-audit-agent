# Full Audit Agent

A reusable, client-independent project audit skill for AI coding agents. It covers security, correctness, accessibility, and maintainability across software stacks, with optional native adapters for OpenCode, Claude Code, and GitHub Copilot.

## Install

### Recommended: install with `skills`

Install the skill into the current project. The installer will ask which supported AI clients to configure:

```bash
npx skills add DevByRayRay/security-audit-agent --skill full-project-audit
```

Or select clients explicitly:

```bash
npx skills add DevByRayRay/security-audit-agent \
  --skill full-project-audit \
  -a codex \
  -a claude-code \
  -a github-copilot \
  -a opencode \
  -a mistral-vibe
```

To install it globally for your user instead of in the current project, add `-g`:

```bash
npx skills add DevByRayRay/security-audit-agent --skill full-project-audit -g
```

The `skills` installer requires Node.js 22.20 or later. It installs the skill files and configures the selected client's skill directory. For example, project installations commonly use `.agents/skills/`; client-specific paths may differ.

### Manual installation

If you do not use Node.js or the `skills` installer, copy the skill folder from this repository into your agent's skill directory. The portable copy is `.agents/skills/full-project-audit/`; Claude Code and GitHub Copilot-specific copies are also included below. Restart or reload the client if it does not detect new skills automatically.

### Supported client paths

The repository includes copies for common client-specific paths as well as the shared Agent Skills location:

| Client / format | Skill path | How to run |
| --- | --- | --- |
| Shared Agent Skills format (Codex and compatible agents) | `.agents/skills/full-project-audit/` | Ask the agent to use `$full-project-audit`, or request a full audit. |
| Claude Code | `.claude/skills/full-project-audit/` | Run `/full-project-audit`. |
| GitHub Copilot | `.github/skills/full-project-audit/` | Ask Copilot to use the `full-project-audit` skill. |
| OpenCode | `.opencode/skills/full-project-audit/` | Use `/full-audit` (command and agent adapter included). |
| Mistral Vibe | `.vibe/skills/full-project-audit/` | Ask Vibe to use the `full-project-audit` skill. |

For other clients, see their skill directory conventions and install the `.agents/skills/full-project-audit/` copy where supported. If a client cannot load skills, provide `SKILL.md` as its project instructions or attach it as context.

## Native adapters

- **OpenCode:** `.opencode/command/full-audit.md` provides `/full-audit`; `.opencode/agents/project-auditor.md` sets the auditor role.
- **Claude Code:** `.claude/agents/project-auditor.md` provides an optional named agent.
- **GitHub Copilot:** `.github/agents/project-auditor.agent.md` provides an optional custom agent.

For **ChatGPT**, use Codex with the skill installed, or provide the skill and project files through a ChatGPT workflow that supports them. A regular ChatGPT conversation cannot inspect a local checkout unless you make the relevant files available. Mistral Vibe is supported by the `skills` installer; other Mistral clients can use the manual instructions above when they support file context.

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
