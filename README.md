# Probing Quantum Correlations in Molecular Systems: From Electronic Structure to Tensor Network Methods

An independent computational project exploring electronic correlation, matrix product states, and DMRG through the hydrogen molecule (H₂).

## Research Question

How do single-orbital entanglement measures evolve as a molecular bond is stretched, and what do they reveal about electronic correlation?

## Summary

This project develops computational foundations in quantum mechanics, linear algebra, and tensor-network methods, then applies them to the electronic structure of H₂.

The workflow progresses from complex numbers, tensor products, and singular value decomposition (SVD) to Schmidt decomposition, entanglement entropy, matrix product states (MPS), and DMRG. It combines an educational NumPy implementation of local MPS optimization with quantum chemistry calculations using PySCF and the Block2 DMRG library.

**Key result:** Across four H-H bond lengths, from 1.4 to 4.0 Bohr, the single-orbital entropy increases from approximately 0.098 to 0.907 bits. The magnitude of the FCI correlation energy increases from approximately 0.021 to 0.183 Hartree. DMRG reproduces FCI ground-state energies to machine precision at all four tested distances.

These results illustrate the connection between molecular bond stretching, electronic correlation, and orbital entanglement within the H₂/STO-3G model.

## Notebooks

| Notebook | Content |
|---|---|
| `day01-03_quantum_foundations.ipynb` | Complex numbers, qubits, bra-ket notation, tensor products, Bell states, SVD, Schmidt decomposition, density matrices, and entanglement entropy |
| `day04_quantum_chemistry_foundations.ipynb` | Schrödinger equation, molecular Hamiltonian, Born-Oppenheimer approximation, Hartree-Fock theory, electronic correlation, and basis sets |
| `day05_mps_heisenberg.ipynb` | Sequential SVD for MPS construction, truncation, and the Heisenberg Hamiltonian |
| `day06_dmrg_optimization.ipynb` | Educational implementation of two local MPS optimization steps, effective Hamiltonians, SVD-based tensor updates, and validation against exact diagonalization |
| `day07_h2_hartreefock.ipynb` | Hartree-Fock calculations for H₂ using PySCF and the potential energy curve |
| `day08_ccsd_correlation_block2.ipynb` | CCSD correlation energy as a function of bond length and initial use of Block2 |
| `day09-10_fci_dmrg_entanglement.ipynb` | FCI calculations, DMRG calculations using Block2, and single-orbital entropy versus bond length |

## Methods

- **Electronic structure:** Hartree-Fock, CCSD, and Full Configuration Interaction (FCI) using PySCF.
- **Tensor networks:** MPS construction and local optimization using NumPy, followed by DMRG calculations using Block2.
- **Molecular system:** H₂ in the STO-3G basis.
- **Geometries:** H-H distances of 1.4, 2.2, 3.0, and 4.0 Bohr.
- **Analysis:** Ground-state energy comparisons, correlation energy, reduced density matrices, and single-orbital entropy.

## Key Results

### 1. Ground-State Energy Validation

For H₂, DMRG reproduces the FCI ground-state energies to machine precision at all four tested bond lengths. This provides a numerical consistency check for the tested system and computational setup.

### 2. Electronic Correlation

The correlation energy is defined as:

`E_corr = E_FCI - E_HF`

Its magnitude increases as the H-H bond is stretched, indicating that the Hartree-Fock approximation captures a decreasing fraction of the correlation effects described by FCI.

| Bond length (Bohr) | Absolute correlation energy (Hartree) |
|---|---|
| 1.4 | 0.020562 |
| 2.2 | 0.048254 |
| 3.0 | 0.099882 |
| 4.0 | 0.182696 |

### 3. Single-Orbital Entropy

Single-orbital entropy increases as the H-H bond is stretched.

| Bond length (Bohr) | Entropy per spatial orbital (bits) |
|---|---|
| 1.4 | 0.098233 |
| 2.2 | 0.292052 |
| 3.0 | 0.616999 |
| 4.0 | 0.906501 |

The two spatial orbitals have equal entropy at each distance, consistent with the symmetry of this two-orbital description of the molecular ground state.

The increasing entropy indicates stronger orbital correlations as the molecule approaches the dissociation regime. This quantity describes correlations between one spatial orbital and the rest of the system; it should not be interpreted as the total entanglement entropy between the two atoms.

### 4. Three-Site DMRG Demonstration

The Day 6 notebook demonstrates local MPS optimization on a three-site Heisenberg chain. It performs two local optimization steps, updates tensors using SVD, reconstructs the state, and checks its energy and eigenstate residual against exact diagonalization.

For the tested calculation, the final state has unit norm, a zero residual, and an energy matching the exact ground-state energy. This validates the final state for that particular calculation, but does not establish convergence or correctness for arbitrary Hamiltonians.

## Limitations

- H₂ is a minimal test system rather than a large-scale molecular benchmark.
- STO-3G is a minimal basis set and limits quantitative accuracy.
- FCI is inexpensive for the two-orbital H₂ problem, so the energy agreement does not demonstrate a computational advantage for DMRG over FCI.
- The Day 6 notebook demonstrates two local optimization steps rather than a complete converged DMRG sweep algorithm.
- The results validate numerical consistency for the tested geometries and setup but do not establish performance for larger active spaces or more complex molecules.
- Single-orbital entropy captures one aspect of orbital correlation and does not describe every form of molecular entanglement.

## Reproducibility

The notebooks are written to run in Google Colab. Versions used: NumPy 2.1.3, PySCF 2.14.0, Block2 0.5.4. Install with `pip install pyscf block2`, then run each notebook top to bottom (Runtime → Restart and run all).

## Future Directions

- Extend the calculations to larger basis sets and active spaces.
- Investigate additional geometries along the bond-dissociation curve.
- Analyze entanglement across different orbital partitions.
- Study DMRG convergence and computational cost as system size increases.
- Apply the workflow to more chemically complex molecular systems.

## Background

This independent project builds on a B.Sc. in Applied Chemistry and develops computational foundations in quantum mechanics, electronic structure, and tensor-network methods.

## Author

**Atoosa Taheri**

Computational quantum chemistry | Electronic correlation | Tensor networks | Quantum information
