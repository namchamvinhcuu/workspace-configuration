# Workspace Configuration

A desktop application that helps developers set up and manage development environments.
Supports **Odoo projects** and other project types (Flutter, React, NextJS, .NET, Rust, Go, Java...).

---

**[English](#english)** | **[Tiếng Việt](#tiếng-việt)** | **[한국어](#한국어)**

---

# English

## Features

### Project Management
- **Odoo Projects** — Create, import, and manage Odoo development projects with profiles
- **Other Projects** — Manage any type of project (auto-detects project type)
- **Odoo Workspace View** — Dashboard for managing pinned git repos in `addons/`: batch pull, commit, push, publish
- **Favourite & Search** — Star important projects, search/filter by name, path, type
- **Clone Repository** — Clone Git repos directly from the app with branch and shallow clone options

### Development Tools
- **Nginx Reverse Proxy** — SSL-enabled reverse proxy via Docker (mkcert for local HTTPS)
- **Python & Venv** — Detect Python installations, create/manage virtual environments
- **PostgreSQL** — Detect client tools & server instances, setup Docker-based PostgreSQL
- **Docker** — Status check, install (OrbStack/Docker Desktop), auto-start nginx on launch
- **VSCode Integration** — Open projects in VSCode, generate debug configurations

### Git Operations
- **Git Branches** — Switch, create, delete, publish, clean stale branches with visual UI
- **Git Pull** — Pull all repos via script (Odoo), or single repo pull (Other Projects)
- **Git Commit** — Select files/repos, commit with message, optional push
- **Create PR** — Create GitHub Pull Request directly (requires `gh` CLI). Auto-detects uncommitted changes
- **Workspace Batch** — Pull, commit, publish across multiple repos simultaneously

### App Features
- **Auto Update** — Check for new releases and update in-app
- **Multi-Instance** — Open multiple windows, settings sync across instances automatically
- **Multi-language** — English, Vietnamese, Korean
- **Cross-platform** — Linux (AppImage/deb/rpm), macOS (DMG), Windows (MSIX installer / portable exe)
- **Theme** — Light/Dark/System mode with accent color picker
- **Window Sizes** — Small, Medium, Large presets (saved across sessions)

## Installation

### Linux (AppImage — portable, any distro)

```bash
chmod +x WorkspaceConfiguration.AppImage
./WorkspaceConfiguration.AppImage
```

<details>
<summary>Add to app menu & dock (optional)</summary>

```bash
mkdir -p ~/AppImages
mv WorkspaceConfiguration.AppImage ~/AppImages/

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
</details>

### Linux (deb — Ubuntu/Debian/Mint)

```bash
sudo dpkg -i WorkspaceConfiguration-*.deb
sudo apt-get install -f  # install dependencies if needed
```

### Linux (rpm — Fedora/RHEL/CentOS)

```bash
sudo dnf install ./WorkspaceConfiguration-*.rpm
```

### macOS

1. Download `WorkspaceConfiguration.dmg` from [Releases](https://github.com/namchamvinhcuu/workspace-configuration/releases/latest)
2. Open DMG → Drag to **Applications**
3. First launch: **System Settings** > **Privacy & Security** > **Open Anyway**

> If you see "App is damaged": `xattr -cr /Applications/Workspace\ Configuration.app`

### Windows (Installer — MSIX)

1. Download all 4 files: `.msix`, `.pfx`, `.ps1`, `.bat`
2. Place in the same folder
3. Right-click `install.bat` > **Run as Administrator**
4. Launch from **Start Menu**

### Windows (Portable)

1. Download `WorkspaceConfiguration.exe`
2. Place anywhere and double-click to run — no installation needed

## Card Interaction

| Action | Effect |
|--------|--------|
| Single click | Select card (highlighted border) |
| Double click | Open in VSCode |
| Right click | Context menu (all actions) |
| Mouse back button | Navigate back |
| Mouse forward button | Navigate forward |

## Quick Start

### 1. First Launch
- App checks Docker status — banner if not found/running
- Click **Start Docker** or **Go to Settings** to install
- Docker banner auto-dismisses when Docker starts (polls every 10s)

### 2. Create an Odoo Project

**Quick Create:**
1. Create a **Profile** (Profiles tab): venv, database settings, git account
2. **Odoo Projects** > **Create** > Select profile → generates project structure

**Import existing:**
1. **Odoo Projects** > **Import** > Browse to project directory
2. Ports auto-detected from `odoo.conf`

### 3. Manage Other Projects

**Import:** Browse to any project folder — type auto-detected from marker files.

**Clone:** Enter Git URL → clone with optional branch and shallow clone.

### 4. Setup Nginx (Optional)

1. **Settings** > **Nginx** > **Init Nginx Project** (first time)
2. Open project info > **Setup Nginx** > Enter subdomain
3. App generates config, SSL cert, updates hosts file, reloads nginx

### 5. Odoo Workspace View

1. Click **Workspace** button on any Odoo project
2. Search and pin repos from `addons/`
3. Batch actions: Pull Selected, Git Commit, Publish Branch
4. Per-repo: Pull, Push, Branch dialog, Remove

### 6. Multi-Instance

- Click **New Window** in sidebar to open another instance
- Settings sync automatically between instances
- Each window runs as independent process

## Auto Update

- Click **Check Update** in sidebar (shows current version)
- New version → banner with **Update Now**
- macOS/Linux: auto-replace + relaunch
- Windows MSIX: auto-install + relaunch
- Windows portable: auto-replace, reopen manually

## Prerequisites

| Tool | Required for | Install |
|------|-------------|---------|
| Docker | Nginx, PostgreSQL | App can install (Settings > Docker) |
| Python 3.10+ | Odoo projects | App can install (Settings > Python) |
| Git | All git operations | App auto-installs if missing |
| `gh` CLI | Create PR | App auto-installs if missing |
| mkcert | Local SSL | App auto-installs when setting up Nginx |

## Data Storage

```
~/.config/odoo_auto_config/odoo_auto_config.json
```

Contains: projects, workspaces, profiles, settings (theme, locale, nginx, git accounts...)

## Supported Package Managers (Linux)

| Distro | Package Manager | Status |
|--------|----------------|--------|
| Ubuntu, Debian, Mint | apt | Supported |
| Fedora, RHEL, CentOS | dnf | Supported |
| Others | — | Use AppImage |

---

# Tiếng Việt

## Tính năng

### Quản lý dự án
- **Odoo Projects** — Tạo, import, quản lý dự án Odoo với profile
- **Other Projects** — Quản lý mọi loại dự án (tự nhận diện loại project)
- **Odoo Workspace View** — Dashboard quản lý repos đã ghim trong `addons/`: pull, commit, push, publish hàng loạt
- **Favourite & Search** — Gắn sao, tìm kiếm/lọc theo tên, đường dẫn, loại
- **Clone Repository** — Clone repos Git trực tiếp từ app, chọn branch và shallow clone

### Công cụ phát triển
- **Nginx Reverse Proxy** — Reverse proxy SSL qua Docker (mkcert cho HTTPS local)
- **Python & Venv** — Phát hiện Python, tạo/quản lý virtual environment
- **PostgreSQL** — Phát hiện client tools & server, setup PostgreSQL Docker
- **Docker** — Kiểm tra trạng thái, cài đặt (OrbStack/Docker Desktop), tự start nginx khi mở app
- **VSCode** — Mở dự án trong VSCode, sinh cấu hình debug

### Git
- **Git Branches** — Chuyển, tạo, xóa, publish, clean stale branches
- **Git Pull** — Pull tất cả repos qua script (Odoo), hoặc pull đơn lẻ (Other Projects)
- **Git Commit** — Chọn files/repos, commit chung message, tùy chọn push
- **Create PR** — Tạo Pull Request trên GitHub (cần `gh` CLI). Tự phát hiện file chưa commit
- **Workspace Batch** — Pull, commit, publish nhiều repos cùng lúc

### Tính năng app
- **Tự động cập nhật** — Kiểm tra và cập nhật phiên bản mới
- **Multi-Instance** — Mở nhiều cửa sổ, settings tự đồng bộ
- **Đa ngôn ngữ** — Tiếng Anh, Tiếng Việt, Tiếng Hàn
- **Đa nền tảng** — Linux (AppImage/deb/rpm), macOS (DMG), Windows (MSIX / portable exe)
- **Giao diện** — Light/Dark/System, chọn màu chủ đạo
- **Kích thước cửa sổ** — Nhỏ, Vừa, Lớn (lưu lại cho lần sau)

## Cài đặt

### Linux (AppImage — portable, mọi distro)

```bash
chmod +x WorkspaceConfiguration.AppImage
./WorkspaceConfiguration.AppImage
```

<details>
<summary>Thêm vào app menu & dock (tùy chọn)</summary>

```bash
mkdir -p ~/AppImages
mv WorkspaceConfiguration.AppImage ~/AppImages/

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
</details>

### Linux (deb — Ubuntu/Debian/Mint)

```bash
sudo dpkg -i WorkspaceConfiguration-*.deb
sudo apt-get install -f  # cài dependencies nếu cần
```

### Linux (rpm — Fedora/RHEL/CentOS)

```bash
sudo dnf install ./WorkspaceConfiguration-*.rpm
```

### macOS

1. Tải `WorkspaceConfiguration.dmg` từ [Releases](https://github.com/namchamvinhcuu/workspace-configuration/releases/latest)
2. Mở DMG → Kéo vào **Applications**
3. Lần đầu mở: **System Settings** > **Privacy & Security** > **Open Anyway**

> Nếu hiện "App is damaged": `xattr -cr /Applications/Workspace\ Configuration.app`

### Windows (Installer — MSIX)

1. Tải đủ 4 file: `.msix`, `.pfx`, `.ps1`, `.bat`
2. Đặt cùng thư mục
3. Chuột phải `install.bat` > **Run as Administrator**
4. Mở từ **Start Menu**

### Windows (Portable)

1. Tải `WorkspaceConfiguration.exe`
2. Đặt bất kỳ đâu, double-click để chạy — không cần cài đặt

## Thao tác trên Card

| Thao tác | Kết quả |
|----------|---------|
| Click 1 lần | Chọn card (viền highlight) |
| Double click | Mở trong VSCode |
| Click chuột phải | Menu ngữ cảnh (đầy đủ thao tác) |
| Nút Back trên chuột | Quay lại |
| Nút Forward trên chuột | Tiến tới |

## Hướng dẫn nhanh

### 1. Lần đầu mở app
- App kiểm tra Docker — hiện banner nếu chưa cài/chưa chạy
- Bấm **Start Docker** hoặc **Go to Settings** để cài
- Banner tự biến mất khi Docker khởi động (kiểm tra mỗi 10 giây)

### 2. Tạo dự án Odoo

**Quick Create:**
1. Tạo **Profile** (tab Profiles): chọn venv, cài đặt database, tài khoản git
2. **Odoo Projects** > **Create** > Chọn profile → tạo cấu trúc project

**Import dự án có sẵn:**
1. **Odoo Projects** > **Import** > Chọn thư mục dự án
2. Ports tự phát hiện từ `odoo.conf`

### 3. Quản lý Other Projects

**Import:** Chọn thư mục dự án — tự nhận diện loại từ file đặc trưng.

**Clone:** Nhập URL Git → clone với tùy chọn branch và shallow clone.

### 4. Setup Nginx (Tùy chọn)

1. **Settings** > **Nginx** > **Init Nginx Project** (lần đầu)
2. Mở info dự án > **Setup Nginx** > Nhập subdomain
3. App tạo config, chứng chỉ SSL, cập nhật hosts file, reload nginx

### 5. Odoo Workspace View

1. Bấm nút **Workspace** trên dự án Odoo
2. Tìm kiếm và ghim repos từ `addons/`
3. Thao tác hàng loạt: Pull Selected, Git Commit, Publish Branch
4. Thao tác từng repo: Pull, Push, Branch dialog, Xóa

### 6. Multi-Instance

- Bấm **New Window** ở sidebar để mở cửa sổ mới
- Settings tự đồng bộ giữa các instance
- Mỗi cửa sổ chạy như process độc lập

## Cập nhật tự động

- Bấm **Check Update** ở sidebar (hiện phiên bản hiện tại)
- Có phiên bản mới → banner **Update Now**
- macOS/Linux: tự thay thế + mở lại
- Windows MSIX: tự cài + mở lại
- Windows portable: tự thay thế, mở lại thủ công

## Yêu cầu

| Công cụ | Cần cho | Cài đặt |
|---------|---------|---------|
| Docker | Nginx, PostgreSQL | App có thể cài (Settings > Docker) |
| Python 3.10+ | Dự án Odoo | App có thể cài (Settings > Python) |
| Git | Mọi thao tác git | App tự cài nếu thiếu |
| `gh` CLI | Create PR | App tự cài nếu thiếu |
| mkcert | SSL local | App tự cài khi setup Nginx |

## Lưu trữ dữ liệu

```
~/.config/odoo_auto_config/odoo_auto_config.json
```

Bao gồm: projects, workspaces, profiles, settings (theme, locale, nginx, git accounts...)

## Package Manager hỗ trợ (Linux)

| Distro | Package Manager | Trạng thái |
|--------|----------------|------------|
| Ubuntu, Debian, Mint | apt | Hỗ trợ |
| Fedora, RHEL, CentOS | dnf | Hỗ trợ |
| Khác | — | Dùng AppImage |

---

# 한국어

## 기능

### 프로젝트 관리
- **Odoo Projects** — 프로필을 사용한 Odoo 개발 프로젝트 생성, 가져오기, 관리
- **Other Projects** — 모든 유형의 프로젝트 관리 (프로젝트 유형 자동 감지)
- **Odoo Workspace View** — `addons/`의 고정 repo 관리 대시보드: 일괄 pull, commit, push, publish
- **즐겨찾기 & 검색** — 중요 프로젝트에 별표, 이름/경로/유형으로 검색/필터
- **Clone Repository** — 앱에서 직접 Git repo 클론, branch 및 shallow clone 옵션

### 개발 도구
- **Nginx Reverse Proxy** — Docker를 통한 SSL 리버스 프록시 (로컬 HTTPS용 mkcert)
- **Python & Venv** — Python 설치 감지, 가상 환경 생성/관리
- **PostgreSQL** — 클라이언트 도구 & 서버 인스턴스 감지, Docker 기반 PostgreSQL 설정
- **Docker** — 상태 확인, 설치 (OrbStack/Docker Desktop), 앱 실행 시 nginx 자동 시작
- **VSCode** — VSCode에서 프로젝트 열기, 디버그 구성 생성

### Git 작업
- **Git Branches** — 시각적 UI로 branch 전환, 생성, 삭제, publish, 정리
- **Git Pull** — 스크립트로 모든 repo pull (Odoo) 또는 단일 repo pull
- **Git Commit** — 파일/repo 선택, 메시지와 함께 커밋, push 옵션
- **Create PR** — GitHub Pull Request 직접 생성 (`gh` CLI 필요). 커밋되지 않은 변경사항 자동 감지
- **Workspace 일괄 작업** — 여러 repo에 동시에 pull, commit, publish

### 앱 기능
- **자동 업데이트** — 새 릴리스 확인 및 인앱 업데이트
- **Multi-Instance** — 여러 창 열기, 인스턴스 간 설정 자동 동기화
- **다국어** — English, Tiếng Việt, 한국어
- **크로스 플랫폼** — Linux (AppImage/deb/rpm), macOS (DMG), Windows (MSIX / portable exe)
- **테마** — 라이트/다크/시스템 모드, 강조 색상 선택
- **창 크기** — 소, 중, 대 프리셋 (세션 간 저장)

## 설치

### Linux (AppImage — 포터블, 모든 배포판)

```bash
chmod +x WorkspaceConfiguration.AppImage
./WorkspaceConfiguration.AppImage
```

### Linux (deb — Ubuntu/Debian/Mint)

```bash
sudo dpkg -i WorkspaceConfiguration-*.deb
sudo apt-get install -f
```

### Linux (rpm — Fedora/RHEL/CentOS)

```bash
sudo dnf install ./WorkspaceConfiguration-*.rpm
```

### macOS

1. [Releases](https://github.com/namchamvinhcuu/workspace-configuration/releases/latest)에서 `WorkspaceConfiguration.dmg` 다운로드
2. DMG 열기 → **Applications**로 드래그
3. 첫 실행: **시스템 설정** > **개인 정보 보호 및 보안** > **그래도 열기**

> "앱이 손상되었습니다" 메시지: `xattr -cr /Applications/Workspace\ Configuration.app`

### Windows (설치 — MSIX)

1. 4개 파일 모두 다운로드: `.msix`, `.pfx`, `.ps1`, `.bat`
2. 같은 폴더에 배치
3. `install.bat` 우클릭 > **관리자 권한으로 실행**
4. **시작 메뉴**에서 실행

### Windows (포터블)

1. `WorkspaceConfiguration.exe` 다운로드
2. 아무 곳에나 놓고 더블 클릭하여 실행 — 설치 불필요

## 카드 상호작용

| 동작 | 결과 |
|------|------|
| 한 번 클릭 | 카드 선택 (테두리 강조) |
| 더블 클릭 | VSCode에서 열기 |
| 우클릭 | 컨텍스트 메뉴 |
| 마우스 뒤로 버튼 | 뒤로 이동 |
| 마우스 앞으로 버튼 | 앞으로 이동 |

## 요구 사항

| 도구 | 용도 | 설치 |
|------|------|------|
| Docker | Nginx, PostgreSQL | 앱에서 설치 가능 (Settings > Docker) |
| Python 3.10+ | Odoo 프로젝트 | 앱에서 설치 가능 (Settings > Python) |
| Git | 모든 git 작업 | 없으면 자동 설치 |
| `gh` CLI | PR 생성 | 없으면 자동 설치 |
| mkcert | 로컬 SSL | Nginx 설정 시 자동 설치 |

## 데이터 저장

```
~/.config/odoo_auto_config/odoo_auto_config.json
```

## 지원 패키지 매니저 (Linux)

| 배포판 | 패키지 매니저 | 상태 |
|--------|-------------|------|
| Ubuntu, Debian, Mint | apt | 지원 |
| Fedora, RHEL, CentOS | dnf | 지원 |
| 기타 | — | AppImage 사용 |

---

## Download

Go to **[Releases](https://github.com/namchamvinhcuu/workspace-configuration/releases/latest)** to download the latest version for your platform.

## License

This software is provided as-is for personal and commercial use.
