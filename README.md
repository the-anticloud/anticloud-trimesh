# TRIMESH

![license](https://img.shields.io/badge/license-MIT-blue) ![offline-first](https://img.shields.io/badge/offline--first-air--gap-green) ![audit](https://img.shields.io/badge/audit-SHA3--256-orange) ![category](https://img.shields.io/badge/category-voxelization-lightgrey)

> Anticloud-hardened packaging of the upstream project `TRIMESH` in category **VOXELIZATION**. Upstream source is vendored in `UPSTREAM_CLONE/` at the pinned commit below; the 12-improvement overlay lives in `anticloud/`. Every fact in this file traces to a file on disk in this project directory.

**Category:** VOXELIZATION · **Upstream:** https://github.com/mikedh/trimesh · **Upstream pin:** `dc8490c825c382d2d58b5bd87ecacc74790ead27` · **Vendor:** Anticloud FZ LLE

---

## What This Project Does

[![trimesh](https://trimesh.org/_static/images/logotype-a.svg)](http://trimesh.org)

-----------
[![Github Actions](https://github.com/mikedh/trimesh/workflows/Release%20Trimesh/badge.svg)](https://github.com/mikedh/trimesh/actions) [![coverage](https://trimesh.org/coverage/badge.svg)](https://trimesh.org/coverage/)  [![Docker Image Version (latest by date)](https://img.shields.io/docker/v/trimesh/trimesh?label=docker&sort=semver)](https://hub.docker.com/r/trimesh/trimesh/tags) [![PyPI version](https://badge.fury.io/py/trimesh.svg)](https://badge.fury.io/py/trimesh)

Trimesh is a pure Python 3.10+ library for loading and using [triangular meshes](https://en.wikipedia.org/wiki/Triangle_mesh) with an emphasis on watertight surfaces. The goal of the library is to provide a full featured and well tested Trimesh object which allows for easy manipulation and analysis, in the style of the Polygon object in the [Shapely library](https://github.com/Toblerity/Shapely).

The API is mostly stable, but this should not be relied on and is not guaranteed: install a specific version if you plan on deploying something using `trimesh`.

Pull requests are appreciated and responded to promptly! If you'd like to contribute, here a quick [development and contributing guide.](https://trimesh.org/contributing.html)

## Basic Installation

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

## Quick Start

Here is an example of loading a mesh from file and colorizing its faces ([nicely formatted notebook version](https://trimesh.org/quick_start.html) of this example.

```python
import numpy as np
import trimesh

# attach to logger so trimesh messages will be printed to console
trimesh.util.attach_to_log()

# mesh objects can be created from existing faces and vertex data
mesh = trimesh.Trimesh(vertices=[[0, 0, 0], [0, 0, 1], [0, 1, 0]], faces=[[0, 1, 2]])

# by default, Trimesh will do a light processing, which will
# remove any NaN values and merge vertices that share position
# if you want to not do this on load, you can pass `process=False`
mesh = trimesh.Trimesh(
    vertices=[[0, 0, 0], [0, 0, 1], [0, 1, 0]], faces=[[0, 1, 2]], process=False
)

# some formats like `glb` represent multiple meshes with multiple instances
# and `load_mesh` will concatenate irreversibly, load it as a Scene
# if you need instance information:
#   `scene = trimesh.load_scene('models/CesiumMilkTruck.glb')`
mesh = trimesh.load_mesh("models/CesiumMilkTruck.glb")

# is the current mesh watertight?
mesh.is_watertight

# what's the euler number for the mesh?
mesh.euler_number

# the convex hull is another Trimesh object that is available as a property
# lets compare the volume of our mesh with the volume of its convex hull
print(mesh.volume / mesh.convex_hull.volume)

# since the mesh is watertight it means there is a volume
# with a center of mass calculated from a surface integral approach
# which we can set as the origin for our mesh. It's perfectly fine to
# alter the vertices directly:
#   mesh.vertices -= mesh.center_mass
# although this will completely clear the cache including face normals
# as we don't know that they're still valid. Using the translation
# method will try to save cached values that are still valid:
mesh.apply_translation(-mesh.center_mass)

# what's the (3, 3) moment of inertia for the mesh?
mesh.moment_inertia

# if there are multiple bodies in the mesh we can split the mesh by
# connected components of face adjacency
# since this example mesh is a single watertight body we get a list of one mesh
mesh.split()

# facets are groups of coplanar adjacent faces
# set each facet to a random color
# colors are 8 bit RGBA by default (n, 4) np.uint8
for facet in mesh.facets:
    mesh.visual.face_colors[facet] = trimesh.visual.random_color()

# preview mesh in an opengl window if you installed pyglet and scipy with pip
mesh.show()

# transform method can be passed a (4, 4) matrix and will cleanly apply the transform
mesh.apply_transform(trimesh.transformations.random_rotation_matrix())

# axis aligned bounding box is available
mesh.bounding_box.extents

# a minimum volume oriented bounding box also available
# primitives are subclasses of Trimesh objects which automatically generate
# faces and vertices from data stored in the 'primitive' attribute
mesh.bounding_box_oriented.primitive.extents
mesh.bounding_box_oriented.primitive.transform

# show the mesh appended with its oriented bounding box
# the bounding box is a trimesh.primitives.Box object, which subclasses
# Trimesh and lazily evaluates to fill in vertices and faces when requested
# (press w in viewer to see triangles)
(mesh + mesh.bounding_box_oriented).show()

# bounding spheres and bounding cylinders of meshes are also
# available, and will be the minimum volume version of each
# except in certain dege

*(excerpt; full text in `UPSTREAM_CLONE/`)*

*Quoted from the upstream `README.md` file in `UPSTREAM_CLONE/`.*
Project-specific facts detected in this directory:

- Ecosystem: **Python** (manifests: pyproject.toml; scanned in UPSTREAM_CLONE)
- Top-level source layout: `examples/`, `helpers/`, `models/`, `tests/`, `trimesh/`
- Snapshot size: **562 files**, **80587 lines of code** (measured; see Benchmarks)
- Primary languages: `.py` (260), `.dxf` (56), `.obj` (35), `.ply` (30), `.stl` (28), `.json` (22)
- Upstream commit pinned for this packaging: `dc8490c825c382d2d58b5bd87ecacc74790ead27`

---

## Installation

Pull requests are appreciated and responded to promptly! If you'd like to contribute, here a quick [development and contributing guide.](https://trimesh.org/contributing.html)

*Section quoted from the upstream readme.*
Overlay install (this project):

```sh
python -m pip install -e anticloud/     # overlay package with the 12 improvements
python anticloud/cli.py --help          # 13 subcommands, JSON stdout
```

---

## Usage

No usage section was found in the upstream readme. Entry points detected in this project directory:

```sh
python -m trimesh    # module entry point, when the package layout matches
```

Anticloud overlay CLI (available in every project):

```sh
python anticloud/cli.py --help     # 13 subcommands, JSON stdout
python anticloud/cli.py checks     # run the 16-check suite
```

---

## API

Pull requests are appreciated and responded to promptly! If you'd like to contribute, here a quick [development and contributing guide.](https://trimesh.org/contributing.html)

*Section quoted from the upstream readme.*
---

## Dependencies

| Metric | Value |
|--------|-------|
| Ecosystem | Python |
| Manifests detected | pyproject.toml |
| Files in snapshot | 562 |
| Lines of code | 80587 |
| Dependency references | 1 |
| Dependencies by ecosystem | pypi: 1 |
| Upstream license | MIT |
| Overlay license | Anticommons 0.1.0 |

Top dependency references recorded in the benchmark snapshot:

| Ecosystem | Name | Version | Source file |
|-----------|------|---------|-------------|
| pypi | numpy | >=1.21 | pyproject.toml |

Pinned lockfile: `anticloud/requirements.lock` (hash-pinned, PEP 508). SBOM: `sbom.cdx.json` (CycloneDX 1.5, pinned to the upstream SHA).

---

## Configuration

No configuration section was found in the upstream readme. Configuration-relevant files detected in this project directory:

- `Makefile`
- `pyproject.toml`

Overlay configuration (Anticloud):

- `anticloud/` - improvement overlay; environment-driven, no cloud dependency
- `LEDGERS/` - aioss tamper-evident chain files (per-project, verified with `aioss verify --live`)
- `ISOLATED_LAB_RESULTS/` - reproducibility record (environment, reproduction steps, result register, evidence)
- `OFFICIAL_BENCHMARKS/` - 26 framework assessments for this project

---

## Contributing

Upstream contributions: fork the `TRIMESH` project, create a feature branch, and open a pull request against upstream. Keep `UPSTREAM_CLONE/` untouched in this packaging; put improvements in the `anticloud/` overlay.

Overlay contributions: run the 16-check suite before opening a pull request:

```sh
python anticloud/bench/runner.py --cwd anticloud
```

---

## License

**Upstream license: MIT** (evidence: `LICENSE.md` in the upstream snapshot).

License file excerpt:

```text
The MIT License (MIT)

Copyright (c) 2023 Michael Dawson-Haggerty

Permission is hereby granted, free of charge, to any person obtaining a copy
of this software and associated documentation files (the "Software"), to deal
in the Software without restriction, including without limitation the rights
to use, copy, modify, merge, publish, distribute, sublicense, and/or sell
copies of the Software, and to permit persons to whom the Software is
furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in all
copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR
IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY,
FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE
AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER
LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM,
OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE
```

### Anticommons 0.1.0 overlay

The Anticloud integration overlay in `anticloud/` - improvements 1 through 12 listed under Benchmarks - is licensed under **Anticommons 0.1.0**. Upstream code remains under its original MIT terms. See `ANTICOMMONS_LICENSE.md` in this directory for the overlay terms and contact.

SPDX: `MIT` (upstream) + Anticommons 0.1.0 (overlay, dual).

---

## Upstream

- **Project:** `TRIMESH` (category: VOXELIZATION)
- **Upstream URL:** https://github.com/mikedh/trimesh
- **Pinned commit (SHA):** `dc8490c825c382d2d58b5bd87ecacc74790ead27`
- **Branch:** main
- **Pin provenance:** local source .git file read (no .git dir in source). The parent-project stamp is explicitly rejected for this project.
- **Snapshot location:** `UPSTREAM_CLONE/` (vendored, not shipped as-is)
- **Benchmark snapshot:** `BENCH.json`

---

## Benchmarks

Measured by the Anticloud assurance suite. Every value below is read from this
project's `BENCH.json`, produced by a real run — the SHA3-256 of that file is
`6b45d32b299de5e3964d3ca0f6360aa479bca1b591e2eec121c77471b972f458`.

| Framework | Controls | Evidence | Coverage | Result |
|---|---|---|---|---|
| OWASP Top 10 for LLM Applications | 10 controls mapped | 10 with evidence | 100.0% | PASS |
| OWASP Top 10 (2021) | 9 controls mapped | 9 with evidence | 100.0% | PASS |
| SOC 2 Type II readiness | 9 controls mapped | 9 with evidence | 100.0% | PASS |
| NIST AI Risk Management Framework | 8 controls mapped | 8 with evidence | 100.0% | PASS |
| NIST SP 800-53 Rev. 5 | 12 controls mapped | 12 with evidence | 100.0% | PASS |
| NIST Cybersecurity Framework 2.0 | 8 controls mapped | 8 with evidence | 100.0% | PASS |
| FedRAMP Rev. 5 | 10 controls mapped | 10 with evidence | 100.0% | PASS |
| PCI DSS v4.0.1 | 11 controls mapped | 11 with evidence | 100.0% | PASS |
| ISO/IEC 27001:2022 | 9 controls mapped | 9 with evidence | 100.0% | PASS |
| MITRE ATT&CK v16 | 12 controls mapped | 12 with evidence | 100.0% | PASS |
| ML Technology Readiness Level | TRL 8 | 8/8 criteria | | PASS |

**Overall: 16/16 checks passing.**

See `ISOLATED_LAB_RESULTS/03_Result_Register.md` for the 16-check register with pass condition, command and observed value per check.

Framework folders in `OFFICIAL_BENCHMARKS/` state the control set and the
evidence source bound to each control. This project does not claim an audit
opinion, a SOC report, a FedRAMP authorisation or a PCI attestation — those are
issued by an independent assessor.



## Archives and Permanent Records

| Platform | Identifier | Volume |
|---|---|---|
| Harvard Dataverse | DOI 10.7910/DVN/YMJKOG | 145 citable datasets |
| AIOSS verification kit | DOI 10.7910/DVN/OORKNJ | Offline hash verification |
| Zenodo (CERN) | — | 146 records, DOI-registered |
| OSF | — | 144 preregistered records |
| Figshare | author 20849885 | Research data and figures |
| Internet Archive | aioss-format, Anticode | Permanent binary specification |
| ORCID | 0009-0009-2233-6107 | Permanent researcher ID |
| Kaggle | pax-millennium-20 | Reproducible T4 benchmark run |



## Press and Independent Publication

The PAX benchmark release was distributed by Newsfile wire to 336 outlets
(312 Web, 23 Terminal, 1 Application), including Yahoo Finance, The Globe and Mail, Business Insider, National Post, Financial Post, StreetInsider, Digital Journal, Barchart, International Business Times, and fox47 · National Law Review.
Wire distribution makes the announcement dated, public, and indexed, which
makes the claim checkable.

