<p align="center">
  <img src="docs/logo.svg" width="140" alt="hexa-antimatter">
</p>

<h1 align="center">🌀 hexa-antimatter</h1>

<p align="center"><strong>HEXA-Antimatter Family</strong> — antimatter physics · factory · tabletop · PET cyclotron · n=6 Dirac-mirror lattice</p>

<p align="center">
  <a href="LICENSE"><img alt="License" src="https://img.shields.io/badge/license-MIT-blue"></a>
  <a href="https://doi.org/10.5281/zenodo.20077465"><img alt="DOI" src="https://zenodo.org/badge/DOI/10.5281/zenodo.20077465.svg"></a>
  <img alt="Spec" src="https://img.shields.io/badge/spec-v1.1.0--RSC--FINAL-success">
  <img alt="Verbs" src="https://img.shields.io/badge/verbs-3%2F3_wired-informational">
  <img alt="Verify" src="https://img.shields.io/badge/verify-38%2F38_PASS-informational">
  <img alt="Closure" src="https://img.shields.io/badge/closure-100%25-informational">
  <img alt="Sibling" src="https://img.shields.io/badge/sibling-hexa--cern%20·%20hexa--ufo%20·%20hexa--bio-blueviolet">
</p>

<p align="center">Dirac-mirror · n=6 lattice · σ·φ=24 · CPT-conjugate · falsifier-ladder · RSC-saturated · MIT</p>

---

`hexa-antimatter` is a HEXA-family substrate for antimatter physics — three independent verbs (factory / tabletop / PET-cyclotron) anchored onto the n=6 invariant lattice, with a 38-step bookkeeping closure (T1 algebraic + T2 numerical + T3 archival-empirical) and Phase A→D paper-spec scaffolding (BOM → numerics → sim → board pinout → HDL/MCU skeletons).

