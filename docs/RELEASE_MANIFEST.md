# `desktop-releases.json` — the release manifest

A small, cacheable JSON file at the root of this repository that says what the
current version is and where to get it. It exists so that an updater, a fleet
tool or a script never has to scrape the releases page.

**Canonical URL**

```
https://raw.githubusercontent.com/corezoid/simulator-desktop-releases/main/desktop-releases.json
```

Serve it with a short cache lifetime (a minute is plenty). The assets it points
at are immutable, so they may be cached forever.

> **Status:** the application does not consume this file yet — it has no
> auto-updater. The manifest is published so that one can be added without
> changing the distribution, and so that tooling has a stable contract today.

---

## Shape

```jsonc
{
  "schema": 1,
  "minimumVersion": "0.1.0",   // below this, an update is required, not optional
  "latestVersion": "0.1.0",    // what a fresh install should get
  "publishedAt": "2026-08-08T10:00:00Z",
  "notesUrl": "https://github.com/corezoid/simulator-desktop-releases/releases/tag/v0.1.0",

  "platforms": {
    "darwin-arm64": {
      "downloadUrl": "https://github.com/corezoid/simulator-desktop-releases/releases/download/v0.1.0/Simulator-Desktop-0.1.0-arm64.dmg",
      "bytes": 471859200,
      "sha256": "…64 hex…",
      "signature": null          // detached signature, see below
    },
    "darwin-x64":  { "…": "…" },
    "win32-x64":   { "…": "…" },
    "linux-x64":   { "…": "…" }
  },

  "beta": {                      // optional; omit the key entirely when none
    "minimumVersion": "0.1.0",
    "latestVersion": "0.2.0-beta.1",
    "platforms": { "…": "…" }
  }
}
```

### Fields

| Field | Meaning |
|---|---|
| `schema` | Format version. A consumer that sees a higher number must fall back to doing nothing, not guess. |
| `minimumVersion` | The oldest version still considered supported. Anything older should be told to update rather than offered a choice. |
| `latestVersion` | The version a fresh install or an update should land on. Must correspond to a published tag. |
| `publishedAt` | ISO-8601, UTC. Informational. |
| `notesUrl` | Where a human reads what changed. |
| `platforms.<key>` | Key is `<platform>-<arch>` exactly as Node reports it (`darwin-arm64`, `win32-x64`, `linux-x64`). Only keys with a published asset may appear. |
| `downloadUrl` | Direct link to the release asset. Must be HTTPS and must support range requests (GitHub's asset URLs do). |
| `bytes` | Exact size. A download that does not match it is wrong before its hash is even computed. |
| `sha256` | Lowercase hex of the asset. |
| `signature` | Detached signature of the asset, or `null` while none is published. See below. |

### Rules that make this safe to consume

1. **Never install what you did not verify.** `bytes` first (cheap), then
   `sha256`, and only then anything else. On macOS the operating system's own
   notarisation check is a second, independent gate — do not skip it because the
   hash matched.
2. **The manifest is the trust anchor, so it must come over TLS** from the
   canonical URL. A manifest fetched over anything else is worthless: it carries
   the hashes everything else is checked against.
3. **A missing platform key is not an error** — it means no build exists for that
   platform yet. Say so; do not fall back to a different architecture.
4. **`latestVersion` may go backwards.** If a release is withdrawn, we republish
   the previous version here. A consumer must handle "the latest version is older
   than what I am running" by doing nothing.

---

## Signatures

`signature` is reserved for a detached signature over the asset bytes, so that a
future updater does not have to trust GitHub's transport alone. Until we publish
a signing key, the field is `null` and the honest verification chain is:

- **macOS** — Apple notarisation plus our Developer ID (`spctl`, `codesign`),
  which is a stronger check than any signature we could add;
- **all platforms** — the `sha256` in this manifest, fetched over TLS.

When a key is published, this section will name the algorithm, the key, and
where to get it. Do not infer a scheme from the field's presence.

---

## How it is updated

`desktop-releases.json` is committed **after** the release is published and its
assets are known-good — never before. The sequence and the checks are in the
internal `RELEASING.md`; the invariant that matters to a consumer is that every
URL in this file points at an asset that already exists and whose hash already
matches.

---

## `simulator-desktop.json` — the next-generation application

**Simulator Desktop**, the application that will succeed the current one, is
published in this same repository under `desktop-v*` tags. Its manifest is a
**separate file** of the same shape:

```
https://raw.githubusercontent.com/corezoid/simulator-desktop-releases/main/simulator-desktop.json
```

Why a second file rather than a key inside this one: `desktop-releases.json` is
the contract the **current** application's updater reads. Anything written there
is something the installed fleet may act on, so a pre-release of a different
application has no business appearing in it — not even under a key the current
updater is expected to ignore. Separate files make that impossible rather than
merely unlikely.

Differences from `desktop-releases.json`:

| | |
|---|---|
| `channel` | `"prerelease"` while the application is in development. Consumers must not offer these builds as an upgrade from the current application. |
| Tags | `desktop-v<version>`, always marked as GitHub pre-releases, never `latest`. |
| Platform keys | The same `<platform>-<arch>` scheme. The Linux entry names the `.deb`; the `.rpm` and `.AppImage` of the same build are attached to the release next to it. |

Everything else — the verification rules, the meaning of `bytes`/`sha256`, the
`null` signature field, the "missing key is not an error" rule — is identical
and is not restated here.
