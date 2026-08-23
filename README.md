# 8-bit Processor Design & Simulation using Logisim

A custom 8-bit processor designed and simulated in **Logisim-evolution** as a
Computer Organization and Architecture project.

The project focuses on understanding the internal organization of a basic CPU:
instruction fetching, instruction decoding, register operations, arithmetic and
logical processing, memory access, control signals, and write-back.

> **Note:** The project report demonstrates the multiplication operation in
> detail. The Logisim implementation was further experimented with for the
> arithmetic operations **ADD, SUB, MUL, and DIV**, along with logical
> operations and processor datapath/control blocks.

---

## 🚀 Project Overview

This project implements a small **register-based, single-cycle processor**
using digital logic components in Logisim-evolution.

### Architecture

- Register-based processor
- Shared datapath / bus-oriented organization
- Single-cycle instruction execution model
- Centralized control logic
- 8-bit data paths
- Register file
- Instruction memory
- Data memory
- Instruction Register (IR)
- Program Counter (PC)
- Arithmetic and Logic Unit (ALU/datapath)
- Multiplexers and selection logic
- Decoder / demultiplexer based control
- Combinational and sequential logic

The processor follows the basic execution flow:

```text
FETCH → DECODE → OPERAND FETCH → EXECUTE → MEMORY ACCESS → WRITE BACK
```

---

## 🧠 Processor Architecture

```text
                 ┌──────────────────┐
                 │ Program Counter  │
                 │       PC         │
                 └────────┬─────────┘
                          │
                          ▼
                 ┌──────────────────┐
                 │ Instruction      │
                 │ Memory           │
                 └────────┬─────────┘
                          │
                          ▼
                 ┌──────────────────┐
                 │ Instruction      │
                 │ Register (IR)    │
                 └────────┬─────────┘
                          │
                          ▼
                 ┌──────────────────┐
                 │ Control / Decode │
                 │ Logic            │
                 └────────┬─────────┘
                          │
             ┌────────────┴────────────┐
             │                         │
             ▼                         ▼
      ┌──────────────┐         ┌─────────────────┐
      │ Register File│────────►│ Arithmetic /    │
      │    8-bit     │         │ Logic Datapath  │
      └──────┬───────┘         └────────┬────────┘
             │                          │
             │                          ▼
             │                  ┌──────────────┐
             │                  │ Data Memory  │
             │                  └──────┬───────┘
             │                         │
             └──────────────┬──────────┘
                            ▼
                     ┌─────────────┐
                     │  Write Back │
                     └─────────────┘
```

---

## ⚙️ Processor Components

| Component | Purpose |
|---|---|
| **Program Counter (PC)** | Holds the address of the current instruction |
| **Instruction Memory** | Stores processor instructions |
| **Instruction Register (IR)** | Holds the fetched instruction |
| **Register File** | Stores operands and processor results |
| **ALU / Arithmetic Datapath** | Performs arithmetic and logical operations |
| **Data Memory** | Provides memory access for LOAD/STORE operations |
| **Control Unit** | Decodes instructions and generates control signals |
| **Multiplexers** | Select register, ALU and write-back data paths |
| **Decoder** | Generates selection/control signals |
| **Demultiplexer** | Routes write/control signals |
| **Logic Gates** | Implement control and datapath logic |

---

## ➕ Arithmetic Operations

The Logisim implementation was extended/experimented with to support the
following arithmetic operations:

| Operation | Description |
|---|---|
| **ADD** | Addition of two operands |
| **SUB** | Subtraction of two operands |
| **MUL** | Multiplication of two operands |
| **DIV** | Division of two operands |

The project report specifically demonstrates the multiplication datapath with:

```text
Operand A = 2
Operand B = 2

2 × 2 = 4
```

The complete Logisim project is included in:

```text
Processor/coa_project.circ
```

---

## 🔢 Logical Operations

The processor design also includes logical operations:

- **AND**
- **OR**
- **XOR**

These operations use combinational logic and selection/control circuitry to
produce the required result.

---

## 📦 Data Transfer & Memory Operations

The processor architecture supports the following data movement concepts:

### LOAD

```text
Data Memory → Register
```

### STORE

```text
Register → Data Memory
```

### MOV

```text
Source Register → Destination Register
```

### NOP

A no-operation/control instruction used for simple processor flow.

---

## 🔄 Instruction Execution Cycle

### 1. Instruction Fetch

```text
PC → Instruction Memory → IR
```

The Program Counter provides the instruction address and the fetched
instruction is stored in the Instruction Register.

