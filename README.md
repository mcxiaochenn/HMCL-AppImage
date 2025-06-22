# HMCL AppImage GitHub Actions

此GitHub Actions脚本旨在自动化HMCL (Hello Minecraft! Launcher) 的AppImage打包和发布过程。它能够监听HMCL项目的稳定版本发布，自动下载最新的 `.sh` 文件，并将其打包为AppImage格式。此外，它还支持手动触发，方便用户随时生成AppImage。

## 功能特点

- **自动监听**: 监听 [HMCL-dev/HMCL](https://github.com/HMCL-dev/HMCL) 项目的 `release` 事件，当有新的稳定版本发布时自动触发。
- **手动触发**: 支持通过GitHub Actions界面手动触发工作流，用于获取最新稳定版并打包。
- **AppImage打包**: 自动下载HMCL的 `.jar` 文件，并将其打包成独立的AppImage可执行文件。
- **图标集成**: 使用HMCL官方图标 (`HMCL.ico`) 并转换为PNG格式，集成到AppImage中。
- **自动发布**: 对于自动触发的构建，生成的AppImage将作为发布资产上传到HMCL的GitHub Releases页面。
- **手动下载**: 对于手动触发的构建，生成的AppImage将作为工作流产物提供下载。

## 如何使用

1. **将工作流文件添加到您的仓库**:

   将 `hmcl_appimage.yml` 文件复制到您的GitHub仓库的 `.github/workflows/` 目录下。如果这些目录不存在，请手动创建它们。

   ```bash
   mkdir -p .github/workflows
   cp hmcl_appimage.yml .github/workflows/
   ```

2. **配置GitHub Token (可选，仅用于自动发布到HMCL仓库)**:

   如果您希望自动将AppImage发布到HMCL-dev/HMCL项目的Releases页面，您需要一个具有 `repo` 权限的GitHub Token。通常，对于跨仓库发布，您需要创建一个Personal Access Token (PAT) 并将其添加到您的仓库Secrets中，命名为 `RELEASE_TOKEN`。

   **注意**: 如果您只是想在自己的仓库中构建AppImage并作为Artifact下载，则无需此步骤。

3. **运行工作流**:

   - **自动触发**: 当HMCL-dev/HMCL项目发布新的稳定版本时，此工作流将自动运行。
   - **手动触发**: 
     1. 导航到您的GitHub仓库的 `Actions` 选项卡。
     2. 在左侧导航栏中找到 `HMCL AppImage Builder` 工作流。
     3. 点击 `Run workflow` 按钮，然后点击绿色的 `Run workflow` 按钮来手动触发。

## 文件说明

- `.github/workflows/hmcl_appimage.yml`: GitHub Actions工作流定义文件。

## 注意事项

- 本脚本依赖 `jq`、`wget`、`curl`、`imagemagick` 和 `appimagetool`。这些工具会在工作流运行时自动安装。
- 图标路径是硬编码的，如果HMCL官方更改图标路径，您需要更新 `hmcl_appimage.yml` 文件中的 `ICON_URL`。
- 脚本会尝试获取最新稳定版的 `.sh` 文件。如果HMCL项目发布结构发生变化，可能需要调整脚本中的解析逻辑。

## 许可证

本项目采用MIT许可证。

