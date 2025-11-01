# obsidian-remote Fork

This is a fork of [obsidian-remote](https://github.com/sytone/obsidian-remote) customized for local development and deployment.

## Changes from Upstream

### Configuration Management
- Added `.env` file support for managing volume paths without checking them into version control
- Environment variables `VAULTS_PATH` and `CONFIG_PATH` allow users to specify their own vault and config locations
- `.env` is gitignored to prevent accidental commits of local paths

### Docker Compose Setup
- Created `docker-compose.yml` for easier local development
- Configured to use port `8888` for HTTP access (instead of default `8080`)
- Includes git support via `DOCKER_MODS=linuxserver/mods:universal-git` for obsidian-git plugin

## Quick Start

1. **Copy the example environment file:**
   ```powershell
   Copy-Item .env.example .env
   ```

2. **Update `.env` with your paths:**
   ```
   VAULTS_PATH=/mnt/e/path/to/your/vaults
   CONFIG_PATH=/mnt/e/path/to/your/config
   ```

3. **Start the container:**
   ```powershell
   docker-compose up -d
   ```

4. **Access Obsidian:**
   - Open `http://localhost:8888/` in your browser

## Environment Variables

See `.env` file for configuration. Key variables:
- `VAULTS_PATH` - Path to your Obsidian vaults (WSL2 format, e.g., `/mnt/e/...`)
- `CONFIG_PATH` - Path to Obsidian config directory

## Notes

- Paths should use WSL2 format (`/mnt/e/...`) not Windows format (`E:\...`)
- The `/config` directory stores SSH keys and git credentials for the obsidian-git plugin
- Container runs on port `8888` locally; adjust in `docker-compose.yml` if needed

## Upstream Repository

Original project: https://github.com/sytone/obsidian-remote
