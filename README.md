<div align="center">

<img src="logo.png" alt="KafkaGuard" width="72" height="72" />

# KafkaGuard

### Automated Security & Compliance Scanner for Apache Kafka

[![Release](https://img.shields.io/github/v/release/KafkaGuard/kafkaguard-releases?style=flat-square&color=047857&label=Latest)](https://github.com/KafkaGuard/kafkaguard-releases/releases/latest)
[![Downloads](https://img.shields.io/github/downloads/KafkaGuard/kafkaguard-releases/total?style=flat-square&color=047857&label=Downloads)](https://github.com/KafkaGuard/kafkaguard-releases/releases)
[![Platforms](https://img.shields.io/badge/Platforms-Linux%20%7C%20macOS-047857?style=flat-square)](#-download)
[![License](https://img.shields.io/badge/License-Proprietary-636e72?style=flat-square)](https://kafkaguard.com/docs/enterprise)

**Scan Kafka clusters in under 90 seconds. Get audit-ready reports mapped to PCI-DSS, SOC 2, and ISO 27001. Free for one cluster — forever.**

[Website](https://kafkaguard.com) · [Docs](https://kafkaguard.com/docs) · [Quick Start](https://kafkaguard.com/docs/guide/quickstart) · [Pricing](https://kafkaguard.com/pricing)

</div>

---

## What is KafkaGuard?

KafkaGuard is a single-binary CLI that scans Apache Kafka clusters against security and compliance policies. It collects broker configs, ACLs, TLS settings, and operational metrics — evaluates them against **55 controls** across security, reliability, and operations — and produces reports in JSON, HTML, PDF, and CSV.

Runs entirely inside your network. No data leaves your environment.

```bash
kafkaguard scan --bootstrap kafka-prod:9092 --policy policies/finance-iso.yaml --format pdf
# KafkaGuard v2.3.0 | 55 controls | Score: 68% | Report saved in 1.4s
```

---

## Features

| | |
|--|--|
| **55 Security Controls** | Authentication, authorization, encryption, replication, retention, KRaft |
| **4 Report Formats** | JSON · HTML · PDF (branded, sign-off ready) · CSV |
| **3 Compliance Frameworks** | PCI-DSS 4.0 · SOC 2 Type II · ISO 27001 — every finding has a framework ID |
| **Alerting** | Slack · Microsoft Teams · Generic webhook — fire on completion or score threshold |
| **On-Prem Dashboard** | Multi-cluster view, trend charts, fleet compare, findings explorer |
| **Kafka 2.6 → 4.x** | ZooKeeper and KRaft modes, Confluent Platform 6–8, Amazon MSK, Aiven |
| **Air-gapped** | Fully offline — RSA-signed license, no outbound connections |
| **Fast** | Parallel collector — full 55-control scan in under 90 seconds |

---

## Dashboard

The on-prem dashboard ships with all tiers including Community (single cluster, free forever).

### Clusters Overview

<img src="https://kafkaguard.com/images/screenshots/clusters.png" alt="KafkaGuard Clusters Dashboard" width="100%" />

*All your Kafka clusters in one view — compliance score, environment tag, and open finding count.*

### Findings Explorer

<img src="https://kafkaguard.com/images/screenshots/findings.png" alt="KafkaGuard Findings Explorer" width="100%" />

*Filter by severity, acknowledge findings, and expand inline remediation guidance.*

### Trend Charts

<img src="https://kafkaguard.com/images/screenshots/trends.png" alt="KafkaGuard Trend Charts" width="100%" />

*Compliance score over time (7d / 30d / 90d / 1y) with regression highlighting.*

### Scan Detail

<img src="https://kafkaguard.com/images/screenshots/scan-detail.png" alt="KafkaGuard Scan Detail" width="100%" />

*Drill into any scan — severity breakdown, all findings, download reports in any format.*

### HTML Report

<img src="https://kafkaguard.com/images/screenshots/report-html.png" alt="KafkaGuard HTML Report" width="100%" />

*Interactive browser report with expandable remediation and tabbed compliance framework mapping.*

---

## Community vs Paid

| | Community | Starter | Team | Enterprise |
|--|:---------:|:-------:|:----:|:----------:|
| **Price** | Free forever | $99/cluster/mo | $199/cluster/mo | $299/cluster/mo |
| **Clusters** | 1 | Up to 2 | Up to 10 | Unlimited |
| **Controls** | 55 (finance-iso) | 45 | 55 | 55 + custom |
| **Report formats** | JSON · HTML · PDF · CSV | All | All | All |
| **Compliance mapping** | — | PCI-DSS · SOC 2 · ISO | All frameworks | + custom |
| **Alerts** | Slack / Teams / Webhook | ✓ | ✓ | ✓ |
| **On-prem dashboard** | ✓ | ✓ | ✓ | ✓ |
| **Support** | Community | Email · 2 days | Email · 1 day | Dedicated SE · 24/7 |

[→ Full feature comparison at kafkaguard.com/pricing](https://kafkaguard.com/pricing)

---

## Quick Start

### 1. Install

```bash
# macOS — Apple Silicon
curl -LO https://github.com/KafkaGuard/kafkaguard-releases/releases/latest/download/kafkaguard_Darwin_arm64.tar.gz
tar -xzf kafkaguard_Darwin_arm64.tar.gz && sudo mv kafkaguard /usr/local/bin/

# macOS — Intel
curl -LO https://github.com/KafkaGuard/kafkaguard-releases/releases/latest/download/kafkaguard_Darwin_x86_64.tar.gz
tar -xzf kafkaguard_Darwin_x86_64.tar.gz && sudo mv kafkaguard /usr/local/bin/

# Linux — x86_64
curl -LO https://github.com/KafkaGuard/kafkaguard-releases/releases/latest/download/kafkaguard_Linux_x86_64.tar.gz
tar -xzf kafkaguard_Linux_x86_64.tar.gz && sudo mv kafkaguard /usr/local/bin/

# Linux — ARM64
curl -LO https://github.com/KafkaGuard/kafkaguard-releases/releases/latest/download/kafkaguard_Linux_arm64.tar.gz
tar -xzf kafkaguard_Linux_arm64.tar.gz && sudo mv kafkaguard /usr/local/bin/
```

```bash
kafkaguard version
# KafkaGuard v2.3.0
```

### 2. Run your first scan

```bash
kafkaguard scan \
  --bootstrap kafka-prod:9092 \
  --policy policies/finance-iso.yaml \
  --format json,html,pdf,csv \
  --out ./audit-reports
```

```
KafkaGuard v2.3.0
Scan ID: a1b2c3d4 · kafka-prod:9092 · finance-iso (55 controls)

Collecting cluster data...
  ✓ Broker configs   3 brokers
  ✓ ACL entries      142 rules
  ✓ TLS metadata     SASL_SSL
  ✓ KRaft quorum     controller elected
  ✓ Topic metadata   89 topics

Evaluating 55 controls...

  PASS  KG-004  No wildcard ACL entries                  MEDIUM
  PASS  KG-005  TLS certificate expiry > 30 days         HIGH
  PASS  KG-006  TLS 1.2+ enforced on all listeners       HIGH
  FAIL  KG-007  Inter-broker uses PLAINTEXT              HIGH
  FAIL  KG-001  SASL authentication not enabled          HIGH
  FAIL  KG-002  SSL/TLS not configured on listeners      HIGH
  ...  49 more controls

────────────────────────────────────────────────────
  Score   68%    39 passed · 16 failed · 0 N/A
  Policy  finance-iso · 55 controls
  Time    1.4s
────────────────────────────────────────────────────

Reports saved to ./audit-reports/
  scan-20260503-a1b2c3d4.json   (39 KB)
  scan-20260503-a1b2c3d4.html   (77 KB)
  scan-20260503-a1b2c3d4.pdf    (76 KB)
  scan-20260503-a1b2c3d4.csv    ( 8 KB)
```

### 3. Common patterns

```bash
# Slack alert when score drops below 85%
kafkaguard scan \
  --bootstrap kafka-prod:9092 \
  --policy policies/finance-iso.yaml \
  --alert-slack-webhook "$SLACK_WEBHOOK" \
  --alert-threshold 85

# CI/CD — fail pipeline on any HIGH finding
kafkaguard scan \
  --bootstrap localhost:9092 \
  --policy policies/baseline-dev.yaml \
  --format json \
  --fail-on high

# Upload results to the on-prem dashboard
export KAFKAGUARD_API_KEY=kg_prod_xxxxxxxxxxxx
kafkaguard scan \
  --bootstrap kafka-prod:9092 \
  --policy policies/finance-iso.yaml \
  --upload http://kafkaguard-api:3001
```

---

## Alerting

```bash
# Slack
kafkaguard scan --bootstrap kafka:9092 \
  --alert-slack-webhook https://hooks.slack.com/services/... \
  --alert-threshold 85

# Microsoft Teams
kafkaguard scan --bootstrap kafka:9092 \
  --alert-teams-webhook https://outlook.office.com/webhook/...

# Generic HTTP endpoint (PagerDuty, Discord, custom)
kafkaguard scan --bootstrap kafka:9092 \
  --alert-webhook https://your-api/kafka-alerts
```

Persist webhook URLs in `~/.kafkaguard.yaml` to avoid repeating flags on every run.

---

## On-Prem Stack

```bash
docker compose -f docker-compose.onprem.yml --env-file .env.onprem up -d
# Dashboard → http://localhost:3000
# API       → http://localhost:3001
```

```bash
docker pull kafkaguard/api:2.3.0
docker pull kafkaguard/worker:2.3.0
docker pull kafkaguard/dashboard:2.3.0
```

[→ Full on-prem setup guide](https://kafkaguard.com/docs/guide/installation-onprem)

---

## Download

### v2.3.0

### On-Prem Bundle (Recommended)

Includes CLI binary + Docker Compose stack + installer scripts + policies — everything in one download:

| Platform | Download |
|:---------|:---------|
| macOS (Apple Silicon) | [kafkaguard-onprem-v2.3.0-Darwin_arm64.tar.gz](https://github.com/KafkaGuard/kafkaguard-releases/releases/latest/download/kafkaguard-onprem-v2.3.0-Darwin_arm64.tar.gz) |
| macOS (Intel) | [kafkaguard-onprem-v2.3.0-Darwin_x86_64.tar.gz](https://github.com/KafkaGuard/kafkaguard-releases/releases/latest/download/kafkaguard-onprem-v2.3.0-Darwin_x86_64.tar.gz) |
| Linux (x86_64) | [kafkaguard-onprem-v2.3.0-Linux_x86_64.tar.gz](https://github.com/KafkaGuard/kafkaguard-releases/releases/latest/download/kafkaguard-onprem-v2.3.0-Linux_x86_64.tar.gz) |
| Linux (ARM64) | [kafkaguard-onprem-v2.3.0-Linux_arm64.tar.gz](https://github.com/KafkaGuard/kafkaguard-releases/releases/latest/download/kafkaguard-onprem-v2.3.0-Linux_arm64.tar.gz) |

### CLI Binary Only

| Platform | Architecture | Download |
|:---------|:------------|:---------|
| Linux | x86\_64 | [kafkaguard\_Linux\_x86\_64.tar.gz](https://github.com/KafkaGuard/kafkaguard-releases/releases/latest/download/kafkaguard_Linux_x86_64.tar.gz) |
| Linux | ARM64 | [kafkaguard\_Linux\_arm64.tar.gz](https://github.com/KafkaGuard/kafkaguard-releases/releases/latest/download/kafkaguard_Linux_arm64.tar.gz) |
| macOS | Apple Silicon (ARM64) | [kafkaguard\_Darwin\_arm64.tar.gz](https://github.com/KafkaGuard/kafkaguard-releases/releases/latest/download/kafkaguard_Darwin_arm64.tar.gz) |
| macOS | Intel (x86\_64) | [kafkaguard\_Darwin\_x86\_64.tar.gz](https://github.com/KafkaGuard/kafkaguard-releases/releases/latest/download/kafkaguard_Darwin_x86_64.tar.gz) |

**Note:** The "Source code" downloads on this page contain only this repository's README and logo — not the KafkaGuard application source code, which is proprietary.

### Verify integrity

```bash
curl -LO https://github.com/KafkaGuard/kafkaguard-releases/releases/latest/download/checksums.txt

# macOS
shasum -a 256 -c checksums.txt

# Linux
sha256sum -c checksums.txt
```

---

## Supported Distributions

| Distribution | Versions |
|:-------------|:---------|
| Apache Kafka | 2.6 – 4.x (ZooKeeper and KRaft) |
| Confluent Platform | 6.x – 8.x |
| Amazon MSK | All managed versions |
| Aiven for Apache Kafka | All managed versions |
| Redpanda | Compatible via Kafka API |

KRaft clusters are auto-detected. ZooKeeper-only controls skip automatically and are marked N/A.

---

## Policy Tiers

| Policy | Controls | Use case |
|:-------|:--------:|:---------|
| `baseline-dev` | 21 | Dev, staging, sandbox |
| `enterprise-default` | 45 | Production, general security posture |
| `finance-iso` | 55 | Regulated industries — PCI-DSS, SOC 2, ISO 27001 |

The Community free tier runs any policy including `finance-iso` (55 controls) — no restrictions.

---

## License Activation

```bash
kafkaguard license activate --key kg_xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx
kafkaguard license status
```

Licenses are RSA-signed and validated fully offline. No internet required after activation.
Get a license at [kafkaguard.com/pricing](https://kafkaguard.com/pricing).

---

<div align="center">

[Website](https://kafkaguard.com) · [Docs](https://kafkaguard.com/docs) · [Pricing](https://kafkaguard.com/pricing) · [Changelog](https://kafkaguard.com/changelog) · [Contact](https://kafkaguard.com/contact)

© 2026 KafkaGuard, Inc. All rights reserved.

</div>
