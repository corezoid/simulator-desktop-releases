<p align="center">
  <img src="assets/app-icon.png" alt="" width="96">
</p>

<h1 align="center">Installing Simulator.Company</h1>

Download the installer for your platform from the
[releases page](https://github.com/corezoid/simulator-desktop-releases/releases) —
look for the newest `v<version>` tag (this repository also hosts the separate
Simulator Desktop pre-release, tagged `desktop-v<version>`, which is not this
application) — then follow the section for your operating system. To check the
download first, see [Verifying a download](SECURITY.md#verifying-a-download).

---

## System requirements

**For the application itself** — an ordinary desktop machine.

**For the local platform** (running Corezoid and Simulator on your own machine)
the requirements are real, and the application checks them before it starts
anything. They depend on which of the two you install — Corezoid on its own is
noticeably lighter than both together:

| | Corezoid | Corezoid + Simulator |
|---|---|---|
| Memory | **4 GB free** | **6 GB free** |
| Processor | **2 cores** | **4 cores** |
| Disk | **20 GB free** | **30 GB free** |
| Download, first start | **~1 GB** | **~1.6 GB** |

Free memory means on top of what the rest of the machine already uses; the disk
figure covers the components, the platform's data and its snapshots. Both
variants also need hardware virtualisation enabled (macOS: Apple Silicon or a
VT-x capable Intel Mac; Windows: WSL2; Linux: native).

*Downloads → Local platform* offers Corezoid, Simulator and Full server as three
tabs, each showing these figures for your machine, and the built-in check reports
every requirement with the actual numbers. Adding Simulator to an installed
Corezoid later downloads only the difference and enlarges the virtual machine,
which restarts the platform once.

You can install and use the application without the local platform at all.

---
## 🍎 macOS

macOS builds are released on their own cadence — take the newest macOS release
from the [releases page](https://github.com/corezoid/simulator-desktop-releases/releases).


## 🪟 Windows

1. Download `SimulatorCompany-Setup-win-<arch>.exe`.
2. Run it. The installer places the application in your user profile and starts
   it; no administrator rights are required for the application itself.
3. If the local platform is used, it runs inside **WSL2** — the installer does
   not enable WSL2 for you.


## 🐧 Linux

1. Download the `.deb` (Debian/Ubuntu) or `.rpm` (Fedora/RHEL) for your
   architecture.
2. Install it:

```sh
sudo apt install ./SimulatorCompany-linux-x64.deb     # Debian/Ubuntu
sudo dnf install ./SimulatorCompany-linux-x64.rpm     # Fedora/RHEL
```

3. Launch **SimulatorCompany** from your application menu.

The Linux assets are also published as torrents — any BitTorrent client works,
and the torrent carries a webseed so it completes even with no peers online.

1. Download the `.dmg` for your processor (`arm64` for Apple Silicon, `x64` for
   Intel).
2. Open it and drag the application into *Applications*.
3. Launch it from *Applications*. If Gatekeeper warns about the application,
   verify the download against `SHA256SUMS`
   ([how](SECURITY.md#verifying-a-download)) before allowing it.

---

## 📱 Mobile

| | |
|---|---|
| **iOS** | [App Store — Simulator.Company](https://apps.apple.com/app/simulator-company/id6754986862) |
| **Android** | [Google Play — Simulator.Company](https://play.google.com/store/apps/details?id=company.simulator.app) |

---

## Updating

The installed application checks for updates itself and offers them when they
are available. Installing a newer version over the existing one by hand also
works — settings, the signed-in session and an installed local platform are
kept.

## Uninstalling

Removing the application does not remove an installed local platform — remove
it first from *Downloads → Remove* if you want the disk space back (it is
several gigabytes inside a virtual machine).
