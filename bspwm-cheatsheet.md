# bspwm + sxhkd Keybindings Cheat Sheet

![bspwm](https://img.shields.io/badge/Window_Manager-bspwm-1f1f1f?style=flat&logo=linux&logoColor=white)
![sxhkd](https://img.shields.io/badge/Hotkeys-sxhkd-1f1f1f?style=flat&logo=linux&logoColor=white)
![Linux](https://img.shields.io/badge/OS-Linux-1793d1?style=flat&logo=linux&logoColor=white)

Well-organized and feature-rich keybindings for **bspwm** using **sxhkd**.

To use: place the contents in `~/.config/sxhkd/sxhkdrc` (or symlink it).

Reload anytime with **Super + Escape**

---

## Most Used (Memorize These)

| Keybinding                  | Action                              |
|-----------------------------|-------------------------------------|
| `Super + Enter`             | Open terminal (Alacritty)           |
| `Super`                     | Application launcher (rofi/dmenu)   |
| `Super + F`                 | Toggle fullscreen                   |
| `Super + Space`             | Toggle tiled ↔ floating             |
| `Super + C`                 | Close focused window                |
| `Super + 1–8`               | Switch to workspace 1–8             |
| `Super + Shift + 1–8`       | Send window to workspace 1–8        |
| `Super + ←→↑↓`              | Focus window directionally          |
| `Super + Shift + ←→↑↓`      | Swap windows directionally          |
| `Print`                     | Screenshot (full screen)            |
| `Super + Print`             | Screenshot (select area)            |

---

## Full Reference

### Applications
| Keybinding                  | Action                         |
|-----------------------------|--------------------------------|
| `Super + Enter`             | Terminal (Alacritty)           |
| `Super + Shift + Enter`     | Floating terminal              |
| `Super + Alt + Enter`       | Fullscreen terminal            |
| `Super + Shift + F`         | File manager (Thunar)          |
| `Super + Shift + E`         | Text editor (Geany)            |
| `Super + Shift + W`         | Web browser (Firefox)          |

### Launchers & Applets
| Keybinding       | Action                         |
|------------------|--------------------------------|
| `Super`          | Application launcher           |
| `Alt + F1`       | Application launcher           |
| `Alt + F2`       | Run command                    |
| `Super + N`      | Network manager applet         |
| `Super + B`      | Bluetooth applet               |
| `Super + M`      | Music player applet            |
| `Super + X`      | Powermenu                      |
| `Super + S`      | Screenshot applet              |
| `Super + R`      | Run apps as root               |
| `Super + T`      | Theme switcher                 |
| `Super + W`      | Window rules applet            |

### Screenshots & Hardware
| Keybinding                  | Action                                   |
|-----------------------------|------------------------------------------|
| `Print`                     | Screenshot now                           |
| `Alt + Print`               | Screenshot in 5s                         |
| `Shift + Print`             | Screenshot in 10s                        |
| `Ctrl + Print`              | Screenshot active window                 |
| `Super + Print`            | Screenshot selected area                 |
| `XF86Audio*` / `XF86MonBrightness*` | Volume, mute, brightness, media keys |

### Workspaces
| Keybinding                        | Action                              |
|-----------------------------------|-------------------------------------|
| `Super + 1–8`                     | Go to workspace                     |
| `Super + Shift + 1–8`             | Send window to workspace            |
| `Ctrl + Alt + ←/→`                | Previous / Next workspace           |
| `Super + Ctrl + Shift + ←/→`      | Send to prev/next workspace         |

### Window Management
| Keybinding                          | Action                                      |
|-------------------------------------|---------------------------------------------|
| `Super + C`                         | Close window                                |
| `Super + Shift + C`                 | Kill window                                 |
| `Super + Shift + H`                 | Hide/Unhide window                          |
| `Super + ←→↑↓`                      | Focus directionally                         |
| `Super + Shift + ←→↑↓`              | Swap windows                                |
| `Super + Alt + Shift + ←→↑↓`        | Move floating window                        |
| `Super + Ctrl + ←→↑↓`               | Expand tiled window                         |
| `Super + Alt + ←→↑↓`                | Shrink tiled window                         |
| `Super + H/V/Q`                     | Preselect horizontal / vertical / cancel    |
| `Super + Ctrl + 1–9`                | Preselect split ratio                       |
| `Super + L`                         | Toggle tiled ↔ monocle                      |
| `Super + F`                         | Toggle fullscreen                           |
| `Super + Space`                     | Toggle floating ↔ tiled                     |
| `Super + Shift + Space`             | Toggle pseudo-tiled                         |
| `Super + Ctrl + M/X/Y/Z`            | Marked / Locked / Sticky / Private flags    |
| `Alt + Tab`                         | Cycle windows (incl. floating)              |

### Window Manager Control
| Keybinding             | Action                |
|------------------------|-----------------------|
| `Ctrl + Shift + R`     | Restart bspwm         |
| `Ctrl + Shift + Q`     | Quit bspwm            |
| `Super + Escape`       | Reload sxhkd (keybinds) |

### Miscellaneous
| Keybinding               | Action                         |
|--------------------------|--------------------------------|
| `Ctrl + Alt + V/R/H/M`   | vim │ vim │ ranger │ htop │ ncmpcpp |
| `Ctrl + Alt + L`         | Lock screen                    |
| `Super + P`              | Color picker                   |
| `Ctrl + Alt + Escape`    | xkill (click to kill)          |

---

## Optional Enhancements (Recommended)

Add these to your `sxhkdrc` if you want even more power:

```bash
# Monitor focus/swap
super + {_,shift + }comma   focus {previous,next} monitor
super + {_,shift + }period  send window to {previous,next} monitor

# Gaps control
super + minus               gaps inner -= 5
super + equal               gaps inner += 5
super + shift + minus       bspc config window_gap 0
super + shift + equal       bspc config window_gap 10   # or your default

# Layout utilities
super + r                   bspc desktop -l next      # rotate tiled ↔ monocle
super + shift + r   bspc node -R 90     # rotate layout 90°

# Floating window resize with mouse
super + button3     resize floating window (hold & drag)

# Always backup before editing
cp ~/.config/sxhkd/sxhkdrc ~/.config/sxhkd/sxhkdrc.bak

# Reload keybindings instantly
super + Escape
