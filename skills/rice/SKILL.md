---
name: rice
description: Make and safely apply desktop/ricing changes on this Arch + Hyprland T2 MacBook — status bar (ags shell), eww widgets, Hyprland config/keybinds, wallpaper theming, lock screen, wlogout, audio routing. Use for any tweak to the Hyprland desktop, bar, theme, or related configs.
---

# Hyprland rice-change workflow

Linux-only (T2 MacBook Pro 2019, Arch + Hyprland, Tokyo Night). Run this loop for **every** change
so the setup doesn't drift and memory stays accurate.

## 1. Locate — verify against memory, then the filesystem (memory can be stale)
- **Hyprland config**: `~/.config/hypr/hyprland.lua`, run by a compiled `start-hyprland` (embedded
  Lua; binds show as `__lua N`). **There is no `hyprland.conf` — never edit or create one.**
- **Status bar**: ags / Astal **GTK4** shell at `~/.config/ags` (TSX + SCSS). ags is also the
  **notification daemon** (mako was dropped).
- **eww**: `~/.config/eww` is kept only as rollback — the live bar is ags.
- **Theming**: wallpaper → colors via wallrizz (`wallrizz-reload`); swww's package is `awww`.
- **Lock screen**: `qs -c lock` (Quickshell, replaced hyprlock). **Wallpaper picker**: Super+Shift+P.
- Skim `memory/MEMORY.md` for the current truth before assuming anything.

## 2. Edit the relevant config.

## 3. Apply — don't tell the user to log out / restart the session
- Hyprland: `hyprctl reload`.
- ags: restart the shell (`ags run -d ~/.config/ags`, killing the old instance) and **watch stdout
  for TS/bundle errors** — a silent type error means the bar won't load.
- eww (only if touched): `eww reload`.
- Theme: trigger `wallrizz-reload`.

## 4. Verify visually — never claim "done" without looking
- Screenshot with `grim` and actually inspect it: one bar (no duplicate eww/ags), icons render,
  dropdowns sit directly under their item, theme applied.

## 5. Update memory if behavior changed
- Changed the bar framework, a keybind, daemon ownership, the theming path, etc.? Update the
  matching memory note **and** its MEMORY.md index line. (The bar note was once wrong — still said
  eww after the switch to ags.)

## Known gotchas (full detail in memory)
- **Battery dropdown shows "—"**: `AstalBattery.get_default()` returns UPower's DisplayDevice
  (voltage/temp/capacity/cycles all 0). Use the real `BAT0` power-supply device.
- **ags = notif daemon**: notifications drop during any ags restart/crash.
- **Stuck notification popup**: a gtk4-layer-shell window keeps its last buffer when the box empties
  — bind the window `visible` to popup-count so it unmaps.
- **eww boot panic**: future-dated `~/.cache/eww` log mtimes (T2 RTC jumps) kill the daemon at
  startup — rm the logs + enable NTP.
