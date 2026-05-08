# `firmware/hdl/` — Phase D Verilog skeletons

> §A.6.1 Phase D scope.  Synthesizable HDL skeletons for the 4 Stage-1
> benchtop FPGAs (Xilinx UltraScale+ family).  **Compiles** with Vivado
> 2024.1+ but **not flashable** until physical boards arrive.

**Status**: skeleton (2026-05-08) · **Toolchain**: Vivado Design Edition 2024.1 · **Boards**: ✗ (Phase D awaits funding)

---

## §1 Module inventory

| File | Target board | FPGA | Sim source |
|:-----|:-------------|:-----|:-----------|
| `cyclotron_trigger.v` | board_v0_pet_cyclotron | (n/a — STM32, see `firmware/mcu/`) | sim/cyclotron_trigger.hexa |
| `penning_rf.v` | board_v0_tabletop_penning | XCZU9EG | sim/penning_rf.hexa |
| `atomic_clock.v` | board_v0_atomic_clock | XCKU040 | sim/atomic_clock_counter.hexa |
| `thrust_acq.v` | board_v0_thrust_acquisition | XCVU13P | sim/thrust_acquisition.hexa |

(`cyclotron_trigger` is MCU-only — STM32H7 controller, no FPGA.  See
`firmware/mcu/pet_cyclotron.rs` for that board's logic.)

## §2 Build (Vivado)

```bash
cd firmware/hdl
vivado -mode batch -source build.tcl
```

`build.tcl` per-target sets:
- target FPGA part
- timing constraints (.xdc)
- IP catalog (clock wizards, MIG, JESD204C, PCIe)
- synthesis + implementation + bitstream

## §3 Out of scope (this skeleton)

- Vivado IP customizations (DDR controller params, JESD204C SerDes
  config) — needs board-specific `.xdc` constraints
- Timing closure for highest-speed paths (32 Gbps GTYE4) — only viable
  with real-board signal integrity data
- Bitstream encryption / DPA countermeasures
- ChipScope / ILA debug instances
- Hardware test benches (board-required)

## §4 Verification

Each module has a Verilator testbench under `tb/` (skeleton, not yet
runnable in repo because Verilator setup is per-host):

```
firmware/hdl/
├─ README.md             (this file)
├─ cyclotron_trigger.v   (pure-Verilog spec; STM32-target board)
├─ penning_rf.v          (UltraScale+ MPSoC PL skeleton)
├─ atomic_clock.v        (Kintex UltraScale skeleton)
├─ thrust_acq.v          (Virtex UltraScale+ skeleton)
└─ build.tcl             (Vivado entry — placeholder)
```

## §5 Cross-link

- `firmware/sim/*.hexa` — golden behavioral sim (PASS criterion)
- `firmware/doc/board_v0_*.md` — pinout + constraints source
- `firmware/mcu/*.rs` — MCU companion code (PS-side on MPSoC)
- `.roadmap §A.6 step 4` — actual board build
