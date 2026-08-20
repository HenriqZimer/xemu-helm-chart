# Changelog

All notable changes to this Helm chart will be documented in this file.

The format is based on [Keep a Changelog](https://keepachangelog.com/en/1.0.0/),
and this project adheres to [Semantic Versioning](https://semver.org/spec/v2.0.0.html).

## [Unreleased]

## [1.1.4] - 2026-08-17

### Changed
- README now shows the emulator's logo at the top.

## [1.1.3] - 2026-08-17

### Added
- Chart releases are now GPG-signed (`helm package --sign`) - see `artifacthub.io/signKey` in `Chart.yaml` for the public key URL and fingerprint. Powers the "Signed" badge on ArtifactHub.

## [1.1.2] - 2026-08-16

### Added
- `chart/values.schema.json` validating `values.yaml` - powers the "Values schema" feature on ArtifactHub, previously absent since no chart in this project ever had one.

## [1.1.1] - 2026-08-16

### Added
- `icon` in Chart.yaml, pointing at linuxserver.io's own logo image for this app - was missing entirely before, which is why no image ever showed up on ArtifactHub for this chart.

## [1.1.0] - 2026-08-15

### Added
- `gpu.vendor: nvidia` mode (alongside the existing `intel-amd` VA-API mode), requesting `nvidia.com/gpu`
  via the NVIDIA Kubernetes device plugin and setting `NVIDIA_VISIBLE_DEVICES`/`NVIDIA_DRIVER_CAPABILITIES`.
  Documented the `nvidia-drm.modeset=1` kernel parameter (and, on headless nodes, a dummy HDMI/DP plug)
  needed on the node for the compositor to render anything instead of a solid black desktop.
- `seccompUnconfined` to work around a JIT recompiler crashing with `SIGBUS` under the default seccomp
  profile on some kernel/libseccomp combinations.

### Changed
- Bumped the default `shmSize` from `1Gi` to `2Gi`, matching the fix confirmed on this chart's sibling
  `pcsx2-helm-chart` for a JIT recompiler crashing with `SIGBUS` under Docker/Kubernetes' small default
  `/dev/shm`.

## [1.0.0] - 2026-08-12

### Added
- Initial release of the xemu Helm chart
- Deployment, Service, optional Ingress and PVC for the linuxserver.io xemu KasmVNC webtop image
- Configurable `serviceAccount` (create/name/annotations)
- Readiness and liveness probes (TCP check on the KasmVNC HTTP port)
- Optional VA-API (`/dev/dri`) GPU passthrough via `gpu.enabled`
- `extraVolumes`/`extraVolumeMounts` for mounting an existing ROMs/BIOS library
- `streaming.enabled`/`streaming.brokerPort` for RomM's Emulator Streaming (xemu-romm-integration mod)
