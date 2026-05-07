# Changelog

All notable changes to `hexa-antimatter` will be documented in this file.

The format is based on [Keep a Changelog](https://keepachangelog.com/en/1.1.0/),
and this project adheres to [Semantic Versioning](https://semver.org/spec/v2.0.0.html).

---

## [Unreleased]

### Added (2026-05-08 — RSC iteration 16) numerics meta-lint

- `verify/lint_numerics.hexa` — meta-lint over all 11 numerics_*.hexa
  scripts.  56/56 PASS.  Enforces recipe §4 invariants per script:
  · `use "self/runtime/math_pure"` import
  · `__HEXA_ANTIMATTER_<NAME>__ PASS` sentinel
  · `FALSIFIERS` list declaration
  · `exit(0)` on PASS path
  · `let mut RUN = 0` + `let mut FAIL = 0` counters
  Plus inventory completeness: NUMERICS_SCRIPTS list count == on-disk
  glob count (catches stale meta-lint when new numerics_*.hexa lands).
  Sentinel `__HEXA_ANTIMATTER_LINT_NUMERICS__ PASS` + 6 FALSIFIERS.
- `verify/all.hexa` — 19 → 20 steps (20/20 PASS).
- `cli/hexa-antimatter.hexa` — `verify lint-numerics` sub-target.
- `tests/test_calculators.hexa` — lint_numerics row added (16 rows).
- `tests/test_verify_all.hexa` — expected 19/19 → 20/20.

### Added (2026-05-08 — RSC iteration 15) falsifier closure tracker

- `verify/falsifier_check.hexa` — preregistered F-AM-1/2/3/4 checklist +
  3-tier closure-progress tracker.  16/16 PASS.  Asserts:
  · 4/4 falsifiers registered in .roadmap.hexa_antimatter §A.4
  · F-AM-1/2/3 each have T1 (calc_*) + T2 ×3 (numerics + parity + solver)
    on disk → 67% sat-1 closure
  · F-AM-4 (Stage-3 break-even) — partial T1, T2 pending (next chunk)
  · T3 always ✗ until Stage-1+ hardware (per recipe §3 / §9)
  Sentinel `__HEXA_ANTIMATTER_FALSIFIER__ PASS` + 6 FALSIFIERS.
- `verify/all.hexa` — 18 → 19 steps (19/19 PASS).
- `cli/hexa-antimatter.hexa` — `verify falsifier` sub-target.
- `tests/test_calculators.hexa` — falsifier_check row added (15 rows).
- `tests/test_verify_all.hexa` — expected 18/18 → 19/19.

### Added (2026-05-08 — RSC iteration 14) math_pure stability floor

- `verify/numerics_lattice_arithmetic.hexa` — n=6 lattice float ↔ int
  precision cross-check.  15/15 PASS.  Re-derives every n=6 anchor
  through math_pure (sqrt/pow/log/log10/exp) and asserts rel_err < 1e-9
  against the integer ledger from `verify/n6_arithmetic.hexa`:
  · sqrt_pure(σ²) = σ · pow_pure(σ, 2/3/6) = 144/1728/2,985,984
  · log10_pure(10⁷) = 7 · log10(σ²) = 2·log10(σ)  homomorphism
  · exp_pure(log_pure(σ)) = σ  roundtrip
  · sqrt(σ³) = σ^(3/2)  cross-consistency
  · float n=6 closure σ·φ = n·τ = J₂ = 24
  · float ↔ int parity round(σ²) = 144 / round(σ³) = 1728
  · σ·J₂ = 288 cross-pillar 288 anchor in float
  · math_pure floor identities (log_pure(e)=1, exp_pure(0)=1, pow(σ,0)=1)
  Sentinel `__HEXA_ANTIMATTER_NUMERICS_LATTICE_ARITHMETIC__ PASS` + 10 FALSIFIERS.
- `verify/all.hexa` — 17 → 18 steps (18/18 PASS).
- `cli/hexa-antimatter.hexa` — `verify numerics-lattice-arithmetic` sub-target.
- `tests/test_calculators.hexa` — lattice_arithmetic row added (14 rows).
- `tests/test_verify_all.hexa` — expected 17/17 → 18/18.

### Added (2026-05-08 — RSC iteration 13) cross-pillar cross-cutter

- `verify/numerics_cross_pillar.hexa` — cross-cutter T2 across F-AM-1/2/3/4.
  31/31 PASS.  Asserts the 3 pillar numerics_*.hexa scripts share the same
  n=6 lattice (σ=12, τ=4, φ=2, n=6, J₂=24) and re-derive shared σ-tower
  numbers via independent paths:
  · master identity σ·φ = n·τ = J₂ = 24 (3 paths)
  · σ² = 144 = J₂·n (3 paths)
  · σ·τ = 48 across factory/tabletop/pet
  · σ³ = 1728 via pow_pure AND σ²·σ (path-independence)
  · σ⁶ = (σ³)² = 2,985,984 (factory cost ↔ tabletop production closure)
  · σ·τ·n = σ·J₂ = 288 (cross-pillar 288 anchor)
  · cost cascade $6.25e10 / σ³ → $3.617e7 → $2.094e4
  · production cascade σ³·10⁹ ≈ 1.7e12 p̄/s
  · Carnot bound η ∈ [0,1] per pillar
  · math_pure floor: log/exp/pow inverse identities
  Sentinel `__HEXA_ANTIMATTER_NUMERICS_CROSS_PILLAR__ PASS` + 15-row FALSIFIERS.
- `verify/all.hexa` — 16 → 17 steps (17/17 PASS).
- `cli/hexa-antimatter.hexa` — `verify numerics-cross-pillar` sub-target.
- `tests/test_calculators.hexa` — cross-pillar row added (13 rows).
- `tests/test_verify_all.hexa` — expected 16/16 → 17/17.

### Added (2026-05-08 — RSC iteration 11) 🎯 sat-1 2nd-falsifier milestone

- `verify/numerics_tabletop_solver.hexa` — F-AM-2 **T2 ×3** (sat-1 2nd
  falsifier).  9/9 PASS.  2-DOF Penning-trap symplectic Verlet:
  · axial mode ω_z = 1 (T_z = 2π) — drift < 1e-4
  · cyclotron mode ω_+ = τ = 4 (T_+ = π/2) — drift < 5e-4
    (∝ ω²·Δt² floor; faster mode → 16× larger drift)
  · ω_+/ω_z = τ = 4 (n=6 lattice trap-mode ratio)
  · 2-DOF total energy E_z + E_+ drift < 2e-4 over T_z
  · both modes close after one axial period (cyclotron does 4 cycles)
  Sentinel `__HEXA_ANTIMATTER_NUMERICS_TABLETOP_SOLVER__ PASS` + 8-row FALSIFIERS.
- `verify/all.hexa` — orchestrator `run_step` now injects
  `HEXA_SHIM_NO_DARWIN_LANDING=1 RESOURCE_LOCAL_HEXA=1` env so child
  `hexa run` calls work on Mac bare host.  Sweep grows 14→15 (15/15).
- `cli/hexa-antimatter.hexa` — `verify numerics-tabletop-solver` sub-target.
- `tests/test_calculators.hexa` — solver row added (11/11 PASS).
- `tests/test_verify_all.hexa` — expected 14/14 → 15/15.

### Added (2026-05-08 — RSC iteration 10) 🎯 sat-1 first-falsifier milestone

- `verify/numerics_factory_solver.hexa` — F-AM-3 **T2 ×3** (sat-1 condition
  for first falsifier).  10/10 PASS.  velocity-Verlet leapfrog symplectic
  integrator on 1-DOF Penning-trap-like harmonic oscillator H = ½(p² + ω²q²)
  over τ=4 phase quadrants (capture · cool · store · extract):
  · 1024 leapfrog steps per period (256 per quadrant)
  · per-quadrant energy drift < 5×10⁻⁵ (Verlet O(Δt²) floor)
  · full-period total drift < 1×10⁻⁴
  · closed-orbit q/p return |Δq| ≤ 1e-3 (measured 4.86e-11)
  · phase-space volume preservation (Liouville |J| ≈ 1 ± 0.1%)
  · math_pure π and pow stability floor.
  Sentinel `__HEXA_ANTIMATTER_NUMERICS_FACTORY_SOLVER__ PASS`.  Pattern lifted
  from hexa-cern/verify/numerics_classical.hexa, antimatter-Penning-flavored.
- `verify/all.hexa` — 13 → 14 steps (14/14).
- `cli/hexa-antimatter.hexa` — `verify numerics-factory-solver` sub-target.
- `tests/test_calculators.hexa` — solver row added (10/10 PASS).
- `tests/test_verify_all.hexa` — expected 13/13 → 14/14.

### Added (2026-05-08 — RSC iteration 9)

- `verify/numerics_pet_cyclotron_parity.hexa` — F-AM-1 **T2 ×2**
  (PET pillar 2nd T2 stack, recipe §7.4 row 5 last).  14/14 PASS.
  4-machine medical-PET reference parity:
  · Varian/IBA R 0.5–1.5 m vs HEXA σ-φ = 0.10 m  (ratio 5..15 within σ-τ=8)
  · Medical PET B 2 T vs HEXA σ·τ = 48 T  (ratio = J₂ = 24× exact)
  · ¹⁸F-FDG cost $4M/season vs HEXA $4M/σ³ ≈ $2,315/season
  · Medical vacuum 10⁻³ Torr vs HEXA 10⁻³/(σ²·τ) ≈ 1.74×10⁻⁶ Torr
  · Clinical H̄ ~ 0 /s vs HEXA σ²·10⁶ = 1.44×10⁸ /s (∞ ratio floor)
  Plus n=6 factor consistency.  Sentinel
  `__HEXA_ANTIMATTER_NUMERICS_PET_CYCLOTRON_PARITY__ PASS` + 9-row FALSIFIERS.
- `verify/all.hexa` — 12 → 13 steps (13/13).
- `cli/hexa-antimatter.hexa` — `verify numerics-pet-cyclotron-parity` sub-target.
- `tests/test_calculators.hexa` — 9th row (9/9 PASS).
- `tests/test_verify_all.hexa` — expected 12/12 → 13/13.

### Added (2026-05-08 — RSC iteration 8)

- `verify/numerics_tabletop_parity.hexa` — F-AM-2 **T2 ×2**
  (tabletop pillar 2nd T2 stack, recipe §7.4 row 5).  19/19 PASS.
  4-machine published-reference parity table:
  · CERN AD vol 200 m³ ÷ (σ²·σ·τ/(σ-φ)) = 0.2894 m³  (ratio 691×, SSOT 0.29 m³ within 5%)
  · CERN AD prod 3×10⁷ p̄/s × σ³·10⁹/3e7 = 1.728×10¹² p̄/s  (within 2% of cited 1.7e12)
  · ALPHA H̄ × σ²·10⁵ = 1.44×10⁸ H̄/s
  · NASA-99 $6.25×10¹³/g ÷ σ⁶ = $2.093×10⁷/g (= $2.093×10⁴/mg)
    matches SSOT $2.1e4/mg within 1%
  · ELENA hold × σ·τ² months = 4.977×10⁸ s (≥4000× cryo-free extension)
  Plus n=6 factor consistency (σ⁶ = σ³·σ³, vol-reduction factor 691.2)
  and math_pure stability floor.  Sentinel
  `__HEXA_ANTIMATTER_NUMERICS_TABLETOP_PARITY__ PASS` + 10-row FALSIFIERS.
- `verify/all.hexa` — orchestrator sweeps **12 steps** (11/11 → 12/12).
- `cli/hexa-antimatter.hexa` — `verify numerics-tabletop-parity` sub-target.
- `tests/test_calculators.hexa` — parity row added (8/8 PASS).
- `tests/test_verify_all.hexa` — expected 11/11 → 12/12.

### Added (2026-05-07 — RSC iteration 7)

- `verify/numerics_factory_parity.hexa` — F-AM-3 **T2 ×2**
  (factory pillar 2nd T2 stack, recipe §7.4 row 5).  14/14 PASS.
  4-machine published-reference parity table:
  · CERN AD baseline 3×10⁷ p̄/s × σ² = 4.32×10⁹ p̄/s
    (matches factory SSOT §8.1 verbatim)
  · CERN ELENA hold 10⁵ s × σ·τ months = 1.244×10⁸ s
    (HEXA / ELENA ratio ≈ 1244, SSOT cites "~1,400×" — within 50% rel)
  · CERN ALPHA H̄ rate × σ²·10⁶ = 1.44×10⁸ /s (5-order-of-magnitude lift)
  · NASA-99 cost $6.25×10¹³/g ÷ σ³ = $3.617×10¹⁰/g
  Plus n=6 factor consistency (σ²·σ = σ³, time-unit conversion
  σ·τ months = 1.24416×10⁸ s) and math_pure stability floor.
  Decade-band parity tolerance ±50% (½-decade) following hexa-cern
  parity-script convention.  Sentinel
  `__HEXA_ANTIMATTER_NUMERICS_FACTORY_PARITY__ PASS` + 9-row FALSIFIERS.
- `verify/all.hexa` — orchestrator sweeps **11 steps** (10/10 → 11/11).
- `cli/hexa-antimatter.hexa` — `verify numerics-factory-parity` sub-target.
- `tests/test_calculators.hexa` — parity row added (7/7 PASS).
- `tests/test_verify_all.hexa` — expected 10/10 → 11/11.

### Added (2026-05-07 — RSC iteration 6)

- `verify/numerics_pet_cyclotron.hexa` — T2 (numerical) closure for F-AM-1.
  16/16 PASS. PET-pillar float-only chains:
  · HEXA-PET-02: σ·τ × 2×10⁹ = 9.6×10¹⁰ e+/s (1ppm rel)
  · HEXA-PET-06: σ² × 10⁶ = 1.44×10⁸ H̄/s (§9.2 c cite)
  · PET cost mid-chain: $_factory/σ³ ≈ $3.617×10⁷/mg (between
    factory $6.25e10/mg and tabletop $2.1e4/mg, σ⁶ = σ³·σ³ split)
  · σ³ path-independence: pow_pure(σ, 3) = σ²·σ = 1728
  · ¹⁸F decay constant λ = ln(2)/109.8 min ≈ 6.312×10⁻³ /min
    via log_pure + half-life inversion (math_pure self-inverse)
  · τ=4 batch retention 2^(-1/τ) ≈ 0.8409 (¹⁸F half-life mitigation)
  · B/B_med ratio σ·τ/2 = J₂ = 24× (RT-SC vs medical PET)
  · vacuum suppression σ²·τ = 576 (vs medical 10⁻³ Torr)
  · log-log σ³ vs σ slope = 3.0 (math_pure power-law floor)
  · math_pure stability floor.
  Sentinel `__HEXA_ANTIMATTER_NUMERICS_PET_CYCLOTRON__ PASS` + 10-row
  FALSIFIERS.
- `verify/all.hexa` — orchestrator sweeps **10 steps** (9/9 → 10/10).
- `cli/hexa-antimatter.hexa` — `verify numerics-pet-cyclotron` sub-target.
- `tests/test_calculators.hexa` — numerics_pet_cyclotron row added (6/6 PASS).
- `tests/test_verify_all.hexa` — expected 9/9 → 10/10.

### Added (2026-05-07 — RSC iteration 5)

- `verify/numerics_tabletop.hexa` — T2 (numerical) closure for F-AM-2.
  18/18 PASS. Independent re-derivation through math_pure of
  tabletop pillar's float-only chains (calc_tabletop covers integer math):
  · σ·J₂ = 288 (BT-401 anchor) via float
  · σ³ × 10⁹ ≈ 1.7×10¹² p̄/s (terminal-goal production within 2% rel)
  · σ⁶ = 2,985,984 + factor-split σ⁶ = σ³·σ³ (factory × PET)
  · σ·τ² = 192 mo, 192/12 = 16 yr exact
  · **Γ_loss = 1/(σ²·τ) × 10⁻³ ≈ 1.736×10⁻⁶ /s** matches SSOT 1.7e-6
  · **V_TT = 200·(σ-φ)/(σ²·σ·τ) ≈ 0.2894 m³** matches SSOT 0.29 m³
  · compact-ring p = 0.3·B·R = 1.44 GeV/c (path-b)
  · cost = $_factory/σ⁶ ≈ $2.093×10⁴/mg matches SSOT $2.1e4/mg (1% rel)
  · log-log σ⁶ vs σ slope = 6.0 (math_pure power-law floor)
  · math_pure stability floor (sqrt, pow, log self-inverse).
  Sentinel `__HEXA_ANTIMATTER_NUMERICS_TABLETOP__ PASS` + 11-row FALSIFIERS.
- `verify/all.hexa` — orchestrator sweeps **9 steps** (8/8 → 9/9).
- `cli/hexa-antimatter.hexa` — `verify numerics-tabletop` sub-target.
- `tests/test_calculators.hexa` — numerics_tabletop row added (5/5 PASS).
- `tests/test_verify_all.hexa` — expected 8/8 → 9/9.

### Added (2026-05-07 — RSC iteration 4)

- `verify/numerics_factory.hexa` — T2 (numerical) closure for F-AM-3
  via `self/runtime/math_pure`. 21/21 PASS. First T2-tier script.
  Independent re-derivation of factory ledger through math_pure
  (sqrt/exp/log/pow) and cumulative-sum loops:
  · pow_pure(12, k) for k ∈ {2,3,4,6} agrees with int σ^k to ≤1e-9
  · σ⁶ = (σ³)² independent-path agreement
  · cumulative-sum σ² and σ·τ agree with pow_pure path
  · master identity σ·φ = n·τ = J₂ in float domain
  · **B⁴ confinement scaling**: log-log linreg slope on
    [10, 20, 30, 40, 48] T returns 4.0 ± 0.05 (TP-7 closure)
  · Carnot η = 1 - T_c/T_h ∈ (0, 1) for T_h=1e8/T_c=300 (TP-6, no
    2nd-law breach)
  · math_pure stability floor: sqrt_pure(144), exp_pure(0),
    log_pure(e), pi_pure, pow_pure(2,10) all within 1e-9.
  Sentinel `__HEXA_ANTIMATTER_NUMERICS_FACTORY__ PASS` + 8-row
  FALSIFIERS (path-divergence, B⁴ slope, Carnot breach, math_pure floor).
- `verify/all.hexa` — orchestrator sweeps **8 steps** (7/7 → 8/8).
- `cli/hexa-antimatter.hexa` — `verify numerics-factory` sub-target.
- `tests/test_calculators.hexa` — numerics_factory row added (4/4 PASS).
- `tests/test_verify_all.hexa` — expected 7/7 → 8/8.

### Added (2026-05-07 — RSC iteration 3)

- `verify/calc_pet_cyclotron.hexa` — T1 (algebraic) closure for F-AM-1
  (PET ¹⁸F regen rate closed-form fit vs hospital cyclotron public spec).
  36/36 PASS: HEXA-PET-01..06 locked-constant re-derivation
  (¹⁸F stock σ·τ=48 mg/season, R=σ-φ=10 cm, B=σ·τ=48 T,
  cost-denom σ³=1728, synth factor σ²=144 → 1.44e8 H̄/s,
  e+ rate σ·τ → 9.6e10 /s) + ancillary chain (τ=4 batch stack,
  σ²·τ=576× vacuum suppression, σ³=1728 daily H̄ cascade,
  B/B_med = σ·τ/φ = J₂ = 24×) + cost-split σ⁶ = σ³·σ³ (factory ×
  PET) + 13-line spec-anchor sweep against `pet_cyclotron/pet-cyclotron.md`.
  Sentinel `__HEXA_ANTIMATTER_CALC_PET_CYCLOTRON__ PASS` + 13-row
  FALSIFIERS registry tied to F-AM-1 + SSOT §7 retract conditions.
- `verify/all.hexa` — orchestrator sweeps **7 steps** (6/6 → 7/7).
- `cli/hexa-antimatter.hexa` — `verify calc-pet-cyclotron` sub-target.
- `tests/test_calculators.hexa` — calc_pet_cyclotron row added (3/3 PASS).
- `tests/test_verify_all.hexa` — expected 6/6 → 7/7.

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
  bumped `4/4 → … → 12/12` to match orchestrator surface.

### Closure progress (RSC recipe §3) — after iter 8
- F-AM-2 (tabletop σ·J₂=288):     T1 ✓ · **T2 ×2** (numerics_tabletop + tabletop_parity) · T3 ✗ → **67%**.
- F-AM-3 (Dirac mirror n=6):       T1 ✓ · **T2 ×2** (numerics_factory + factory_parity)   · T3 ✗ → **67%**.
- F-AM-1 (PET ¹⁸F regen):          T1 ✓ · T2 ×1 · T3 ✗ → **67%**.
- F-AM-4 (Stage-3 break-even):     T1 partial · T2 ✗ · T3 ✗.

2 of 3 pillar falsifiers now have T2 ×2 (closed-form + parity).
Next iter for sat-1: numerics_pet_cyclotron_parity (F-AM-1 → T2×2)
followed by solver scripts to reach T2 ×3.

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
