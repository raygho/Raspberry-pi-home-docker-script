# Raspberry Pi Automated Setup Script

This repository contains a bash script to automate the setup of a Raspberry Pi for development and server use. The script provides a menu-driven interface to install and configure essential tools, Docker containers, databases, and developer utilities.

## Features

- **Menu-driven installation** of:
  - System update & upgrade
  - Python, pip, venv
  - Git
  - Screen
  - Docker (with automatic setup)
  - MongoDB, MySQL, InfluxDB, Grafana, Portainer, Traefik (all as Docker containers)
  - SQLite (via Docker helper)
  - UFW firewall (auto-configures ports for installed services)
- **Centralised directory structure** under `~/Developer/docker_containers`:
  - `configs/` for configuration files (docker-compose.yml, container_configs.txt)
  - `volumes/` for persistent data storage for each Docker service
- **Automatic configuration tracking**: URLs, credentials, and connection info are saved in `container_configs.txt`.
- **Status tracking**: See which services are installed and running.
- **Selective install**: Run multiple setup steps at once (e.g., `1,2,5,6,13`).

## Usage

1. **Clone the repository**
   ```bash
   git clone https://github.com/raygho/rpi-setup.git
   cd rpi-setup
   ```
2. **Make the script executable**
   ```bash
   chmod +x rpi_setup.sh
   ```
3. **Run the script with sudo**
   ```bash
   sudo ./rpi_setup.sh
   ```
4. **Follow the menu prompts** to install/configure desired services.

## Directory Structure

```
~/Developer/
└── docker_containers/
    ├── configs/
    │   ├── docker-compose.yml
    │   └── container_configs.txt
    └── volumes/
        ├── mongodb/
        ├── mysqldb/
        ├── sqlite/
        ├── influxdb/
        ├── grafana/
        ├── portainer/
        └── traefik/
```

## Services & Ports

| Service    | Port(s)   | Default Credentials         |
|------------|-----------|----------------------------|
| MongoDB    | 27017     | admin / (none)             |
| MySQL      | 3306      | root / set during install  |
| InfluxDB   | 8086      | admin / password123        |
| Grafana    | 3000      | admin / admin123           |
| Portainer  | 9000,9443 | set on first access        |
| Traefik    | 80,443,8080 | dashboard: 8080          |
| SQLite     | -         | file-based, no login       |

## Firewall

- UFW is installed and configured automatically.
- Only necessary ports for installed services are opened.

## Customisation

- You can edit the script to add more services or change configuration details.
- All persistent data and configs are stored in the `Developer/docker_containers` directory for easy backup and migration.


