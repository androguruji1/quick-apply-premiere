# Quick Apply for Premiere Pro

Spotlight-style search for Adobe Premiere Pro. Press **⌥ Space**, type an effect, transition or one of your own saved presets, and press **↩** to apply it to the selected clips. Any result can get its own keyboard shortcut in two keystrokes.

**[⬇ Download the latest version](https://github.com/androguruji1/quick-apply-premiere/releases/latest)** · free for 14 days · **[Buy a license](https://superprofile.bio/androguruji)**

> The source code is private. This repository describes what Quick Apply does and hosts the installer.

---

## Install

1. Download `QuickApply-<version>-Install.zip` from the [latest release](https://github.com/androguruji1/quick-apply-premiere/releases/latest) and unzip it.
2. Double-click **Install Quick Apply.command**.
   If macOS says it can't be opened: **System Settings → Privacy & Security**, scroll down, click **Open Anyway**, then double-click it again.
3. The key window opens. Paste your license key and click **Activate**, or **Start 14-day free trial**.
4. In Premiere Pro, open **Window → UXP Plugins → Quick Apply** once. Then press **⌥ Space**.

The installer puts **Quick Apply.app** in Applications (it opens at login, with a ⚡ in the menu bar) and installs the Premiere plugin with Adobe's own installer.

---

## Features

### Search everything from the keyboard
- **⌥ Space** opens a search window over Premiere, like Spotlight. (⌃⌥ Space, ⇧⌘ Space or ⇧ Space can be chosen instead.)
- Searches **video effects, audio effects, transitions and your saved effect presets** in one list.
- **Fuzzy matching:** `gblur` finds Gaussian Blur, and `fade` finds Cross Dissolve.
- **↩** applies the result to every selected clip, as **one undo step** (two for a preset).
- With an empty search, the window shows your **favorites and recent items**.

### A shortcut for anything
- Press **⌘K** on any result, then press the key combo you want. That combo now applies the item directly, without opening the window.
- **Clash check:** if Premiere already uses the combo, you're warned (for example *"Premiere uses ⌘K for sequence › razorateditline"*) and can override it. Combos that macOS or other apps own are refused.
- Shortcuts only work **while Premiere is the front app**. Everywhere else your keys behave normally.

### Your own effect presets
- Every preset saved with **Save Preset** in Premiere shows up in search, with its folder (for example *Preset · Motion › Zoom In*). Typing a folder name finds the presets inside it.
- A newly saved preset appears **immediately**, with no restart.
- Presets are rebuilt on the clip effect by effect:
  - values, checkboxes, menus, positions and colors
  - keyframes, placed from the clip start, from the clip end, or stretched to fit, the way the preset was saved
  - Linear, Hold and Bezier keyframes
- **Ease curves and motion paths are kept.** Premiere's plugin API can't set ease handles, so Quick Apply adds in-between keyframes that follow the saved curve within 0.5% of the move.

### Transitions
- Choose the duration (0.5, 1 or 2 s) and placement (clip end, clip start, or both ends) from the menu bar.
- Names match Premiere's Effects panel, including the "(Legacy)" versions.

### Small touches
- **⇥** cycles filters: All → Video FX → Audio FX → Transitions → Presets.
- Search prefixes: `v:` video effects, `a:` audio effects, `t:` transitions, `p:` presets.
- **⌘D** favorites an item. A ✓ pop-up confirms each apply, for example *"Gaussian Blur → 3 clips"*.
- Menu bar icon (⚡) with an Open at Login option.

---

## Keys

| Key | In the search window |
|---|---|
| type | search |
| ↑ ↓ | move |
| ↩ | apply to the selected clips |
| ⌘K | record a shortcut for the highlighted item (⎋ cancel, ⌫ remove) |
| ⌘D | favorite / unfavorite |
| ⇥ | change filter |
| ⌘R | reload the effect list from Premiere |
| ⎋ | clear the search, then close |

---

## License and updates

- **14-day free trial** on each Mac, no key needed.
- **One key works on 2 Macs.** To move it: ⚡ menu → License… → Deactivate on this Mac.
- **Updates:** when a new version is out, the Quick Apply panel in Premiere shows **Update now**. One click updates the app and the plugin; Premiere doesn't need a restart. The ⚡ menu has **Check for Updates** too.
- Works offline; the license is re-checked online about once a week.

---

## How it works

Quick Apply has two parts:
- **A UXP panel inside Premiere Pro** reads Premiere's effect and transition lists and applies items to the selected clips.
- **A small macOS menu bar app** runs the search window, the shortcuts and the confirmation pop-up. It also reads your saved presets.

The two parts only talk to each other on your own Mac. The app contacts the license server only to check your key and look for updates; your projects, effects and presets never leave your Mac.

## Requirements

- macOS 14 or later, Apple silicon or Intel
- Adobe Premiere Pro 25.6 or later (2026 recommended). It was tested on 26.5.2, finding 108 video effects, 78 audio effects and 106 transitions.

## Known limits

- **Lumetri curves, LUTs and Looks, and masks** inside presets aren't copied, because Premiere's API can't set them. Other Lumetri sliders are copied.
- **Effects that Premiere 2026 removed** are skipped when a preset uses them, and the pop-up names them.
- **Audio presets** aren't supported yet.
- In preset colors, **blue can be off by up to 4/255**, because Premiere's API rounds it.
