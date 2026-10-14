# Technical Architecture — TRIMESH

**Upstream:** [https://github.com/mikedh/trimesh](https://github.com/mikedh/trimesh)
**License:** MIT
**Category:** VOXELIZATION
**Anticloud Integration:** PAX L5 Narrow L2 General 27B + AIOSS + Offline-First

## Upstream Description

3D mesh processing with voxelization

## Anticloud Architectural Changes

1. PAX L5 Narrow L2 General 27B local 3D scene understanding from voxel grids
2. AIOSS provenance chain for all 3D scan and reconstruction data
3. AES-256 encryption for proprietary 3D models and point clouds
4. Single-binary voxelization tool with no cloud dependency
5. Zero-cloud: all meshing, analysis, and AI inference run locally
6. GPU/CPU equalizer: CUDA voxelization on GPU, CPU fallback for deployment
7. Open point cloud format: LAS/LAZ/PLY export without proprietary lock-in
8. Offline coordinate system and georeference support

## Integration Points

- **PAX Inference Socket:** Local HTTP endpoint at `127.0.0.1:11434/v1/chat` — same OpenAI-compatible API, zero cloud
- **AIOSS Hook:** Every write operation calls `aioss_append(event, payload)` before commit
- **Encryption Layer:** All file I/O routed through `anticloud_crypto.encrypt_at_rest()`
- **Single Binary Build:** `pyinstaller anticloud_trimesh.spec` or `go build -o trimesh`

## Deployment Modes

| Mode | Hardware | Notes |
| --- | --- | --- |
| Edge CPU | Raspberry Pi 4 / Intel NUC | Full feature set, PAX on CPU |
| Desktop GPU | RTX 3060 / A10 | PAX GPU inference, <1s latency |
| Server | 2× A100 | Full batch throughput |
| Air-gapped | Any x86/ARM | Zero network dependency |