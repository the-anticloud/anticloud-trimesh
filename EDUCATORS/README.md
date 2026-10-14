# Educators — TRIMESH

**Project:** TRIMESH  
**Category:** VOXELIZATION  
**Upstream:** see BENCH.json  
**Pinned commit:** `dc8490c825c382d2d58b5bd87ecacc74790ead27`  
**Assurance:** 16/16 checks passing  
**Ledger head:** `59c62c367411c871bf347b5d8f20142e13f0c4f9cebfa86c1d26839dc470072b`  
**Date:** October 2026

## Teaching with TRIMESH

The project is usable as a worked example of offline-first packaging with a
cryptographic audit chain. It ships with the assurance suite, the evidence
register and the ledger, so students can verify claims rather than take them on
faith.

## Suggested exercises

1. Run `python tools/run_bench.py --out BENCH.json` and read the 16 results.
2. Recompute the SHA3-256 of a row's evidence file and compare to the register.
3. Walk the AIOSS chain from genesis to head `59c62c367411c871bf347b5d8f20142e13f0c4f9cebfa86c1d26839dc470072b` and confirm every link.
4. Break one artifact and observe the chain fail to verify.

## Licence for teaching

Apache 2.0 terms apply to academic and teaching use. See `24_ANTICOMMONS_LICENSE`.
