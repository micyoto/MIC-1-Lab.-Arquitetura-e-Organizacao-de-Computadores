# MIC-1 Lab - Computer Architecture and Organization

This project implements the fundamental components of the MIC-1 microprocessor as described in Andrew S. Tanenbaum's book "Computer Architecture and Organization", using Altera/Intel's Quartus II 64-bit.

## 📋 Table of Contents

- [Overview](#overview)
- [Project Structure](#project-structure)
- [Implemented Components](#implemented-components)
- [Requirements](#requirements)
- [How to Use](#how-to-use)
- [Simulation](#simulation)
- [File Structure](#file-structure)
- [Contributing](#contributing)

## 🎯 Overview

MIC-1 (Microprocessor Implementation Computer - 1) is an educational microprocessor designed to demonstrate fundamental computer architecture concepts. This project implements all essential components using Block Diagram Files (BDF) in Quartus II.

![MIC-1 Architecture](images/mic1_architecture.png)
*Complete MIC-1 architecture diagram - Data path and control unit*

### Key Features:
- **Architecture**: 32-bit
- **Technology**: Cyclone II FPGA
- **Methodology**: Bottom-up (1-bit components → 8-bit → 32-bit)
- **Simulation**: ModelSim-Altera with Vector Waveform Files (VWF)

> 📋 **Note**: For detailed architecture diagrams, see [ARCHITECTURE_DIAGRAM.md](ARCHITECTURE_DIAGRAM.md)

## 🏗️ Project Structure

```
MIC1/
├── 📁 Basic Components (1-bit)
│   ├── full_adder_1bit.bdf       # 1-bit Full Adder
│   ├── register_1bit.bdf         # 1-bit Register
│   └── ula_1bit.bdf              # 1-bit ALU
│
├── 📁 Intermediate Components (8-bit)
│   ├── register_8bit.bdf         # 8-bit Register
│   └── ula_8bit.bdf              # 8-bit ALU
│
├── 📁 Advanced Components (32-bit)
│   ├── register_32bit.bdf        # 32-bit Register
│   └── ula_32bit.bdf             # 32-bit ALU
│
├── 📁 Control Components
│   ├── decoder_2x4.bdf           # 2x4 Decoder
│   ├── logic_unit.bdf            # Logic Unit
│   ├── shifter.bdf               # Shifter Unit
│   ├── sra1.bdf                  # Shift Right Arithmetic (1 bit)
│   └── sll8.bdf                  # Shift Left Logical (8 bits)
│
├── 📁 Simulation Files
│   ├── *.vwf                     # Vector Waveform Files
│   └── *.vwf.temp                # Temporary simulation files
│
└── 📁 Project Files
    ├── MIC1.qpf                  # Quartus Project File
    ├── MIC1.qsf                  # Project Settings File
    └── *.bsf                     # Block Symbol Files
```

## ⚙️ Implemented Components

![Component Hierarchy](images/component_hierarchy.png)
*Hierarchy of implemented components - from 1-bit to 32-bit*

### 1. **Full Adder - 1 bit**
- **File**: `full_adder_1bit.bdf`
- **Function**: Performs binary addition of two bits with carry
- **Inputs**: A, B, Cin
- **Outputs**: Sum, Cout

![Full Adder](images/full_adder_diagram.png)
*Logic diagram of 1-bit full adder*

### 2. **Register - 1, 8 and 32 bits**
- **Files**: `register_1bit.bdf`, `register_8bit.bdf`, `register_32bit.bdf`
- **Function**: Temporary data storage
- **Control**: Clock, Enable, Reset
- **Application**: MIC-1 registers (MAR, MDR, PC, SP, LV, CPP, TOS, OPC, H)

![Registers](images/registers_diagram.png)
*Structure of 1, 8, and 32-bit registers*

### 3. **ALU (Arithmetic Logic Unit)**
- **Files**: `ula_1bit.bdf`, `ula_8bit.bdf`, `ula_32bit.bdf`
- **Arithmetic Operations**: Addition, Subtraction
- **Logic Operations**: AND, OR, NOT
- **Function**: Computational heart of the processor

![ALU](images/alu_diagram.png)
*32-bit ALU architecture with arithmetic and logic operations*

### 4. **2x4 Decoder**
- **File**: `decoder_2x4.bdf`
- **Function**: Converts 2 input bits to 4 output lines
- **Application**: Control signal decoding

### 5. **Shifter Unit**
- **Files**: `shifter.bdf`, `sra1.bdf`, `sll8.bdf`
- **Operations**: 
  - SLL (Shift Left Logical)
  - SRA (Shift Right Arithmetic)
- **Function**: Bit shifting operations

![Shifter](images/shifter_diagram.png)
*Shifter unit with SLL and SRA operations*

### 6. **Logic Unit**
- **File**: `logic_unit.bdf`
- **Function**: Complex logic operations
- **Integration**: Combines multiple logic operations

## 🔧 Requirements

### Required Software:
- **Quartus II 64-bit** (version 13.0 SP1 or higher)
- **ModelSim-Altera** (for simulation)
- **Windows** (compatible with development environment)

### Recommended Hardware:
- **FPGA**: Cyclone II (configured in project)
- **RAM**: Minimum 4GB
- **Processor**: x64 compatible

## 🚀 How to Use

### 1. **Opening the Project**
```bash
# Open Quartus II
# File → Open Project → Select MIC1.qpf
```

### 2. **Compilation**
```bash
# In Quartus II:
# Processing → Start Compilation (Ctrl+L)
```

### 3. **Simulation**
```bash
# Open desired .vwf file
# Simulation → Start Simulation
# Analyze waveforms in ModelSim
```

### 4. **FPGA Synthesis**
```bash
# Tools → Programmer
# Configure Cyclone II device
# Start Programming
```

## 📊 Simulation

The project includes simulation files (.vwf) for each component:

![Simulation](images/simulation_waveforms.png)
*Example simulation waveforms for 8-bit ALU*

### Implemented Tests:
- **8-bit ALU**: 
  - `ULA_8bit_ADD.vwf` - Addition test
  - `ULA_8bit_AND.vwf` - AND test
  - `ULA_8bit_OR.vwf` - OR test
  - `ULA_8bit_CONSTANTS.vwf` - Constants test

- **Registers**:
  - `register_8bit.vwf` - Storage test
  - `register_32bit.vwf` - Full register test

- **Individual Components**:
  - Each component has its corresponding `.vwf` file

### How to Interpret Simulations:

![Simulation Guide](images/simulation_guide.png)
*Guide for interpreting waveforms in ModelSim*

1. **Clock Signals**: Identify operation cycles
2. **Enable Signals**: Control when components are active
3. **Input Data**: Values applied to components
4. **Output Data**: Results of operations
5. **Status Signals**: Flags like carry, zero, overflow

## 📁 File Structure

| Extension | Description |
|-----------|-------------|
| `.bdf` | Block Diagram File - Schematic diagram |
| `.bsf` | Block Symbol File - Symbol file |
| `.vwf` | Vector Waveform File - Simulation file |
| `.qpf` | Quartus Project File - Project file |
| `.qsf` | Quartus Settings File - Settings |
| `.qws` | Quartus Workspace File - Workspace |

### System Directories:
- **`db/`**: Project database (compilation files)
- **`incremental_db/`**: Incremental compilation
- **`output_files/`**: Synthesis output files
- **`simulation/`**: ModelSim simulation files

## 🎓 Educational Concepts

This project demonstrates:

1. **Design Hierarchy**: Bottom-up approach
2. **Component Reuse**: 1-bit blocks to build larger systems
3. **Simulation and Verification**: Extensive testing of each component
4. **Hardware Synthesis**: Real implementation on FPGA

## 📚 Reference

Based on the book:
**"Computer Architecture and Organization"**
*Andrew S. Tanenbaum*

### Relevant Chapters:
- Chapter 4: Microarchitecture Level
- Section 4.1: Microarchitecture Example: MIC-1

## 🎯 Learning Objectives

Students will learn:

- **Digital Logic Design**: From basic gates to complex systems
- **Computer Architecture**: Understanding processor internals
- **FPGA Development**: Real hardware implementation
- **Simulation Techniques**: Verification and testing methods
- **Hierarchical Design**: Building complex systems from simple components

## 🔍 Component Details

### MIC-1 Architecture Overview

The MIC-1 is a simple CISC processor with:
- **Data Path**: 32-bit wide
- **Registers**: 9 main registers
- **Memory**: Unified instruction/data memory
- **Control**: Microprogram control unit

### Register Set:
- **MAR** (Memory Address Register): Holds memory addresses
- **MDR** (Memory Data Register): Data buffer for memory operations
- **PC** (Program Counter): Points to next instruction
- **SP** (Stack Pointer): Points to stack top
- **LV** (Local Variable): Base of current stack frame
- **CPP** (Constant Pool Pointer): Points to constant pool
- **TOS** (Top of Stack): Stack operations
- **OPC** (OpCode): Current instruction
- **H** (Holding Register): Temporary storage

### Data Path Components:
1. **ALU**: Performs arithmetic and logic operations
2. **Shifter**: Handles bit shifting operations
3. **Registers**: Store operands and intermediate results
4. **Buses**: Connect components (A-bus, B-bus, C-bus)

## 🛠️ Advanced Usage

### Custom Component Creation:
1. Open Quartus II Block Editor
2. Design your component using basic gates
3. Save as `.bdf` file
4. Create symbol (`.bsf`) for reuse
5. Add to project and compile

### Testing Methodology:
1. **Unit Testing**: Test individual components
2. **Integration Testing**: Test component combinations
3. **System Testing**: Full processor verification
4. **Timing Analysis**: Check timing constraints

### Optimization Techniques:
- **Logic Minimization**: Reduce gate count
- **Pipeline Consideration**: Plan for future pipelining
- **Resource Utilization**: Efficient FPGA usage
- **Power Optimization**: Minimize power consumption

## 📈 Performance Metrics

Typical performance characteristics:
- **Clock Frequency**: Up to 50 MHz on Cyclone II
- **Logic Elements**: ~2000 LEs for full implementation
- **Memory Usage**: 32KB instruction + data memory
- **Instruction Set**: 16 basic instructions

## 🔧 Troubleshooting

### Common Issues:

1. **Compilation Errors**:
   - Check file dependencies
   - Verify component connections
   - Review signal naming

2. **Simulation Problems**:
   - Verify input stimulus
   - Check timing constraints
   - Validate expected outputs

3. **FPGA Programming Issues**:
   - Confirm device selection
   - Check pin assignments
   - Verify programming cable

## 🌐 Additional Resources

### Documentation:
- [Quartus II Handbook](https://www.intel.com/content/www/us/en/programmable/documentation/lit-index.html)
- [ModelSim User Guide](https://www.intel.com/content/www/us/en/programmable/documentation/zks1462824262282.html)
- [Cyclone II Device Handbook](https://www.intel.com/content/www/us/en/programmable/documentation/lit-index.html)

### Tutorials:
- Digital Logic Design with Quartus II
- VHDL/Verilog Integration
- FPGA Design Best Practices

## 🤝 Contributing

To contribute to this project:

1. Fork the repository
2. Create a feature branch (`git checkout -b feature/AmazingFeature`)
3. Commit your changes (`git commit -m 'Add some AmazingFeature'`)
4. Push to the branch (`git push origin feature/AmazingFeature`)
5. Open a Pull Request

### Contribution Guidelines:
- Follow consistent naming conventions
- Document all components thoroughly
- Include simulation files for new components
- Test all changes before submission

## 📄 License

This project is educational and follows Altera/Intel license terms for development tools.

## 👥 Authors

*Developed as support material for Computer Architecture and Organization courses*

---

**Keywords**: MIC-1, Microprocessor, FPGA, Quartus II, Computer Architecture, Digital Logic, Educational Project, Tanenbaum
