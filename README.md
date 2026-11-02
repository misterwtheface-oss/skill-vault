# skill_vault

Skills built here for use on other machines, and the local skill vault. Nothing in this folder is installed in Claude
Code's skill folders, so no skill here costs tokens at session start. Locally, `tools/ctx` routes them: on each prompt the
ctx hook scores the prompt against each skill's `keywords:` frontmatter and surfaces only the skills that clear the
threshold, as a pointer to their `SKILL.md` (`python tools/ctx/ctx.py skills` lists them). The pattern is for anyone with
many skills: at work, with around 150, it keeps the startup list short. To install one elsewhere as a normal skill, copy
its folder into that machine's `~/.claude/skills/` (user level) or `<project>/.claude/skills/` (project level); to vault it
there instead, see `user-context-harness/references/skill-vault.md`. Each skill is self-contained: scripts locate their
own assets relative to `SKILL.md`, so the folder can be moved as a unit.

- `user-context-harness/` — first-week setup for Claude Code: installs the tools Claude needs (no-admin routes for work laptops), then house rules and a project map (built 2026-10-31, toolchain-first refactor 2026-11-02). Also published standalone at https://github.com/misterwtheface-oss/user-context-harness (this folder is the source;
  publish with `git subtree push --prefix=user-context-harness https://github.com/misterwtheface-oss/user-context-harness.git main`
  from inside `skill_vault/` after committing here)

## Install from this repo (another machine)

With git, in PowerShell:

```powershell
git clone https://github.com/misterwtheface-oss/skill-vault "$env:TEMP\skill-vault"
New-Item -ItemType Directory -Force "$env:USERPROFILE\.claude\skills" | Out-Null
Copy-Item "$env:TEMP\skill-vault\user-context-harness" "$env:USERPROFILE\.claude\skills\" -Recurse -Force
```

Mac / Linux:

```bash
git clone https://github.com/misterwtheface-oss/skill-vault /tmp/skill-vault
mkdir -p ~/.claude/skills && cp -r /tmp/skill-vault/user-context-harness ~/.claude/skills/
```

Without git: download `https://github.com/misterwtheface-oss/skill-vault/archive/refs/heads/main.zip`, unzip it, and
copy the skill folder into `~/.claude/skills/`. If only a browser is allowed, Claude Code on that machine can be pointed
at the raw files (for example `https://raw.githubusercontent.com/misterwtheface-oss/skill-vault/main/user-context-harness/SKILL.md`)
and asked to recreate the folder locally, file by file.
