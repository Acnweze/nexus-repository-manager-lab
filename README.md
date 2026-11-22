# Sonatype Nexus Repository Manager on Ubuntu Server

A hands-on DevOps lab documenting the installation and configuration of Sonatype Nexus Repository Manager on an Ubuntu Server virtual machine hosted in Microsoft Azure. The lab also covers publishing and verifying Maven artifacts, including a Spring Boot application build.

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

## Lab walkthrough and screenshots

### 1. Connect to the Azure virtual machine

SSH access to the Ubuntu VM used for the lab.

![SSH connection to the virtual machine](<ssh to vitaul machine.jpg>)

### 2. Install and access Nexus Repository Manager

The Nexus Repository Manager interface was brought online and accessed through the browser.

![Sonatype Nexus Repository Manager](<nexus sonatype.jpg>)

![Nexus login page](<nexus login.jpg>)

### 3. Verify the Nexus service

The Nexus service was checked to confirm that it was active.

![Nexus service active](<nexus status active.jpg>)

### 4. Configure Nexus users and repository policies

The lab included user administration and repository policy configuration.

![Nexus users added](<nexus users added.jpg>)

![Nexus applied policy](<nexus applied policy.jpg>)

![Nexus cleaning policy](<nexus cleaning policy.jpg>)

### 5. Build and publish a Maven application

A Maven build was completed and its artifact was deployed to Nexus. The repository view was checked to confirm that the snapshot artifact was available.

![Successful Maven build](<maven build successful.jpg>)

![Maven application deployment successful](<maven app deployment success.jpg>)

![Maven snapshots in Nexus](<maven snapshots in nexus.jpg>)

### 6. Spring Boot application experiment

The Spring Boot application used in the Maven build/deployment experiment is shown below.

![Spring Boot application](<spring boot.jpg>)

### 7. Application port verification

A terminal check was used to inspect the process listening on port `7071` during the Java application experiment.

![Process listening on port 7071](<grep 7071.jpg>)

## Implementation summary

### Ubuntu and Java setup

Prepared an Ubuntu Server 24.04.5 LTS VM and installed/verified OpenJDK 25.0.4.1.

### Nexus installation and service account

Installed Sonatype Nexus Repository Manager `3.98.1-01` under `/opt/nexus-3.98.1-01` and ran the service under the dedicated, non-root Linux account `ada`.

### systemd service management

Configured Nexus as a systemd-managed service and verified its active state and HTTP responses.

### Azure network access

Configured the Azure Network Security Group to allow access to the Nexus web interface on TCP port `8081`. The inbound source was restricted to the permitted client IP during the lab.

> Security note: avoid exposing the Nexus administration interface to the entire internet. Use a restricted source range, private connectivity, or an appropriately secured reverse proxy for real environments.

### Health verification

Checked the local web interface and Nexus status endpoint using `curl`, then confirmed browser access after resolving the initial network-access issue.

## Skills demonstrated

- Ubuntu Linux server administration
- Java / OpenJDK installation and verification
- Linux users, groups, ownership, and permissions
- Running an application under a non-root service account
- systemd service configuration and troubleshooting
- Azure VM networking and Network Security Group rules
- Nexus Repository Manager installation and administration
- Maven build and artifact deployment
- Repository and snapshot verification
- Spring Boot application build/deployment workflow
- HTTP endpoint and service-health verification

## Security and learning notes

This repository documents a practical learning lab, not a production deployment guide. Production use should include HTTPS, authentication and authorization review, secure secret management, backups, monitoring, and network access controls. Do not commit passwords, private keys, tokens, or other secrets.

---

**Project type:** DevOps / Linux Administration / Azure Infrastructure / Artifact Repository Lab
