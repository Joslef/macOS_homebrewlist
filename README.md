# 📦 macOS_homebrewlist

A snapshot of all Homebrew formulae, Homebrew casks, and Mac App Store apps installed on this machine — automatically kept in sync with the system.

> **Auto-generated.** This repository is managed by the [`brewsync`](https://github.com/Joslef/scripts/tree/main/brewsync) script from the [`scripts`](https://github.com/Joslef/scripts) repository. Do not edit these files by hand — they will be overwritten on the next sync. See the brewsync README for full documentation on scheduling, configuration, and restore behaviour.

## 📋 Package Lists

- 📄 **`brewlist-formula.txt`** — Homebrew formulae installed via `brew install`
- 📄 **`brewlist-cask.txt`** — Homebrew casks installed via `brew install --cask`
- 📄 **`maslist.txt`** — Mac App Store apps installed via the `mas` CLI; each line contains the numeric App Store ID, app name, and installed version

## 🖥️ Restoring Packages on a New Machine

Clone this repository and run the appropriate installer for each list.

**Homebrew formulae:**
```bash
xargs brew install < brewlist-formula.txt
```

**Homebrew casks:**
```bash
xargs brew install --cask < brewlist-cask.txt
```

**Mac App Store apps** (requires [`mas`](https://github.com/mas-cli/mas) and an Apple ID signed in to the App Store):
```bash
awk '{print $1}' maslist.txt | xargs mas install
```

Restore is always **additive** — packages present in the repo but missing locally are installed; packages already installed are left untouched; nothing is ever removed.

## 🔄 How Syncing Works

The [`brewsync`](https://github.com/Joslef/scripts/tree/main/brewsync) script exports the three package lists, detects whether anything has changed since the last run, and pushes a new commit to this repository only when a change is found. It can run on a launchd schedule (hourly, daily, or weekly) or be triggered on demand. See the [brewsync README](https://github.com/Joslef/scripts/tree/main/brewsync) for setup instructions.
