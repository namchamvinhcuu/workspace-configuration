# Workspace Configuration

A desktop application that helps developers set up and manage development environments.
Supports **Odoo projects** and other project types (Flutter, React, NextJS, .NET, Rust, Go, Java...).

---

**[English](#english)** | **[Tiếng Việt](#tiếng-việt)**

---

# English

## Features

### Project Management
- **Odoo Projects** — Create, import, and manage Odoo development projects with profiles
- **Other Projects** — Manage any type of project (auto-detects project type)
- **Odoo Workspace View** — Dashboard for managing multiple git repos in `addons/`: batch pull, commit, push, switch branch
- **Favourite & Search** — Star important projects, search by name/path/port

### Development Tools
- **Nginx Reverse Proxy** — SSL-enabled reverse proxy via Docker (mkcert for local HTTPS)
- **Python & Venv** — Detect Python installations, create/manage virtual environments
- **PostgreSQL** — Detect client tools & server instances, setup Docker-based PostgreSQL
- **Docker** — Status check, install, auto-start nginx container on app launch
- **VSCode Integration** — Open projects in VSCode, generate debug configurations

### Git Operations
- **Git Pull** — Pull all repos via script, or selective pull specific repos
- **Git Commit** — Select files/repos, commit with shared message, optional push
- **Git Branches** — Switch, create, delete, merge branches with visual UI
- **Selective Pull** — Pin repos you work on frequently, pull only those

### App Features
- **Auto Update** — Check for new releases and update in-app
- **Multi-language** — English, Vietnamese, Korean
- **Cross-platform** — Linux, macOS, Windows
- **Theme** — Light/Dark/System mode with accent color picker

## Installation

### Linux

1. Go to [Releases](https://github.com/namchamvinhcuu/workspace-configuration/releases/latest)
2. Download `WorkspaceConfiguration.AppImage`
3. Make executable and run:
   ```bash
   chmod +x WorkspaceConfiguration.AppImage
   ./WorkspaceConfiguration.AppImage
   ```

**Add to app menu & dock (optional):**

Move the AppImage to a permanent location, then create a `.desktop` file:

```bash
# Move AppImage
mkdir -p ~/AppImages
mv WorkspaceConfiguration.AppImage ~/AppImages/

# Create desktop entry
cat > ~/.local/share/applications/workspace_configuration.desktop << 'EOF'
[Desktop Entry]
Name=Workspace Configuration
Exec=$HOME/AppImages/WorkspaceConfiguration.AppImage
Icon=workspaces
Type=Application
Categories=Development;
Comment=Setup and manage development environments
Terminal=false
StartupWMClass=com.namchamvinhcuu.WorkspaceConfiguration
EOF
```

> Replace `Exec=` path if you placed the AppImage elsewhere.
> `StartupWMClass` is required for the dock to correctly group windows.

### macOS

1. Go to [Releases](https://github.com/namchamvinhcuu/workspace-configuration/releases/latest)
2. Download `WorkspaceConfiguration.dmg`
3. Open DMG → Drag to **Applications**
4. First launch: **System Settings** > **Privacy & Security** > **Open Anyway**

> If you see "App is damaged":
> ```bash
> xattr -cr /Applications/Workspace\ Configuration.app
> ```

### Windows

1. Go to [Releases](https://github.com/namchamvinhcuu/workspace-configuration/releases/latest)
2. Download all 4 files: `WorkspaceConfiguration.msix`, `certificate.pfx`, `install.ps1`, `install.bat`
3. Place all 4 files in the same folder
4. Right-click `install.bat` > **Run as Administrator**

## Prerequisites

### Docker (Required)

Docker is required for Nginx reverse proxy and PostgreSQL setup.

> **⚠️ macOS users:** The app supports both **OrbStack** and **Docker Desktop**.
> When installing Docker from the app, you can choose which one to install.
>
> **OrbStack is recommended** — lightweight, fast, and fully compatible with Docker CLI.
> The app auto-detects OrbStack and will use it when starting Docker.
>
> If Docker is already running (via OrbStack, Docker Desktop, or any other method), the app detects it automatically.

| Platform | Install method |
|----------|---------------|
| macOS | `brew install --cask orbstack` (recommended) or `brew install --cask docker` |
| Windows | `winget install Docker.DockerDesktop` |
| Linux | `apt install docker.io docker-compose-v2` |

Or install from the app: **Settings** > **Docker** > **Install**

### Python (Required for Odoo)

Python 3.10+ recommended. The app can detect and install Python via brew/apt/winget.

### mkcert (Auto-installed)

Required for local SSL certificates. Installed automatically when setting up Nginx.

## Quick Start

### 1. First Launch

- The app checks Docker status on launch
- If not found → banner with install link
- If installed but stopped → **Start Docker** button

### 2. Create an Odoo Project

**Quick Create (recommended):**
1. Create a **Profile** first (Profiles tab): venv, odoo-bin path, database settings
2. **Odoo Projects** > **Create** > Select profile, directory, name, ports
3. App generates: folder structure, odoo.conf, git script, venv symlink

**Import existing:**
1. **Odoo Projects** > **Import** > Browse to project directory
2. Ports auto-detected from `odoo.conf`

### 3. Setup Nginx (Optional)

Access projects via `https://myproject.yourdomain.test` instead of `http://localhost:8069`.

**First-time:**
1. **Settings** > **Nginx** > **Init Nginx Project**
2. Choose directory and domain suffix (e.g., `yourdomain.test`)

**Per project:**
1. Open project info (ℹ️ button) > **Setup Nginx** > Enter subdomain
2. App generates config, SSL cert, updates hosts file, reloads nginx

### 4. Odoo Workspace View

Manage multiple repos in `addons/`:

1. Click **Workspace** button (⬡) on any Odoo project
2. **Add repos** via search dropdown → pin repos you're working on
3. **Select repos** → check the ones to operate on (saved across restarts)
4. **Actions:** Pull Selected, Git Commit, Switch Branch
5. **Per-repo:** Pull, Push, Remove

### 5. Python & Venv

**Settings** > **Python**: detect installations, install new versions, manage venvs (list/scan/create)

### 6. PostgreSQL

**Settings** > **PostgreSQL**: detect client tools, server status, setup Docker PostgreSQL

## Auto Update

- Click **Check Update** (bottom of navigation rail)
- New version → banner with **Update Now**
- macOS: `.zip` replace + relaunch
- Linux: `.AppImage` replace + relaunch
- Windows: `.msix` install via `Add-AppPackage`

## Data Storage

```
~/.config/odoo_auto_config/odoo_auto_config.json
```

---

# Tiếng Việt

## Tính năng

### Quản lý dự án
- **Odoo Projects** — Tạo, import, quản lý dự án Odoo với profile
- **Other Projects** — Quản lý mọi loại dự án (tự nhận diện loại project)
- **Odoo Workspace View** — Dashboard quản lý nhiều repos trong `addons/`: pull, commit, push, switch branch hàng loạt
- **Favourite & Search** — Gắn sao dự án quan trọng, tìm kiếm theo tên/đường dẫn/port

### Công cụ phát triển
- **Nginx Reverse Proxy** — Reverse proxy SSL qua Docker (mkcert cho HTTPS local)
- **Python & Venv** — Phát hiện Python, tạo/quản lý virtual environment
- **PostgreSQL** — Phát hiện client tools & server, setup PostgreSQL Docker
- **Docker** — Kiểm tra trạng thái, cài đặt, tự động start nginx container khi mở app
- **VSCode** — Mở dự án trong VSCode, sinh cấu hình debug

### Git
- **Git Pull** — Pull tất cả repos qua script, hoặc selective pull repos cụ thể
- **Git Commit** — Chọn files/repos, commit chung message, tùy chọn push
- **Git Branches** — Chuyển, tạo, xóa, merge nhánh với giao diện trực quan
- **Selective Pull** — Ghim repos hay dùng, chỉ pull những repos đó

### Tính năng app
- **Tự động cập nhật** — Kiểm tra phiên bản mới và cập nhật trong app
- **Đa ngôn ngữ** — Tiếng Anh, Tiếng Việt, Tiếng Hàn
- **Đa nền tảng** — Linux, macOS, Windows
- **Giao diện** — Light/Dark/System, chọn màu chủ đạo

## Cài đặt

### Linux

1. Vào [Releases](https://github.com/namchamvinhcuu/workspace-configuration/releases/latest)
2. Tải `WorkspaceConfiguration.AppImage`
3. Cấp quyền chạy:
   ```bash
   chmod +x WorkspaceConfiguration.AppImage
   ./WorkspaceConfiguration.AppImage
   ```

**Thêm vào app menu & dock (tùy chọn):**

Di chuyển AppImage tới vị trí cố định, sau đó tạo file `.desktop`:

```bash
# Di chuyển AppImage
mkdir -p ~/AppImages
mv WorkspaceConfiguration.AppImage ~/AppImages/

# Tạo desktop entry
cat > ~/.local/share/applications/workspace_configuration.desktop << 'EOF'
[Desktop Entry]
Name=Workspace Configuration
Exec=$HOME/AppImages/WorkspaceConfiguration.AppImage
Icon=workspaces
Type=Application
Categories=Development;
Comment=Setup and manage development environments
Terminal=false
StartupWMClass=com.namchamvinhcuu.WorkspaceConfiguration
EOF
```

> Sửa đường dẫn `Exec=` nếu bạn đặt AppImage ở nơi khác.
> `StartupWMClass` bắt buộc để dock nhóm đúng cửa sổ app.

### macOS

1. Vào [Releases](https://github.com/namchamvinhcuu/workspace-configuration/releases/latest)
2. Tải `WorkspaceConfiguration.dmg`
3. Mở DMG → Kéo vào **Applications**
4. Lần đầu mở: **System Settings** > **Privacy & Security** > **Open Anyway**

> Nếu hiện "App is damaged":
> ```bash
> xattr -cr /Applications/Workspace\ Configuration.app
> ```

### Windows

1. Vào [Releases](https://github.com/namchamvinhcuu/workspace-configuration/releases/latest)
2. Tải đủ 4 file: `WorkspaceConfiguration.msix`, `certificate.pfx`, `install.ps1`, `install.bat`
3. Đặt 4 file cùng thư mục
4. Chuột phải `install.bat` > **Run as Administrator**

## Yêu cầu

### Docker (Bắt buộc)

Docker cần cho Nginx reverse proxy và PostgreSQL.

> **⚠️ Người dùng macOS:** App hỗ trợ cả **OrbStack** và **Docker Desktop**.
> Khi cài Docker từ app, bạn có thể chọn cài OrbStack hoặc Docker Desktop.
>
> **Khuyến nghị dùng OrbStack** — nhẹ, nhanh, tương thích hoàn toàn với Docker CLI.
> App tự phát hiện OrbStack và ưu tiên sử dụng khi start Docker.
>
> Nếu Docker đang chạy (qua OrbStack, Docker Desktop, hay cách khác), app tự phát hiện.

| Nền tảng | Cách cài |
|----------|----------|
| macOS | `brew install --cask orbstack` (khuyến nghị) hoặc `brew install --cask docker` |
| Windows | `winget install Docker.DockerDesktop` |
| Linux | `apt install docker.io docker-compose-v2` |

Hoặc cài từ app: **Settings** > **Docker** > **Install**

### Python (Bắt buộc cho Odoo)

Khuyến nghị Python 3.10+. App phát hiện và cài Python qua brew/apt/winget.

### mkcert (Tự động cài)

Cần cho chứng chỉ SSL local. App tự cài mkcert khi setup Nginx.

## Hướng dẫn sử dụng

### 1. Lần đầu mở app

- App kiểm tra Docker khi khởi động
- Chưa cài → hiện banner hướng dẫn cài
- Đã cài nhưng chưa chạy → hiện nút **Start Docker**

### 2. Tạo dự án Odoo

**Quick Create (khuyến nghị):**
1. Tạo **Profile** trước (tab Profiles): chọn venv, đường dẫn odoo-bin, cài đặt database
2. **Odoo Projects** > **Create** > Chọn profile, thư mục, tên, ports
3. App tự tạo: cấu trúc thư mục, odoo.conf, script git, symlink venv

**Import dự án có sẵn:**
1. **Odoo Projects** > **Import** > Chọn thư mục dự án
2. Ports tự phát hiện từ `odoo.conf`

### 3. Setup Nginx (Tùy chọn)

Truy cập dự án qua `https://myproject.yourdomain.test` thay vì `http://localhost:8069`.

**Lần đầu:**
1. **Settings** > **Nginx** > **Init Nginx Project**
2. Chọn thư mục và domain suffix (VD: `yourdomain.test`)

**Cho từng dự án:**
1. Mở info dự án (nút ℹ️) > **Setup Nginx** > Nhập subdomain
2. App tạo config, chứng chỉ SSL, cập nhật hosts file, reload nginx

### 4. Odoo Workspace View

Quản lý nhiều repos trong `addons/`:

1. Bấm nút **Workspace** (⬡) trên dự án Odoo
2. **Thêm repos** qua dropdown tìm kiếm → ghim repos đang làm việc
3. **Chọn repos** → tick những repos cần thao tác (lưu lại cho lần sau)
4. **Thao tác hàng loạt:** Pull Selected, Git Commit, Switch Branch
5. **Thao tác từng repo:** Pull, Push, Xóa khỏi workspace

> Danh sách repos ghim và selection được lưu theo từng dự án — giữ nguyên khi mở lại app.

### 5. Python & Venv

**Settings** > **Python**: phát hiện Python, cài phiên bản mới, quản lý venv (danh sách/quét/tạo mới)

### 6. PostgreSQL

**Settings** > **PostgreSQL**: phát hiện client tools, trạng thái server, setup PostgreSQL Docker

## Cập nhật tự động

- Bấm **Check Update** (cuối thanh navigation bên trái)
- Có phiên bản mới → hiện banner **Update Now**
- macOS: tải `.zip` thay thế + mở lại
- Linux: tải `.AppImage` thay thế + mở lại
- Windows: tải `.msix` cài qua `Add-AppPackage`

## Lưu trữ dữ liệu

Tất cả dữ liệu app lưu tại:
```
~/.config/odoo_auto_config/odoo_auto_config.json
```

Bao gồm: projects, workspaces, profiles, settings (theme, locale, nginx, git accounts...)

---

## License

This software is provided as-is for personal and commercial use.
