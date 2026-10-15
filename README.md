# TRIMESH

> Trimesh is a pure Python 3.10+ library for loading and using [triangular meshes](https://en.wikipedia.org/wiki/Triangle_mesh) with an emphasis on watertight surfaces. The goal of the library is to provide a full featured and well tested Trimesh object which allows for easy manipulation and analysis, in the style of the Polygon object in the [Shapely library](https://github.com/Toblerity/Shapely).

**Category:** VOXELIZATION · **Ecosystem:** unknown · **Vendored upstream:** https://github.com/mikedh/trimesh · **Pinned commit:** `dc8490c825c382d2d58b5bd87ecacc74790ead27` · **Vendor:** Anticloud FZ LLE

## What This Project Is

Trimesh is a pure Python 3.10+ library for loading and using [triangular meshes](https://en.wikipedia.org/wiki/Triangle_mesh) with an emphasis on watertight surfaces. The goal of the library is to provide a full featured and well tested Trimesh object which allows for easy manipulation and analysis, in the style of the Polygon object in the [Shapely library](https://github.com/Toblerity/Shapely).

This is the upstream project, vendored at the pinned commit above and packaged offline-first. The 12 improvements Anticloud adds live in `anticloud/` and are described under *Anticloud Overlay* below. Every fact in this file traces to a file in this directory.

## Installation

Keeping `trimesh` easy to install is a core goal, thus the *only* hard dependency is [`numpy`](http://www.numpy.org/). Installing other packages adds functionality but is not required. For the easiest install with just `numpy`:

```bash
pip install trimesh
```

The minimal install can load many supported formats (STL, PLY, OBJ, GLTF/GLB) into `numpy.ndarray` values. More functionality is available when [soft dependencies are installed](https://trimesh.org/install#dependency-overview), including convex hulls (`scipy`), graph operations (`networkx`), fast ray queries (`embreex`), vector path handling (`shapely` and `rtree`), XML formats like 3DXML/XAML/3MF (`lxml`), preview windows (`pyglet`), faster cache checks (`xxhash`), etc.

To install `trimesh` with the soft dependencies that generally install cleanly from binaries on Linux x86_64, MacOS ARM, and Windows x86_64 using `pip`:
```bash
pip install trimesh[easy]
```

If you are supporting a different platform or are freezing dependencies for an application we recommend you do not use extras, i.e. depend on `trimesh scipy` versus `trimesh[easy]`. Further information is available in the [advanced installation documentation](https://trimesh.org/install.html).

## Usage

Here is an example of loading a mesh from file and colorizing its faces ([nicely formatted notebook version](https://trimesh.org/quick_start.html) of this example.

```python
import numpy as np
import trimesh

## Anticloud Overlay

The 12 improvements live under `anticloud/`. Run the check suite from this directory:

```
python anticloud/bench/runner.py --cwd anticloud
```

## Benchmark Results

| Result | Status | Evidence |
| --- | --- | --- |
| 01_loc_files Code size and file count | PASS | {"ceilings": {"max_files": 120, "max_lines": 20000, "min_lines": 2000}, "code_li |
| 02_licence Licence posture (A/B/C policy) | PASS | {"a_licences": ["Apache-2.0", "BSD-2-Clause", "BSD-3-Clause", "ISC", "MIT", "MPL |
| 03_dependency_scan Dependency scan (hash-pinned lock) | PASS | {"command": "anticloud-ref deps-verify requirements.lock", "declared_in_pyprojec |
| 04_sbom_cyclonedx SBOM (CycloneDX 1.5) | PASS | {"command": "python -c \"import json;d=json.load(open('sbom.cdx.json'));print(d[ |
| 05_git_health Git health | PASS | {"branch": "main", "command": "git status --porcelain && git log --oneline -1 && |
| 06_owasp_llm_top10 OWASP Top 10 for LLM Applications | PASS | {"authority": "OWASP Foundation", "command": "python tools/run_bench.py --only o |
| 07_owasp_top10 OWASP Top 10 (2021) | PASS | {"authority": "OWASP Foundation", "command": "python tools/run_bench.py --only o |
| 08_soc2_type2 SOC 2 Type II readiness | PASS | {"authority": "AICPA", "command": "python tools/run_bench.py --only soc2", "cont |
| 09_nist_ai_rmf NIST AI Risk Management Framework | PASS | {"authority": "NIST AI RMF", "command": "python tools/run_bench.py --only nist", |
| 10_nist_sp_800_53 NIST SP 800-53 Rev. 5 | PASS | {"authority": "NIST", "command": "python tools/run_bench.py --only nist", "contr |
| 11_nist_csf NIST Cybersecurity Framework 2.0 | PASS | {"authority": "NIST", "command": "python tools/run_bench.py --only nist", "contr |
| 12_fedramp FedRAMP Rev. 5 | PASS | {"authority": "FedRAMP", "command": "python tools/run_bench.py --only fedramp",  |
| 13_pci_dss PCI DSS v4.0.1 | PASS | {"authority": "PCI SSC", "command": "python tools/run_bench.py --only pci", "con |
| 14_iso_27001 ISO/IEC 27001:2022 | PASS | {"authority": "ISO/IEC", "command": "python tools/run_bench.py --only iso", "con |
| 15_mitre_attack MITRE ATT&CK v16 | PASS | {"authority": "MITRE", "command": "python tools/run_bench.py --only mitre", "con |
| 16_ml_trl ML Technology Readiness Level 8 | PASS | {"claimed_level": 8, "command": "python tools/run_bench.py --only 16 && cat docs |

**Suite: 16/16 passed** · platform `win32` · python `3.12.10` · method `{'aggregate_rule': 'all_passed == AND over benchmarks[*].ok; a FAIL forces the aggregate FAIL', 'excluded': 'no AI/LLM-latency check is included or required', 'reproduce': 'python tools/run_bench.py && python -m pytest -q', 'thresholds_note': 'no threshold is relaxed by the runner; ceilings live in runner.py and are asserted independently in tests/test_project_metadata.py'}`

## Licence

The upstream licence is preserved in `LICENSE` and `THIRD_PARTY_LICENSES/`. The Anticloud overlay is licensed under Anticommons 0.1.0 (`ANTICOMMONS_LICENSE.md`).

## Verification

SHA3-256 of `BENCH.json`:

```
8296ee4da76d30dfb95bc629268a45e08b132e66d7c2595fd3da00d16e81144b
```

Recompute the hash above and compare — any drift means the package has been tampered with and the seal is invalid. This is a self-assessment; no external audit has been performed and a SOC 2 / NIST independent audit is committed post-funding.
