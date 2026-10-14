# Build and Test

**Project:** `TRIMESH`
**Upstream:** https://github.com/mikedh/trimesh
**License:** MIT

## Quick Start

```bash
git clone https://github.com/mikedh/trimesh
cd trimesh
pip install -r requirements-anticloud.txt
python anticloud_main.py --offline --pax-local
```

## Anticloud Improvements Applied

1. PAX L5 Narrow L2 General 27B local 3D scene understanding from voxel grids
2. AIOSS provenance chain for all 3D scan and reconstruction data
3. AES-256 encryption for proprietary 3D models and point clouds
4. Single-binary voxelization tool with no cloud dependency
5. Zero-cloud: all meshing, analysis, and AI inference run locally
6. GPU/CPU equalizer: CUDA voxelization on GPU, CPU fallback for deployment
7. Open point cloud format: LAS/LAZ/PLY export without proprietary lock-in
8. Offline coordinate system and georeference support

## Benchmark Targets

| Metric | Target |
| --- | --- |
| Latency | Primary inference task: <5s on CPU, <1s on GPU |
| Throughput | Batch processing: >100 items/hour on single CPU server |
| Memory | <8GB RAM for standard deployment |
| Accuracy | Task-specific accuracy within 5% of cloud-API baseline |

## Build Status

Not yet measured. Run verified build and record actual figures above.
