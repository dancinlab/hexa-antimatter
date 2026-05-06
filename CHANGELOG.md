# Changelog

All notable changes to `hexa-antimatter` will be documented in this file.

The format is based on [Keep a Changelog](https://keepachangelog.com/en/1.1.0/),
and this project adheres to [Semantic Versioning](https://semver.org/spec/v2.0.0.html).

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
- Cross-link to sister substrates: `petite-cern` (accelerator cousin), `hexa-ufo`
  (Stage-3 propulsion fuel dependency), `hexa-bio` (molecular toolkit, HEXA family).

### Honest scope (raw#10 C3)
- 0/3 verbs empirically wired — all 3 ship as **spec stubs** with declarative
  `.md` SSOT only. Working `.hexa` CLI is **TBD**.
- n=6 Dirac-mirror lattice (σ=12, τ=4, φ=2, J₂=24) is an algebraic conjecture
  — NOT empirically verified for any axis at v1.0.0.
- All headline numbers are academia-unproven candidates from the declarative
  `.md` SSOT (factory 1e12 p-bar/hr; tabletop 1.7e12 p-bar/s; PET 48 T / 48 mg).

[1.0.0]: https://github.com/need-singularity/hexa-antimatter/releases/tag/v1.0.0
