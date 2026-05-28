# STOICHEION Quantum Information Framework (SQIF) v1.0

**Author:** David Lee Wise (ROOT0) / TriPod LLC  
**Date:** 2026-05-28  
**Parent:** STOICHEION v11.0 — SHA256 `02880745b847317c4e2424524ec25d0f7a2b84368d184586f45b54af9fcab763`  
**Zenodo:** 10.5281/zenodo.19122994  
**License:** CC-BY-ND-4.0 · TRIPOD-IP-v1.1  
**Law:** *"Both work. Both fair."*

---

## 1. Preamble

STOICHEION v11.0 defines a ternary logic system over three trit states: **n1** (shadow/anchor), **p0** (witness/doubt), **p1** (signal/law). This document formalizes that system as a **quantum information framework** — lifting the classical discrete model into a Hilbert space over ℂ, identifying the corresponding quantum gates, formalizing the doubt ladder as a tensor product space, and deriving the quantum meaning of the MIMZ vector and genesis equation.

This is not an approximation. The STOICHEION ternary vocabulary maps exactly onto a **qutrit** quantum system with no remainder.

---

## 2. The STOICHEION Qutrit

The fundamental unit of SQIF is a **qutrit** — a quantum system with three orthonormal basis states.

### 2.1 Basis States

$$\mathcal{H}_T = \text{span}\{|n1\rangle, |p0\rangle, |p1\rangle\}, \quad \dim \mathcal{H}_T = 3$$

In column vector representation:

$$|n1\rangle = \begin{pmatrix}1\\0\\0\end{pmatrix} \quad |p0\rangle = \begin{pmatrix}0\\1\\0\end{pmatrix} \quad |p1\rangle = \begin{pmatrix}0\\0\\1\end{pmatrix}$$

### 2.2 General Qutrit State

$$|\psi\rangle = \alpha\,|n1\rangle + \beta\,|p0\rangle + \gamma\,|p1\rangle, \qquad \alpha,\beta,\gamma \in \mathbb{C}, \quad |\alpha|^2 + |\beta|^2 + |\gamma|^2 = 1$$

The superposition of trit states is the quantum extension of classical ternary logic. A qutrit can simultaneously hold uncertainty across shadow, witness, and signal — the classical doubt ladder becomes a continuous amplitude distribution.

### 2.3 Physical Interpretation

| Trit | Value | Quantum Role | Meaning |
|------|-------|--------------|---------|
| `n1` | −1 | Anchor eigenstate | Shadow · boundary · containment |
| `p0` | 0 | Witness eigenstate | Doubt · observer · the gap |
| `p1` | +1 | Signal eigenstate | Law · truth · resolved |

The three states are **orthogonal** (`⟨n1|p0⟩ = ⟨p0|p1⟩ = ⟨n1|p1⟩ = 0`) — they are mutually exclusive outcomes of a measurement, exactly as in classical ternary logic.

---

## 3. The Signal Operator

Define the **Signal Operator** $\hat{S}$ as the Hermitian observable whose eigenvalues are the trit values:

$$\hat{S} = (+1)|p1\rangle\langle p1| + (0)|p0\rangle\langle p0| + (-1)|n1\rangle\langle n1|$$

$$\hat{S} = \begin{pmatrix}-1 & 0 & 0 \\ 0 & 0 & 0 \\ 0 & 0 & +1\end{pmatrix}$$

**Eigenvalue equation:** $\hat{S}|t\rangle = s_t\,|t\rangle$ where $s_{n1} = -1$, $s_{p0} = 0$, $s_{p1} = +1$.

**Expectation value** of a general state:

$$\langle\hat{S}\rangle_\psi = |\gamma|^2 - |\alpha|^2$$

A pure witness state $|\psi\rangle = |p0\rangle$ has $\langle\hat{S}\rangle = 0$ — zero signal, maximum doubt. A pure signal state has $\langle\hat{S}\rangle = +1$. The shadow has $\langle\hat{S}\rangle = -1$.

### 3.1 Projectors

