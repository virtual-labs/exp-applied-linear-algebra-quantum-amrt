#### 1. Introduction

Quantum computing harnesses the principles of quantum mechanics to process information in fundamentally different ways than classical computers. This experiment focuses on applying linear algebra concepts to understand and visualize real quantum gates and circuits. Linear algebra provides the mathematical framework for describing quantum states, quantum operations, and quantum measurements.

#### 2. Quantum Bits (Qubits)

Unlike classical bits that are either 0 or 1, quantum bits (qubits) can exist in a **superposition** of both states simultaneously.

##### 2.1 Quantum State Representation

A single qubit state is represented as a vector in a 2-dimensional complex Hilbert space:

**Qubit state: |ψ⟩ = α|0⟩ + β|1⟩**

Where:

- **|0⟩ = [1, 0]** (computational basis state 0)
- **|1⟩ = [0, 1]** (computational basis state 1)
- **α, β ∈ C** are complex amplitudes
- **Normalization condition**: |α|² + |β|² = 1

The probability of measuring state |0⟩ is |α|² and state |1⟩ is |β|².

##### 2.2 Multi-Qubit Systems

For a system of n qubits, the state vector lives in a 2^n-dimensional Hilbert space:

**|ψ⟩ = Σ(i=0 to 2^n-1) c_i|i⟩**

With normalization: Σ(i=0 to 2^n-1) |c_i|² = 1

#### 3. Quantum Gates as Unitary Matrices

Quantum gates are linear operators that evolve quantum states. They are represented by **unitary matrices** - matrices U satisfying:

**U† U = U U† = I**

Where U† is the complex conjugate transpose (adjoint), and I is the identity matrix.

##### Properties of Unitary Operations:

- **Reversibility**: Quantum operations are reversible
- **Determinism**: They are deterministic (unlike measurement)
- **Probability Conservation**: They preserve the normalization of quantum states

#### 4. Common Quantum Gates

##### 4.1 Single-Qubit Gates

###### Pauli Gates

**Pauli-X (NOT gate)**:

```
X = [0  1]
    [1  0]
```

Flips |0⟩ → |1⟩ and |1⟩ → |0⟩

**Pauli-Y**:

```
Y = [0  -i]
    [i   0]
```

**Pauli-Z**:

```
Z = [1   0]
    [0  -1]
```

Applies a phase of -1 to |1⟩

###### Hadamard Gate

```
H = (1/√2) * [1   1]
             [1  -1]
```

Creates superposition: H|0⟩ = (1/√2)(|0⟩ + |1⟩)

###### Phase Gates

**S Gate (Phase gate)**:

```
S = [1  0]
    [0  i]
```

**T Gate**:

```
T = [1    0  ]
    [0  e^(iπ/4)]
```

##### 4.2 Two-Qubit Gates

###### CNOT (Controlled-NOT) Gate

A 4×4 unitary matrix acting on two qubits:

```
CNOT = [1  0  0  0]
       [0  1  0  0]
       [0  0  0  1]
       [0  0  1  0]
```

The CNOT gate flips the target qubit if the control qubit is |1⟩.

###### SWAP Gate

```
SWAP = [1  0  0  0]
       [0  0  1  0]
       [0  1  0  0]
       [0  0  0  1]
```

Exchanges the states of two qubits.

#### 5. Quantum Circuits

A quantum circuit is a sequence of quantum gates applied to qubits in a specific order. Circuit diagrams show:

- **Horizontal lines** represent qubits
- **Boxes** represent quantum gates
- **Reading left to right** shows the temporal order of operations

##### Circuit States Evolution

For a circuit with gates U₁, U₂, ..., U_n applied sequentially to initial state |ψ₀⟩:

**|ψ_f⟩ = U_n · ... · U₂ · U₁ · |ψ₀⟩**

The transformation is computed by matrix multiplication.

#### 6. Bell States (Two-Qubit Entanglement)

Bell states are maximally entangled two-qubit states. They form an orthonormal basis and cannot be factored into individual qubit states.

##### The Four Bell States:

**|Φ⁺⟩ = (1/√2)(|00⟩ + |11⟩)**

**|Φ⁻⟩ = (1/√2)(|00⟩ - |11⟩)**

**|Ψ⁺⟩ = (1/√2)(|01⟩ + |10⟩)**

**|Ψ⁻⟩ = (1/√2)(|01⟩ - |10⟩)**

##### Bell State Preparation (Bell Pair Circuit)

To create the Bell state |Φ⁺⟩:

1. Initialize two qubits to |00⟩
2. Apply Hadamard gate to first qubit: H|00⟩ = (1/√2)(|00⟩ + |10⟩)
3. Apply CNOT gate with first qubit as control: CNOT · H|00⟩ = (1/√2)(|00⟩ + |11⟩) = |Φ⁺⟩

##### Mathematical Representation:

State vector representation:

