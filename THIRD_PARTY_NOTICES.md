# Third-party notices

The Simulator.Company desktop application is proprietary software. It is built
with and distributed alongside the components below. This file is a notice, not
a claim of ownership: each component remains under its own licence.

---

## Application runtime

| Component | Licence |
|---|---|
| Electron and Chromium | MIT (Electron); Chromium under its own BSD-style licence and the licences of its dependencies |
| Node.js | MIT |

Electron's own complete third-party licence list is included in the application
bundle, as shipped by Electron.

## Local platform

The optional local platform downloads and runs container images at first start
(published by Corezoid and by third parties — PostgreSQL, ScyllaDB, RabbitMQ,
Valkey, Transmission and others), and uses minikube (Apache-2.0) and a container
runtime installed on the machine. Those images and tools are **not**
redistributed by this repository; each remains under the licence of its
publisher and is fetched from its own distribution channel.

## Torrents

The `.torrent` files attached to releases describe our own builds; downloading
them uses whatever BitTorrent client you choose. No third-party client is
redistributed here.

---

## Corrections

If something is listed incorrectly, or a component is missing from this file,
tell us at support@corezoid.com and we will correct it in the next release.
This file describes the assets currently published in this repository; when the
next-generation application (Simulator Desktop) starts shipping here, its
bundled components — including a GPL-licensed BitTorrent client with the
corresponding written source offer — will be added.