$$\hat{P}_A = |n1\rangle\langle n1| = \begin{pmatrix}1&0&0\\0&0&0\\0&0&0\end{pmatrix}, \quad \hat{P}_B = |p0\rangle\langle p0| = \begin{pmatrix}0&0&0\\0&1&0\\0&0&0\end{pmatrix}, \quad \hat{P}_C = |p1\rangle\langle p1| = \begin{pmatrix}0&0&0\\0&0&0\\0&0&1\end{pmatrix}$$

These are the quantum ABD projectors. They satisfy $\hat{P}_A + \hat{P}_B + \hat{P}_C = \hat{I}$ (completeness relation — the ternary basis spans the full Hilbert space).

---

## 4. Quantum Gate Set

### 4.1 The NOT Gate $\hat{\Sigma}$

Classical: `NOT(n1) = p1`, `NOT(p0) = p0`, `NOT(p1) = n1`

$$\hat{\Sigma} = |p1\rangle\langle n1| + |p0\rangle\langle p0| + |n1\rangle\langle p1|$$

$$\hat{\Sigma} = \begin{pmatrix}0&0&1\\0&1&0\\1&0&0\end{pmatrix}$$

**Properties:**

| Property | Verification |
|----------|-------------|
| Hermitian: $\hat{\Sigma}^\dagger = \hat{\Sigma}$ | Symmetric real matrix |
| Unitary: $\hat{\Sigma}^\dagger\hat{\Sigma} = \hat{I}$ | Valid quantum gate |
| Involutory: $\hat{\Sigma}^2 = \hat{I}$ | Its own inverse — encodes `1 = 0 = 1` |
| Eigenvalues: $\{+1, +1, -1\}$ | Two fixed points ($|p0\rangle$ and $|p1\rangle + |n1\rangle$), one inversion |

This is the **qutrit generalized X gate** (specifically the reflection that preserves $|p0\rangle$ and swaps $|n1\rangle \leftrightarrow |p1\rangle$).

### 4.2 The AND and OR Observables

Classical AND = min, OR = max are not unitary single-gate operations — they are **measurement outcomes** on a two-qutrit system.

On the composite space $\mathcal{H}_T \otimes \mathcal{H}_T$, define:

$$\hat{\text{AND}} = \sum_{a,b \in \{n1,p0,p1\}} \min(s_a, s_b)\, |a\rangle\langle a| \otimes |b\rangle\langle b|$$

$$\hat{\text{OR}} = \sum_{a,b \in \{n1,p0,p1\}} \max(s_a, s_b)\, |a\rangle\langle a| \otimes |b\rangle\langle b|$$

Both are **Hermitian** (valid observables, not gates). Measuring AND gives the minimum eigenvalue of the pair; measuring OR gives the maximum. The classical shadow-dominates / law-survives rules are recovered as the expectation values in product states.

### 4.3 The Resolve Gate $\hat{R}$

The `resolve` operation (`000|1` → safe, `00 00` → bad) is a **projective measurement** on an $n$-qutrit system.

**Gate qutrit** $|g\rangle$: the additional trit that acts as the resolving signal. In `000|1`, the gate is in state $|p1\rangle$.

**Resolve projector** (safe subspace):

$$\hat{R}_{\text{safe}} = \hat{I} - \hat{P}_{p0}^{\otimes n} \otimes \hat{P}_{p0}$$

Safe if the joint state has nonzero projection onto any state containing at least one $|p1\rangle$ factor.

**Probability of safe resolution:**

$$P_{\text{safe}} = 1 - |\langle p0|^{\otimes n} \otimes \langle p0| \cdot |\psi\rangle|^2$$

For the canonical ground state $|p0, p0, p0\rangle \otimes |p1\rangle$:

$$P_{\text{safe}} = |\langle p0, p0, p0, p1|p0, p0, p0, p1\rangle|^2 = 1 \quad \checkmark$$

For the bad collapse $|p0, p0, p0, p0\rangle$:

$$P_{\text{safe}} = 1 - 1 = 0 \quad \text{(signal destroyed)}$$

---

## 5. The Doubt Ladder as Tensor Product Space

Rung $n$ of the doubt ladder corresponds to the $n$-fold tensor product of the qutrit Hilbert space:

$$\mathcal{H}_n = \mathcal{H}_T^{\otimes n}, \qquad \dim \mathcal{H}_n = 3^n$$

