# hermes-desktop-builder

GitHub Action that builds [Hermes Desktop](https://github.com/NousResearch/hermes-agent) app from source for macOS, Linux, and Windows.

## Usage

1. Go to **Actions** → **Build Hermes Desktop** → **Run workflow**.
2. Enter a release tag (for example, `v0.23.3`) or leave it empty to build the latest release.
3. Download the installer from the resulting GitHub Release.

## What it does

- Checks out `NousResearch/hermes-agent` at the selected tag.
- Installs dependencies from the tag’s pnpm or npm lockfile.
- Builds and packages the desktop app on macOS, Linux, and Windows.
- Publishes the installers in a GitHub Release named `desktop-<tag>`.

## Output formats

- macOS builds produce DMG and ZIP files without Developer ID signing or notarization.
- Linux builds produce an AppImage.
- Windows builds use the upstream format for the selected tag. Current tags produce unsigned MSIX packages. Older tags may produce NSIS `.exe` and MSI installers.
