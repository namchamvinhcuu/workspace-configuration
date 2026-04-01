# Workspace Configuration

A desktop application that helps developers set up and manage development environments.

Supports **Odoo projects** and other project types (Flutter, React, NextJS, .NET, Rust, Go, Java...).

Provides a GUI to manage projects, Python/venv, Nginx reverse proxy, Docker, PostgreSQL, and VSCode debug configurations.

## Features

- **Odoo Projects** - Create, manage, and configure Odoo development projects with profiles
- **Other Projects** - Manage any type of project (auto-detects project type from marker files)
- **Nginx Reverse Proxy** - Setup SSL-enabled reverse proxy via Docker (mkcert for local HTTPS)
- **Python & Venv** - Detect Python installations, create/manage virtual environments
- **PostgreSQL** - Detect client tools & server instances, setup Docker-based PostgreSQL
- **Docker** - Status check, auto-start nginx container on app launch
- **VSCode Integration** - Generate debug configurations (launch.json)
- **Auto Update** - Check for new releases and update in-app
- **Multi-language** - English, Vietnamese, Korean
- **Cross-platform** - Linux, macOS, Windows

## Installation

### Linux

1. Go to [Releases](https://github.com/namchamvinhcuu/workspace-configuration/releases/latest)
2. Download `WorkspaceConfiguration.AppImage`
3. Make it executable:
   ```bash
   chmod +x WorkspaceConfiguration.AppImage
   ```
4. Run:
   ```bash
   ./WorkspaceConfiguration.AppImage
   ```

> **Tip:** Move the AppImage to `~/Applications/` or `/opt/` for easy access. You can also create a desktop shortcut.

### macOS

1. Go to [Releases](https://github.com/namchamvinhcuu/workspace-configuration/releases/latest)
2. Download `WorkspaceConfiguration.dmg`
3. Open the DMG file
4. Drag **Workspace Configuration** to the **Applications** folder
5. First launch: right-click the app > **Open** (to bypass Gatekeeper)

> **Note:** If you see "App is damaged", open Terminal and run:
> ```bash
> xattr -cr /Applications/Workspace\ Configuration.app
> ```

### Windows

1. Go to [Releases](https://github.com/namchamvinhcuu/workspace-configuration/releases/latest)
2. Download **all 4 files**:
   - `WorkspaceConfiguration.msix`
   - `certificate.pfx`
   - `install.ps1`
   - `install.bat`
3. Place all 4 files in the **same folder**
4. Right-click `install.bat` > **Run as Administrator**
5. The installer will:
   - Install the signing certificate
   - Install the MSIX application
6. Launch **Workspace Configuration** from the Start Menu

> **Note:** The certificate installation requires Administrator privileges. This is a self-signed certificate needed for sideloading the MSIX package.

## Quick Start

### 1. First Launch

When you open the app for the first time:
- The app checks if **Docker** is installed and running
- If Docker is not found, a banner appears with a link to Settings > Docker to install it

### 2. Create an Odoo Project

1. Go to **Odoo Projects** tab
2. Click the **+** button to create a new project
3. Fill in project details:
   - **Name** - Project name
   - **Path** - Select project directory
   - **Ports** - Odoo HTTP and longpolling ports
   - **Description** (optional)
4. Click **Save**

> **Quick Create:** Set up a **Profile** first (Profiles tab), then use Quick Create to generate projects with pre-configured settings including folder structure, venv, and odoo.conf.

### 3. Setup Nginx Reverse Proxy (Optional)

This allows you to access projects via `https://myproject.localhost` instead of `http://localhost:8069`.

**First-time setup:**

1. Go to **Settings** > **Nginx** tab
2. Click **Init Nginx Project**
3. Choose a directory for nginx configuration files
4. The app will:
   - Create nginx config structure (conf.d/, certs/, docker-compose.yml)
   - Install **mkcert** if needed (for local SSL certificates)
   - Start the nginx Docker container

**Add nginx to a project:**

1. Go to **Odoo Projects** or **Other Projects**
2. Right-click a project > **Setup Nginx**
3. Enter a subdomain (e.g., `myproject`)
4. The app will:
   - Generate nginx config with SSL
   - Create SSL certificate via mkcert
   - Add entry to hosts file (requires password/admin)
   - Reload nginx container
5. Access your project at `https://myproject.localhost`

### 4. Manage Python & Virtual Environments

1. Go to **Settings** > **Python** tab
2. View detected Python installations
3. Install Python if needed (via brew/apt/winget)
4. **Venv Manager** (embedded below):
   - **List** - View registered virtual environments
   - **Scan** - Find venvs in a directory
   - **Create** - Create a new venv with a specific Python version

### 5. Setup PostgreSQL

1. Go to **Settings** > **PostgreSQL** tab
2. **Client Tools** - Shows detected PostgreSQL client tools (psql, pg_dump, etc.)
3. **Server Status** - Shows running PostgreSQL instances (Docker + local)
4. If no server found, click **Setup PostgreSQL Docker** to create a Docker-based PostgreSQL instance

## Auto Update

The app checks for updates from this repository. When a new version is available:
1. A notification appears in the app
2. Click **Download** to download the update
3. Click **Install** to apply the update (the app will restart)

## Requirements

- **Docker** - Required for Nginx reverse proxy and PostgreSQL Docker setup
- **Python** - Required for Odoo development (venv management)
- **mkcert** - Auto-installed by the app for local SSL certificates

## License

This software is provided as-is for personal and commercial use.