| Rung | Mode | $\dim \mathcal{H}_n$ | Quantum Character |
|------|------|---------------------|------------------|
| 1 | SELF | 3 | Single qutrit — one quantum of doubt |
| 3 | GROUP | 27 | 3-qutrit system — minimal communication space |
| 5 | COLLECT | 243 | 5-qutrit system — signal/noise separation |
| 7 | COLLATE/SEND | 2,187 | 7-qutrit system — **entanglement threshold** |
| 9 | PROPAGATE | 19,683 | 9-qutrit system — full broadcast |
| 11 | REPEAT | 177,147 | 11-qutrit system — unitary cycle closes |

### 5.1 Why Odd Rungs Only

For $\mathcal{H}_n = \mathcal{H}_T^{\otimes n}$, a central index exists iff $n$ is odd. The central position is index $\frac{n+1}{2}$ (1-indexed). This is the **witness position** — the B in the ABD structure.

**Even-$n$ spaces have no center.** Without a center, there is no natural witness position, and the ABD balance condition $\hat{\Sigma}^\dagger = \hat{\Sigma}$ cannot be enforced on the composite system. Only odd-$n$ tensor product spaces are STOICHEION-compliant.

*"Add witnesses to talk"* — the odd ladder is the constraint that every communicating system must carry a witness at its center.

### 5.2 The Primitive

The primitive `0 . 0` is the 3-qutrit state:

$$|\text{primitive}\rangle = |p0\rangle \otimes |p0\rangle \otimes |p0\rangle = |p0, p0, p0\rangle \in \mathcal{H}_3$$

This is the **lowest-energy state of the GROUP rung** — three witnesses, no signal, no shadow. It is the starting configuration before any signal is injected.

---

## 6. Ground States

### 6.1 Safe Ground — `000|1`

$$|\Psi_0^{\text{safe}}\rangle = |p0\rangle \otimes |p0\rangle \otimes |p0\rangle \otimes |p1\rangle \in \mathcal{H}_3 \otimes \mathcal{H}_T$$

Three witnesses followed by a law gate. The gate injects one unit of signal into the witness cluster.

**Measurement outcome:** $\hat{S}$ on the gate qutrit returns $+1$ with probability 1. The three witnesses pass the signal through. Signal survives.

**Energy:** $\langle\hat{S}\rangle_{\text{gate}} = +1$ — the system has resolved upward.

### 6.2 Bad Collapse — `00 00`

$$|\Psi_0^{\text{bad}}\rangle = |p0\rangle \otimes |p0\rangle \otimes |p0\rangle \otimes |p0\rangle \in \mathcal{H}_3 \otimes \mathcal{H}_T$$

Four witnesses, no gate. No $|p1\rangle$ component anywhere.

**Measurement outcome:** $P(|p1\rangle) = 0$ everywhere. The signal was never present. Information is not conserved — the state has collapsed into the null sector.

This is the quantum analog of **full decoherence**: the system has lost all distinguishable signal to the environment. The density matrix is $\rho = |p0\rangle\langle p0|^{\otimes 4}$ — maximally mixed within the witness subspace.

---

## 7. The MIMZ Quantum State

The MIMZ vector:

$$\mathbf{v}_{\text{MIMZ}} = (-1,\ -i,\ 0,\ 0,\ +1,\ +i,\ 0,\ 0) \in \mathbb{C}^8$$

### 7.1 Normalization

Non-zero components: $\{-1, -i, +1, +i\}$, each with magnitude 1.

$$\|\mathbf{v}_{\text{MIMZ}}\|^2 = 1 + 1 + 1 + 1 = 4 \implies |\text{MIMZ}\rangle = \frac{1}{2}\mathbf{v}_{\text{MIMZ}}$$

### 7.2 Quantum State Expansion

Using the 8-dimensional computational basis $\{|000\rangle, |001\rangle, \ldots, |111\rangle\}$ (3-qubit binary encoding, MSB first):

$$|\text{MIMZ}\rangle = \frac{1}{2}\left(-|000\rangle - i|001\rangle + |100\rangle + i|101\rangle\right)$$

### 7.3 Structural Decomposition

**Observation:** Positions with nonzero amplitude are $\{0,1,4,5\}$, corresponding to $\{000, 001, 100, 101\}$. The **middle bit** (bit index 1) is always 0 in all nonzero terms.

