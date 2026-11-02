# Agent guide

This file maps the mand repository: git@tangled.org:crooy.tngl.sh/mand (canonical, mirrored at github.com/crooy/mand). It is a lean fork of [ayghri/i-have-adhd](https://github.com/ayghri/i-have-adhd) merged with compression mechanics from [JuliusBrussee/caveman](https://github.com/JuliusBrussee/caveman) — see README Credits. The canonical skill rules live in `skills/mand/SKILL.md`; this file does not replace them.

## Start here

1. Read `README.md` for the purpose and user-facing behavior.
2. Read `INSTALL.md` for installation paths and platform-specific setup.
3. Read `skills/mand/SKILL.md` for the canonical skill behavior.

## Repository map

| Area | Location | Purpose |
| --- | --- | --- |
| Canonical skill | `skills/mand/SKILL.md` | The source of truth for the 13 mand response rules (10 English always, 11 diagrams over words, 13 fewer words). |
| Skill mirror | `.cursor/skills/mand/SKILL.md` | Cursor-compatible copy; keep it byte-identical with the canonical skill. |
| Gemini inline copy | `skills/mand/agents/gemini.toml` | Self-contained Gemini command; keep rules aligned with SKILL.md. |
| Shared hooks | `hooks/hooks.json`, `hooks/always-on.*` | Always-on hook declarations; flag file `.mand-always`. |
| Plugin manifests | `.claude-plugin/`, `.codex-plugin/`, `plugin.json`, `package.json` | Claude Code, Codex, Pi/OMP plugin metadata. |
| OpenCode | `.opencode/` | Auto-discovered plugin and command entry points. |
| Documentation | `README.md`, `INSTALL.md` | User-facing overview and installation. |

## Conventions

- Change `skills/mand/SKILL.md` first when changing skill behavior, then synchronize the `.cursor` mirror (byte-identical, verified with `cmp`).
- 13 rules, fixed numbering. README and always-on blocks (INSTALL.md) must match the rule count and wording; translated block wording must stay in the block's file language.
- No tests or eval harness remain in this fork (pruned from upstream); verify prose changes by reading every carrier and running `grep -c "^13\."`-style count checks across install blocks.
- No CONTRIBUTING.md, no evals, no translation dirs: this is a personal fork; changes are made directly.

## Attribution

Original i-have-adhd by Ayoub Ghriss (MIT); caveman compression mechanics by Julius Brussee (Apache-2.0). Keep both attributions intact in README.md Credits and LICENSE when editing.