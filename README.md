# hermes-desktop-builder

GitHub Action that builds [Hermes Desktop](https://github.com/NousResearch/hermes-agent) app from source for macOS, Linux, and Windows.

## Usage

1. Push this repo to GitHub
2. Go to **Actions** → **Build Hermes Desktop** → **Run workflow**
3. Enter a release tag (e.g. `v2026.6.19`) or leave empty for latest
4. Download the built app from the resulting draft Release

## What it does

- Clones `NousResearch/hermes-agent` at the specified tag
- Builds the Electron desktop app (`npm run pack`)
- Uploads platform-specific artifacts (dmg/zip/AppImage/deb/rpm/exe/msi) to a draft GitHub Release

## Notes

- macOS builds are **not code-signed** (no Apple Developer account). Run `xattr -cr Hermes.app` on first launch.
- Linux builds produce AppImage, deb, and rpm.
- Windows builds produce NSIS installer and MSI.
