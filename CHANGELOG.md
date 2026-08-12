# Changelog

All notable changes to this Helm chart will be documented in this file.

The format is based on [Keep a Changelog](https://keepachangelog.com/en/1.0.0/),
and this project adheres to [Semantic Versioning](https://semver.org/spec/v2.0.0.html).

## [Unreleased]

## [1.0.0] - 2026-08-12

### Added
- Initial release of the xemu Helm chart
- Deployment, Service, optional Ingress and PVC for the linuxserver.io xemu KasmVNC webtop image
- Configurable `serviceAccount` (create/name/annotations)
- Readiness and liveness probes (TCP check on the KasmVNC HTTP port)
- Optional VA-API (`/dev/dri`) GPU passthrough via `gpu.enabled`
- `extraVolumes`/`extraVolumeMounts` for mounting an existing ROMs/BIOS library
- `streaming.enabled`/`streaming.brokerPort` for RomM's Emulator Streaming (xemu-romm-integration mod)
