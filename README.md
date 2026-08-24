# whoscam-desktop-releases

Public release metadata and download assets for **Who's Cam Desktop**.

This repository contains no source code and no signing material. Release
manifests published here are signed offline; the private key never touches
GitHub, CI, or any automated system.

## Verifying a release

Release manifests in this repository are signed offline with an Ed25519 key.
The signature covers the canonical encoding of the manifest, including the
download URL and the payload SHA-256. Who's Cam verifies that signature
against a key compiled into the application before any update is applied.

## Signing key

Releases are signed with:

| | |
|---|---|
| Key id | `whoscam-2026-08` |
| Public key | `86f817d9254d420130ccce684f28f22db62572736694e608e3421cf5e5ed3396` |
| Fingerprint | `0bf8dfce40b7f6b823f16bff6fad1aed3ee9967533b2fdb00d6e529c8720238b` |

The fingerprint is the SHA-256 of the raw 32-byte public key. Publishing it
lets anyone confirm that the key compiled into their copy of Who's Cam is the
same key that signs releases here.

## Where things are published

Two kinds of artifact, delivered two different ways.

| | Where |
|---|---|
| **Signed manifest** | `manifest.json` at this repository's root, on `main` |
| **Light-update payloads** | attached as assets to a GitHub release here |
| **Full bootstrap installers** | **hosted separately — not in this repository** |

**Full installers are not GitHub release assets.** The Who's Cam installer
bundles an embedded Python runtime and the ONNX models, which puts it well past
GitHub's per-file release-asset limit. It is therefore distributed from separate
hosting, and this repository carries only the release notes and the link.

**Light-update payloads are small** — a few megabytes of compiled modules — and
are attached here as normal release assets.

The manifest is a signed envelope: the manifest itself, the `key_id` it was
signed with, the algorithm, and the signature. A release is not considered
published until its manifest is committed here.

## Updating from 2.1.6

**2.1.6 cannot update itself.** It contains no updater, no signing key and no
version-check logic, and nothing shipped later changes that retroactively.

Moving from 2.1.6 to 2.2.0 is a **one-time manual step**: download and run the
2.2.0 installer. From 2.2.0 onward, updates are checked, downloaded and staged
automatically, and installed only on explicit approval.

Until a release after 2.2.0 exists, a 2.2.0 client will report that no update
source is available. That is expected, and not an error.