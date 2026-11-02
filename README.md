# skill_vault

Skills built here for use on other machines. Nothing in this folder is loaded by Claude Code locally and nothing is
registered with tools/ctx. To install one elsewhere, copy its folder into that machine's `~/.claude/skills/` (user level)
or `<project>/.claude/skills/` (project level). Each skill is self-contained: scripts locate their own assets relative to
`SKILL.md`, so the folder can be moved as a unit.

- `user-context-harness/` — first-week setup for Claude Code: installs the tools Claude needs (no-admin routes for work laptops), then house rules and a project map (built 2026-10-31, toolchain-first refactor 2026-11-02)

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
