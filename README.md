# Assignment 1: Quantum Computing

**Author:** Siddhant Kankaria  
**Program:** PGP in AI & Data Science, Jio Institute  
**Quarter:** 5 - Quantum Computing  

---

## About

This submission covers **Assignment 1** of the Quantum Computing module. It contains implementations of two fundamental quantum information protocols — **Quantum Teleportation** and **Superdense Coding** — developed using the **Qiskit** framework from IBM and executed on the **Aer** simulation backend.

---

## File Listing

| File | Description |
|------|-------------|
| `Siddhant_Kankaria_Assignment_1_Problem_1_Part_A.ipynb` | Problem 1: Teleportation protocol implementation |
| `Siddhant_Kankaria_Assignment_1_Problem_2_Part_A.ipynb` | Problem 2: Superdense coding implementation |
| `README.md` | This file |

---

## Problem 1: Teleportation Protocol (Part A)

### Objective
Show that an unknown quantum state can be faithfully transmitted from one party (Alice) to another (Bob) through the quantum teleportation algorithm, relying on shared entanglement and quantum gate operations.

### Implementation Details

The protocol is carried out in five stages:

1. **Initializing the Source State** — Qubit 0 is prepared in an arbitrary state |ψ⟩ using Ry(α) and Rz(γ) rotations with α = 1.2, γ = 2.1 (within the required range of 0.5–2.5).
2. **Creating the EPR Pair** — Qubits 1 and 2 are entangled into a Bell state via Hadamard + CNOT. Alice retains qubit 1; Bob holds qubit 2.
3. **Alice's Operations** — A CNOT (qubit 0 → qubit 1) and Hadamard (qubit 0) project Alice's qubits into the Bell basis.
4. **Bob's Corrections** — Quantum controlled gates (CX conditioned on qubit 1, CZ conditioned on qubit 0) are applied to qubit 2, replacing the classical communication step.
5. **Checking the Result** — The adjoint of the state preparation (Rz(−γ) then Ry(−α)) is applied to Bob's qubit and it is measured.

### Result
Over 5000 simulation shots, the output is **`{'0': 5000}`** — all measurements return |0⟩. This confirms that the quantum state was **teleported with unit fidelity**.

---

## Problem 2: Superdense Coding (Part A)

### Objective
Demonstrate that two bits of classical information can be encoded into and decoded from a single qubit, provided the communicating parties share an entangled pair beforehand.

### Implementation Details

The protocol proceeds as follows:

1. **Entangled Pair Setup** — A Bell state |Φ+⟩ is created across qubit 0 (Alice) and qubit 1 (Bob) using H + CNOT.
2. **Choosing the Payload** — The two-bit message **'11'** is selected for transmission.
3. **Encoding Step** — For message '11', the encoding table prescribes applying X (bit-flip) then Z (phase-flip) on Alice's qubit.
4. **Decoding Step** — Bob applies CNOT and Hadamard to undo the entanglement and map the encoded state to computational basis states.
5. **Measurement** — Both qubits are measured to extract the two classical bits.

### Result
With 1000 shots, the simulator yields **`{'11': 1000}`** — the intended message is **recovered perfectly** every time.

---

## Dependencies

| Package | Purpose |
|---------|---------|
| **Python 3.12.0** | Runtime environment |
| **Qiskit** | Building and manipulating quantum circuits |
| **Qiskit Aer** | Local quantum circuit simulation |
| **Matplotlib** | Rendering circuit diagrams and result histograms |

---

## Execution Instructions

1. **Set up the environment:**
   ```bash
   pip install qiskit qiskit-aer matplotlib
   ```

2. **Open Jupyter:**
   ```bash
   jupyter notebook
   ```

3. Navigate to the desired notebook and run all cells from top to bottom.

---

## Glossary

| Concept | Description |
|---------|-------------|
| **Quantum Teleportation** | Protocol for transmitting quantum information using entanglement and two classical bits |
| **Superdense Coding** | Protocol for encoding two classical bits into one qubit via shared entanglement |
| **Bell / EPR State** | Two-qubit maximally entangled state, the key resource for both protocols |
| **Hadamard Gate (H)** | Single-qubit gate producing equal superposition: \|0⟩ → (\|0⟩+\|1⟩)/√2 |
| **CNOT (CX)** | Two-qubit gate that flips the target qubit conditioned on the control being \|1⟩ |
| **Ry / Rz Rotation Gates** | Parameterized gates rotating a qubit state about the Y or Z axis by a specified angle |

---

## License

Academic submission for **Jio Institute** coursework.
