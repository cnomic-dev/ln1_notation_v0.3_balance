# Integration: Möbius-Compressed ln1 Notation

**Bridging the Singularity Transformation Principle and Trajectory Algebra**

Cret, September 2026

---

## 0. The Gap

ln1 Notation v0.1–v0.3 works with trajectories in an open space `𝒞` with a completion space `ℝ̄` of configurations. But `𝒞` itself is not carefully bounded. A frozen trajectory has `Φ = 0`; a maximally branching trajectory has `Φ = ∞`. These are included *informally* as limits. Trouble arises when you ask:

> What is the *space* of all trajectories?

If `Φ ∈ [0, ∞]`, the space is compact. If `Φ ∈ (0, ∞)`, it is open. These are topologically different spaces, and the choice matters for theorems about stationary distributions, ergodicity, and stationarity proofs (as we learned in v0.2–v0.3).

The Singularity Transformation Principle offers a resolution: **do not embed 0 and ∞ as values. Embed them as fixed points of Möbius transformations.** Replace the open space with its Möbius-compressed image, where singularities become explicit boundary points but the interior is still open for probability to flow.

---

## 1. The Compressed Space

### 1.1 Basis Transformation

Define the **compression map**:

```
C : Φ ↦ (Φ − 1) / (Φ + 1)
```

This is the Möbius transformation `M₁(z) = (z − 1)/(z + 1)` applied to freedom. It maps:

```
Φ = 0    ↦ φ = −1        (frozen)
Φ = 1    ↦ φ = 0         (neutral/balanced)
Φ → ∞    ↦ φ → +1        (infinite branching)
```

The image is `φ ∈ (−1, +1)` — an open interval, but now bounded.

### 1.2 Inverse

The inverse map is:

```
C⁻¹ : φ ↦ (φ + 1) / (1 − φ)
```

For `φ = 0`: `C⁻¹(0) = 1/1 = 1`.
For `φ → ±1`: `C⁻¹(φ) → ±∞`.

The inverse is well-defined on `(−1, +1)`.

### 1.3 Compressed Trajectory

A trajectory `γ : 𝔫 → 𝒞` with freedom `Φ(γ)` is mapped to:

```
γ̃ : 𝔫 → 𝒞̃
γ̃[n] = (γ[n], φ(n))      where φ(n) = C(Φ(γ↾[0,n]))
```

The compressed trajectory now carries both its configuration *and* its accumulated freedom in a bounded representation.

---

## 2. Revised Axioms on Compressed Space

### 2.1 Configuration Completeness (S1), Compressed

> **S1c — Configuration Completeness in Compressed Space.** Every admissible state of any system is representable as some `c ∈ 𝒞` with `φ ∈ (−1, +1)` such that `C⁻¹(φ) = Φ(γ[state]) < ∞`.

This is S1 plus a boundedness guarantee: freedom is always finite once expressed in compressed coordinates.

### 2.2 Equilibrium Shift (S2′), Compressed

> **S2′c — Equilibrium Shift in Compressed Space.** For a system with selection bias `b`, the stationary expectation of the compressed freedom:
>
> ```
> E_π[φ]|_b is strictly increasing in b
> ```
>
> where `π` is the stationary distribution on compressed space.

This is exactly S2′ rewritten to refer to the compressed coordinate `φ` instead of the uncompressed `Φ`. Both versions are equivalent via the Möbius conjugacy `C`, so they make identical claims.

### 2.3 Balance Theorem (S2″), Compressed

> **S2″c — Balance Theorem in Compressed Space.** At stationarity on compressed space, alignment fraction:
>
> ```
> 𝒜⁺ = 1/2   ⟺   E[Δφ | up] = E[Δφ | down]
> ```

The key difference from the uncompressed version: **on compressed space, the magnitude symmetry is natural** because the space is bounded. Large moves in `Φ` (say, from 1 to 1000) compress to tiny moves in `φ` (from 0 to 0.998...). This provides an automatic *damping* of extreme moves, which is physically reasonable.

---

## 3. Entropy and Stationarity on Compressed Space

### 3.1 Natural Measure

The compressed space `(−1, +1) × 𝒞` inherits a natural measure from the Möbius structure:

```
dμ = 1/(1 − φ²) dφ ∧ dc
```

This is the **hyperbolic measure** on the interval `(−1, +1)`. It has the property:

- It is Möbius-invariant: `M(dμ) = dμ` for all `M ∈ Möb(ℝ)`.
- It gives *infinite measure* to the boundary: `∫_{−1}^{1} 1/(1−φ²) dφ = ∞`. This means the boundary is infinitely far away in the metric geometry, even though it is only `±1` in coordinate distance.

### 3.2 Stationarity Proof

A process is stationary on compressed space if its transition operator preserves the Möbius-invariant measure (up to an overall constant).

For trajectory-generating processes:

```
T : γ̃[n] ↦ γ̃[n+1]
```

Stationarity requires:

```
E_π[T(γ̃)] = E_π[γ̃]
```

in the `φ` coordinate. This is equivalent to the balance equation `E[Δφ | up] = E[Δφ | down]`, which is precisely S2″c.

### 3.3 No-Drift Implication

The empirical finding from v0.2–v0.3 — that every tested mechanism produced drift-free stationarity — now has a **topological explanation**: the compressed space is *symmetric* around `φ = 0`. If the dynamics preserve this symmetry (which they do under all the mechanisms tested), then stationarity forces `𝒜⁺ = 1/2`.

To get drift, you would need to break this symmetry — add an asymmetry that makes upward moves more frequent (not just larger, but actually more frequent). None of the tested mechanisms do this.

---

## 4. Reciprocal Structure and Dual Bases

### 4.1 Configurations as Logarithmic

