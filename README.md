# Digital-VLSI-SoC-Design-and-planning

Welcome to the OpenLane workshop! In this workshop, we will delve into the process of designing an Application Specific Integrated Circuit (ASIC) from the Register Transfer Level (RTL) to the Graphical Data System (GDS) file using the OpenLane ASIC flow. The flow is composed of several key steps, starting with an RTL file and culminating in a GDS file.

# PHYSICAL DESIGN IN VLSI

# Day 1 - Inception of open-source EDA OpenLANE and sky130 PDK

# KY L1 Introduction to QFN-48 Package chip pads core die and IPs
## Arduino Board
This is an arduino microcontroller board. The encircled area shows the chip(microprocessor) which is interfaced with other components of the board. The designing of this chip from abstract level all the way down to the fabrication is done by RTL to GDSll flow.Arduino consists of both a physical programmable circuit board (often referred to as a microcontroller) and a piece of software, or IDE (Integrated Development Environment) that runs on the computer, used to write and upload computer code to the physical board.

## RISC-V SOC

![image](https://github.com/user-attachments/assets/685a8ad3-8b55-4572-8f41-44311c2ce130)
It consist of SRAM,SOC,ADC,DAC,SPI these all are called foundary IP's.All devices depends upon foundary where all chips are fabricated using deposition and lithography techniques and so on.

## INSIDE A MICROCONTROLLER BOARD
![image](https://github.com/user-attachments/assets/ca774362-62fb-482d-8a28-62d9a1d8bd44)
![image](https://github.com/user-attachments/assets/c71640b5-d605-4280-89e7-7c98e1a280a0)

## Microcontroller Board Components
### Core:
Definition: The central processing unit (CPU) of the microcontroller that executes instructions. Example: ARM Cortex-M, RISC-V core. 
### Die:
Definition: The physical silicon chip on which the microcontroller’s circuitry is fabricated.
### Pad:
Definition: The physical connection points on the microcontroller chip where external components are connected.

### GPIO (General-Purpose Input/Output):
Definition: Pins on the microcontroller that can be programmed to either input signals (e.g., sensors) or output signals (e.g., LEDs).

### Bank:
Definition: A grouping of I/O pins or memory segments used for organization within the microcontroller. For GPIO, it refers to a set of pins grouped together.

### Foundries:
Definition: Facilities where the microcontroller chips are manufactured. Examples include TSMC, Intel.

### IPs (Intellectual Properties):
Definition: Pre-designed blocks of logic that can be integrated into the microcontroller. Examples include UART, SPI, and I2C controllers.

### SRAM (Static Random-Access Memory):
Definition: A type of volatile memory used for temporary data storage within the microcontroller. Fast but more expensive and power-consuming than DRAM.

### DRAM (Dynamic Random-Access Memory):
Definition: A type of volatile memory used for larger, temporary data storage. Requires periodic refreshing to maintain data.

### ADC (Analog-to-Digital Converter):
Definition: Converts analog signals (e.g., sensor outputs) into digital values that can be processed by the microcontroller.

### DAC (Digital-to-Analog Converter):
Definition: Converts digital values into analog signals (e.g., to drive speakers or analog displays).

### RISC-V SoC (System on Chip):
Definition: A microcontroller or microprocessor incorporating a RISC-V core along with additional integrated components such as memory, peripherals, and communication interfaces.

### Macros:
Definition: Predefined sequences of code or hardware configurations used to simplify and automate repetitive tasks in programming or hardware design.

### Connecting All Components
#### Core: 
Executes instructions and processes data. Die: Houses the core and other integrated components. Pad: Connects the die to external components via GPIO. GPIO: Interfaces with external devices, configured via macros. Bank: Organizes GPIO and other resources. Foundries: Manufacture the microcontroller with the integrated core, SRAM, DRAM, ADC, DAC, and IPs. IPs: Provide specialized functions like UART and SPI, integrated into the SoC. SRAM & DRAM: Store data temporarily for processing and operation. ADC & DAC: Enable analog signal processing and generation. This layout ensures a microcontroller can interact with the external world and perform complex tasks by integrating various components into a single, functional chip.

## SKY L1 Introduction to all components of an open-source digital ASIC design
### RTL Design (Register Transfer Level Design):
Definition: Describes the logic and behavior of a digital circuit using registers and the data transfers between them. Purpose: Defines the functionality and operations of the circuit.

### EDA Tools (Electronic Design Automation Tools):
Definition: Software tools used for designing, simulating, and verifying electronic systems and integrated circuits.

### Open-Source Tools:
QROad: Focuses on routing within digital ASIC designs. OpenROAD: Provides a comprehensive tool suite for placement, routing, and design rule checking. OpenLane: Offers an end-to-end RTL-to-GDSII flow, integrating with other open-source tools.

### PDK (Process Design Kit):
Definition: Contains files and information from semiconductor foundries describing the manufacturing process and design rules. Purpose: Ensures designs are manufacturable and provides parameters for accurate simulation.

### Google Skywater 130nm PDK:
Definition: An open-source PDK for the SkyWater 130nm process technology. Features: Includes libraries, design rules, and models specific to the 130nm technology node.

# simplified RTL TO GDSII MODEL
![image](https://github.com/user-attachments/assets/480062ed-1c64-45c9-86c9-1c555d1f4862)
### RTL Design: 
Create a high-level description of the circuit.
### Synthesis: 
Convert RTL code to a gate-level netlist.
### Floorplanning and Power Planning: 
Arrange blocks and plan power distribution.
### Clock Tree Synthesis: 
Design the clock distribution network.
### Routing: 
Connect the gates and flip-flops.
### Signoff: 
Verify design with DRC, LVS, and ERC.
### GDSII File Generation: 
Generate the final layout file for manufacturing.

![image](https://github.com/user-attachments/assets/f629ae7a-2846-4ee0-b3f7-3ec13dc5c648)
### RTL Synthesis: 
Converting Register Transfer Level (RTL) code into a gate-level netlist.
### Floorplanning & Placement: 
Planning the chip layout and placing standard cells.
### CTS & Routing: 
Clock Tree Synthesis and interconnecting placed cells with metal layers.
### Static Timing Analysis (STA): 
Verifying timing closure.
### Physical Verification: 
Ensuring design rule compliance (DRC) and layout vs. schematic (LVS) correctness.
### DFT(Design for Test): 
it perform scan inserption, automatic test pattern generation, Test patterns compaction, Fault coverage, Fault simulation.After that physical implementation is done by OpenROAD app
### Static Timing analysis(STA): 
It involves the interconnect RC Extraction(DEF2SPEF) from the routed layout, followed by STA on OpenSTA(OpenROAD) tool. resulting report will shows the timing violations if any violations is there.
### Physical Verification(DRC and LVS): 
Magic is used for design Rules checking and SPICE Extraction from Layout. Magic and Netgen are used for LVS.

Every time the netlist is modified.(CTS modifies the netlist and Post Placements optimization also modifies the netlist).So for that verification must be performed. The LCE(yosys) is used to formally confirm that the function did not change after modifying the netlist.

# DAY 1 (LABS)
## Understanding the use of various linux commands :
### Open the LINUX Terminal (in desktop directory)
![image](https://github.com/user-attachments/assets/787cc954-f1f1-467c-8184-f26972754822)


#### Important LINUX Commands

#### 1. cd : It is used to change the current working directory.
#### 2. ls : It lists the contents of a directory.
#### 3.ls -ltr : It lists the contents of a directory in long format, sorted by modification time in reverse order (oldest first).
#### 4.ls --help: It displays a help message with a list of options and usage information for the "ls" command. Note : You can give any command name and then type "--help" to get info about that command.
#### 5.cd : Using this command we can move in both ways in the directory tree.
#### 6.clear: It clears the terminal screen.

## Now, moving to the work directory where all files related to the workshop are stored,use the follwoing commands
```
cd Desktop
cd work/tools/
cd openlane_working_dir/
cd openlane/

















































































