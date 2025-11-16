# VSD-IAT
This repository contains files and documentation for my VSD physical design project.
Pad – Send signal
Core – All digital logic cells are placed
Die – Size

Foundry – Factory where chips are manufactured
Macros – Digital logic

Instruction Set Architecture (ISA) –
The way we talk to a computer

Apps → System → Software → Hardware

It converts into binary language for hardware

System Software – Composed of:

OS → Handle I/O operations

Allocate memory

C, VB

Compiler – When a program is given in C / Java,
it converts it into instructions so the hardware can understand.

Instruction varies from model and hardware
(e.g., Intel → Intel instruction format)

Assembler – Converts into binary language so that the hardware can understand.

Instr (Instruction) is a language
where humans talk to the machine.
So it is called the architecture of computers or ISA.

Program → Synthesis → Netlist → Physical Design

ASIC

→ EDA tools
→ PDK data
→ RTL
→ Design

What is PDK?
A set of data a company makes to help designers design a chip
Lynn Conway
1 person said we can separate
design from manufacture.

They introduced:
→ Structured-based methodology
→ λ-based rule (lambda rule)

These rules make design work
independently from manufacturer.

Result: New companies started.
Pure-play fabs → manufacture chip
Fabless → design the chip

PDK = Process Design Kit
It is a data package that the manufacturing
company gives to designers.
Composed of: rules, parameters, models,
libraries.

IS 130nm Fast?
Yes
Simplified RTL to GDSII flow

(RTL → Synth → FP/PP → Placement → CTS → Route → Sign-off)

Synth – convert program into logic gates

Synth → FP/PP → Placement → CTS → Route → Sign-off (GDSII)

FP/PP → Macro floorplanning → dimension/pin location, rows, power planning; plan the power packets
(e.g., Intel, IBM etc.)

So own manufacturing technology + own designers.

Placement → place cells on floorplan
• Steps:
1) Place Global → Align, may overlap
2) Detailed Placement → Rearranges perfectly
3) CTS → Clock Tree Synth

• After placement the interconnect wires can be done layer by layer
→ Route → perform routing
→ DRC → No short, no DRC violations
→ GDS2 generation → Final mask generation
→ GDS2 → Final output

• DRC → Design Rule Checking
• Physical Verification
• LVS → Layout vs Schematic
• Detailed Routing
• Global Routing
• Metal Stack / Power Routing grid

Big and medium designs
• Straight
• Slicing
• Time verification
• Static timing analysis
• Tuning … tool solution not done, work done with a few tunings
• High speed
• Low speed
• Many blocks

The problem when using open-source EDA tools
OpenLane → Started as open-source
Best tape-out experiment:
Sky130 family – how many DRC? (once)
Many DRCs?
Possible (in) GDSII without human intervention
By OS tools with no LVS, no DRC violations

→ OpenLane (our base tool) to transform VLSI chip (converting RTL design into final layouts)


❖ 2 modes of operation

Design Space Exploration – selecting which among many flow settings gives the best one (evaluation).

Standard Flow Mode – designers know which configuration to use.

OpenLane ASIC Flow

Design → RTL → Digital circuit with interconnect
RTL → Synth → Program to gate-level netlist

STA – check timing of design

DFT (Faculty) – Manufacturing testing

FP (Floorplan) –
• Define raw dimension → pin locations
• Placement → arranging cells on silicon area

CTS – build clock distribution network
Optimization → Fix issues after placement

Global Routing → Rough routing paths
Detailed Routing → Final routing path

LVS – check whether layout = netlist
DRC – check rule violations

Fill & Scripts (add) → remove antenna effects
• RC Extraction – wiring → (so that metal won’t damage transistor)

STA – again checks timing
Physical Verification → DRC, LVS checks
GDS-II Streaming – digital GDS-II file
SKY130 PDK – process rules + libraries
GDS-II → Final layout sent to foundry
Designers couldn't work independently;
they need to follow the factory process.
