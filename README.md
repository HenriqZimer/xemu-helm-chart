# xemu Helm Chart Repository

<p align="center">
  <img src="https://raw.githubusercontent.com/linuxserver/docker-templates/master/linuxserver.io/img/xemu-logo.png" alt="xemu logo" width="140" />
</p>

[![License](https://img.shields.io/badge/License-MIT-blue.svg)](LICENSE)
[![Helm Version](https://img.shields.io/badge/Helm-v3-blue)](https://helm.sh)
[![Artifact Hub](https://img.shields.io/endpoint?url=https://artifacthub.io/badge/repository/xemu-helm-chart)](https://artifacthub.io/packages/search?repo=xemu-helm-chart)

This repository contains a production-ready Helm chart for deploying [xemu](https://docs.linuxserver.io/images/docker-xemu/) on Kubernetes.

## About xemu

xemu is a free and open-source original Xbox emulator. This chart deploys the
[linuxserver.io](https://docs.linuxserver.io/images/docker-xemu/) build, which serves the full
emulator desktop in your browser over KasmVNC — no local install needed, play from any device on
your network:

- 🎮 Full original Xbox emulator desktop, streamed over the browser (KasmVNC)
- 🖥️ No client install — works from any modern browser
- 🗄️ Config/BIOS/HDD-image persistence via a mounted `/config` volume
- 🎯 Bring your own ROMs library via `extraVolumes`
- ⚡ Optional VA-API GPU passthrough for hardware-accelerated rendering
- 🔌 Optional integration with [RomM's Emulator Streaming](https://docs.romm.app/latest/using/emulator-streaming/)

## Quick Start

### Add Helm Repository

```bash
helm repo add xemu-helm-chart https://henriqzimer.github.io/xemu-helm-chart/
helm repo update
```

### Install Chart

```bash
helm install my-xemu xemu-helm-chart/xemu --version 1.1.5
```

For detailed installation instructions and configuration options, see the [chart README](chart/README.md).

## Repository Structure

```
.
├── chart/              # Helm chart for xemu
│   ├── Chart.yaml      # Chart metadata
│   ├── values.yaml     # Default configuration values
│   ├── README.md       # Detailed chart documentation
│   └── templates/      # Kubernetes manifest templates
├── LICENSE             # Repository license
└── README.md           # This file
```

## Documentation

- **[Chart Documentation](chart/README.md)** - Complete installation and configuration guide
- **[linuxserver.io xemu Docs](https://docs.linuxserver.io/images/docker-xemu/)** - Upstream image documentation
- **[Values Reference](chart/values.yaml)** - All available configuration options

## Prerequisites

- Kubernetes 1.19+
- Helm 3.0+
- Persistent storage, if you enable `persistence.config` (NFS, local-path, or cloud storage)
- (Optional) Ingress controller
- (Optional) cert-manager for automatic TLS
- (Optional) A node exposing `/dev/dri` for GPU passthrough

## Features

This Helm chart provides:

- ✅ Production-ready Kubernetes Deployment/Service
- ✅ Optional persistent `/config` volume (BIOS, HDD image, settings)
- ✅ `extraVolumes`/`extraVolumeMounts` for a ROMs library
- ✅ Optional Ingress with TLS support
- ✅ Resource limits and requests
- ✅ Readiness/liveness probes
- ✅ Configurable ServiceAccount
- ✅ Optional VA-API (`/dev/dri`) GPU passthrough
- ✅ Optional RomM Emulator Streaming broker port

## Contributing

Contributions are welcome! Please feel free to submit a Pull Request. See [CONTRIBUTING.md](CONTRIBUTING.md).

## License

This Helm chart is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

xemu itself is licensed under its own terms. See the [xemu project](https://xemu.app/) and the
[linuxserver.io image](https://github.com/linuxserver/docker-xemu) for more information.

## Support

- 🐛 [Report Issues](https://github.com/HenriqZimer/xemu-helm-chart/issues)
- 💬 [Discussions](https://github.com/HenriqZimer/xemu-helm-chart/discussions)
- 📖 [Documentation](chart/README.md)

---

Made with ❤️ for the retro gaming community
