# Linux Enterprise Automation

> Enterprise-grade Linux administration and automation using Bash, Ansible, GitHub Actions, and Infrastructure as Code principles.

![Platform](https://img.shields.io/badge/Platform-RHEL%20%7C%20Rocky%20%7C%20AlmaLinux-red)
![Automation](https://img.shields.io/badge/Automation-Ansible-blue)
![CI](https://img.shields.io/badge/CI-GitHub%20Actions-success)
![License](https://img.shields.io/badge/License-MIT-green)

---

## Overview

This project demonstrates how an enterprise Linux/DevOps engineer automates the complete lifecycle of Linux servers—from a freshly installed operating system to a production-ready, secure, compliant, and auditable environment.

Rather than treating Linux administration as a collection of manual commands, this repository implements repeatable, idempotent automation that can be applied consistently across an entire fleet of servers.

The project focuses on real operational tasks performed by Enterprise Linux, Platform Engineering, and DevOps teams.

---

# Objectives

- Automate Day-0 server provisioning
- Standardize server configuration
- Enforce enterprise security baselines
- Automate operating system patching
- Perform compliance auditing
- Centralize system logging
- Automate user lifecycle management
- Replace cron jobs with systemd timers
- Implement Infrastructure as Code practices
- Validate automation through CI/CD

---

# Technology Stack

| Technology | Purpose |
|------------|----------|
| Bash | Bootstrap automation |
| Ansible | Configuration management |
| GitHub Actions | Continuous Integration |
| ShellCheck | Shell linting |
| ansible-lint | Playbook validation |
| firewalld | Host firewall |
| SELinux | Mandatory Access Control |
| rsyslog | Log forwarding |
| chrony | NTP synchronization |
| systemd Timers | Scheduled automation |
| LVM | Snapshot & rollback |
| OpenSSH | Secure remote access |

---

# Architecture

```

+----------------------+
| Control Node |
| Ubuntu/RHEL |
| |
| Bash |
| Ansible |
| GitHub Actions |
+----------+-----------+
|
SSH
|
+--------------------------------------+
| |
| |
v v

+----------------+ +----------------+
| Rocky Linux | | RHEL |
| Target Host 1 | | Target Host 2 |
| | | |
| Bootstrap | | Bootstrap |
| Patching | | Patching |
| Compliance | | Compliance |
| Logging | | Logging |
+--------+-------+ +--------+-------+
| |
| |
+-----------+--------------+
|
|
v
+----------------------+
| Log Collector |
| rsyslog Server |
+----------------------+

```

---

# Project Structure

```
linux-enterprise-automation/

├── ansible/
│   ├── inventory/
│   ├── playbooks/
│   ├── roles/
│   │   ├── bootstrap/
│   │   ├── ssh-hardening/
│   │   ├── firewall/
│   │   ├── chrony/
│   │   ├── users/
│   │   ├── compliance/
│   │   ├── logging/
│   │   ├── patching/
│   │   └── systemd-timers/
│   └── group_vars/
│
├── bash/
│   ├── bootstrap.sh
│   ├── patch.sh
│   ├── rollback.sh
│   ├── compliance-check.sh
│   ├── onboard-user.sh
│   └── offboard-user.sh
│
├── docs/
│   ├── architecture.png
│   ├── compliance.md
│   ├── patch-management.md
│   └── user-lifecycle.md
│
├── github/
│
├── .github/
│   └── workflows/
│       └── ci.yml
│
├── inventory/
│
├── scripts/
│
├── README.md
│
└── LICENSE

```

---

# Features

## 1. Bootstrap Automation

Provision a fresh Linux server into a standardized enterprise host.

Includes:

- Hostname configuration
- Timezone
- Chrony configuration
- Package installation
- Standard users/groups
- SSH hardening
- sudo policies
- firewalld baseline
- SELinux configuration

Result:

Every server starts from the same secure baseline.

---

# 2. Patch Management

Enterprise patch workflow.

Process

```

Pre-check

↓

LVM Snapshot

↓

dnf update

↓

Health Check

↓

Success?
│

├── YES → Snapshot Removed

│

└── NO → Rollback Snapshot

```

Health checks include:

- SSH availability
- SELinux state
- Network connectivity
- Required services
- Application ports
- Disk utilization

---

# 3. Configuration Compliance

Audit every server against a predefined enterprise baseline.

Checks include:

- SELinux Enforcing
- Root account secured
- Password policies
- SSH hardening
- Firewall enabled
- Required packages installed
- Time synchronization
- Services enabled
- World-writable files
- File permissions

Produces reports such as:

```

PASS
FAIL
WARNING

```

to quickly identify configuration drift.

---

# 4. Centralized Logging

Configure rsyslog forwarding.

Logs collected:

- Authentication
- sudo
- SSH
- Kernel
- System
- Audit

Destination:

Dedicated Log Collector VM.

---

# 5. User Lifecycle Automation

Automates onboarding and offboarding.

### Onboarding

- Create user
- Create home directory
- Generate SSH keys
- Assign groups
- Configure sudo
- Apply ACLs
- Set password expiration

### Offboarding

- Lock account
- Archive home directory
- Remove SSH keys
- Remove sudo access
- Disable login
- Generate audit report

---

# 6. systemd Timers

Replace traditional cron jobs with modern systemd timers.

Benefits:

- Better logging
- Service dependency handling
- Retry support
- Improved monitoring

---

# 7. CI/CD

Every push automatically runs:

```

ShellCheck

↓

ansible-lint

↓

YAML Validation

↓

Syntax Checks

↓

Repository Status

```

This ensures infrastructure code remains production ready.

---

# Idempotency

All automation is designed to be idempotent.

Running the automation multiple times should produce the same desired system state without introducing unintended changes.

---

# Enterprise Practices Demonstrated

- Infrastructure as Code
- Configuration Management
- Immutable Configuration Principles
- Security Hardening
- Fleet Management
- Compliance Auditing
- Patch Governance
- Rollback Strategy
- Operational Documentation
- CI for Infrastructure
- Automation First Operations

---

# Skills Demonstrated

- Linux Administration
- Bash Scripting
- Ansible
- Systemd
- SELinux
- firewalld
- SSH
- LVM
- rsyslog
- GitHub Actions
- Infrastructure Automation
- Configuration Drift Detection
- Security Hardening
- Production Operations

---

# Future Enhancements

- Podman automation
- OpenSCAP integration
- CIS Benchmark automation
- Prometheus Node Exporter
- Grafana dashboards
- HashiCorp Vault integration
- Active Directory integration
- LDAP authentication
- Satellite Server support
- AWX Automation Controller
- Molecule testing
- Terraform integration

---

# Target Audience

This project is intended for:

- Linux System Administrators
- DevOps Engineers
- Platform Engineers
- Site Reliability Engineers (SRE)
- Cloud Engineers
- Students learning Enterprise Linux Administration

---

# Why this Project?

The goal is not simply to automate Linux commands but to demonstrate the operational mindset of an Enterprise Linux Administrator.

The repository reflects real-world workflows used to provision, secure, patch, audit, and maintain Linux infrastructure at scale using repeatable, version-controlled automation.

---

## License

MIT License