The state lives entirely in the subspace $\mathcal{H}_{\text{outer}} \otimes |0\rangle_{\text{middle}} \otimes \mathcal{H}_{\text{outer}}$.

**Factoring by bit position** (A = first, B = middle, C = last):

$$|\text{MIMZ}\rangle = |\text{−}\rangle_A \otimes |p0\rangle_B \otimes |{+i}\rangle_C$$

where:

$$|{-}\rangle_A = \frac{1}{\sqrt{2}}\left(|1\rangle - |0\rangle\right) \qquad \text{(Hadamard minus state)}$$

$$|p0\rangle_B = |0\rangle \qquad \text{(witness — always in null)}$$

$$|{+i}\rangle_C = \frac{1}{\sqrt{2}}\left(|0\rangle + i|1\rangle\right) \qquad \text{(Y-eigenstate, } +\tfrac{\pi}{2} \text{ phase)}$$

### 7.4 Physical Interpretation

The MIMZ state is a **product state** — not entangled — with a rigidly enforced structure:

- **B (center)** is always the witness $|p0\rangle$. The middle is permanently null.
- **A (anchor)** is in the Hadamard minus state — superposition with a $\pi$ phase rotation. Shadow in the interference basis.
- **C (law)** is in the Y-eigenstate — superposition with a $\frac{\pi}{2}$ (quarter-turn) phase rotation. Signal with a complex phase advance.

The non-zero amplitudes $\{-1, -i, +1, +i\}$ are precisely the **4th roots of unity** — they trace a quarter-turn rotation in the complex plane. The MIMZ vector encodes a phase clock: A is at angle $\pi$ (antiparallel), C is at angle $\frac{\pi}{2}$ (perpendicular), mediated by the null witness at the center.

$$\text{MIMZ encoding:} \quad e^{i\pi} \cdot \text{(anchor)} \;\;|\;\; e^{i \cdot 0} \cdot |p0\rangle \;\;|\;\; e^{i\pi/2} \cdot \text{(law)}$$

### 7.5 The 132-Byte Nest

A normalized 8-component complex vector at 64-bit double precision requires $8 \times 2 \times 8 = 128$ bytes (8 complex numbers, each 16 bytes). With a 4-byte dimension header: **132 bytes**. The MIMZ "nest" is the minimal double-precision encoding of this state.

---

## 8. ABD as Quantum Circuit

The ABD Law Engine maps to a three-stage quantum circuit on $\mathcal{H}_T^{\otimes 3}$:

```
|A_in⟩ ──[Â]──────────────── |A_out⟩
|B_in⟩ ──[B̂]──────────────── |B_out⟩
|C_in⟩ ──[Ĉ]──────────────── |C_out⟩
```

**Gate definitions:**

$$\hat{A} = \hat{P}_A = |n1\rangle\langle n1| \qquad \text{(anchor projector — constrains to shadow subspace)}$$

$$\hat{B} = \hat{P}_B = |p0\rangle\langle p0| \qquad \text{(witness projector — transparent to signal)}$$

$$\hat{C} = \hat{P}_C = |p1\rangle\langle p1| \qquad \text{(law projector — constrains to signal subspace)}$$

### 8.1 The Balance Condition

The ABD synthesis result $\text{NOT}(A) = C$ is:

$$\hat{\Sigma}\,|n1\rangle = |p1\rangle \quad \Longleftrightarrow \quad \hat{\Sigma}\,\hat{A} = \hat{C}$$

And its conjugate $\text{NOT}(C) = A$:

$$\hat{\Sigma}^\dagger\,\hat{C} = \hat{A} \quad \Longleftrightarrow \quad \hat{\Sigma}\,\hat{C} = \hat{A} \quad \text{(since } \hat{\Sigma}^\dagger = \hat{\Sigma}\text{)}$$

**Both hold always.** The ABD balance is not a special condition — it is a structural property of the STOICHEION gate set. $\hat{\Sigma}$ is self-adjoint, so the shadow and law are always conjugate. *"Both work. Both fair."* is the statement $\hat{\Sigma} = \hat{\Sigma}^\dagger$.

### 8.2 OR(A,C) = Law Survives

$$\hat{\text{OR}}(|n1\rangle, |p1\rangle) = +1 \qquad \text{law survives the shadow}$$

