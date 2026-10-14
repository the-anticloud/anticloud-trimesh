# Ethics — TRIMESH

**Project:** TRIMESH  
**Category:** VOXELIZATION  
**Upstream:** see BENCH.json  
**Pinned commit:** `dc8490c825c382d2d58b5bd87ecacc74790ead27`  
**Assurance:** 16/16 checks passing  
**Ledger head:** `59c62c367411c871bf347b5d8f20142e13f0c4f9cebfa86c1d26839dc470072b`  
**Date:** October 2026

## Position

TRIMESH is packaged for offline deployment with a verifiable audit trail. The
ethical questions this raises are answered by making the system's behaviour
checkable rather than by policy statements.

## The four commitments

1. **No hidden egress.** The deployment has no external API dependency; this is
   testable by running it with the network disconnected.
2. **Attributable output.** Every artifact is recorded in a hash chain, so what
   the system produced can be reconstructed.
3. **Operator control.** The institution owns the hardware and the keys.
4. **Refusal to overclaim.** Where a certification is not held, the project says
   so rather than implying it.

## Dual use

This project is packaged for civilian and public-sector deployment. Where an
upstream has dual-use characteristics, the licence gate and the reference-only
marking in `BENCH.json` record that.
