# Full Audit for OpenCode

A reusable OpenCode command, auditor agent, and skill for structured security, quality, accessibility, and documentation reviews across software stacks.

## Contents

- `.opencode/command/full-audit.md` — invoke with `/full-audit`.
- `.opencode/agents/project-auditor.md` — auditor role and safety boundaries.
- `.opencode/skills/full-project-audit/SKILL.md` — six-phase audit workflow and report format.

## Install in a project

Copy the `.opencode` directory into the root of your project. Restart OpenCode so it loads the command, agent, and skill. Then run:

```text
/full-audit
```

Add project-specific scope or report preferences after the command, for example:

```text
/full-audit Focus on the API and save the report as audit-report.md
```

## Safety

Static review is the default. Active runtime testing is restricted to authorized targets and, by default, an isolated local instance with disposable data and synthetic credentials. The auditor must not probe remote systems without explicit authorization, expose or reuse secrets, or perform destructive, denial-of-service, or persistence testing. See the agent and skill instructions for the full boundaries.

## License

MIT. See [LICENSE](LICENSE).