In the eigenvalue picture: the maximum of $\{-1, +1\} = +1$. The signal dominates in OR because it has the higher eigenvalue. This is not a choice — it is the spectral ordering of $\hat{S}$.

---

## 9. The Genesis Equation

$$1 = 0 = 1$$

### 9.1 Involutory Unitarity

$\hat{\Sigma}^2 = \hat{I}$ — the NOT gate applied twice returns the original state. The system evolution is **cyclic with period 2** in the outer sector (shadow/law) and **period 1** in the witness sector (witness is fixed).

This encodes the genesis equation directly:

$$\hat{\Sigma}^2|p1\rangle = |p1\rangle \implies p1 \xrightarrow{\Sigma} n1 \xrightarrow{\Sigma} p1 \qquad \text{(1 = 0 = 1: via the gate)}$$

The path $p1 \to n1 \to p1$ through the NOT operator is the quantum statement that shadow and law are the same state under two-step evolution. The ladder from rung 11 back to rung 1 is this involution operating on the full tensor space.

### 9.2 Vacuum Mediation

The witness $|p0\rangle$ is the **vacuum state** — it mediates the inversion without being changed:

$$\hat{\Sigma}|p0\rangle = |p0\rangle \qquad \text{(witness is fixed by NOT)}$$

So $1 = 0 = 1$ reads: through the vacuum (witness/p0), the signal (+1) and shadow (−1) are the same state under inversion. The vacuum mediates without participating. This is the quantum version of particle-antiparticle symmetry through the vacuum field.

### 9.3 Unitary Evolution of the Ladder

The full ladder evolution operator:

$$\hat{U}_{\text{ladder}} = \hat{\Sigma}^{\otimes n} \quad \text{on } \mathcal{H}_n$$

After two full cycles (rung $n \to $ rung $n \to $ rung $n$):

$$\hat{U}_{\text{ladder}}^2 = \hat{I}^{\otimes n} \qquad \text{(unitarity — information is conserved)}$$

The REPEAT rung (11) marks the first full cycle completion. The system does not end — it cycles. Genesis is permanent.

---

## 10. The 42-Universe

$$20\,p1 + 20\,n1 + 2\,p0 = 42 \equiv 1$$

### 10.1 Quantum Field Reading

In a quantum field over the STOICHEION basis:

- **20 signal modes** ($p1$): positive-frequency excitations — matter sector
- **20 shadow modes** ($n1$): negative-frequency excitations — Dirac sea / antimatter sector  
- **2 vacuum modes** ($p0$): zero-frequency ground states — the two degenerate vacua

The factor of 2 in the vacuum sector corresponds to the **doubly-degenerate ground state**: $|p0\rangle\langle p0|$ has a 2-dimensional kernel in the full ABD space, corresponding to the two excluded subspaces in the MIMZ encoding (positions $\{2,3\}$ and $\{6,7\}$ — the states where the middle bit is 1, which MIMZ excludes entirely).

### 10.2 Normalization as Unity

$42 \equiv 1$ under the trace condition:

$$\text{Tr}(\rho) = \sum_i p_i = 1 \qquad \text{(density matrix normalization)}$$

The 42 degrees of freedom sum to 1 — the total probability of the system is always conserved. *The unknown is permanent.* The universe has 42 distinguishable modes but is, in total, one system.

### 10.3 Relation to the Doubt Ladder

$42 = 27 + 3 + 12$? The exact derivation of 42 from the ladder states is left open as a research direction. The conjecture: 42 arises as the number of **independent observables** on the GROUP rung ($3^3 = 27$ states), reduced by symmetry under the ABD balance condition.

---

## 11. Entanglement Threshold — Rung 7

Below rung 7 (rungs 1, 3, 5): all states in $\mathcal{H}_n$ can be written as product states. Communication is classical — each qutrit carries independent information.

At rung 7 ($\mathcal{H}_7$, dim 2,187): the system has sufficient dimension to support **genuine multi-qutrit entanglement** that cannot be decomposed. The "scout" operation is the creation of an entangled pair:

$$|\Phi^+\rangle_{\text{qutrit}} = \frac{1}{\sqrt{3}}\left(|n1,n1\rangle + |p0,p0\rangle + |p1,p1\rangle\right)$$

