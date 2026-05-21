# ⌨️ Developer's Dream Corne - Layout Documentation

This document summarizes the technical logic and operational guide for the custom 42-key Corne layout.

## 🚀 Core Design Principles

### 1. Cross-Platform Finger Consistency
The primary goal is an **identical physical experience** on both macOS and Linux.
*   **The "Shortcut Finger" (Index):** Maps to `LGUI` (Cmd) on Mac and `LALT` (Zellij Prefix) on Linux.
*   **The "Tool Finger" (Middle):** Always maps to `LCTRL`. This ensures that Vim, Zellij, and terminal `Ctrl+C` (Kill) commands are in the exact same spot on every OS.

### 2. Unified Action Keys (Nav Layer)
To solve the terminal vs. browser copy/paste conflict on Linux, we use "Smart Action Keys":
*   **Hold Left Thumb (Middle) + X:** 
    *   Mac: Sends `Cmd+C`
    *   Linux: Sends `Ctrl+Insert` (Universal copy for both terminal & browser).
*   **Hold Left Thumb (Middle) + C:** 
    *   Mac: Sends `Cmd+V`
    *   Linux: Sends `Shift+Insert` (Universal paste).

### 3. German Umlaute (Vertical Combos)
Fast typing of `äöüß` using vertical combos on the base layer. **Requires OS layout to be set to "US-International".**
*   `A` + `Z` = `ä`
*   `O` + `/` = `ö`
*   `U` + `E` = `ü`
*   `S` + `C` = `ß`

---

## 🛠 Operation Guide (Layer Navigation)

| Thumb Key | Tap Action | Hold Action |
| :--- | :--- | :--- |
| **L-Outer** | `LALT` (Zellij) | `LALT` |
| **L-Middle** | `SPACE` | **NAV** (Arrows, Copy/Paste) |
| **L-Inner** | `RET` | **FN** (F1-F12, Media) |
| **R-Inner** | `RET` | **SYS** (BT, OS-Toggle) |
| **R-Middle** | `NUM` (Smart) | **NUM** (Numpad) |
| **R-Outer** | `CAPS-WORD` | **LSHIFT** |

### OS Toggle
To switch between Linux and Mac profiles:
1.  Hold **Right Thumb Inner** (SYS Layer).
2.  Press **Q** (top left).
3.  The layout toggles and persists.

---

## 🔧 Troubleshooting & Setup

### Bluetooth Reset (The "Nuclear" Option)
If pairing fails with `AuthenticationFailed`:
1.  **On PC:** `bluetoothctl` -> `remove [MAC]`.
2.  **On Keyboard:** Go to **SYS Layer** -> Press **BT_CLR** (Middle row, 2nd key from left).
3.  **Restart Bluetooth:** `sudo systemctl restart bluetooth`.
4.  **Pair again.**

### Display Configuration
The display is configured in `config/corne.conf`.
*   `CONFIG_ZMK_DISPLAY=y`
*   `CONFIG_ZMK_WIDGET_BATTERY_STATUS=y` (Shows % on left side).
*   `CONFIG_ZMK_WIDGET_OUTPUT_STATUS=y` (Shows connection status).

### Visual Layout
A visual representation is always available at `draw/corne.pdf`. To regenerate locally, use `just draw`.

---
*Last updated: Mai 2026*
