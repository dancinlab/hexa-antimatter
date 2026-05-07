# Changelog

All notable changes to `hexa-antimatter` will be documented in this file.

The format is based on [Keep a Changelog](https://keepachangelog.com/en/1.1.0/),
and this project adheres to [Semantic Versioning](https://semver.org/spec/v2.0.0.html).

---

## [Unreleased]

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
  bumped `4/4 → 5/5 → 6/6 → 7/7 → 8/8 → 9/9 → 10/10 → 11/11` to match orchestrator.

### Closure progress (RSC recipe §3) — after iter 7 (1st T2-stack thickening)
- F-AM-3 (Dirac mirror n=6):       T1 ✓ · **T2 ×2** (numerics_factory + factory_parity) · T3 ✗ → **67%**.
- F-AM-1 (PET ¹⁸F regen):          T1 ✓ · T2 ×1 · T3 ✗ → **67%**.
- F-AM-2 (tabletop σ·J₂=288):     T1 ✓ · T2 ×1 · T3 ✗ → **67%**.
- F-AM-4 (Stage-3 break-even):     T1 partial · T2 ✗ · T3 ✗.

F-AM-3 now has T2 ×2 (closed-form math_pure + 4-machine ref parity).
Toward sat-1 (T2 ×3 each): need numerics_factory_solver, plus parity
for tabletop and pet_cyclotron.

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
