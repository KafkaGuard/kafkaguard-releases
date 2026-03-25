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

### 🖥️ CLI Scan Output

```
$ kafkaguard scan --bootstrap kafka-prod:9092 --policy enterprise-default

# Connecting to cluster...
Cluster: kafka-prod (3 brokers) · Protocol: SASL_SSL

# Running 40 controls...
PASS  SEC-001  TLS encryption enabled on all listeners
PASS  SEC-002  SASL authentication mechanism configured
FAIL  SEC-004  ACL authorization is not enabled
PASS  REL-001  Replication factor ≥ 3 for all topics
WARN  REL-003  min.insync.replicas = 1 (recommended: 2)
PASS  OPS-007  Log retention policy configured
... 34 more controls

─────────────────────────────────────────
Score: 87/100 · 36 passed · 3 warnings · 1 failed
Report saved: ./kafkaguard-report.html
Completed in 8.2s
```

### 📄 HTML Report

KafkaGuard generates **professional, audit-ready HTML reports** — perfect for compliance teams and security reviews.

```
┌──────────────────────────────────────────────────────────────────────┐
│  ░░░░░░░░░░░░░░░  KafkaGuard Scan Report  ░░░░░░░░░░░░░░░░░░░░░░  │
│  ░░░░░░░░░░░░░░░░░░  kafka-prod cluster  ░░░░░░░░░░░░░░░░░░░░░░░  │
├──────────────────────────────────────────────────────────────────────┤
│                                                                      │
│  📋 EXECUTIVE SUMMARY                                                │
│  ┌──────────┬──────────┬──────────┬────────────────┐                 │
│  │ Cluster  │ Brokers  │ Topics   │ ZooKeeper      │                 │
│  │kafka-prod│    3     │   47     │   3 nodes      │                 │
│  └──────────┴──────────┴──────────┴────────────────┘                 │
│                                                                      │
│              ╔══════════════════════╗                                 │
│              ║    87.0%             ║                                 │
│              ║  COMPLIANCE SCORE    ║                                 │
│              ║    87 / 100          ║                                 │
│              ╚══════════════════════╝                                 │
│                                                                      │
│    ┌────────────┐  ┌────────────┐  ┌────────────┐                    │
│    │  ✅  36    │  │  ❌   1    │  │  ➖   3    │                    │
│    │  Passed    │  │  Failed    │  │   N.A.     │                    │
│    └────────────┘  └────────────┘  └────────────┘                    │
│                                                                      │
│  Policy: enterprise-default (v2.1)                                   │
│  Scan ID: 8f2a4b6c · Mar 25, 2026 10:30 AM · Duration: 8200ms      │
│                                                                      │
├──────────────────────────────────────────────────────────────────────┤
│                                                                      │
│  🔍 CONTROLS EVALUATION                                              │
│  ┌────────┬──────────┬────────────────────────────────┬──────────┐   │
│  │ Status │ Control  │ Title                          │ Severity │   │
│  ├────────┼──────────┼────────────────────────────────┼──────────┤   │
│  │   ✓    │ SEC-001  │ TLS encryption on listeners    │   HIGH   │   │
│  │   ✓    │ SEC-002  │ SASL authentication configured │   HIGH   │   │
│  │   ✗    │ SEC-004  │ ACL authorization not enabled   │   HIGH   │   │
│  │   ✓    │ REL-001  │ Replication factor ≥ 3         │  MEDIUM  │   │
│  │   ✓    │ REL-003  │ In-sync replicas configured    │  MEDIUM  │   │
│  │   ✓    │ OPS-007  │ Log retention policy set        │   LOW    │   │
│  └────────┴──────────┴────────────────────────────────┴──────────┘   │
│                                                                      │
│  ⚠️  REMEDIATION — SEC-004                                           │
│  │ Enable ACL authorization by setting                               │
│  │ authorizer.class.name=kafka.security.authorizer.AclAuthorizer     │
│  │ in server.properties and restart brokers.                         │
│                                                                      │
├──────────────────────────────────────────────────────────────────────┤
│                                                                      │
│  📑 COMPLIANCE MAPPING                                               │
│  ┌─────────────┬─────────────┬──────────────┐                        │
│  │  PCI-DSS    │    SOC2     │  ISO 27001   │                        │
│  ├─────────────┼─────────────┼──────────────┤                        │
│  │ Req 2.2.1   │ CC6.1       │ A.10.1.1     │                        │
│  │ Req 4.1     │ CC6.6       │ A.13.1.1     │                        │
│  │ Req 7.1     │ CC6.3       │ A.9.4.1      │                        │
│  │ Req 10.1    │ CC7.2       │ A.12.4.1     │                        │
│  └─────────────┴─────────────┴──────────────┘                        │
│                                                                      │
└──────────────────────────────────────────────────────────────────────┘
  Generated by KafkaGuard v1.0.0
```

> 💡 Reports are generated as **interactive HTML files** with expandable remediation guidance, tabbed compliance mapping, and print-friendly styling. Export as **JSON** or **CSV** for CI/CD integration.

---

<div align="center">

### 🔗 Links

[🌐 Website](https://kafkaguard.com) · [📖 Docs](https://kafkaguard.com/docs) · [🚀 Quick Start](https://kafkaguard.com/docs/guide/quickstart) · [💼 Enterprise](https://kafkaguard.com/docs/enterprise) · [📝 Changelog](https://kafkaguard.com/docs/community/changelog)

---

**Built for teams that take Kafka security seriously.**

© 2025 KafkaGuard. All rights reserved.

</div>
