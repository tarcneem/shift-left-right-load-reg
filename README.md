# 8-bit Shift Register with Load (Verilog)

An 8‑bit register that can **load**, **shift left**, or **shift right** with zero‑fill.
Includes a simple testbench that drives control signals on **posedge clk** (as written).

## Module
`shift_left_right_load_reg.v`

**Controls**
- `reset_n` (active‑low): clears `q` to `8'b0`
- `load_enable = 0`: load `i` into `q` on the next `posedge clk`
- `load_enable = 1`:
  - `shift_left_right = 0`: shift left (`q <= {q[6:0], 1'b0}`)
  - `shift_left_right = 1`: shift right (`q <= {1'b0, q[7:1]}`)

## Testbench
`tb_shift_left_right_reg.v`

- Clock: `1 MHz` (`timescale 1us/1ns`, toggle every `#0.5`)
- Drives `i`, `load_enable`, and `shift_left_right` on **`@(posedge clk)`**  
  (This is intentional here; it may cause **one extra shift** compared to “exact N shifts,” because the DUT samples at the same edge.)


## How to run

### EDA Playground
1. Create a new Verilog playground.
2. Paste `shift_left_right_load_reg.v` and `tb_shift_left_right_reg.v`.
3. Select Synopsys VCS 2023.03 and run (EPWave to view waves).

