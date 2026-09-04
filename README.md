# LEEWAY-AGENT-AVATAR-FACTORY

Governed hybrid avatar presentation and capability-integration layer for **InteractAvatar + MultiTalk**.

## What runs on GitHub Pages

The `site/` directory is a dependency-free interactive control/presentation UI. It supports agent profiles, embodiment staging, MultiTalk staging, hybrid route planning, runtime binding, browser simulation, and governed worker dispatch. Browser simulation is deliberately labeled **SIMULATION** and never reported as real GPU execution.

## What does not run on GitHub Pages

CUDA/PyTorch inference. Real InteractAvatar and MultiTalk rendering belongs on a GPU worker behind LeeWay Runtime Fabric. The fail-closed worker contract is under `worker/` and execution is disabled by default.

## Upstream capability donors

- InteractAvatar — `angzong/InteractAvatar@5ca013e571891e7d00dea3cebd739f98d7942f26` — Apache-2.0.
- MultiTalk — `MeiGen-AI/MultiTalk@c1ad84009b99ed36c97ab18e4517ca5f98692438` — Apache-2.0.

See `docs/ARCHITECTURE.md` and `THIRD_PARTY_NOTICES.md`.

## Local static test

```bash
node tests/static-check.mjs
python -m http.server 8080 --directory site
```

Then open `http://localhost:8080`.

## Worker contract test

```bash
node worker/router.mjs
```

With the default environment, `/health` will report reachability while execution remains disabled. This is intentional.