```
|Φ⁺⟩ = [1/√2]
       [  0 ]
       [  0 ]
       [1/√2]
```

(In basis ordering |00⟩, |01⟩, |10⟩, |11⟩)

#### 7. GHZ State (Three-Qubit Entanglement)

The GHZ state is a three-qubit entangled state with interesting properties.

##### GHZ State Definition:

**|GHZ⟩ = (1/√2)(|000⟩ + |111⟩)**

##### GHZ State Preparation Circuit:

1. Initialize three qubits to |000⟩
2. Apply Hadamard to first qubit: H|000⟩ = (1/√2)(|000⟩ + |100⟩)
3. Apply CNOT (control: qubit 1, target: qubit 2): Creates (1/√2)(|000⟩ + |110⟩)
4. Apply CNOT (control: qubit 1, target: qubit 3): Creates |GHZ⟩ = (1/√2)(|000⟩ + |111⟩)

##### Properties:

- **Three-qubit correlations**: Measuring all three qubits always gives either all 0s or all 1s
- **Perfect correlations**: GHZ state demonstrates perfect multi-partite correlation
- **Basis ordering**: |000⟩, |001⟩, |010⟩, |011⟩, |100⟩, |101⟩, |110⟩, |111⟩

#### 8. Quantum State Measurement

Measurement collapses a quantum state to a classical outcome according to the Born rule.

##### Born Rule:

For a state |ψ⟩ = Σ_i c_i|i⟩ measured in the computational basis:

- **Probability** of obtaining outcome i: P(i) = |c_i|²
- **State collapse**: Upon measurement of outcome i, state becomes |i⟩

##### State Vector Visualization:

For a qubit state |ψ⟩ = α|0⟩ + β|1⟩:

- Plot amplitudes α and β as complex numbers
- Magnitude represents amplitude strength
- Phase represents phase relationship

##### Measurement Outcomes:

For Bell state |Φ⁺⟩ = (1/√2)(|00⟩ + |11⟩):

- Probability of measuring |00⟩: |(1/√2)|² = 0.5 or 50%
- Probability of measuring |11⟩: |(1/√2)|² = 0.5 or 50%
- Probability of measuring |01⟩ or |10⟩: 0%

#### 9. Matrix Decomposition of Quantum Gates

Complex quantum gates can be decomposed into simpler, fundamental gates. This is important for implementation on real quantum hardware.

##### 9.1 Universal Gate Sets

A set of quantum gates is **universal** if any quantum operation can be approximated arbitrarily closely using only gates from this set.

Common universal gate sets include:

- **{H, S, CNOT}**: Hadamard, Phase, CNOT
- **{T, H, CNOT}**: T-gate, Hadamard, CNOT
- **{X, Y, Z, CNOT}**: All Pauli + CNOT

##### 9.2 Basis Decomposition Example

Any single-qubit unitary can be decomposed as:

```
U = e^(iα) * [e^(-iβ/2)cos(γ/2)   -e^(-iδ/2)sin(γ/2)]
             [e^(iδ/2)sin(γ/2)    e^(iβ/2)cos(γ/2)]
```

This is known as the **Euler decomposition** for single-qubit rotations.

##### 9.3 Circuit Optimization

Gate decomposition allows:

- **Hardware mapping**: Expressing gates in terms of available hardware gates
- **Circuit depth reduction**: Minimizing circuit length
- **Error mitigation**: Using noise-resilient gate sequences

#### 10. Quantum Circuit Simulation

##### 10.1 State Vector Simulation

In this simulation, we track the full quantum state vector through each gate application:

1. **Initialize**: State vector for n qubits is length 2^n
2. **Apply gates**: Multiply by unitary matrix of each gate
3. **Normalize**: Ensure state remains normalized after operations
4. **Measure**: Sample from probability distribution |c_i|² for each basis state

##### 10.3 Single Qubit Rotation Gates

General rotations around axis **n̂** = (n_x, n_y, n_z) by angle θ:

**R_n̂(θ) = cos(θ/2)I - i·sin(θ/2)(n_x·X + n_y·Y + n_z·Z)**

##### 10.4 Bloch Sphere Representation

For visualizing single-qubit states:

- **Point on sphere** represents qubit state
- **North pole** (↑) represents |0⟩
- **South pole** (↓) represents |1⟩
- **Equator** represents equal superposition states

#### 11. Practical Applications

##### 11.1 Quantum Superposition

Bell states demonstrate:

- **Entanglement**: Qubits correlated in a way impossible classically
- **Non-locality**: Measurement on one qubit affects the other
- **Quantum teleportation**: Transmit unknown quantum state using Bell pairs

##### 11.2 Quantum Algorithms

These gate operations form the basis of quantum algorithms:

- **Deutsch-Jozsa Algorithm**: Uses superposition and phase kickback
- **Grover's Search**: Uses amplitude amplification via controlled gates
- **Shor's Algorithm**: Factoring using quantum phase estimation
