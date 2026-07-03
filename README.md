# Flet App Template

A cross-platform app template built with [Flet](https://flet.dev). One Python codebase, six platform targets.

## Requirements

- Python >= 3.10 (recommended 3.14)
- [uv](https://docs.astral.sh/uv/) (recommended) or pip

## Setup

```bash
# Using uv (recommended)
uv sync --group dev

# Or using pip + venv
python3.14 -m venv .venv
source .venv/bin/activate
pip install flet==0.85.3 flet-cli==0.85.3 flet-desktop==0.85.3 flet-web==0.85.3
```

## Run Locally

### Desktop window (default)

```bash
flet run src
```

Opens the app as a native desktop window (macOS/Windows/Linux).

### Web browser

```bash
flet run src --web
```

Starts a local web server at http://localhost:8550.

### Android emulator/device

```bash
flet run src --android
```

Requires a connected Android device or running emulator via adb.

### iOS simulator

```bash
flet run src --ios
```

Requires macOS + Xcode + a running iOS simulator.

## Build Locally

Flet 0.85.3 auto-downloads the required Flutter SDK and JDK on first build.

```bash
flet build web            # Web
flet build apk            # Android APK
flet build aab            # Android App Bundle (Google Play)
flet build ipa            # iOS (requires macOS + Xcode)
flet build macos          # macOS
flet build linux          # Linux (requires GTK dev libs)
flet build windows        # Windows (must run on Windows)
```

Build output goes to `build/<platform>/`.

### Platform build matrix

| Target  | macOS | Linux | Windows |
|---------|-------|-------|---------|
| web     | Yes   | Yes   | Yes     |
| apk/aab | Yes   | Yes   | Yes     |
| ipa     | Yes   | No    | No      |
| macos   | Yes   | No    | No      |
| linux   | No    | Yes   | Yes(WSL)|
| windows | No    | No    | Yes     |

## CI/CD

Push a `v*` tag to trigger GitHub Actions builds for all platforms:

```bash
git tag v0.1.0
git push origin v0.1.0
```

You can also trigger manually via `workflow_dispatch` on the Actions page.

Build artifacts are uploaded to [GitHub Releases](https://github.com/OrekiYuta/flet-app-template/releases).

## GitHub Pages

A static landing page is deployed at [orekiyuta.github.io/flet-app-template](https://orekiyuta.github.io/flet-app-template/) with download links for each platform.

To preview locally, open `docs/index.html` in a browser.

## Project Structure

```
├── .github/workflows/
│   ├── build.yml              # Multi-platform build + release
│   └── pages.yml              # GitHub Pages deployment
├── .gitignore
├── docs/
│   └── index.html             # Landing page
├── pyproject.toml             # Project config + Flet build settings
├── README.md
└── src/
    ├── assets/
    │   ├── icon.png           # App icon
    │   └── splash_android.png # Android splash screen
    └── main.py                # App entry point
```