> [!NOTE]
> Member of the HEXA family (parent: `dancinlab/echoes`). Sister substrates: [`hexa-cern`](https://github.com/dancinlab/hexa-cern) (compact accelerator), [`hexa-ufo`](https://github.com/dancinlab/hexa-ufo) (Stage-3 propulsion fuel consumer), [`hexa-bio`](https://github.com/dancinlab/hexa-bio) (molecular toolkit). All share the n=6 lattice scaffold and the same falsifier-ladder convention.

## Why (n=6 Dirac-mirror lattice)

Antimatter is the Dirac-mirror partner of ordinary matter — every fermion has a CPT-conjugate. The n=6 invariant lattice anchors three independent antimatter axes (factory / tabletop / PET-cyclotron) onto a single algebraic substrate:

```
σ(6) = 12        Dirac-mirror cycle states (hypothesized)
τ(6) = 4         4-stage ladder (production / capture / storage / regeneration)
φ(6) = 2         binary dichotomy (matter vs antimatter)
J₂   = 24        octahedral O ⊂ icosahedral I subgroup

master identity:   σ · φ = n · τ = 12 · 2 = 6 · 4 = 24
```

The lattice serves as an organizing scaffold for the three verbs; its empirical verification for any antimatter axis is **not** claimed at v1.0.0.

## Status

- **3/3 verbs wired computationally** — each verb derives candidate numbers from the n=6 lattice (`σ·τ=48`, `σ²=144`, `σ-φ=10`, `σ³=1728`, `σ⁶≈3×10⁶`) at runtime.  `0/3 wired empirically`.
- `.hexa` CLI now dispatches 30+ `verify` sub-targets across **25 verify scripts** (4 cross-cutter + 4 calc T1 + 14 numerics T2 + 4 empirical T3 + 3 meta).  `verify all` runs the 38-step aggregator.
- **All 4 falsifiers (F-AM-1/2/3/4)** carry T1 algebra + T2 ×4 numerics (incl. Stage-1 sim parity) + T3 paper-existence (Inspire-HEP, ≥3 of 4 milestones per falsifier).  → 100% bookkeeping closure.  Strict raw-data fit awaits Stage-1+ hardware (.roadmap §A.6, v2.0.0 ASPIRATIONAL).
- `verify/saturation_check.hexa` emits `__HEXA_ANTIMATTER_RSC_SATURATED__ STOP` + `__RSC_FULL_CLOSURE__ 100%` — RSC closure-depth-accumulation loop properly terminates.
- Phase A → B → C → C.5 → D paper specifications **all landed** (BOM → numerics → sim → board pinout → HDL/MCU skeletons).  No PCBs / no flashed firmware exist; § A.6.1 step 4 awaits funding.

> [!IMPORTANT]
> `__HEXA_ANTIMATTER_RUN_ALL__ PASS` means **bookkeeping closure** of the verified-stable core, NOT antimatter physics settled. No PCB, no flashed firmware, no physical antihydrogen yield from this repo. Per [`LATTICE_POLICY.md`](LATTICE_POLICY.md): lattice tautologies (σ·φ=24) alone are NOT sufficient verification; the `numerics_*` tier carries the real-limits anchors (¹⁸F half-life 109.77 min, CPT invariance, Tsiolkovsky rocket equation — see [`LIMIT_BREAKTHROUGH.md`](LIMIT_BREAKTHROUGH.md)).

## Install

```sh
# 1. Install hexa-lang (gives you `hexa` + `hx` package manager)
/bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/dancinlab/hexa-lang/main/install.sh)"

# 2. Install hexa-antimatter
hx install hexa-antimatter
```

`hexa-antimatter` is **pure hexa-lang stdlib** — zero Python deps, zero external. All default subcommands run with `hx install hexa-antimatter` alone. Cross-substrate extras (e.g. `qmirror` for ANU-QRNG + Aer state-vector simulator) are auto-resolved by `hx install` when declared in `hexa.toml`.

## Run

```sh
hexa-antimatter factory          # CERN-scale antimatter factory verb [WIRED]   (1e12 p-bar/hr candidate)
hexa-antimatter tabletop         # desktop 1.7e12 p-bar/s candidate [WIRED]
hexa-antimatter pet_cyclotron    # 18F beta+ on-site regeneration [WIRED]        (48 mg/season stock)
hexa-antimatter status           # 3/3 wired verb table + verdict + caveats
hexa-antimatter verify [target]  # run verifier(s); target ∈ all|n6|docs|ladder|...
hexa-antimatter compute <name>   # show derived numbers; name ∈ n6|factory|tabletop|pet_cyclotron
hexa-antimatter selftest         # 3-verb sentinel sweep + n=6 algebra check
```

## Verify

Single-command bookkeeping closure sweep (sister-substrate pattern — hexa-rtsc / hexa-cern / hexa-chip):

```sh
hexa run verify/run_all.hexa     # exit 0 = all 38 green-core subscripts PASS
                                 # → __HEXA_ANTIMATTER_RUN_ALL__ PASS — 38/38 green
```

Inventory (38 green-core subscripts):

| tier | count | scripts |
|:-----|:-----:|:--------|
| T1 algebraic            |  5 | `n6_arithmetic` + 4 `calc_{factory,tabletop,pet_cyclotron,break_even}` |
| T2 numerical            | 18 | 4 `numerics_<pillar>` + 4 `_parity` + 4 `_solver` + 4 Stage-1 specials + `cross_pillar` + `lattice_arithmetic` |
| T3 archival empirical   |  4 | `empirical_{pet,tabletop,dirac,break_even}_inspire` (Inspire-HEP fixture-fallback) |
| inventory + cross-doc   |  2 | `cross_doc_audit` + `release_ladder` |
| firmware Phase C sim    |  4 | `firmware/sim/{cyclotron_trigger,penning_rf,atomic_clock_counter,thrust_acquisition}` |
| firmware Phase D lint   |  1 | `firmware_phase_d_lint` |
| meta closure gates      |  3 | `falsifier_check` + `lint_numerics` + `saturation_check` |
| selftest sentinel       |  1 | `selftest/selftest` (3-verb sweep) |

### Honesty

`__HEXA_ANTIMATTER_RUN_ALL__ PASS` means RC=0 from each of the 38 green-core subscripts —
**bookkeeping closure** of the verified-stable core, **NOT antimatter physics settled**.
Anti-matter physics is academically grounded (CERN ALPHA / AEGIS / PUMA actively measure
antihydrogen), but "tabletop antimatter factory" and "n=6 Dirac-mirror lattice" claims
remain **UNPROVEN apparatus-wise**. No PCB, no flashed firmware, no physical antihydrogen
yield from this repo. `RSC_SATURATED__ STOP` + 4/4 F-AM 100% bookkeeping closure
≠ apparatus working.

Per [`LATTICE_POLICY.md`](LATTICE_POLICY.md): lattice tautologies (σ·φ=24) alone are
NOT sufficient verification; numerics_* tier carries the real-limits anchors
(¹⁸F half-life 109.77 min, CPT invariance, Tsiolkovsky rocket equation, etc. —
see [`LIMIT_BREAKTHROUGH.md`](LIMIT_BREAKTHROUGH.md)).

own published invariants; this orchestrator does NOT pin n=6 lattice anchors on external
entities — those checks live in `cross_doc_audit` / `release_ladder` for our own SSOTs only.

## Build & verify

```sh
# legacy 38-step orchestrator (kept for historical compatibility — run_all.hexa is canonical)
hexa run verify/all.hexa                                  # → 38/38 verifiers PASS

# Phase A — abstract BOM (docs)
ls {factory,tabletop,pet_cyclotron}/doc/benchtop_v0_design.md

# Phase B — Stage-1 simulation parity
hexa run verify/numerics_pet_realistic.hexa               # F-AM-1 T2×4
hexa run verify/numerics_tabletop_relativistic.hexa       # F-AM-2 T2×4
hexa run verify/numerics_dirac_precision.hexa             # F-AM-3 T2×4
hexa run verify/numerics_break_even_thrust.hexa           # F-AM-4 T2×4

# Phase C — golden behavioral sim
hexa run firmware/sim/cyclotron_trigger.hexa              # 13/13 PASS
hexa run firmware/sim/penning_rf.hexa                     # 11/11 PASS
hexa run firmware/sim/atomic_clock_counter.hexa           # 11/11 PASS
hexa run firmware/sim/thrust_acquisition.hexa             # 10/10 PASS

# T3 paper-existence (Inspire-HEP API + fixture fallback)
hexa run verify/empirical_pet_inspire.hexa                # F-AM-1 T3
hexa run verify/empirical_tabletop_inspire.hexa           # F-AM-2 T3
hexa run verify/empirical_dirac_inspire.hexa              # F-AM-3 T3
hexa run verify/empirical_break_even_inspire.hexa         # F-AM-4 T3
HEXA_ANTIMATTER_OFFLINE=1 hexa run verify/empirical_*_inspire.hexa  # offline (fixture only)

# meta — closure tracker + lint + saturation
hexa run verify/falsifier_check.hexa                      # 4/4 F-AM at 100%
hexa run verify/lint_numerics.hexa                        # 18 numerics conform
hexa run verify/firmware_phase_d_lint.hexa                # Phase D paper-spec drift
hexa run verify/saturation_check.hexa                     # → __RSC_SATURATED__ STOP

# CLI dispatch (30+ sub-targets)
hexa run cli/hexa-antimatter.hexa status
hexa run cli/hexa-antimatter.hexa verify [target]         # target = all|n6|docs|...|empirical-pet|firmware-thrust|saturation
hexa run cli/hexa-antimatter.hexa compute n6
hexa run cli/hexa-antimatter.hexa selftest

# regression: 7 .hexa test harnesses
for t in tests/test_*.hexa; do hexa run "$t"; done        # → 7/7 PASS
```

### Closure progress — 2026-05-08

| F-AM | Pillar | T1 (algebra) | T2 (numerical, ×4) | T3 (paper proxy) | Closure |
|:-----|:-------|:------------:|:-------------------|:----------------:|:-------:|
| F-AM-1 | PET ¹⁸F regen | calc_pet_cyclotron | numerics ×4 (basic + parity + solver + realistic) | empirical_pet_inspire | **100%** |
| F-AM-2 | tabletop σ·J₂=288 | calc_tabletop | numerics ×4 (basic + parity + 2-DOF + relativistic) | empirical_tabletop_inspire | **100%** |
| F-AM-3 | Dirac mirror | calc_factory | numerics ×4 (basic + parity + Verlet + precision) | empirical_dirac_inspire | **100%** |
| F-AM-4 | Stage-3 break-even | calc_break_even | numerics ×4 (basic + parity + Tsiolkovsky + thrust) | empirical_break_even_inspire | **100%** |

Re-run after any SSOT edit. Verifiers exit non-zero on drift. RSC saturation_check passes only when all 4 falsifiers carry T1+T2≥3+T3≥1 simultaneously.

## Repo layout

```
hexa-antimatter/
├── README.md / CHANGELOG.md / LICENSE / hexa.toml      ← project meta
├── AGENTS.tape                                          ← identity + governance (.tape v1.2)
├── .roadmap.hexa_antimatter                             ← §A.1–§A.6.1 (release + falsifiers + hardware path)
│
├── factory/        ← F-AM-3 (Dirac mirror n=6)
│   ├── antimatter-factory.md              (declarative SSOT)
│   ├── factory.hexa                       (n=6 derived numbers)
│   └── doc/benchtop_v0_design.md          (Phase A: $4.2M CPT bench BOM)
├── tabletop/       ← F-AM-2 (σ·J₂=288 density)
│   ├── tabletop-antimatter.md
│   ├── tabletop.hexa
│   └── doc/benchtop_v0_design.md          (Phase A: $3.5M Penning trap BOM)
├── pet_cyclotron/  ← F-AM-1 (¹⁸F β⁺ regen)
│   ├── pet-cyclotron.md
│   ├── pet_cyclotron.hexa
│   └── doc/benchtop_v0_design.md          (Phase A: ~$1.3M cyclotron BOM)
│
├── cli/hexa-antimatter.hexa               ← 3-verb router + 30+ verify sub-targets
│
├── verify/                                ← 25 .hexa scripts (T1+T2+T3+meta)
│   ├── n6_arithmetic.hexa                 ← σ·φ = n·τ = J₂ = 24 algebraic
│   ├── cross_doc_audit.hexa               ← SSOT lattice alignment
│   ├── release_ladder.hexa                ← v1.0 → v2.0 cadence
│   ├── calc_{factory,tabletop,pet_cyclotron,break_even}.hexa  ← T1 algebra ×4
│   ├── numerics_{...}.hexa                ← T2 numerical ×14 (basic + parity + solver + Stage-1 sim parity)
│   ├── empirical_*_inspire.hexa           ← T3 paper-feed proxy ×4 (Inspire-HEP)
│   ├── falsifier_check.hexa               ← 4/4 F-AM closure tracker
│   ├── lint_numerics.hexa                 ← 5-invariant grep-lint
│   ├── firmware_phase_d_lint.hexa         ← Phase D paper-spec drift catcher
│   ├── saturation_check.hexa              ← RSC self-stop signal (sat-1+sat-2+sat-3)
│   ├── all.hexa                           ← 38-step aggregator
│   └── fixtures/                          ← 16 cached Inspire-HEP JSON
│
├── firmware/                              ← Phase C / C.5 / D scaffolding
│   ├── doc/README.md                       (Phase C/C.5/D file-layout map)
│   ├── doc/board_v0_*.md            ×4    (Phase C.5: pinout + catalog SKUs + bring-up)
│   ├── doc/schematic_v0_*.md        ×4    (Phase C.5: block schematic + net list)
│   ├── sim/*.hexa                   ×4    (Phase C: golden behavioral sim)
│   ├── hdl/{*.v, *.xdc, build.tcl}        (Phase D: Vivado-synthesizable Verilog)
│   └── mcu/{*.rs, Cargo.toml, lib.rs}     (Phase D: Rust no_std skeletons)
│
├── selftest/selftest.hexa                 ← 3-verb sentinel sweep
└── tests/test_*.hexa (7)                  ← regression harness
```

## Cross-link

- **`dancinlab/hexa-cern`** — accelerator cousin (compact-accelerator substrate)
- **`dancinlab/hexa-ufo`** — Stage-3 propulsion fuel dependency (UFO substrate sources its antimatter fuel from this repo)
- Sister substrate: [`dancinlab/hexa-bio`](https://github.com/dancinlab/hexa-bio) (molecular toolkit, HEXA family)
- Upstream concept SSOTs (declarative):
  - `canon/domains/physics/antimatter-factory/antimatter-factory.md`
  - `canon/domains/physics/tabletop-antimatter/tabletop-antimatter.md`
  - `canon/domains/physics/pet-cyclotron/pet-cyclotron.md`
- Provenance commit: `canon` SHA `c0f1f570`

## License

[MIT](LICENSE) — permissive. See [LICENSE](LICENSE).
