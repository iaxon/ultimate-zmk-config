# ⌨️ Corne ZMK Configuration

This repository contains a specialized ZMK firmware configuration for a 42-key Corne keyboard, optimized for developers.

## ✨ Key Features
- **Colemak-DH Base Layout** for improved ergonomics.
- **urob's Timeless Home Row Mods** for a seamless typing experience.
- **Unified Action Keys** for consistent copy/paste across macOS and Linux terminals.
- **German Umlaute** via vertical combos on the base layer.
- **Smart Mouse & Number layers** for efficient workflow.
- **OLED Support** showing layer names and battery/connection status.

## 📄 Documentation
Detailed technical principles and an operational guide can be found in:
👉 **[CORNE_LAYOUT_DOCS.md](./CORNE_LAYOUT_DOCS.md)**

---

## 🎨 How to Regenerate the Visual Keymap

If you make changes to your `config/corne.keymap`, you can update the visual diagrams (`.svg` and `.pdf`) using the following steps.

### 1. Prerequisites
You need the following tools installed on your system:
- **Python 3**
- **keymap-drawer** (Python package)
- **rsvg-convert** (from the `librsvg` package, for PDF generation)

### 2. Setup (One-time)
If you don't have a virtual environment yet, create one and install the drawer:
```bash
python3 -m venv .venv
.venv/bin/pip install keymap-drawer
```

### 3. Generate the Layout
Run the drawing command to parse your keymap and generate the files:
```bash
# Using the pre-configured virtual environment
.venv/bin/keymap -c draw/config.yaml parse -z config/corne.keymap > draw/corne.yaml
.venv/bin/keymap -c draw/config.yaml draw draw/corne.yaml -k "crkbd/rev1" > draw/corne.svg

# Convert to PDF
rsvg-convert -f pdf -o draw/corne.pdf draw/corne.svg
```

### 4. Simplified with `just` (If installed)
If you have the `just` task runner installed, simply run:
```bash
just draw
```

---

## 🚀 Building the Firmware
The firmware is automatically built via **GitHub Actions** on every push to the `main` branch.
1. Push your changes: `git push origin main`
2. Go to the **Actions** tab in your GitHub repository.
3. Download the `firmware` artifact from the latest successful run.
4. Flash both halves of your Corne.

---
*Happy Typing!*
