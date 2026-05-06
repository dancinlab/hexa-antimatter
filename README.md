# ☄️ hexa-antimatter

> 반물질 substrate — antimatter-factory + tabletop + PET cyclotron. n=6 Dirac-mirror lattice.

[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](LICENSE)
[![Version](https://img.shields.io/badge/version-1.0.0-informational.svg)](CHANGELOG.md)
[![Verbs: 0/3 wired](https://img.shields.io/badge/verbs-0%2F3_wired_(spec--first)-orange.svg)](#verbs)
[![n=6 Dirac-mirror](https://img.shields.io/badge/n%3D6-σ%3D12_τ%3D4_φ%3D2_J₂%3D24-purple.svg)](#why)
[![Status: SPEC_FIRST](https://img.shields.io/badge/status-SPEC__FIRST-lightgrey.svg)](#status)

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

| Verb            | Status         | Source                              | Headline candidate                          |
|-----------------|----------------|-------------------------------------|---------------------------------------------|
| `factory`       | SPEC v1.0.0    | n6-architecture/antimatter-factory  | 1e12 p-bar/hr, 24-month Penning storage     |
| `tabletop`      | SPEC v1.0.0    | n6-architecture/tabletop-antimatter | 0.29 m³, 1.7e12 p-bar/s, $2.1e4/mg          |
| `pet_cyclotron` | SPEC v1.0.0    | n6-architecture/pet-cyclotron       | R=10 cm, B=48 T, 48 mg ¹⁸F/season           |

The three verbs form a **triangle** within the HEXA family substrate registry:

```
                    ┌─────────────────────┐
                    │      factory        │
                    │  (CERN-scale 200 m³)│
                    └──────────┬──────────┘
                               │
                ┌──────────────┴──────────────┐
                │                             │
       ┌────────▼─────────┐         ┌─────────▼────────┐
       │     tabletop     │         │   pet_cyclotron  │
       │  (desktop 0.29 m³)│         │ (¹⁸F β⁺ on-site) │
       └──────────────────┘         └──────────────────┘
            [SPEC]                        [SPEC]
```

---

## § Status

**3-verb 반물질 substrate. spec-first (작동 .hexa CLI TBD). PET-사이클로트론(¹⁸F β⁺ on-site regeneration) + 탁상반물질(desktop 1.7×10¹² p̄/s 후보) + 반물질 공장. 학계 미증명 후보.**

- 0/3 verbs empirically wired. All 3 ship as **spec stubs** with declarative `.md` SSOT extracted from `n6-architecture/domains/physics/` (SHA `c0f1f570`).
- The `.hexa` CLI is a **placeholder router** that prints sentinels and caveat tables — no working numerical sandbox.
- n=6 Dirac-mirror lattice (σ=12, τ=4, φ=2, J₂=24) is an **algebraic conjecture** — NOT independently verified for any of the 3 axes.
- All headline numbers (1e12 p-bar/hr factory throughput, 1.7e12 p-bar/s tabletop, 48 T RT-SC Penning trap, 48 mg ¹⁸F/season) are **academia-unproven candidates** sourced from the declarative `.md` SSOT.
- No working apparatus, no clinical PET cyclotron operation, no anti-H synthesis is performed by this repo.

---

## § Install

### Via `hx` (recommended, when registered)

```bash
hx install hexa-antimatter            # global, pulls latest from registry
hx install hexa-antimatter@1.0.0      # pin specific version
hexa-antimatter --version             # → 1.0.0
```

### Via git clone (works today)

```bash
git clone https://github.com/need-singularity/hexa-antimatter.git ~/.hexa-antimatter
export HEXA_ANTIMATTER_ROOT=~/.hexa-antimatter
export PATH="$HEXA_ANTIMATTER_ROOT/cli:$PATH"

# Run any subcommand:
hexa run $HEXA_ANTIMATTER_ROOT/cli/hexa-antimatter.hexa selftest
```

### Quick Start

```bash
hexa-antimatter selftest                # 3-verb sentinel sweep
hexa-antimatter status                  # status table + caveats
hexa-antimatter factory                 # spec sentinel
hexa-antimatter tabletop                # spec sentinel
hexa-antimatter pet_cyclotron           # spec sentinel
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
