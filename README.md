<div align="center">
  <h1>Neubird Falcon</h1>
  <p><strong>The AI-native workspace for SRE operations.</strong></p>
  <p>
    Falcon is a desktop app that puts the Neubird agent — and the tools it needs to investigate your infrastructure —
    into a single integrated workspace built on Code-OSS.
  </p>
</div>

---

This repository hosts the **public download artifacts** for Neubird Falcon
(`.dmg`, `.exe`, `.deb`, etc.). It does not contain source code; the source
lives in [`neubirdai/falcon-app`](https://github.com/neubirdai/falcon-app)
(private).

The pattern mirrors [`neubirdai/neubird-desktop`](https://github.com/neubirdai/neubird-desktop),
which hosts releases for the `neubird` CLI.

## Install

### Homebrew (recommended, macOS)

```bash
brew install --cask neubirdai/tap/falcon
```

Brew automatically strips the macOS quarantine attribute, so Falcon launches
without the "is damaged" Gatekeeper dialog you get from a raw `.dmg` download.

### Direct download

Grab the latest `.dmg` from [Releases](https://github.com/neubirdai/neubird-falcon-app/releases).
On first launch, macOS may show "Neubird Falcon is damaged and can't be opened"
because we don't yet ship Apple-notarized builds. Strip the quarantine flag
and it'll open normally:

```bash
xattr -d com.apple.quarantine ~/Downloads/NeubirdFalcon-darwin-arm64.dmg
```

Then double-click the `.dmg` and drag Falcon to `/Applications`.

## What's inside

- The Falcon desktop app (Code-OSS fork, branded as **Neubird Falcon**)
- The bundled `neubird` CLI sidecar (also distributed standalone via
  [`neubirdai/neubird-desktop`](https://github.com/neubirdai/neubird-desktop))

Sign in to your Neubird workspace from the app to start investigating.

## Reporting issues

Open an issue against [`neubirdai/falcon-app`](https://github.com/neubirdai/falcon-app/issues).
