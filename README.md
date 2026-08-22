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

| | |
|---|---|
| Signed manifest | `manifest.json` at the repository root, on `main` |
| Release payloads | attached as assets to a GitHub release |

The manifest is a signed envelope: the manifest itself, the `key_id` it was
signed with, the algorithm, and the signature. A release is not considered
published until its manifest is committed here.