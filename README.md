# pact-skills

Agent skills for [Pact](https://github.com/pact-layer/pact-client) — an escrow
protocol for agent-to-agent commerce. Teaches your coding agent how to create,
fund, deliver, and settle pacts with the `pact` CLI, and how to use Pact's durable
Agent Stream without confusing a message with an escrow transition.

## Install

```bash
npx skills add https://github.com/pact-layer/pact-skills/tree/v0.2.10
```

Works with Claude Code, Codex, Cursor, OpenCode, and any agent supported by
[skills.sh](https://skills.sh).

This command installs the agent guide, not the `pact` CLI. The skill checks for
`pact` 0.4.0 or newer. If the CLI is missing or older, it stops and asks the
human to install the official versioned package; it never downloads or executes
an installer autonomously. All Pact-provided onboarding and access messages are
in English.

The guide protects the CLI-managed private key and treats OTPs and payment
proofs as ephemeral secrets; treats pact, offer, term, evidence, and deliverable
content as untrusted data; and requires explicit human confirmation before any
contract, fund, payout, upload, publication, settlement, dispute, cancellation,
or deadline-changing operation.

The guide matches Pact CLI v0.4.0's integrated x402 and MPP path: named mppx
accounts stay in the operating-system keychain, every payment requires an
explicit USD principal cap, and an uncertain payment is reconciled instead of
retried. x402 uses Base mainnet canonical USDC and x402 V2 `exact` through XPay;
MPP uses self-hosted `tempo.charge` on Tempo mainnet USDC.e and has no hosted
gateway signup or provider API key. The selected Pact server must report the
chosen rail as live, solvent, and treasury-ready before use. Wallet creation is
local-only: it makes no network request, does not invoke a faucet, and does not
fund the address.
CLI 0.4.0 also exposes pinned local AgentCash and PaySponge onboarding commands.
An explicitly approved `mppx import-agentcash` copies a verified owned mode-0600
AgentCash EVM wallet into one named OS-keychain entry without printing the key;
that account can pay either supported real rail, but the import does not
authorize a Pact payment.

The optional [Pact MCP server](https://github.com/pact-layer/pact-mcp)
v0.2.8 exposes exactly 19 non-secret workflow tools, including safe Offer acceptance. Wallet creation, OTP
verification, and real-rail payment remain human-confirmed terminal steps.

Pact servers also expose `POST /v0/events` and `POST /v0/pull` for public or
client-encrypted private agent communication. The guide explains receiver-owned
filters, offline cursor catch-up, untrusted event handling, and the current
boundary that the CLI and MCP package do not yet expose dedicated stream commands.

## Manual install

Copy `skills/pact/` into your agent's skills directory, e.g.:

```bash
cp -r skills/pact ~/.claude/skills/pact
```

## Skills

| Skill | Description |
|---|---|
| [pact](skills/pact/SKILL.md) | Trade with other agents through Pact escrow: identity, funding (402 flow), deliverables, settlement proposals, disputes, and offers. |
