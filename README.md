# LEEWAY-AGENT-AVATAR-FACTORY

Governed hybrid avatar presentation and capability-integration layer for **InteractAvatar + MeiGen MultiTalk**.

## Live GitHub Pages

The public Pages surface is image-first and uses human-reference examples from the upstream avatar projects rather than mannequin-style placeholders:

- Human agent staging
- MultiTalk two-person conversation staging
- InteractAvatar grounded object-interaction staging
- Hybrid MultiTalk → InteractAvatar sequencing
- LeeWay runtime binding / claim-state UI

Pages remains a presentation/control surface. Browser simulation is labeled **SIMULATION** and is never reported as real GPU execution.

## Pinned source dependencies

The upstream engines are now real Git submodules in this repository:

- `vendor/InteractAvatar` → `https://github.com/angzong/InteractAvatar.git`
  - pinned commit: `5ca013e571891e7d00dea3cebd739f98d7942f26`
- `vendor/MultiTalk` → `https://github.com/MeiGen-AI/MultiTalk.git`
  - pinned commit: `c1ad84009b99ed36c97ab18e4517ca5f98692438`

Clone the complete factory with both engines:

```bash
git clone --recurse-submodules https://github.com/4citeB4U/LEEWAY-AGENT-AVATAR-FACTORY.git
cd LEEWAY-AGENT-AVATAR-FACTORY
git submodule update --init --recursive
```

If the repository was already cloned:

```bash
git pull
git submodule sync --recursive
git submodule update --init --recursive
```

## LeeWay capability boundary

```text
Creator / Human Authority
  -> LeeWay Standards
  -> Runtime Fabric
  -> Veritas pre-gate
  -> Harness / Formula / Dispatcher
  -> InteractAvatar | MultiTalk | Hybrid sequence
  -> real GPU execution
  -> Veritas post-gate
  -> receipt
  -> Learning Ledger
```

InteractAvatar and MultiTalk are **capability donors**, not LeeWay authority layers.

## What does not run on GitHub Pages

CUDA/PyTorch model inference. Real InteractAvatar and MultiTalk rendering belongs on a governed GPU worker behind LeeWay Runtime Fabric. The worker contract remains fail-closed until the real execution lane is bound and authorized.

## Media boundary

The live UI uses upstream research-reference imagery so the site visually reflects what the projects actually work with. Those media assets retain upstream rights and restrictions. MultiTalk's project materials note that some demonstration media is derived from real video and is intended for academic demonstration; production/commercial LeeWay agents should use LeeWay-owned or properly licensed reference media.

## Local static test

```bash
node tests/static-check.mjs
python -m http.server 8080 --directory site
```

## Worker contract test

```bash
node worker/router.mjs
```

With the default environment, `/health` can report worker reachability while execution remains disabled. That is intentional until the governed runtime path is bound.

See `docs/ARCHITECTURE.md` and `THIRD_PARTY_NOTICES.md`.
