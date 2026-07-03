# Flet Hello World

基于 [Flet](https://flet.dev) 框架的跨平台应用模板。

## 环境要求

- Python >= 3.10（推荐 3.14）
- [uv](https://docs.astral.sh/uv/)（推荐）或 pip

## 安装

```bash
# 使用 uv（推荐）
uv sync --group dev

# 或使用 pip + venv
python3.14 -m venv .venv
source .venv/bin/activate
pip install flet==0.85.3 flet-cli==0.85.3 flet-desktop==0.85.3 flet-web==0.85.3
```

## 本地运行

### 桌面窗口模式（默认）

```bash
flet run src
```

以原生桌面窗口打开应用（macOS/Windows/Linux）。

### Web 浏览器模式

```bash
flet run src --web
```

启动本地 Web 服务器，在浏览器中查看效果（默认 http://localhost:8550）。

### Android 模拟器/真机

```bash
flet run src --android
```

需要连接 Android 设备或运行中的模拟器（通过 adb 连接）。

### iOS 模拟器

```bash
flet run src --ios
```

需要 macOS + Xcode + 运行中的 iOS 模拟器。

## 本地打包

Flet 0.85.3 会**自动下载**所需的 Flutter SDK 和 JDK，无需手动安装。

```bash
# Web
flet build web

# Android APK
flet build apk

# Android App Bundle（上传 Google Play）
flet build aab

# iOS（需要 macOS + Xcode）
flet build ipa --no-codesign

# macOS
flet build macos

# Linux（需要 GTK 开发库）
flet build linux

# Windows（需要在 Windows 上运行）
flet build windows
```

构建产物输出到 `build/<platform>/` 目录。

### 平台限制矩阵

| 构建目标 | macOS | Linux | Windows |
|---------|-------|-------|---------|
| web     | ✅    | ✅    | ✅      |
| apk/aab | ✅    | ✅    | ✅      |
| ipa     | ✅    | ❌    | ❌      |
| macos   | ✅    | ❌    | ❌      |
| linux   | ❌    | ✅    | ✅(WSL) |
| windows | ❌    | ❌    | ✅      |

## CI/CD 打包

Push 一个 `v*` 格式的 tag 即可触发 GitHub Actions 自动构建所有平台：

```bash
git tag v0.1.0
git push origin v0.1.0
```

也可在 GitHub Actions 页面手动触发 `workflow_dispatch`。

构建完成后，各平台产物会作为 Artifacts 上传，可在 Actions 运行记录中下载。

## 项目结构

```
├── .github/workflows/build.yml   # CI/CD 多平台打包
├── .gitignore
├── pyproject.toml                 # 项目配置 + Flet 构建配置
├── README.md
└── src/
    ├── assets/
    │   ├── icon.png               # 应用图标
    │   └── splash_android.png     # Android 启动画面
    └── main.py                    # 应用入口
```
