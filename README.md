# zeep-orbit-agent-skills

Agent skill for building against [Zeep Orbit](https://github.com/zeeplabs/zeep-orbit) — REST API, MCP tools, and the 6 official client SDKs. This is for **consumers** of an Orbit app (frontend/backend integrators, or agents with MCP access to an Orbit instance) — not for working on Orbit's own internal codebase.

The skill content lives once, at [`skills/orbit-usage/SKILL.md`](skills/orbit-usage/SKILL.md) (+ `references/`), following the `SKILL.md` + frontmatter + optional `references/` shape shared by Claude Code, OpenCode, Codex CLI, and Google Antigravity. Adding future skills to this repo just means adding another `skills/<name>/SKILL.md` — every install method below picks up new skills automatically without changing anything but the flag you pass.

## Index

- [Quick install — any agent, via `npx skills`](#quick-install--any-agent-via-npx-skills)
- [Manual install, per agent](#manual-install-per-agent)
  - [Claude Code](#claude-code)
  - [OpenCode](#opencode)
  - [Codex CLI](#codex-cli)
  - [Google Antigravity](#google-antigravity)
- [What's covered](#whats-covered)
- [What's NOT covered](#whats-not-covered)
- [Contributing](CONTRIBUTING.md) · [Code of Conduct](CODE_OF_CONDUCT.md) · [Security Policy](SECURITY.md) · [License](LICENSE)

## Quick install — any agent, via `npx skills`

[`npx skills`](https://github.com/vercel-labs/skills) (Vercel Labs) auto-detects which coding agents you have installed (73+ supported, including Claude Code, OpenCode, Codex, Cursor) and wires the skill in for each with no manual config:

```bash
npx skills add zeeplabs/zeep-orbit-agent-skills
```

Prompts you to pick agents/skills if it can't auto-detect. To skip prompts and install everything for every detected agent:

```bash
npx skills add zeeplabs/zeep-orbit-agent-skills --all
```

Or target one skill / one agent explicitly (useful once this repo has more than one skill):

```bash
npx skills add zeeplabs/zeep-orbit-agent-skills --skill orbit-usage -a claude-code opencode
```

This is the recommended path — it's the only one that works the same way across Claude Code, OpenCode, Codex, and everything else `npx skills` supports, and it stays correct as skills are added/renamed in this repo.

## Manual install, per agent

Use these only if you can't run `npx`/Node in your environment.

### Claude Code

```
/plugin marketplace add zeeplabs/zeep-orbit-agent-skills
/plugin install orbit-client
```

### OpenCode

Clone this repo locally, then add to your project's `opencode.json` (or `~/.config/opencode/opencode.json` for a global install):

```json
{
  "instructions": [
    "path/to/zeep-orbit-agent-skills/skills/orbit-usage/SKILL.md"
  ]
}
```

> [Incerto] `instructions` aceita paths/globs — confirmado pela documentação do OpenCode — mas não validei essa chave exata contra um `opencode.json` real. Prefira `npx skills add` acima, que já é validado pelos mantenedores da ferramenta pra OpenCode.

### Codex CLI

Clone this repo locally (Codex does not fetch remote skills), then register `skills/orbit-usage/SKILL.md` in `~/.codex/config.toml` per your installed Codex version's skills docs.

> [Incerto] Não validei a chave TOML exata. Prefira `npx skills add` acima, que já suporta Codex nativamente.

### Google Antigravity

```bash
git clone https://github.com/zeeplabs/zeep-orbit-agent-skills /tmp/zeep-orbit-agent-skills
mkdir -p .agents/skills
cp -r /tmp/zeep-orbit-agent-skills/skills/orbit-usage .agents/skills/orbit-usage
```

Or globally under `~/.gemini/config/agents/`.

## What's covered

- REST API shape (`/{app}/auth`, `/{app}/files`, `/{app}/{table}`) — routes, filters, RLS behavior, error format
- The 6 official clients (TypeScript, Python, Go, Rust, Java, PHP) — install + basic usage each
- Wiring a frontend end-to-end to an Orbit backend app
- Using Orbit's own MCP server tools correctly (enum-column and partial-update gotchas, RLS defaults)
- Known integration gotchas

## What's NOT covered

Orbit's internal implementation (schema-per-app provisioning, dashboard backend, release process) — that's a separate, internal-only skill maintained in the `zeep-orbit` repo itself.
