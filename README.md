# Claude Code dotfiles (`~/.claude`)

Portable Claude Code configuration, version-controlled so it follows me across
devices. Only curated config is tracked (see `.gitignore`); credentials, caches,
and private session transcripts are intentionally excluded.

## What's tracked
- `settings.json` — global settings (model, theme, hooks)
- `skills/`, `commands/`, `agents/`, `hooks/` — custom config (when present)
- `keybindings.json`, `CLAUDE.md` — when present
- `plugins/config.json` — enabled-plugin config (when present)

## What's NOT tracked (by design)
- `settings.local.json` — machine-specific permission rules
- `projects/` — private session transcripts (and personal memory notes)
- `plugins/marketplaces/` + `plugins/known_marketplaces.json` — re-fetchable / machine-specific
- caches, history, shell-snapshots, backups, etc.

## Set up on a new device
```sh
# Back up any existing config first, then:
git clone <repo-url> ~/.claude
```
If `~/.claude` already exists on the new machine, clone elsewhere and copy the
tracked files in, or init the existing dir against this remote.

## Reinstall plugins on a new device
Re-add marketplaces / reinstall plugins via Claude Code's plugin commands.
(The official marketplace is `anthropics/claude-plugins-official`.)
