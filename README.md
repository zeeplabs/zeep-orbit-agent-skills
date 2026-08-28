# zeep-orbit-agent-skills

Agent skill for building against [Zeep Orbit](https://github.com/zeeplabs/zeep-orbit) — REST API, MCP tools, and the 6 official client SDKs. This is for **consumers** of an Orbit app (frontend/backend integrators, or agents with MCP access to an Orbit instance) — not for working on Orbit's own internal codebase.

The skill content lives once, at [`plugins/orbit-client/skills/orbit-usage/SKILL.md`](plugins/orbit-client/skills/orbit-usage/SKILL.md) (+ `references/`), following the `SKILL.md` + frontmatter + optional `scripts/`/`references/` shape that Claude Code, OpenCode, Codex CLI, and Google Antigravity all read natively. Installation differs per agent since none of them share a common installer yet — pick your agent below.

## Claude Code

```
/plugin marketplace add zeeplabs/zeep-orbit-agent-skills
/plugin install orbit-client
```

## OpenCode

Add to your project's `opencode.json` (or `~/.config/opencode/opencode.json` for a global install):

```json
{
  "instructions": [
    "path/to/zeep-orbit-agent-skills/plugins/orbit-client/skills/orbit-usage/SKILL.md"
  ]
}
```

Clone this repo (or add it as a submodule) somewhere local first, then point the path above at your clone.

> [Incerto] `instructions` aceita paths/globs — confirmado pela documentação do OpenCode — mas não validei a chave exata acima contra um `opencode.json` real. Confira `opencode docs rules` no seu ambiente antes de assumir a sintaxe.

## Codex CLI

Codex reads skills registered in `~/.codex/config.toml`, pointing at a local `SKILL.md` path with an enabled flag. Clone this repo locally first (Codex does not fetch remote skills), then register it — check `codex --help` / the Codex skills docs in your installed version for the exact TOML key names, since this repo's authors have not validated the literal syntax end-to-end.

> [Incerto] Não testei o registro real em `config.toml` — a documentação da OpenAI descreve o mecanismo (path pro `SKILL.md` + flag de habilitação) mas não achei um exemplo literal de chave TOML pra copiar com confiança.

## Google Antigravity

Copy (or symlink) the skill folder into your project's `.agents/skills/` directory:

```bash
git clone https://github.com/zeeplabs/zeep-orbit-agent-skills /tmp/zeep-orbit-agent-skills
mkdir -p .agents/skills
cp -r /tmp/zeep-orbit-agent-skills/plugins/orbit-client/skills/orbit-usage .agents/skills/orbit-usage
```

Or globally under `~/.gemini/config/agents/` to make it available across all your projects.

## What's covered

- REST API shape (`/{app}/auth`, `/{app}/files`, `/{app}/{table}`) — routes, filters, RLS behavior, error format
- The 6 official clients (TypeScript, Python, Go, Rust, Java, PHP) — install + basic usage each
- Wiring a frontend end-to-end to an Orbit backend app
- Using Orbit's own MCP server tools correctly (enum-column and partial-update gotchas, RLS defaults)
- Known integration gotchas

## What's NOT covered

Orbit's internal implementation (schema-per-app provisioning, dashboard backend, release process) — that's a separate, internal-only skill maintained in the `zeep-orbit` repo itself.
