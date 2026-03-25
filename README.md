<div align="center">

# 🛡️ KafkaGuard

### Enterprise Security & Compliance Scanner for Apache Kafka

[![Release](https://img.shields.io/github/v/release/KafkaGuard/kafkaguard-releases?style=flat-square&color=00b894&label=Latest%20Release)](https://github.com/KafkaGuard/kafkaguard-releases/releases/latest)
[![Downloads](https://img.shields.io/github/downloads/KafkaGuard/kafkaguard-releases/total?style=flat-square&color=0984e3&label=Downloads)](https://github.com/KafkaGuard/kafkaguard-releases/releases)
[![Docker](https://img.shields.io/badge/Docker-kafkaguard%2Fkafkaguard-2496ED?style=flat-square&logo=docker&logoColor=white)](https://hub.docker.com/r/kafkaguard/kafkaguard)
[![License](https://img.shields.io/badge/License-Proprietary-636e72?style=flat-square)](https://kafkaguard.com/docs/enterprise)

**Scan your Kafka clusters for security vulnerabilities, enforce compliance policies, and generate audit-ready reports.**

[🌐 Website](https://kafkaguard.com) · [📖 Documentation](https://kafkaguard.com/docs) · [🚀 Quick Start](https://kafkaguard.com/docs/guide/quickstart) · [📦 Download](https://github.com/KafkaGuard/kafkaguard-releases/releases/latest)

---

</div>

## ✨ Features

🔍 **40+ Security Controls** — Comprehensive scanning across authentication, authorization, encryption, and network configuration

📋 **Compliance Frameworks** — Built-in PCI-DSS, SOC2, CIS, and ISO 27001 policy mappings

📊 **Multi-Format Reports** — HTML, JSON, and CSV reports with actionable remediation guidance

🏢 **Enterprise Ready** — LDAP, Kerberos, SCRAM, and mTLS authentication support

⚡ **Fast & Lightweight** — Single binary, zero dependencies, optimized for large-scale clusters

🐳 **Docker Support** — Run anywhere with `docker pull kafkaguard/kafkaguard`

---

## 📥 Download

### Binary Downloads

| Platform | Architecture | Download |
|:---------|:------------|:---------|
| 🐧 Linux | x86_64 | [**kafkaguard_Linux_x86_64.tar.gz**](https://github.com/KafkaGuard/kafkaguard-releases/releases/latest/download/kafkaguard_Linux_x86_64.tar.gz) |
| 🍎 macOS | ARM64 (Apple Silicon) | [**kafkaguard_Darwin_arm64.tar.gz**](https://github.com/KafkaGuard/kafkaguard-releases/releases/latest/download/kafkaguard_Darwin_arm64.tar.gz) |
| 🍎 macOS | x86_64 (Intel) | [**kafkaguard_Darwin_x86_64.tar.gz**](https://github.com/KafkaGuard/kafkaguard-releases/releases/latest/download/kafkaguard_Darwin_x86_64.tar.gz) |

### 🐳 Docker

```bash
docker pull kafkaguard/kafkaguard:latest
```

---

## 🚀 Quick Start

```bash
# 📦 Install (Linux x86_64)
curl -LO https://github.com/KafkaGuard/kafkaguard-releases/releases/latest/download/kafkaguard_Linux_x86_64.tar.gz
tar -xzf kafkaguard_Linux_x86_64.tar.gz
sudo mv kafkaguard /usr/local/bin/

# ✅ Verify installation
kafkaguard version

# 🔍 Scan your Kafka cluster
kafkaguard scan --bootstrap localhost:9092

# 📊 Generate HTML compliance report
kafkaguard scan --bootstrap localhost:9092 --policy enterprise-default --format html --output report.html

# 📋 List all security controls
kafkaguard list-controls
```

### 🐳 Docker Quick Start

```bash
# Scan with Docker
docker run --rm kafkaguard/kafkaguard:latest scan --bootstrap host.docker.internal:9092

# Generate report
docker run --rm -v $(pwd)/reports:/reports kafkaguard/kafkaguard:latest \
  scan --bootstrap host.docker.internal:9092 --format html --output /reports/audit.html
```

---

## 🔐 Verify Downloads

All releases include SHA256 checksums for integrity verification:

```bash
# Download checksums
curl -LO https://github.com/KafkaGuard/kafkaguard-releases/releases/latest/download/kafkaguard_1.0.0_checksums.txt

# Verify
sha256sum -c kafkaguard_1.0.0_checksums.txt
```

---

## 📊 What You Get

```
┌─────────────────────────────────────────────────┐
│           KafkaGuard Security Report            │
├─────────────────────────────────────────────────┤
│  🟢 Authentication (TLS/SASL)      8/8 passed  │
│  🟡 Authorization (ACLs)           6/7 passed  │
│  🟢 Encryption (in-transit)        5/5 passed  │
│  🔴 Network Configuration          3/5 passed  │
│  🟢 Audit Logging                  4/4 passed  │
├─────────────────────────────────────────────────┤
│  Overall Score: 87/100  │  Risk Level: LOW      │
│  PCI-DSS: COMPLIANT     │  CIS: 26/29 controls  │
└─────────────────────────────────────────────────┘
```

---

<div align="center">

### 🔗 Links

[🌐 Website](https://kafkaguard.com) · [📖 Docs](https://kafkaguard.com/docs) · [🚀 Quick Start](https://kafkaguard.com/docs/guide/quickstart) · [💼 Enterprise](https://kafkaguard.com/docs/enterprise) · [📝 Changelog](https://kafkaguard.com/docs/community/changelog)

---

**Built for teams that take Kafka security seriously.**

© 2025 KafkaGuard. All rights reserved.

</div>
