# Security

## Reporting a vulnerability

Email **support@corezoid.com** with a subject starting with `[SECURITY]`.
Include the version, the platform and enough detail to reproduce. Do not open a
public issue — issues are disabled in this repository, and a vulnerability
report does not belong in a support channel either.

We acknowledge reports within three working days and will tell you plainly
whether we consider the finding valid, what we intend to do and when.

---

## Verifying a download

### The checksum

Every release has a `SHA256SUMS` asset listing the SHA-256 of every other asset
in that release.

```sh
# macOS / Linux
shasum -a 256 -c SHA256SUMS --ignore-missing

# Windows (PowerShell)
Get-FileHash .\SimulatorCompany-Setup-win-x64.exe -Algorithm SHA256
# compare with the line in SHA256SUMS
```

A checksum published next to the file proves the download was not corrupted or
substituted in transit between GitHub and you. The same values are produced by
our release pipeline directly from the build artifacts, so a mismatch always
means: do not run the file, and tell us.

### The signature

`SHA256SUMS` of every release is signed with the project's
[Sigstore/cosign](https://docs.sigstore.dev/) key. The public key is
[`cosign.pub`](cosign.pub) in this repository; the signature bundle is the
`SHA256SUMS.sigstore.json` asset of the release.

```sh
cosign verify-blob --key cosign.pub \
  --bundle SHA256SUMS.sigstore.json SHA256SUMS
# Verified OK
```

A verified signature plus a matching checksum proves the file is exactly what
we published.

### Torrents

The `.torrent` assets pin the content by hash at the protocol level: a
BitTorrent client verifies every piece against the torrent's own SHA-1 tree, so
a completed download is bit-for-bit the published build. Each torrent also
carries a webseed pointing at our CDN, so it completes even with no other peers
online.

---

## What the application does on your machine

Stated plainly, because a desktop application that runs a local container
platform deserves to be explicit about it.

- **Local platform.** The application can run Corezoid and Simulator on your
  machine inside a local Kubernetes cluster (a VM). This is optional and starts
  only when you install it from the *Downloads* screen.
- **Network.** The local platform binds the loopback interface. The bundled
  BitTorrent client is used to fetch the application's own published content
  and verifies every piece against published hashes before use.
- **Credentials.** The sign-in token is stored through the operating system's
  secure storage. Diagnostics exported from the application have home paths and
  token-like values redacted.

---

## Supported versions

Only the latest published release per platform receives fixes. There is no
long-term support branch. If a release contains a security fix, the release
notes say so in the first line.
