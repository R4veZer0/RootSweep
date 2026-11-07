# RootSweep (Beta v0.03)

**When your `C:` drive is maxed out—even after you've uninstalled everything you can.**

**RootSweep** is a fast, non-destructive Windows `C:` drive diagnostic and space recovery desktop app. It hunts down the hidden gigabytes that standard uninstallers and Windows Storage Settings leave behind—orphaned `AppData` & `ProgramData` leftovers, bloated GPU shader caches, mod manager download archives, dormant installers, and duplicate files—while keeping **you** in 100% control of what gets cleaned or moved.

[![Latest Release](https://img.shields.io/github/v/release/R4veZer0/RootSweep?label=Download%20Latest&style=for-the-badge)](https://github.com/R4veZer0/RootSweep/releases/latest)
[![Platform](https://img.shields.io/badge/Platform-Windows%2010%20%7C%2011-0078D6?style=for-the-badge&logo=windows)](https://github.com/R4veZer0/RootSweep/releases/latest)

---

## Why RootSweep?

Most PC users hit a wall where their `C:` drive shows **95%+ full**, yet *Add or Remove Programs* shows nothing left to uninstall. Where did 100+ GB go?
- **Uninstalled Apps & Games Leave Behind Massive Folders**: Uninstalling a game or app rarely deletes its multi-gigabyte folders inside `AppData\Roaming`, `AppData\Local`, `AppData\LocalLow`, or `C:\ProgramData`.
- **Mod Managers & Launchers Hoard Archives**: Tools like Vortex, Steam, and Epic keep gigabytes of old `.zip` mod archives, shader caches, and interrupted update staging files on `C:`.
- **Silent Caches Grow Forever**: NVIDIA/AMD/DirectX shader caches, HuggingFace AI models, `pip`/`npm` package caches, crash dumps, and `Temp` folders quietly balloon to 50+ GB.

**RootSweep** finds all of them in under a second, explains *why* each item is taking space, rates its safety level, and lets you either **Recycle** it safely or **Relocate** it to another drive (`D:`) without breaking a single app.

---

## Key Features

### 1. Orphaned AppData & ProgramData Leftover Hunter
Cross-references every folder in `AppData` (`Roaming`, `Local`, `LocalLow`) and `C:\ProgramData` against your Windows Uninstall Registry (`HKLM`, `WOW6432Node`, `HKCU`) and `Program Files` to pinpoint leftover folders from long-uninstalled software.

### 2. Games & Mod Staging Scanner
Specifically targets PC gaming space hogs on `C:`:
- **Vortex / Mod Manager Archives**: Surfaces `Roaming\Vortex\downloads` and `temp` separately from your active mod settings so you can reclaim 10+ GB of redundant `.zip` backups without losing your mod load order.
- **Steam & Epic Caches**: Detects `steamapps\downloading`, `steamapps\shadercache`, `Documents\My Games`, `Saved Games`, and `C:` drive Steam games.

### 3. Zero-Breakage "Relocate to D:" Junction Tool (`mklink /J`)
Have a massive folder on `C:` that you **still need** (like a 10 GB Steam game, Vortex mod folder, BlueStacks instance, or AI model cache)?
- Click **Relocate to D:** on any folder row.
- Choose from smart auto-detected presets (e.g., `D:\SteamLibrary\steamapps\common\<Game>`, `D:\steamapps\common\<Game>`, `D:\Vortex Mods`, or any custom folder via the native folder picker).
- RootSweep moves the files to your secondary drive and creates a transparent **Windows Directory Junction (`mklink /J`)** at the original `C:` path. Windows, Steam, and every app still think the files are on `C:`, while **100% of the storage is freed on `C:`**!

### 4. Inline "Inspect Inside" Folder Drill-Down
Not sure what's inside a 10 GB folder marked *Review First*? Click **Inspect Inside** to expand an inline tree of its largest subfolders and files right inside the dashboard, and selectively recycle or open individual subfolders.

### 5. Non-Destructive Cleanup (Windows Recycle Bin + Locked-File Bypass)
- **Nothing is ever deleted automatically.**
- Selected items are sent to the **Windows Recycle Bin** (`SHFileOperationW` with `FOF_ALLOWUNDO`) so you can restore anything anytime.
- **Smart Shared-Cache Cleaning**: If a cache folder (like `NVIDIA\DXCache` or `AppData\Local\Temp`) has 1–2 files locked by a running driver or Windows process, RootSweep automatically steps inside and recycles every unlocked file & subfolder so you still reclaim 99% of the space immediately.

### 6. Fast Two-Pass Duplicate File Finder & OneDrive Cloud Guardrail
- Finds 100% byte-identical duplicate downloads, installers, and videos in `Downloads`, `Desktop`, `Documents`, and `Videos` using a fast size-grouping + 3-chunk SHA-256 signature pass, always keeping the oldest original untouched.
- Automatically detects and skips **OneDrive / Cloud-Only placeholder files** (`FILE_ATTRIBUTE_RECALL_ON_DATA_ACCESS`) so scanning never triggers unwanted cloud downloads or stalls.

### 7. Built-In GitHub Auto-Updater
- Checks `R4veZer0/RootSweep` Releases in the background and lets you download and install updates in-place with one click.

---

## Installation & Updating

1. Go to the [**Releases**](https://github.com/R4veZer0/RootSweep/releases/latest) page and download **`RootSweep_Setup.exe`**.
2. Run **`RootSweep_Setup.exe`**:
   - **New Users**: Installs RootSweep and creates Desktop & Start Menu shortcuts.
   - **Existing Users**: Automatically detects your existing installation and upgrades it in-place to the latest version!
