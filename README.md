# 4Bit-Up-Down-Asynchronous-Reset-Counter-Synthesis

## Aim:

Synthesize 4Bit-Up-Down-Asynchronous-Reset-Counter design using Constraints and analyse reports, Timing, area and Power.

## Tool Required:

Functional Simulation: Incisive Simulator (ncvlog, ncelab, ncsim)

Synthesis: Genus

### Step 1: Getting Started

Synthesis requires three files as follows,

◦ Liberty Files (.lib)

◦ Verilog/VHDL Files (.v or .vhdl or .vhd)

◦ SDC (Synopsis Design Constraint) File (.sdc)

 ### Step 2 : Creating an SDC File

•	In your terminal type “gedit input_constraints.sdc” to create an SDC File if you do not have one.

•	The SDC File must contain the following commands;

create_clock -name clk -period 2 -waveform {0 1} [get_ports "clk"]

set_clock_transition -rise 0.1 [get_clocks "clk"]

set_clock_transition -fall 0.1 [get_clocks "clk"]

set_clock_uncertainty 0.01 [get_ports "clk"]

set_input_delay -max 0.8 [get_ports "rst"] -clock [get_clocks "clk"]

set_output_delay -max 0.8 [get_ports "count"] -clock [get_clocks "clk"]

i→ Creates a Clock named “clk” with Time Period 2ns and On Time from t=0 to t=1.

ii, iii → Sets Clock Rise and Fall time to 100ps.

iv → Sets Clock Uncertainty to 10ps.

v, vi → Sets the maximum limit for I/O port delay to 1ps.

### Step 3 : Performing Synthesis

The Liberty files are present in the library path,

• The Available technology nodes are 180nm ,90nm and 45nm.

• In the terminal, initialise the tools with the following commands if a new terminal is being
used.

◦ csh

◦ source /cadence/install/cshrc

• The tool used for Synthesis is “Genus”. Hence, type “genus -gui” to open the tool.

• Genus Script file with .tcl file Extension commands are executed one by one to synthesize the netlist.

#### Synthesis RTL Schematic :
<img width="1919" height="1079" alt="Screenshot 2025-09-27 104918" src="https://github.com/user-attachments/assets/96d22fc5-af62-4d00-82ae-5d20974e1fe8" />


#### Area report:
<img width="1919" height="1079" alt="Screenshot 2025-09-27 105056" src="https://github.com/user-attachments/assets/feb6243c-831c-497a-8f6e-002cc42e1d08" />


#### Power Report:
<img width="1919" height="1079" alt="Screenshot 2025-09-27 105111" src="https://github.com/user-attachments/assets/42a6d02e-9af3-4e55-8059-35ad9ef8f867" />


#### Timing Report: 
<img width="1919" height="1078" alt="Screenshot 2025-09-27 105129" src="https://github.com/user-attachments/assets/40c31628-a7dc-4dcc-a68c-0bf77e5057f0" />


#### Result: 

The generic netlist has been created, and area, power, and timing reports have been tabulated and generated using Genus.





