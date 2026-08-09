# Simulator.Company — desktop releases

[![Latest release](https://img.shields.io/github/v/release/corezoid/simulator-desktop-releases?label=latest%20release)](https://github.com/corezoid/simulator-desktop-releases/releases/latest)

Official public releases of the **Simulator.Company desktop application** by
[Corezoid Inc.](https://corezoid.com)

> **This repository does not contain source code.** The application is
> proprietary. What lives here is the released installers, their checksums and
> torrents, the release notes, the machine-readable release manifest, and the
> licence notices for bundled third-party components.

**[Download the latest release →](https://github.com/corezoid/simulator-desktop-releases/releases/latest)**

---

## Downloads

Permanent links to the latest release, per platform. Every asset has its
SHA-256 in the `SHA256SUMS` file attached to the same release — see
[Verifying a download](SECURITY.md#verifying-a-download).

| Platform | Installer | Torrent |
|---|---|---|
| Linux x64 (deb) | [`SimulatorCompany-linux-x64.deb`](https://github.com/corezoid/simulator-desktop-releases/releases/latest/download/SimulatorCompany-linux-x64.deb) | [`.torrent`](https://github.com/corezoid/simulator-desktop-releases/releases/latest/download/SimulatorCompany-linux-x64.deb.torrent) |
| Linux x64 (rpm) | [`SimulatorCompany-linux-x64.rpm`](https://github.com/corezoid/simulator-desktop-releases/releases/latest/download/SimulatorCompany-linux-x64.rpm) | [`.torrent`](https://github.com/corezoid/simulator-desktop-releases/releases/latest/download/SimulatorCompany-linux-x64.rpm.torrent) |
| Linux arm64 (deb) | [`SimulatorCompany-linux-arm64.deb`](https://github.com/corezoid/simulator-desktop-releases/releases/latest/download/SimulatorCompany-linux-arm64.deb) | [`.torrent`](https://github.com/corezoid/simulator-desktop-releases/releases/latest/download/SimulatorCompany-linux-arm64.deb.torrent) |
| Linux arm64 (rpm) | [`SimulatorCompany-linux-arm64.rpm`](https://github.com/corezoid/simulator-desktop-releases/releases/latest/download/SimulatorCompany-linux-arm64.rpm) | [`.torrent`](https://github.com/corezoid/simulator-desktop-releases/releases/latest/download/SimulatorCompany-linux-arm64.rpm.torrent) |
| Windows x64 | [`SimulatorCompany-Setup-win-x64.exe`](https://github.com/corezoid/simulator-desktop-releases/releases/latest/download/SimulatorCompany-Setup-win-x64.exe) | — |
| Windows arm64 | [`SimulatorCompany-Setup-win-arm64.exe`](https://github.com/corezoid/simulator-desktop-releases/releases/latest/download/SimulatorCompany-Setup-win-arm64.exe) | — |
| macOS Apple Silicon | see the [releases page](https://github.com/corezoid/simulator-desktop-releases/releases) | — |
| macOS Intel | see the [releases page](https://github.com/corezoid/simulator-desktop-releases/releases) | — |

macOS builds are currently released on their own cadence, so the permalink
above may lag the latest Linux/Windows version; the releases page always lists
the newest build for every platform. A torrent cell with `—` means no torrent
is published for that asset yet; the ones that exist carry a
[webseed](https://www.bittorrent.org/beps/bep_0019.html), so they download at
full CDN speed even with no other peers online.

The same builds are also available from
[app.simulator.company](https://app.simulator.company) — the application's own
update channel. GitHub is an additional, mirrored distribution point; neither
depends on the other.

### Mobile applications

Simulator.Company is also available for phones and tablets:

| | |
|---|---|
| **iOS** | [App Store — Simulator.Company](https://apps.apple.com/app/simulator-company/id6754986862) |
| **Android** | [Google Play — Simulator.Company](https://play.google.com/store/apps/details?id=company.simulator.app) |

Mobile builds are distributed only through the stores; they are not attached to
releases here.

---

## What is in this repository

| | |
|---|---|
| **Installers** | Attached to each [release](https://github.com/corezoid/simulator-desktop-releases/releases) as assets |
| **`SHA256SUMS`** | One per release: the SHA-256 of every asset in that release |
| **Torrents** | `.torrent` assets next to the installers they cover, with a webseed |
| **`desktop-releases.json`** | Machine-readable manifest — see [docs/RELEASE_MANIFEST.md](docs/RELEASE_MANIFEST.md) |
| **Release notes** | On every release, including anything that affects installing or updating |
| **[`CHANGELOG.md`](CHANGELOG.md)** | The same history in one file |
| **[`THIRD_PARTY_NOTICES.md`](THIRD_PARTY_NOTICES.md)** | Licences and source offers for bundled third-party components |

## What is **not** here

- The source code of the application.
- Issue tracking. **Issues are disabled** — see [SUPPORT.md](SUPPORT.md) for
  where to ask questions and report problems.
- Pull requests. Nothing here is built from contributions.

---

## Versions and tags

Releases are tagged `v<major>.<minor>.<patch>` and follow semantic versioning.
A release contains the platforms built for that version; platforms released on
their own cadence (macOS today) appear under their own version tag, and
[`desktop-releases.json`](desktop-releases.json) always names the current
version **per platform** — that file, not the tag list, is the machine-readable
answer to "what should this machine be running".

Pre-releases carry a `-beta.N` suffix and the GitHub *pre-release* mark. They
are published for testing and are not offered to anyone who did not ask for
them.

### The next generation

A new desktop application, **Simulator Desktop**, is in development. Its
releases will be published in this same repository under `desktop-v*` tags,
marked as pre-releases until it becomes the recommended download. Nothing about
the current application changes until then.

---

## Updating

The installed application checks
[app.simulator.company](https://app.simulator.company) and updates itself; you
do not need to watch this repository. Installing a newer version over an
existing one by hand also works and keeps your settings and session.

---

## Licences

The application is proprietary software. It bundles third-party components,
some under copyleft licences. Notices, licence texts and the written offer for
corresponding source code are in
[THIRD_PARTY_NOTICES.md](THIRD_PARTY_NOTICES.md).

## Security

How to verify that a download is genuinely ours, and how to report a
vulnerability: [SECURITY.md](SECURITY.md).