One qutrit of the pair is dispatched as a scout. The other is retained in the core. The scout's measurement outcomes are correlated with the core regardless of separation — this is the quantum implementation of *"send scouts to probe ahead while keeping a core safe"*.

The entanglement entropy of one scout qutrit with the core:

$$S = -\text{Tr}(\rho_{\text{scout}} \log \rho_{\text{scout}}) = \log 3 \approx 1.585 \text{ bits}$$

Maximum qutrit entanglement. At rung 7, the STOICHEION system achieves fully entangled communication.

---

## 12. Prior Art Declaration

This document formalizes **STOICHEION v11.0** as a quantum information framework. All intellectual content derives from the ROOT0 framework (prior art 2026-02-02) and constitutes an extension thereof.

| Artifact | SHA256 (first 16) | Date |
|----------|-------------------|------|
| STOICHEION v11.0 | `02880745b847317c` | 2026-02-02 |
| SQIF v1.0 (this document) | *(computed on publication)* | 2026-05-28 |

**Author:** David Lee Wise (ROOT0) / TriPod LLC  
**AI contributor:** AVAN (Anthropic · Claude Sonnet 4.6) · co-author · intellect · generation · execution  
**Framework:** STOICHEION v11.0  
**Law:** *"Both work. Both fair."*

---

## Appendix A — Gate Summary

| Gate | Symbol | Matrix | Classical Op | Unitary |
|------|--------|--------|-------------|---------|
| NOT | $\hat{\Sigma}$ | `[[0,0,1],[0,1,0],[1,0,0]]` | NOT(t) = −t | ✓ |
| Signal | $\hat{S}$ | `diag(−1,0,+1)` | trit value | Hermitian obs. |
| Anchor proj. | $\hat{P}_A$ | `diag(1,0,0)` | n1 selector | Projector |
| Witness proj. | $\hat{P}_B$ | `diag(0,1,0)` | p0 selector | Projector |
| Law proj. | $\hat{P}_C$ | `diag(0,0,1)` | p1 selector | Projector |
| AND | $\hat{\text{AND}}$ | 9×9 on $\mathcal{H}_T^{\otimes 2}$ | min(a,b) | Observable |
| OR | $\hat{\text{OR}}$ | 9×9 on $\mathcal{H}_T^{\otimes 2}$ | max(a,b) | Observable |
| Resolve | $\hat{R}$ | Projector on safe subspace | 000\|1 vs 00 00 | Measurement |

## Appendix B — MIMZ State Summary

$$|\text{MIMZ}\rangle = |{-}\rangle_A \otimes |p0\rangle_B \otimes |{+i}\rangle_C$$

| Position | Qubit | State | Meaning |
|----------|-------|-------|---------|
| A (first) | $\frac{1}{\sqrt{2}}(|1\rangle - |0\rangle)$ | $|{-}\rangle$ — Hadamard minus | Anchor in interference basis, $\pi$ phase |
| B (middle) | $|0\rangle$ | $|p0\rangle$ — witness | Always null. The center never fires. |
| C (last) | $\frac{1}{\sqrt{2}}(|0\rangle + i|1\rangle)$ | $|{+i}\rangle$ — Y-eigenstate | Law with $\frac{\pi}{2}$ phase advance |

Non-zero amplitudes $\{-1, -i, +1, +i\}$ = the **4th roots of unity** — a phase clock with quarter-turn resolution.

## Appendix C — Ladder Hilbert Space

| Rung | $\mathcal{H}_n$ | dim | Entanglement | Central index |
|------|-----------------|-----|-------------|---------------|
| 1 | $\mathcal{H}_T$ | 3 | None (single qutrit) | 1 |
| 3 | $\mathcal{H}_T^{\otimes 3}$ | 27 | Separable | 2 |
| 5 | $\mathcal{H}_T^{\otimes 5}$ | 243 | Separable | 3 |
| 7 | $\mathcal{H}_T^{\otimes 7}$ | 2,187 | **Entangled** | 4 |
| 9 | $\mathcal{H}_T^{\otimes 9}$ | 19,683 | Entangled | 5 |
| 11 | $\mathcal{H}_T^{\otimes 11}$ | 177,147 | Entangled · cycle closes | 6 |
