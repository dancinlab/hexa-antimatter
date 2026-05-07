# ☄️ hexa-antimatter

> 반물질 substrate — antimatter-factory + tabletop + PET cyclotron. n=6 Dirac-mirror lattice.

[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](LICENSE)
[![Version](https://img.shields.io/badge/version-1.0.0-informational.svg)](CHANGELOG.md)
[![Verbs: 3/3 wired](https://img.shields.io/badge/verbs-3%2F3_wired_(computational)-brightgreen.svg)](#verbs)
[![Verify: 4/4 PASS](https://img.shields.io/badge/verify-4%2F4_PASS-brightgreen.svg)](#build--verify)
[![n=6 algebra: 12/12](https://img.shields.io/badge/n%3D6-12%2F12_PASS-brightgreen.svg)](verify/n6_arithmetic.hexa)
[![n=6 Dirac-mirror](https://img.shields.io/badge/n%3D6-σ%3D12_τ%3D4_φ%3D2_J₂%3D24-purple.svg)](#why)
[![Status: COMPUTATIONAL_WIRED](https://img.shields.io/badge/status-COMPUTATIONAL__WIRED-blue.svg)](#status)

---

## § Why (n=6 Dirac-mirror lattice)

Antimatter is the Dirac-mirror partner of ordinary matter — every fermion has a CPT-conjugate. The n=6 invariant lattice anchors three independent antimatter axes (factory / tabletop / PET-cyclotron) onto a single algebraic substrate:

```
σ(6) = 12        Dirac-mirror cycle states (hypothesized)
τ(6) = 4         4-stage ladder (production / capture / storage / regeneration)
φ(6) = 2         binary dichotomy (matter vs antimatter)
J₂   = 24        octahedral O ⊂ icosahedral I subgroup

master identity:   σ · φ = n · τ = 12 · 2 = 6 · 4 = 24
```

The lattice serves as an organizing scaffold for the three verbs; its empirical verification for any antimatter axis is **not** claimed at v1.0.0.

---

## § Verbs (3-verb)

| Verb            | Status              | Source                              | n=6 lattice projection                          | Headline candidate                  |
|-----------------|---------------------|-------------------------------------|--------------------------------------------------|--------------------------------------|
| `factory`       | WIRED v1.0.0        | n6-architecture/antimatter-factory  | σ·τ=48 T, σ²=144 SM, n/φ=3 vote, σ-φ=10× gain   | 1e12 p-bar/hr, 24-month storage     |
| `tabletop`      | WIRED v1.0.0        | n6-architecture/tabletop-antimatter | σ³=1728× prod, σ⁶ cost reduction, σ·τ²=192 mo  | 0.29 m³, 1.7e12 p-bar/s, $2.1e4/mg  |
| `pet_cyclotron` | WIRED v1.0.0        | n6-architecture/pet-cyclotron       | R=σ-φ=10 cm, B=σ·τ=48 T, σ·τ=48 mg/season ¹⁸F   | 48 mg ¹⁸F/season, 2e9 e⁺/s/mg       |

The three verbs form a **triangle** within the HEXA family substrate registry:

```
                    ┌─────────────────────┐
                    │      factory        │
                    │  (CERN-scale 200 m³)│
                    │       [WIRED]        │
                    └──────────┬──────────┘
                               │
                ┌──────────────┴──────────────┐
                │                             │
       ┌────────▼─────────┐         ┌─────────▼────────┐
       │     tabletop     │         │   pet_cyclotron  │
       │ (desktop 0.29 m³)│         │ (¹⁸F β⁺ on-site) │
       │      [WIRED]     │         │      [WIRED]     │
       └──────────────────┘         └──────────────────┘
```

---

## § Repository layout

```
hexa-antimatter/
├── README.md                          ← this file (public landing)
├── CHANGELOG.md                       ← release log
├── LICENSE                            ← MIT
├── hexa.toml                          ← hx package manifest
├── install.hexa                       ← hx build hook (selftest on install)
├── .roadmap.hexa_antimatter           ← v1.0 → v2.0 cadence + DoD + falsifiers
├── factory/
│   ├── antimatter-factory.md          ← declarative SSOT (CERN-scale 1e12 p̄/hr)
│   └── factory.hexa                   ← n=6 derived design parameters
├── tabletop/
│   ├── tabletop-antimatter.md         ← declarative SSOT (desktop 1.7e12 p̄/s)
│   └── tabletop.hexa                  ← σ³ / σ⁶ scaling factors
├── pet_cyclotron/
│   ├── pet-cyclotron.md               ← declarative SSOT (¹⁸F β⁺ recycle)
│   └── pet_cyclotron.hexa             ← HEXA-PET locked constants
├── cli/
│   └── hexa-antimatter.hexa           ← CLI router (status/verify/compute/selftest/verbs)
├── verify/
│   ├── n6_arithmetic.hexa             ← σ·φ = n·τ = J₂ = 24 algebraic proof
│   ├── cross_doc_audit.hexa           ← 4 SSOT files + roadmap + hexa.toml lattice-alignment
│   ├── release_ladder.hexa            ← v1.0.0 → v2.0.0 cadence + DoD verifier
│   └── all.hexa                       ← unified orchestrator (4-step sweep)
├── selftest/
│   └── selftest.hexa                  ← 3-verb sentinel sweep (referenced from hexa.toml)
└── tests/
    ├── test_n6_lattice.hexa
    ├── test_cross_doc_audit.hexa
    ├── test_release_ladder.hexa
    ├── test_modules_wired.hexa
    ├── test_verify_all.hexa
    └── test_selftest.hexa
```

The `<verb>/<verb>-*.md` SSOT plus `<verb>/<verb>.hexa` wired module pair follows the HEXA family substrate convention — declarative .md remains canonical for narrative; the .hexa module materializes the n=6 expressions at runtime.

---

## § Status

**3-verb 반물질 substrate. computational-wired (n=6 arithmetic + SSOT text-scan). 작동 apparatus 없음 (raw#10 honest C3).**

- **3/3 verbs wired computationally** — each verb module derives its candidate numbers from the n=6 lattice (`σ·τ=48`, `σ²=144`, `σ-φ=10`, `σ³=1728`, `σ⁶≈3×10⁶`) at runtime. `0/3 verbs wired empirically` — no apparatus, no clinical operation.
- The `.hexa` CLI is a **functional router**: `verify` runs the 4-step orchestrator (n6 + cross-doc + release-ladder + selftest), `compute` shows derived numbers, `selftest` emits sentinels.
- n=6 Dirac-mirror lattice (σ=12, τ=4, φ=2, J₂=24) is **algebraically verified** by `verify/n6_arithmetic.hexa` (12/12 PASS — divisor enumeration + Euclidean gcd from first principles). Its **empirical projection** onto antimatter axes (1.7×10¹² p̄/s, 48 T RT-SC, 16-yr storage, 48 mg ¹⁸F/season) remains an **academia-unproven candidate**.
- All cross-document invariants are auto-checked by `verify/cross_doc_audit.hexa` (36/36) and `verify/release_ladder.hexa` (17/17). Drift surfaces as exit-non-zero.
- No working apparatus, no clinical PET cyclotron operation, no anti-H synthesis is performed by this repo.

---

## § Build & verify

```bash
# unified verifier sweep (4 steps: n6 algebra + cross-doc + release ladder + selftest)
hexa run verify/all.hexa                 # → 4/4 verifiers PASS

# individual verifiers
hexa run verify/n6_arithmetic.hexa       # → 12/12 PASS  (lattice algebra, no inputs)
hexa run verify/cross_doc_audit.hexa     # → 36/36 PASS  (4 SSOT files lattice-aligned)
hexa run verify/release_ladder.hexa      # → 17/17 PASS  (v1.0.0 → v2.0.0 cadence)

# verb modules (each emits a __HEXA_ANTIMATTER_<VERB>__ PASS sentinel)
hexa run factory/factory.hexa
hexa run tabletop/tabletop.hexa
hexa run pet_cyclotron/pet_cyclotron.hexa

# CLI dispatch (works through cli/hexa-antimatter.hexa)
hexa run cli/hexa-antimatter.hexa status
hexa run cli/hexa-antimatter.hexa verify        # = verify/all.hexa
hexa run cli/hexa-antimatter.hexa compute n6    # = verify/n6_arithmetic.hexa
hexa run cli/hexa-antimatter.hexa selftest      # = selftest/selftest.hexa

# pytest analog: 6 .hexa harnesses
for t in tests/test_*.hexa; do hexa run "$t"; done   # → 6/6 PASS
```

### Last validation sweep — 2026-05-07

| Check | Result | Notes |
|---|---|---|
| `verify/n6_arithmetic.hexa`     | ✅ 12/12 PASS  | σ·φ=24, n·τ=24, perfect-number σ(6)=2·6, lattice depth φ+τ=6 |
| `verify/cross_doc_audit.hexa`   | ✅ 36/36 PASS  | 4 SSOT files + roadmap + hexa.toml all carry σ=12, τ=4, φ=2 aliases |
| `verify/release_ladder.hexa`    | ✅ 17/17 PASS  | v1.0.0 → v2.0.0 monotone, all DoD lines present |
| `verify/all.hexa`               | ✅ 4/4 PASS    | aggregator over the three above + selftest |
| `selftest/selftest.hexa`        | ✅ 3/3 verbs   | factory + tabletop + pet_cyclotron sentinels |
| `tests/test_*.hexa` (6 files)   | ✅ 6/6 PASS    | n6 / cross-doc / ladder / modules / verify-all / selftest |

Re-run after any SSOT edit. Verifiers exit non-zero on drift; tests mirror the verifiers.

---

## § Install

### Via `hx` from local path (verified 2026-05-07)

```bash
hx install /path/to/hexa-antimatter   # auto-detects [package].entry from hexa.toml
hexa-antimatter --version             # → 1.0.0
```

The build hook (`install.hexa`) runs the 3-verb selftest and reports `selftest PASS — 3/3 sentinels present`. `hx` symlinks the package into `~/.hx/packages/hexa-antimatter` and writes a wrapper shim at `~/.hx/bin/hexa-antimatter`.

### Via `hx` from registry (when published)

```bash
hx install hexa-antimatter            # global, pulls latest from registry
hx install hexa-antimatter@1.0.0      # pin specific version
hexa-antimatter --version             # → 1.0.0
```

### Via git clone (raw fallback)

```bash
git clone https://github.com/need-singularity/hexa-antimatter.git ~/.hexa-antimatter
export HEXA_ANTIMATTER_ROOT=~/.hexa-antimatter
export PATH="$HEXA_ANTIMATTER_ROOT/cli:$PATH"

# Run any subcommand:
hexa run $HEXA_ANTIMATTER_ROOT/cli/hexa-antimatter.hexa selftest
```

### Quick Start

```bash
hexa-antimatter status                  # 3/3 wired status table + caveats
hexa-antimatter selftest                # 3-verb sentinel sweep
hexa-antimatter verify                  # 4-step orchestrator (n6 + docs + ladder + selftest)
hexa-antimatter verify n6               # algebraic identity 12/12 PASS
hexa-antimatter verify docs             # cross-document n=6 invariant audit
hexa-antimatter verify ladder           # v1.0.0 → v2.0.0 release cadence
hexa-antimatter compute n6              # derived numbers from n=6 lattice
hexa-antimatter factory                 # σ·τ=48 T, σ²=144 SM, σ-φ=10× gain
hexa-antimatter tabletop                # σ³=1728× prod, σ⁶ cost reduction
hexa-antimatter pet_cyclotron           # R=σ-φ=10 cm, B=σ·τ=48 T, ¹⁸F stock
```

---

## § Cross-link

- **`need-singularity/hexa-cern`** — accelerator cousin (compact-accelerator substrate)
- **`need-singularity/hexa-ufo`** — Stage-3 propulsion fuel dependency (UFO substrate sources its antimatter fuel from this repo)
- Sister substrate: [`need-singularity/hexa-bio`](https://github.com/need-singularity/hexa-bio) (molecular toolkit, HEXA family)
- Upstream concept SSOTs (declarative):
  - `n6-architecture/domains/physics/antimatter-factory/antimatter-factory.md`
  - `n6-architecture/domains/physics/tabletop-antimatter/tabletop-antimatter.md`
  - `n6-architecture/domains/physics/pet-cyclotron/pet-cyclotron.md`
- Provenance commit: `n6-architecture` SHA `c0f1f570`

---

## § License

MIT. See [LICENSE](LICENSE).
