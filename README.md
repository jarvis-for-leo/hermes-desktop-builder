# hermes-desktop-builder

GitHub Action that builds [Hermes Desktop](https://github.com/NousResearch/hermes-agent) app from source for macOS, Linux, and Windows.

## Install with Scoop (Windows x64)

```powershell
scoop bucket add hermes-builder https://github.com/jarvis-for-leo/hermes-desktop-builder
scoop install hermes-builder/hermes-desktop
```

Open **Hermes Desktop** from the Start menu. Close it before upgrading.

```powershell
scoop update
scoop update hermes-desktop
```

The release workflow refreshes the Scoop manifest from the latest published Windows x64 ZIP and its SHA-256 digest.

## Build from an upstream tag

1. Go to **Actions** → **Build Hermes Desktop** → **Run workflow**.
2. Enter a release tag (for example, `v0.23.3`) or leave it empty to build the latest release.
3. Download the package for your platform from the resulting GitHub Release.
4. On Windows, extract the Windows ZIP to a folder and run `Hermes.exe`. For a signed Windows installer, download the `.appinstaller` from the [official Hermes website](https://hermes-agent.nousresearch.com/).

## What it does

- Checks out `NousResearch/hermes-agent` at the selected tag.
- Installs dependencies from the tag’s pnpm or npm lockfile.
- Builds and packages the desktop app on macOS, Linux, and Windows.
- Publishes the packages in a GitHub Release named `desktop-<tag>`.

## Output formats

- macOS builds produce DMG and ZIP files without Developer ID signing or notarization.
- Linux builds produce an AppImage.
- Windows builds for MSIX-based tags produce a ZIP and an unsigned MSIX. Windows App Installer requires a trusted signature for this MSIX. Older tags may produce NSIS `.exe` and MSI installers.