### 2. Instruction Decode

```text
IR → Control Unit
```

The opcode is decoded and the required control signals are generated.

### 3. Operand Fetch

```text
Register File → Multiplexers → Datapath
```

The required operands are selected from the register file.

### 4. Execute

The arithmetic or logical datapath performs the requested operation.

Examples:

```text
ADD
SUB
MUL
DIV
AND
OR
XOR
```

### 5. Memory Access

For memory instructions:

```text
LOAD  → Memory → Register
STORE → Register → Memory
```

### 6. Write Back

The resulting value is written to the destination register and the processor
continues with the next instruction.

---

## 🧩 Control Unit

The control section decodes the instruction and generates signals for:

- Register write enable
- ALU operation selection
- Memory read
- Memory write
- Multiplexer selection
- Register selection

The implementation uses digital logic components such as:

- Decoder
- Demultiplexer
- AND gates
- OR gate
- NOT gate
- Multiplexers
- Control wiring

---

## 🧪 Verification

The processor was tested by executing individual instructions and observing
the resulting datapath and register values.

The project report records successful verification of the processor behavior
and states that individual instructions produced the expected outputs.

### Verification checklist

| Module / Operation | Status |
|---|---|
| Instruction Fetch | ✅ |
| Instruction Decode | ✅ |
| Register File | ✅ |
| Control Logic | ✅ |
| Arithmetic Datapath | ✅ |
| Addition | ✅ |
| Subtraction | ✅ |
| Multiplication | ✅ |
| Division | ✅ |
| AND | ✅ |
| OR | ✅ |
| XOR | ✅ |
| LOAD | ✅ |
| STORE | ✅ |
| Write Back | ✅ |

---

## 🖥️ Simulation

The processor can be opened and inspected directly in **Logisim-evolution**.

### Open the project

1. Install/open Logisim-evolution.
2. Open:

```text
Processor/coa_project.circ
```

3. Inspect the processor datapath and control logic.
4. Run the circuit using Logisim's simulation controls.
5. Observe register, memory, control and datapath activity.

---

## 📸 Screenshots

### Processor Overview

<img width="937" height="951" alt="image" src="https://github.com/user-attachments/assets/d1570216-19c0-4461-ba90-f300b4c44e2d" />

### Arithmetic Unit

<img width="901" height="787" alt="image" src="https://github.com/user-attachments/assets/97b1ae2e-7f8e-4d27-91dc-26bbfdebb5b1" />


### Multiplication

<img width="901" height="787" alt="image" src="https://github.com/user-attachments/assets/01ec63d9-a0c1-4dfd-9e89-9c86aaf8dc56" />

### Register File

<img width="1912" height="977" alt="image" src="https://github.com/user-attachments/assets/1bab9570-2d82-4a27-8866-74729e27919d" />


---

## 🛠️ Tools & Technologies

- **Logisim-evolution 3.7.2**
- Digital Logic Design
- Computer Organization & Architecture
- Processor Datapath Design
- ALU Design
- Register File
- Multiplexers
- Decoder / Demultiplexer
- RAM
- Combinational Logic
- Sequential Logic

---

## 📁 Repository Structure

```text
8bit-Processor-Design-Logisim/
│
├── README.md
│
├── Processor/
│   └── coa_project.circ
│
├── Documentation/
│   └── COA_Project_Report.pdf
│
└── Screenshots/
    └── Add project screenshots here
```

---

## 🎯 Learning Outcomes

This project provided practical understanding of:

- Internal CPU organization
- Datapath design
- Register-based processor architecture
- Instruction fetch and decode
- ALU operation selection
- Register file organization
- Memory access
- Control signal generation
- Multiplexer-based data routing
- Digital logic implementation of processor components
- Instruction execution flow

---

## 🔮 Future Improvements

Possible extensions include:

- [ ] Expand the instruction set
- [ ] Add branch instructions
- [ ] Add conditional branching
- [ ] Implement interrupt handling
- [ ] Add status/flag registers
- [ ] Increase register count
- [ ] Improve instruction encoding
- [ ] Implement pipelining
- [ ] Add more advanced memory addressing
- [ ] Develop a more complete CPU instruction set

---

## 📚 Documentation

The original academic project report is available here:

```text
Documentation/COA_Project_Report.pdf
```

It documents the processor architecture, components, execution cycle,
simulation results and conclusions.

---

## 👨‍💻 Author

**Chinmay N. Yalawatti**

Electronics & Communication Engineering

Computer Organization & Architecture Project

---

## 📄 License

This project is provided for educational and learning purposes.