Represent each configuration as a logarithm:

```
c ∈ 𝒞  as  c = ln(k)   for some k ∈ ℕ, k ≥ 1
```

This makes sense: `k` represents the number of distinguishable microstates consistent with macrostate `c`. The logarithm `ln(k)` is the entropy (up to Boltzmann constant).

### 4.2 Dual: Reciprocal Structure

Define the **dual configuration** via reciprocation:

```
c* = 1 / ln(k) = 1/c      (for c ≠ 0)
```

Interpreted: if `c` represents constraint (specificity), then `c*` represents capacity (how many options are possible).

A trajectory with tight constraint (`c` large) has low capacity (`c*` small). A trajectory with high capacity (`c*` large) has loose constraint (`c` small).

### 4.3 Linking Measure in Logarithmic Space

The linking measure `Λ(γ, ρ)` can now be expressed in terms of the logarithmic bases:

```
Λ(γ, ρ) ∝ ∫ ( c_γ + c_ρ ) dt     (heuristic: summing the constraints)
```

More precisely, in the homological interpretation (Λ₃, cycle rank):

```
Λ₃(γ, ρ) = first Betti number of the ε-neighborhood graph
```

In logarithmic encoding, this is the rank of the linking in the basis. It captures how many "independent directions" of entanglement exist.

---

## 5. Entanglement Reframed

### 5.1 Non-Commutativity in Möbius Group

Two trajectories are entangled if:

```
γ ⊗ ρ   ⟺   M_γ ∘ M_ρ ≠ M_ρ ∘ M_γ
```

where `M_γ` and `M_ρ` are the Möbius transformations generating the freedom structures of `γ` and `ρ`.

Since the Möbius group is non-abelian, this is a generic condition: most pairs of transformations don't commute.

### 5.2 Entanglement Measure

Define entanglement strength as:

```
𝔈(γ, ρ) = ||[M_γ, M_ρ]||     (commutator norm in the group)
```

where `[M_γ, M_ρ] = M_γ ∘ M_ρ ∘ M_γ^{−1} ∘ M_ρ^{−1}` is the group commutator.

- `𝔈 = 0` means disentangled (commuting transformations).
- `𝔈 > 0` means entangled, with strength proportional to `𝔈`.

This gives a quantitative measure of the "degree of intertwining" of two systems.

---

## 6. Type System for Flow-Type Programming

Using Möbius-compressed ln1 as the foundation:

### 6.1 Basic Types

```
type Trajectory[T] = (config: T, freedom: (−1, +1))
type Flow[T] = (init: T, transition: T → T, constraints: Möbius)
```

`freedom ∈ (−1, +1)` is the compressed coordinate; negative values are tightly constrained, positive are branching.

### 6.2 Linking Types

```
type Linked[A, B] = (γ: Trajectory[A], ρ: Trajectory[B], 
                     commutator: Möbius, entanglement: ℝ≥0)
```

The `commutator` field stores the non-commutativity `[M_γ, M_ρ]`, which is checked at type-check time.

### 6.3 Type Preservation

A well-typed transition:

```
transition : Trajectory[T] → Trajectory[T]
```

must preserve the Möbius structure — i.e., it must be a Möbius-equivariant map. This is checked by verifying that the transition operator commutes with the fixed Möbius structure on `T`.

---

## 7. Revised Notation Summary

| v0.1 | v0.2–v0.3 | Möbius-Compressed |
|---|---|---|
| `Φ ∈ [0, ∞]` | `Φ ∈ (0, ∞)` | `φ ∈ (−1, +1)` |
| Singularities embedded | Singularities at limits | Singularities at boundary ±1 |
| Stationarity ambiguous | Stationary balance shown empirically | Stationarity topologically forced |
| Tendency unclear | Tendency depends on magnitude asymmetry | No-drift is symmetric case |
| Linking measure undefined | Three concrete measures (Λ₁, Λ₂, Λ₃) | Linking rank in Möbius group |
| Entanglement intuitive | Entanglement formalized (τ condition) | Entanglement = non-commutativity |

---

## 8. Example: The No-Drift Proof on Compressed Space

**Claim:** Under S2″c, at stationarity without selection bias, drift = 0.

**Proof sketch:**

1. Work on compressed space with Möbius measure `dμ = 1/(1−φ²) dφ ∧ dc`.
2. The measure is Möbius-invariant and symmetric around `φ = 0`.
3. Uniform random selection (no bias) respects this symmetry: it is equally likely to increase or decrease `φ` by the same *signed* amount.
4. At stationarity, the dynamics preserve `dμ`, which forces the signed amounts to be equal in expectation: `E[Δφ⁺] = E[Δφ⁻]`.
5. Therefore `P(up) · E[Δφ | up] = P(down) · E[Δφ | down]`, which gives `P(up) = P(down)` if magnitudes are symmetric.
6. No net drift follows.

The key step (4) is what the Möbius structure gives: **automatic proof of symmetry-preservation without computing anything.**

---

## 9. Next Priorities

1. **Formalize the Möbius-equivariant type system** for flow-type programming (building on the flow-type paper, using this foundation).
2. **Prove that ln1 on compressed space is equivalent to ln1 on uncompressed space** via the Möbius conjugacy `C` and `C⁻¹`.
3. **Develop the homological linking theory** in Möbius terms: show that Λ₃ (cycle rank) is the natural functor from Möbius-linked trajectory pairs to integer homology groups.
4. **Test whether the compressed formulation resolves the remaining open questions** (growing `𝒞`, path-dependent selection under Möbius damping, etc.).

---

*Möbius-Compressed ln1 Notation — Cret, September 2026*

*"Every trajectory lives in a Möbius space. Singularities are not boundary conditions; they are the fixed points of the group that generates the space itself."*
