# Sonatype Nexus Repository Manager on Ubuntu Server

A hands-on DevOps lab documenting the installation and configuration of Sonatype Nexus Repository Manager on an Ubuntu Server virtual machine hosted in Microsoft Azure.

## Lab environment

| Component | Configuration |
|---|---|
| Cloud platform | Microsoft Azure |
| Operating system | Ubuntu Server 24.04.5 LTS |
| Java runtime | OpenJDK 25.0.4.1 |
| Repository manager | Sonatype Nexus Repository Manager 3.98.1-01 |
| Linux service account | `ada` |
| Web interface | TCP port `8081` |
| Installation location | `/opt/nexus-3.98.1-01` |

## Objectives

- Prepare an Ubuntu Server VM for Nexus Repository Manager.
- Install and verify OpenJDK.
- Configure a dedicated, non-root Linux account for the Nexus process.
- Install Nexus Repository Manager.
- Configure Nexus to run as a systemd service.
- Configure Azure network access for the Nexus web interface.
- Verify the service locally and through its HTTP endpoints.

## Implementation summary

### 1. Prepare the Ubuntu server

Updated the Ubuntu environment and installed the Java runtime required for the Nexus installation. Java and the Java compiler were verified with `java -version` and `javac -version`.

### 2. Install Nexus Repository Manager

Nexus Repository Manager version `3.98.1-01` was installed under `/opt`, using `/opt/nexus-3.98.1-01` as the installation directory.

### 3. Configure a dedicated service account

A dedicated Linux account was used to run Nexus rather than running the application as root. The Nexus process was verified under the `ada` account.

### 4. Configure the systemd service

Nexus was configured as a systemd-managed service. Service status, restart behaviour, and logs were checked using `systemctl` and `journalctl`.

### 5. Configure Azure network access

The Azure Network Security Group was configured to allow access to the Nexus web interface on TCP port `8081`. The inbound source was restricted to the permitted client IP during the lab.

> Security note: avoid exposing the Nexus administration interface to the entire internet. Use a restricted source range, private connectivity, or an appropriately secured reverse proxy for real environments.

### 6. Verify the service

The service was checked locally using `curl` against `http://localhost:8081` and the Nexus status endpoint at `/service/rest/v1/status`. Successful HTTP responses confirmed that the web service and status endpoint were responding. Browser access was also verified after resolving the initial network-access issue.

## Skills demonstrated

- Ubuntu Linux server administration
- Java / OpenJDK installation and verification
- Linux users, groups, ownership, and permissions
- Running an application under a non-root service account
- systemd service configuration and troubleshooting
- Azure VM networking and Network Security Group rules
- HTTP endpoint and service-health verification
- Troubleshooting remote application access

## Screenshots

Screenshots from the lab should document the server configuration, Nexus service status, and browser access. Add the existing image files to a `screenshots/` folder and link them here using their exact filenames.

## Notes

This repository documents a practical learning lab, not a production deployment guide. Production use should include HTTPS, authentication and authorization review, secure secret management, backups, monitoring, and network access controls.

---

**Project type:** DevOps / Linux Administration / Azure Infrastructure Lab
