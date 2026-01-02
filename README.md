# RTL2GDSII – 8-Bit Shifter
### Design and Physical Implementation of an 8-bit Barrel Shifter

**Author:** Om Hingu  
**University:** Pandit Deendayal Energy University  
**Program:** B.Tech – Electronics and Communication Engineering  

---

## Introduction

Shifting operations are a fundamental part of digital systems and are widely used in
processors, address generation, arithmetic operations, and data manipulation circuits.
This project demonstrates the complete **RTL to GDSII ASIC design flow** for a configurable
**8-bit barrel shifter**, starting from Verilog RTL and ending with a routed physical layout.

---

## Objectives

- Understand the complete RTL to GDSII flow  
- Design and verify an 8-bit barrel shifter using Verilog HDL  
- Perform synthesis using Synopsys Design Compiler  
- Carry out physical design using IC Compiler II  
- Perform Static Timing Analysis using PrimeTime  
- Analyze area, power, and timing metrics  

---

## Tools Used

| Tool | Purpose |
|------|---------|
| Synopsys Design Compiler | RTL Synthesis |
| Synopsys IC Compiler II | Floorplanning, Placement, CTS, Routing |
| Synopsys PrimeTime | Static Timing Analysis |
| Synopsys Verdi | RTL Simulation and Debug |
| TCL Scripts | Flow Automation |
| Linux | Execution Environment |

---

## Repository Structure

RTL2GDSII_8bit_Shifter/
├── rtl/
│ ├── shifter.v
│ └── shifter_tb.v
├── CONSTRAINTS/
│ └── 8bit_shifter.sdc
├── DC/
│ └── dc_synthesis.tcl
├── ICCII/
│ ├── floorplan.tcl
│ ├── powerplan.tcl
│ ├── placement.tcl
│ └── routing.tcl
├── PT/
│ └── primetime_sta.tcl
├── images/
│ ├── rtl_waveform.png
│ ├── floorplan.png
│ ├── placement.png
│ ├── cts.png
│ └── routing.png
└── README.md


---

## RTL Design

The shifter supports left and right shift operations with variable shift amounts from 0 to 7.

```verilog
always @(posedge Clock or posedge Reset) begin
  if (Reset)
    Data_Out <= 8'd0;
  else begin
    case(Direction)
      1'b0: Data_Out <= Data_In << Shift_Amount;
      1'b1: Data_Out <= Data_In >> Shift_Amount;
      default: Data_Out <= Data_In;
    endcase
  end
end

RTL Verification

RTL was verified using a Verilog testbench and waveform analysis.

Add your waveform image here:
images/rtl_waveform.png

Synthesis

Clock period: 4.4 ns

Input and output delays applied

Clock uncertainty and transition constraints added through SDC

Physical Design Flow
Step	Description
Floorplanning	Defines die area, core utilization, and IO placement
Power Planning	Creation of power rings and straps
Placement	Placement of standard cells
CTS	Clock Tree Synthesis for balanced clock distribution
Routing	Final metal routing and layout generation

Add screenshots here:

Floorplan image: images/floorplan.png

Placement image: images/placement.png

CTS image: images/cts.png

Routing image: images/routing.png

Static Timing Analysis

Timing analysis was performed using PrimeTime.

Final Slack obtained:
Final Slack = +0.063802 ns

This confirms that the design meets all setup and hold constraints.

Results
Parameter	Value
Area	1,250,000 µm²
Power	0.65 mW
Slack	+0.75 ns

The design satisfies all timing, power, and area goals.

Conclusion

The 8-bit barrel shifter was successfully designed, verified, synthesized, and physically
implemented using industry-standard EDA tools. This project demonstrates a complete
hands-on RTL to GDSII ASIC design flow.

Author

Om Hingu
B.Tech – Electronics and Communication Engineering
Pandit Deendayal Energy University
