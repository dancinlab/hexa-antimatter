# `firmware/` — Phase C sim-firmware (HEXA-FIRMWARE-01)

> §A.6.1 Phase C scope.  Sim-only firmware models for the 4 pillar
> Stage-1 benchtops (HEXA-PET-01 / HEXA-TABLETOP-01 / HEXA-FACTORY-01
> CPT bench / HEXA-PROPULSION-01 thrust bench).

**Status**: paper firmware (2026-05-08) · **HW-in-the-loop**: ✗ (no boards) · **Compiles + tests**: ✓ via `hexa run`

---

## §1 Scope

Each `firmware/sim/*.hexa` models the controller logic of one benchtop:
trigger sequencer, DAC/ADC pipeline, safety interlock, telemetry log.
Pure-software sim — no FPGA bitstream, no MCU flash image, no real
hardware bus.  Hardware-in-the-loop integration deferred to Phase D
(post-§A.6 step 2 funding).

## §2 Inventory (Phase C target)

| Pillar | Sim file | Models | F-AM target |
|:-------|:---------|:-------|:-----------:|
| pet_cyclotron | `firmware/sim/cyclotron_trigger.hexa` | RF burst gate + target shutter + NaI counter | F-AM-1 |
| tabletop | `firmware/sim/penning_rf.hexa` | RF DAC drive + ADC density + cryogenic interlock | F-AM-2 |
| factory CPT | `firmware/sim/atomic_clock_counter.hexa` | Cs ref counter + Penning ω_c PLL + 1S-2S laser lock | F-AM-3 |
| propulsion | `firmware/sim/thrust_acquisition.hexa` | p̄ release pulse + Watt-balance ADC + BGO trigger | F-AM-4 |

## §3 Pattern

Each sim follows hexa-antimatter convention:
- `use "self/runtime/math_pure"`
- `let mut RUN = 0` / `let mut FAIL = 0` counters
- `__HEXA_ANTIMATTER_FIRMWARE_<NAME>__ PASS` sentinel
- `FALSIFIERS` list (firmware-class retract conditions)
- `exit(0)` on PASS

The simulator runs the controller's state machine in-process and
asserts:
1. Timing invariants (e.g., RF burst gate precedes target shutter open)
2. ADC-loop stability (no over/under-flow in nominal envelope)
3. Safety interlock fires within budget (e.g., < 10 ms abort path)
4. Telemetry log integrity (no dropped frames at nominal rate)
5. n=6 anchor preserved through DAC scaling (σ·τ = 48 normalized)

## §4 Phase D readiness

When boards arrive (post-§A.6 step 2):
- Cyclotron trigger → STM32H7 firmware (Cortex-M7, 480 MHz)
- Penning RF → Xilinx UltraScale+ FPGA + AD9162/AD9208
- Atomic clock counter → UltraScale+ + dedicated TDC
- Thrust acquisition → UltraScale+ + 16× ADC + NIM/CAMAC trigger

Sim files are the **specification source** for those firmware images.

## §5 Out of scope

- HDL synthesis (Verilog → bitstream) — Phase D
- MCU cross-compilation (Rust embedded / C bare-metal) — Phase D
- Hardware-in-the-loop with real boards — Phase D + funding
- Real-time scheduling guarantees — Phase D + RTOS layer

## §6 Cross-link

- `verify/numerics_*_{realistic,relativistic,precision,thrust}.hexa` — Phase B sim parity
- `{factory,tabletop,pet_cyclotron}/doc/benchtop_v0_design.md` — Phase A BOM + interfaces
- `.roadmap.hexa_antimatter §A.6 + §A.6.1` — overall hardware path
