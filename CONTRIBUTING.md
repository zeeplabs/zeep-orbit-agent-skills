# Contributing

## Adding or updating a skill

- One skill = one directory: `skills/<name>/SKILL.md` (+ optional `references/`). This is the layout `npx skills` and Claude Code both discover, so don't nest skills any deeper (e.g. no `plugins/<x>/skills/<name>`) or `npx skills add` won't find it.
- `SKILL.md` frontmatter needs `name` (matches the directory, kebab-case) and `description` (specific enough that an agent picks it for the right task — see the existing `skills/orbit-usage/SKILL.md` for the pattern).
- Keep `SKILL.md` itself short — it should route to `references/*.md` by topic, not contain everything inline. Agents load `SKILL.md` on every match; they load a reference file only when that topic is actually needed.
- **No invented facts.** Every claim about Zeep Orbit's API, MCP tools, or SDKs must be verifiable against the [zeep-orbit](https://github.com/zeeplabs/zeep-orbit) source or its own docs — cite the mechanism you checked in your PR description. If something can't be verified, mark it `[Incerto]` in the text rather than stating it as fact.
- If you add a new skill to `.claude-plugin/marketplace.json`'s `plugins` array, keep `source` as `"."` (this repo is a single Claude Code plugin containing all skills under `skills/`) unless you have a concrete reason to split it into multiple plugins.

## Testing your change

- `npx skills add zeeplabs/zeep-orbit-agent-skills --skill <name>` against your local clone (or a branch) to confirm the agent(s) you use actually pick it up.
- For the Claude Code path: `/plugin marketplace add <path-to-your-local-clone>` then `/plugin install orbit-client`.

## Pull requests

Open a PR against `main`. Describe what changed and why (a doc fix, a new skill, an SDK version bump reflected in a reference) — no other process beyond review.
