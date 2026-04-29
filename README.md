<div align="center">
  <h1>Neubird Falcon</h1>
  <p><strong>The AI-native workspace for SRE operations.</strong></p>
</div>

This repository is a **public release host** for Neubird Falcon installers
(`.dmg`, and future platform packages).

- **App source code is not in this repository.**
- Falcon source lives in the private engineering repo: `neubirdai/falcon-app`.

## Install (macOS)

### Homebrew (recommended)

```bash
brew install --cask neubirdai/tap/falcon
```

For upgrades:

```bash
brew upgrade --cask neubirdai/tap/falcon
```

### Direct download

1. Download the latest `NeubirdFalcon-darwin-arm64.dmg` from [Releases](https://github.com/neubirdai/neubird-falcon-app/releases).
2. Remove quarantine (required until notarization is enabled):

```bash
xattr -d com.apple.quarantine ~/Downloads/NeubirdFalcon-darwin-arm64.dmg
```

3. Open the DMG and drag **Neubird Falcon** to **Applications**.
4. Launch and sign in with your Neubird environment URL.

## About “Source code” assets on Releases

GitHub automatically adds **Source code (zip/tar.gz)** links to every tag.
In this repo, those archives contain only this public release metadata
(for example this README) and **not** the private Falcon application source.

## Reporting issues

Please open issues in: https://github.com/neubirdai/falcon-app/issues
