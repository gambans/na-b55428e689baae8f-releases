# Nytro Audio Pitchmachine

Official binary-only update channel for Pitchmachine (macOS 12+, Apple Silicon).

[Download Pitchmachine 0.9.14 installer](https://raw.githubusercontent.com/gambans/na-b55428e689baae8f-releases/main/Pitchmachine-0.9.14-Update.zip)

Install this bootstrap version once. Later updates are discovered automatically when the plugin editor starts, or through Settings → Check for Updates. Updates wait for the initiating audio host to close and preserve a backup.

## Verification

The updater authenticates pitchmachine-channel.json using its pinned Ed25519 public key, verifies the signed SHA-256 and byte count, checks archive paths and bundle identity, and verifies the installed payload. No plugin source code or private signing keys are distributed here.

## Apple signing

0.9.14 is ad-hoc signed and has not been Apple Developer ID signed or notarized. It may require explicit macOS approval on a different Mac. Cryptographic update signing is separate from Apple notarization.

## Publishing future updates

Use the existing private release key with scripts/package_update.py from the private source project. Upload the versioned ZIP first and verify it matches the local archive. Then upload its signed versioned JSON and replace pitchmachine-channel.json with that exact signed JSON as the final publication step. Keep previous ZIPs available. Do not replace the pinned key after distributing this bootstrap version.

## 0.9.14 packaging repair

The native AU build now writes Contents/PkgInfo before code signing. Finder recognizes Pitchmachine.component as a bundle rather than an ordinary folder. A native NSWorkspace package-recognition regression is included. DSP behavior is unchanged. Full native build and offline suites passed. The static update channel is active; Apple notarization and a complete Logic host test remain pending.
