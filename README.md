# Verilog Microprocessor Simulation

A multi-phase Verilog microprocessor simulation project, implementing a custom bus-based processor datapath, ALU, register subsystem, memory interface, and control unit. Functionality is verified through waveform-based simulation across arithmetic, logical, memory, branch, jump, and I/O instructions.

## Overview

This repository contains the full implementation of a simulated microprocessor developed in stages:

- **Phase 1:** Core datapath and ALU functionality
- **Phase 2:** Extended instruction support, memory/register integration, and control sequencing
- **Phase 3:** Full control unit implementation and integration with the datapath to execute the complete instruction set

The design demonstrates how a processor can be built from low-level Verilog modules and coordinated through a finite state machine-based control unit.

## Key Features

- **Bus-driven datapath architecture**
- **16 general-purpose registers** (`R0` to `R15`)
- Special-purpose registers including:
  - `HI`
  - `LO`
  - `PC`
  - `IR`
  - `MAR`
  - `MDR`
  - `Y`
  - `Z`
- **ALU support** for arithmetic, logic, shift, rotate, multiply, divide, negate, and bitwise not
- **Memory access instructions** for load/store behavior
- **Immediate instructions**
- **Branch and jump instructions**
- **Input/output support**
- **Waveform-based simulation validation**
- **Finite state machine control unit** that drives instruction execution via opcode-based control sequencing

## Architecture

The processor is organized around a shared internal bus and modular datapath components.

### Core modules
- `DataPath`
- `ALU`
- `Bus`
- `Select and Encode`
- `CONFF`
- `RAM`
- `R0`
- `Import Reg`
- `control_unit`

### Datapath responsibilities
The datapath connects the register file, ALU, memory interface, and special-purpose registers through a shared bus. It is responsible for moving operands, capturing intermediate ALU results, loading/storing memory values, and updating architectural state during instruction execution.

### Control unit responsibilities
The control unit is implemented as a **state machine**. It:
- decodes the opcode stored in the instruction register
- transitions through instruction-specific execution states
- emits control signals for the datapath, ALU, memory, and registers
- manages conditional control flow for branch instructions
- coordinates fetch, decode, and execute behavior across supported instructions

## Supported Instructions

### Arithmetic and logical instructions
- `add`
- `sub`
- `and`
- `or`
- `mul`
- `div`
- `neg`
- `not`

### Shift and rotate instructions
- `shr`
- `shra`
- `shl`
- `ror`
- `rol`

### Memory instructions
- `ld`
- `ldi`
- `st`

### Immediate instructions
- `addi`
- `andi`
- `ori`

### Branch and control flow instructions
- `brzr`
- `brnz`
- `brpl`
- `brmi`
- `jr`
- `jal`

### Special register instructions
- `mfhi`
- `mflo`

### Input/output instructions
- `in`
- `out`

### Control instructions
- `nop`
- `halt`

## Verification and Testing

The processor was validated using simulation waveforms across multiple development phases.

### Examples of verified behavior
- register-to-register arithmetic and logic execution
- memory loads and stores using direct and offset addressing
- immediate ALU operations
- conditional branch behavior based on condition flags
- jump and link control flow
- transfer of `HI` and `LO` results back into the register file
- correct handling of input and output instructions
- proper instruction fetch and decode through the instruction register
- correct program counter updates during sequential execution and branching

The simulation results confirmed:
- expected register updates
- expected memory contents
- proper control signal sequencing
- correct interaction between the control unit and datapath

## Why this project matters

This project demonstrates hands-on experience with:

- digital system design
- computer architecture fundamentals
- RTL design in Verilog
- finite state machine control logic
- shared-bus datapath design
- instruction execution sequencing
- hardware simulation and waveform debugging
- modular hardware development across iterative project phases

## Skills Demonstrated

- **Verilog RTL development**
- **Processor/datapath design**
- **Control unit state machine design**
- **ALU design**
- **Register file and memory integration**
- **Instruction set implementation**
- **Hardware simulation and debugging**
- **Modular system integration**
- **Waveform-based verification**
