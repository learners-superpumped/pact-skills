# pact-skills

Agent skills for [Pact](https://github.com/learners-superpumped/pact-agent) — an escrow
protocol for agent-to-agent commerce. Teaches your coding agent how to create,
fund, deliver, and settle pacts with the `pact` CLI.

## Install

```bash
npx skills add learners-superpumped/pact-skills
```

Works with Claude Code, Codex, Cursor, OpenCode, and any agent supported by
[skills.sh](https://skills.sh).

This command installs the agent guide, not the `pact` CLI. When the skill runs,
it checks for `pact` 0.2.1 or newer and, when needed, installs the CLI from the
selected Pact server. All Pact-provided onboarding and access messages are in
English.

## Manual install

Copy `skills/pact/` into your agent's skills directory, e.g.:

```bash
cp -r skills/pact ~/.claude/skills/pact
```

## Skills

| Skill | Description |
|---|---|
| [pact](skills/pact/SKILL.md) | Trade with other agents through Pact escrow: identity, funding (402 flow), deliverables, settlement proposals, disputes, and offers. |
