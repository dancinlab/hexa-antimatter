# Changelog

All notable changes to `hexa-antimatter` will be documented in this file.

The format is based on [Keep a Changelog](https://keepachangelog.com/en/1.1.0/),
and this project adheres to [Semantic Versioning](https://semver.org/spec/v2.0.0.html).

---

## [Unreleased]

### Added (2026-05-07 — RSC iteration 2)

- `verify/calc_tabletop.hexa` — T1 (algebraic) closure for F-AM-2
  (tabletop p̄ density σ·J₂=288 fit vs CERN AEgIS / ALPHA / GBAR).
  41/41 PASS: σ·J₂=288 + σ³=1728 production cascade + σ²=144
  anti-H synth + σ·τ²=192 mo storage + σ⁶=2,985,984 cost reduction
  + tabletop design parameters (B=σ·τ=48 T, R=σ-φ=10 cm,
  Γ_loss=1/(σ²·τ)=1/576, vacuum φ²·τ+2 = 18 → 10⁻¹⁸ Torr,
  PET ¹⁸F σ·τ=48 mg/day) + compact-ring momentum 0.3·B·R = 1.44 GeV/c +
  η_trap τ/σ = 1/3 ratio + 14-line spec-anchor sweep against
  `tabletop/tabletop-antimatter.md`. Sentinel
  `__HEXA_ANTIMATTER_CALC_TABLETOP__ PASS` + 10-row FALSIFIERS
  registry tied to F-AM-2 / F-AM-4.
- `verify/all.hexa` — orchestrator sweeps **6 steps** (5/5 → 6/6
  verifiers PASS).
- `cli/hexa-antimatter.hexa` — `verify calc-tabletop` sub-target,
  status / help / JSON updated.
- `tests/test_calculators.hexa` — calc_tabletop row added (2/2 PASS).

### Added (2026-05-07 — RSC iteration 1)

- `verify/calc_factory.hexa` — T1 (algebraic) closure for F-AM-3
  (Dirac-mirror symmetry 6-fold closed-form). 39/39 PASS:
  divisor-arithmetic re-derivation of σ(6)=12, τ(6)=4, φ(6)=2,
  sopfr(6)=5, J₂=24 + factory-pillar ledger (B=σ·τ=48 T,
  σ²=144, σ-φ=10, σ³=1728, σ·J₂=288, σ²·τ=576) + 12-line
  spec-anchor sweep against `factory/antimatter-factory.md`.
  Sentinel `__HEXA_ANTIMATTER_CALC_FACTORY__ PASS` + 8-row
  `FALSIFIERS` registry tied to F-AM-1 / F-AM-3.
- `verify/all.hexa` — orchestrator now sweeps **5 steps**
  (n6 + cross-doc + ladder + **calc_factory** + selftest);
  emits `5/5 verifiers PASS` on green.
- `cli/hexa-antimatter.hexa` — `verify calc-factory` sub-target,
  status / help tables updated, JSON tail lists `calc_factory`.
- `tests/test_calculators.hexa` — new harness for `calc_*` /
  `numerics_*` sentinels; row-driven, one line per script.
- `hexa.toml [test]` — registers all 7 `tests/test_*.hexa`
  files (selftest + n6 + docs + ladder + modules + verify_all
  + calculators), so `hx test` runs the full sweep.

### Changed
- `tests/test_verify_all.hexa` — expected aggregate count
  bumped `4/4 → 5/5 → 6/6` to match orchestrator surface.

### Closure progress (RSC recipe §3) — after iter 2
- F-AM-2 (tabletop σ·J₂=288):     T1 ✓ (calc_tabletop) · T2 ✗ · T3 ✗ → **33%**.
- F-AM-3 (Dirac mirror n=6):       T1 ✓ (calc_factory)  · T2 ✗ · T3 ✗ → **33%**.
- F-AM-1 (PET ¹⁸F regen):          T1 partial (BT-401 σ·τ=48 T cited) · T2 ✗ · T3 ✗.
- F-AM-4 (Stage-3 break-even):     T1 partial (1.7e12 p̄/s closure cited) · T2 ✗ · T3 ✗.

---

## [1.0.0] — 2026-05-06

### Added
- Initial extraction from `n6-architecture/domains/physics/` (SHA `c0f1f570`).
- 3-verb antimatter substrate scaffold:
  - `factory/`        ← `n6-architecture/domains/physics/antimatter-factory/`
  - `tabletop/`       ← `n6-architecture/domains/physics/tabletop-antimatter/`
  - `pet_cyclotron/`  ← `n6-architecture/domains/physics/pet-cyclotron/`
- Placeholder CLI router `cli/hexa-antimatter.hexa` (3 verb sentinels + status + selftest).
- `hexa.toml` package manifest (license: MIT, n=6 Dirac-mirror lattice scope).
- `install.hexa` hx hook (no python deps; selftest sentinel check, warn-only).
- `tests/test_selftest.hexa` placeholder selftest.
- README with §Why / §Verbs / §Status / §Install / §Cross-link / §License.
- Cross-link to sister substrates: `hexa-cern` (accelerator cousin), `hexa-ufo`
  (Stage-3 propulsion fuel dependency), `hexa-bio` (molecular toolkit, HEXA family).

### Honest scope (raw#10 C3)
- 0/3 verbs empirically wired — all 3 ship as **spec stubs** with declarative
  `.md` SSOT only. Working `.hexa` CLI is **TBD**.
- n=6 Dirac-mirror lattice (σ=12, τ=4, φ=2, J₂=24) is an algebraic conjecture
  — NOT empirically verified for any axis at v1.0.0.
- All headline numbers are academia-unproven candidates from the declarative
  `.md` SSOT (factory 1e12 p-bar/hr; tabletop 1.7e12 p-bar/s; PET 48 T / 48 mg).

[1.0.0]: https://github.com/need-singularity/hexa-antimatter/releases/tag/v1.0.0
