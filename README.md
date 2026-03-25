# KafkaGuard Releases

Official release binaries for [KafkaGuard](https://kafkaguard.com) - Enterprise Kafka Security & Compliance Scanner.

## Download

| Platform | Architecture | Download |
|----------|-------------|----------|
| Linux | x86_64 | [kafkaguard_Linux_x86_64.tar.gz](https://github.com/KafkaGuard/kafkaguard-releases/releases/latest/download/kafkaguard_Linux_x86_64.tar.gz) |
| Linux | ARM64 | Coming soon |
| macOS | ARM64 (Apple Silicon) | [kafkaguard_Darwin_arm64.tar.gz](https://github.com/KafkaGuard/kafkaguard-releases/releases/latest/download/kafkaguard_Darwin_arm64.tar.gz) |
| macOS | x86_64 (Intel) | [kafkaguard_Darwin_x86_64.tar.gz](https://github.com/KafkaGuard/kafkaguard-releases/releases/latest/download/kafkaguard_Darwin_x86_64.tar.gz) |

## Quick Start

```bash
# Download (Linux x86_64)
curl -LO https://github.com/KafkaGuard/kafkaguard-releases/releases/latest/download/kafkaguard_Linux_x86_64.tar.gz

# Extract
tar -xzf kafkaguard_Linux_x86_64.tar.gz
sudo mv kafkaguard /usr/local/bin/

# Verify
kafkaguard version

# Scan your cluster
kafkaguard scan --bootstrap localhost:9092 --policy enterprise-default --format html
```

## Verify Downloads

All releases include SHA256 checksums:

```bash
sha256sum -c kafkaguard_1.0.0_checksums.txt
```

## Links

- **Website:** [kafkaguard.com](https://kafkaguard.com)
- **Documentation:** [kafkaguard.com/docs](https://kafkaguard.com/docs)
- **Quick Start:** [kafkaguard.com/docs/guide/quickstart](https://kafkaguard.com/docs/guide/quickstart)
