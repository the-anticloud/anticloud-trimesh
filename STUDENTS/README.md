# Students — TRIMESH

**Project:** TRIMESH  
**Category:** VOXELIZATION  
**Upstream:** see BENCH.json  
**Pinned commit:** `dc8490c825c382d2d58b5bd87ecacc74790ead27`  
**Assurance:** 16/16 checks passing  
**Ledger head:** `59c62c367411c871bf347b5d8f20142e13f0c4f9cebfa86c1d26839dc470072b`  
**Date:** October 2026

## What this project gives you

A complete worked example of offline-first packaging with a cryptographic audit
chain: source pinned at `dc8490c825c382d2d58b5bd87ecacc74790ead27`, a 16-check assurance suite, an evidence register
with per-check hashes, and an AIOSS ledger chain ending at `59c62c367411c871bf347b5d8f20142e13f0c4f9cebfa86c1d26839dc470072b`.

## Learn by verifying

```
python tools/run_bench.py --out BENCH.json
```

Then take any row from `ISOLATED_LAB_RESULTS/03_Result_Register.md`, recompute
the SHA3-256 of its evidence file, and confirm it matches. If it does not match,
the record has been altered — that is the whole point of the chain.

## Licence

Apache 2.0 terms apply to study and teaching use.
