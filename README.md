# ECE 2372 FPGA Scoreboard & Shot Clock

---

## 🎯 Project Overview
Students will design, simulate, and implement a digital game console that:
- Tracks two team scores using pushbuttons  
- Implements a **24-second shot clock** with start, pause, and reset controls  
- Uses an **FSM controller** to manage system states (RUN, PAUSE, EXPIRED)  
- Displays the timer on **multiplexed seven-segment displays**  
- Activates a **buzzer and LED indicators** when the timer expires  

This capstone emphasizes modular Verilog design, simulation-first workflows, and safe hardware interfacing.

---

### 🔧 System Architecture

The FPGA design integrates debounced inputs, a finite state machine (FSM) controller, counters, and display logic to implement a complete scoreboard and shot clock system.

<p align="center">
  <img src="ECE2372_Scoreboard_BlockDiagram.svg" alt="ECE 2372 Scoreboard Block Diagram" width="750"/>
</p>

If the image does not display properly, you can view or download the diagram as a PDF:  
📄 [**ECE2372_Scoreboard_BlockDiagram.pdf**](ECE2372_Scoreboard_BlockDiagram.pdf)

---

## ⚙️ Hardware Requirements
- **Digilent Cmod A7-35T FPGA board**  
- **Breadboard** and jumper wires  
- **Two-digit seven-segment display** (common anode or common cathode)  
- **Pushbuttons** (≥5)  
- **220 Ω resistors** (for segments and LEDs)  
- **Piezo buzzer** (active preferred)  
- **Optional:** NPN transistor + 1 kΩ base resistor for buzzer drive  

---

## 📁 Repository Contents
| File | Description |
|------|--------------|
| `top_cmod_a7.v` | Top-level module integrating all components |
| `clk_en_div.v` | Parameterized clock-enable divider |
| `debounce_oneshot.v` | Debounce and one-shot pulse generator |
| `shot_fsm.v` | Finite-state machine for run/pause/expired control |
| `shot_counter.v` | Two-digit down counter for shot-clock timing |
| `display_mux2.v` | Two-digit display multiplexer |
| `sevenseg_decoder.v` | BCD-to-seven-segment decoder |
| `buzzer_one_shot.v` | One-shot buzzer pulse generator |
| `cmod_a7_scoreboard.xdc` | Starter constraints (pin mapping template) |
| `ECE2372_Scoreboard_BlockDiagram.svg` | Block diagram (for README embedding) |
| `ECE2372_Scoreboard_BlockDiagram.pdf` | Printable block diagram (PDF format) |

---

## 🧰 Software Requirements
- **Vivado Design Suite** (2020.2 or later)  
- Optional: **ModelSim** or Vivado’s built-in simulator  

---

## 🧩 Getting Started
1. **Clone the repository**
   ```bash
   git clone https://github.com/<your-org>/cmod_a7_scoreboard.git
   ```
2. **Open Vivado**
   - Target device: **Cmod A7-35T (XC7A35T-1CPG236C)**
   - Add all `.v` and `.xdc` files.
3. **Assign pins**
   - Edit `cmod_a7_scoreboard.xdc` to match chosen GPIO pins from the official Cmod A7 master XDC.
4. **Synthesize → Implement → Generate Bitstream**
5. **Program the FPGA** and test each module:
   - Verify display counting, debounced buttons, FSM transitions, and buzzer activation.

---

## 🔌 Wiring Notes
- Each segment pin → **220 Ω resistor → FPGA I/O pin**  
- Common anode/cathode pins → `digit[1:0]` outputs (use transistor drivers if needed)  
- Buttons: active-low with pull-ups to 3.3 V  
- Buzzer: direct drive or via NPN transistor  
- Adjust `ACTIVE_HIGH_SEG` in `top_cmod_a7.v` to match your display type  

---

## 🧪 Suggested Milestones
1. Blink an LED using the clock divider.  
2. Display numbers 0–9 on one seven-segment digit.  
3. Add debounced buttons to increment counters.  
4. Implement the FSM and countdown logic.  
5. Integrate buzzer and LED indicators.  
6. Demonstrate full system functionality.  

---

## 🏁 Learning Outcomes
Students completing this project will be able to:
- Design and simulate modular Verilog systems  
- Implement FSMs, counters, and I/O interfaces  
- Apply FPGA clocking and constraint principles  
- Integrate logic design with real-world circuits  

---

## 📜 License
This repository is provided for **educational use** in **ECE 2372** at **Texas Tech University**.  
Reuse and adaptation are permitted for instructional and personal learning purposes.

---

**Developed by:**  
**Derek Johnston**  
Lecturer, Department of Electrical and Computer Engineering  
**Texas Tech University**
