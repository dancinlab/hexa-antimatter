# TAPE-AUDIT — hexa-antimatter

## A. Audit-class ledgers

- `state/markers/*.marker` — **1105 markers** (`_math_pure_smoke_*`, `all_*` repeated cycle markers). `_FAILED.marker` grade encoding heavy. **Class-T** fit — collapse `all_*` cycle markers to `state/cycles.tape`.
- No CLI log file (uncommon — most siblings have one).
- No JSONL ledger.

## B. Identity surface

`AGENTS.md` + `ARCHITECTURE.md` + `LATTICE_POLICY.md` + `LIMIT_BREAKTHROUGH.md` + `SECURITY.md` + `FAQ.md` + `CONTRIBUTING.md` — most paperwork-rich of the batch. Identity = positron source + PET-cyclotron stack. Fit for `hexa-antimatter/identity.tape` with `@I` instrument declarations.

## C. Domain.md files

Only 12 root MD files. Subdir-driven structure: `pet_cyclotron/`, `factory/`, `tabletop/`, `firmware/`, `selftest/`. No `+`-meta-domains.

## D. Per-run/per-event history

`all_*` cycle markers + `_math_pure_smoke_*` math-purity smoke tests. Two distinct event streams that should split: `state/cycles.tape` (production-cycle runs) + `state/math_purity.tape` (deterministic math invariants). Per `.tape` spec, math-purity is **Class-T with `=>` ok** + identity-preserving — high signal-to-noise.

## E. Promotion candidates

- **n6 atoms** — positron creation cross-section + cyclotron resonance frequency (n=6 candidate when axis-closed).
- **hxc binaries** — PET scan reconstructions, positron-emission spectra.
- **n12 cube cells** — particle-source × moderation × storage × scale.

## Verdict

**MEDIUM** — 1105 markers split across two clean event streams (cycles + math-smoke), paperwork-heavy. No imported-canon yet (no `IMPORTED_FROM_CANON.md`) — atom-promotion pipeline less developed than hexa-cern.
