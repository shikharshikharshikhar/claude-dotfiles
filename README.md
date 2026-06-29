# Claude Code dotfiles (`~/.claude`)

Portable Claude Code configuration, version-controlled so it follows me across
devices. Only curated config is tracked (see `.gitignore`); credentials, caches,
and private session transcripts are intentionally excluded.

## What's tracked
- `settings.json` — global settings (model, theme, hooks)
- `skills/`, `commands/`, `agents/`, `hooks/` — custom config (when present)
- `keybindings.json`, `CLAUDE.md` — when present
- `plugins/config.json`, `plugins/known_marketplaces.json` — plugin marketplace list

## What's NOT tracked (by design)
- `settings.local.json` — machine-specific permission rules
- `projects/` — private session transcripts (and personal memory notes)
- `plugins/marketplaces/` — re-fetchable marketplace clones
- caches, history, shell-snapshots, backups, etc.

## Set up on a new device
```sh
# Back up any existing config first, then:
git clone <repo-url> ~/.claude
```
If `~/.claude` already exists on the new machine, clone elsewhere and copy the
tracked files in, or init the existing dir against this remote.

## Reinstall plugins on a new device
Re-add marketplaces / reinstall plugins via Claude Code's plugin commands; the
tracked `known_marketplaces.json` lists which marketplaces were configured.
