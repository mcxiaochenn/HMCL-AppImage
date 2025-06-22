# HMCL AppImage GitHub Actions

[![License: MIT](https://img.shields.io/badge/License-MIT-blue.svg)](LICENSE)

此GitHub Actions脚本旨在自动化HMCL (Hello Minecraft! Launcher) 的AppImage打包和发布过程。它能够监听HMCL项目的稳定版本发布，自动下载最新的 `.jar` 文件，并将其打包为AppImage格式。此外，它还支持手动触发，方便用户随时生成AppImage。

## 功能特点

- **自动监听**: 监听 [HMCL-dev/HMCL](https://github.com/HMCL-dev/HMCL) 项目的 `release` 事件，当有新的稳定版本发布时自动触发。
- **手动触发**: 支持通过GitHub Actions界面手动触发工作流，用于获取最新稳定版并打包。
- **AppImage打包**: 自动下载HMCL的 `.jar` 文件，并将其打包成独立的AppImage可执行文件。
- **图标集成**: 使用HMCL官方图标 (`HMCL.ico`) 并转换为PNG格式，集成到AppImage中。
- **自动发布**: 对于自动触发的构建，生成的AppImage将作为发布资产上传到HMCL的GitHub Releases页面。
- **手动下载**: 对于手动触发的构建，生成的AppImage将作为工作流产物提供下载。

## 如何使用

1. **Fork本项目**

2. **运行工作流**:

   - **自动触发**: 当HMCL-dev/HMCL项目发布新的稳定版本时，此工作流将自动运行。
   - **手动触发**: 
     1. 导航到您的GitHub仓库的 `Actions` 选项卡。
     2. 在左侧导航栏中找到 `HMCL AppImage Builder` 工作流。
     3. 点击 `Run workflow` 按钮，然后点击绿色的 `Run workflow` 按钮来手动触发。

## 文件说明

- `.github/workflows/hmcl_appimage.yml`: GitHub Actions工作流定义文件。

## 注意事项

- 本脚本依赖`wget`、`curl`、`imagemagick` 和 `appimagetool`。这些工具会在工作流运行时自动安装。
- 脚本会尝试获取最新稳定版的 `.jar` 文件。如果HMCL项目发布结构发生变化，可能需要调整脚本中的解析逻辑。

## 许可证

本项目采用MIT许可证。