# ln1 Notation v0.2 — Addendum

**Λ Defined, S2 Refuted, S2′ Established**

Cret, September 2026

---

## 0. What This Addendum Does

Notation v0.1 §11 listed step 1 as: *"Define `Λ`. Pick one candidate from §9.1, work it through §8's examples, and check whether S2 survives. If it does not, that is a result, not a failure."*

This addendum carries that out. All three candidates were instantiated, not one. The result:

**S2 as stated in v0.1 is false.** Its apparent support was an artifact of the notation, not a fact about the system. A replacement axiom, S2′, was derived and holds under all three definitions.

---

## 1. The Three Λ Definitions, Made Concrete

A test system: `N = 12` trajectories over a cyclic configuration space `𝒞 = ℤ/16`, branching degree `β = 3` at every index. Circular distance `d(a,b) = min(|a−b| mod K, K − |a−b| mod K)`.

### Λ₁ — Kernel (similarity)

```
Λ₁(Γ) = Σ_{i<j} exp( −d(cᵢ, cⱼ) / 2 )
```

Continuous, smooth, no free parameters beyond the decay scale. Closest to an intuitive "how connected is this set."

### Λ₂ — Fiedler value (algebraic connectivity)

```
G_ε = (Γ, { (i,j) : d(cᵢ,cⱼ) ≤ ε })
L   = D − A
Λ₂  = λ₂(L)        the second-smallest eigenvalue
```

Zero exactly when the linking graph is disconnected. This is the standard spectral measure of how hard a network is to sever.

### Λ₃ — Cycle rank (first Betti number)

```
Λ₃ = |E(G_ε)| − |V| + comp(G_ε)      =  β₁(G_ε)
```

The number of independent cycles in the neighbourhood graph. This is the candidate closest to ln1's own topological language: it counts genuine topological structure, not mere adjacency.

All three are computable in polynomial time. All three are defined without reference to ln1's interpretive layer.

---

## 2. S2 Tested

**S2 (v0.1):** `lim_{|γ|→∞} 𝒜(γ) > 1/2`, where `𝒜` is the fraction of selections that do not decrease `Λ*`.

Run under **uniform random selection** — this is the critical condition. If tendency is structural, it must appear without agents seeking it. If it appears only when agents seek it, S2 is circular.

Result, 20,000 steps:

| Λ | 𝒜 (uniform selection) | verdict as stated |
|---|---|---|
| Λ₁ kernel | 0.5356 | S2 holds |
| Λ₂ Fiedler | 0.5861 | S2 holds |
| Λ₃ cycle rank | 0.6195 | S2 holds |

S2 appears confirmed under all three. **It is not.**

---

## 3. Why the Confirmation Is Spurious

Two diagnostics kill it.

### 3.1 Net drift is zero

If `Λ*` genuinely tends upward, it must go up. Measured drift over 20,000 steps:

| Λ | net drift over the whole run |
|---|---|
| Λ₁ | +0.074 (on a range of 27) |
| Λ₂ | +0.0003 (on a range of 6) |
| Λ₃ | −0.061 (on a range of 40) |

All three are stationary. `Λ*` fluctuates around a fixed mean and goes nowhere. **A process can have `𝒜 > 1/2` and zero drift simultaneously.** So `𝒜 > 1/2` does not establish tendency.

### 3.2 The excess is entirely ties

Decomposing each selection into strict increase, tie, and strict decrease (40,000 steps):

| Λ | P(up) | P(tie) | P(down) | 𝒜 = P(up)+P(tie) |
|---|---|---|---|---|
| Λ₁ | 0.4685 | 0.0625 | 0.4689 | 0.5311 |
| Λ₂ | 0.4158 | 0.1696 | 0.4146 | 0.5854 |
| Λ₃ | 0.3787 | 0.2404 | 0.3808 | 0.6192 |

`P(up) ≈ P(down)` in every case. The entire margin above 1/2 is `P(tie)`, which v0.1's `≥` silently counted as aligned.

Excluding ties gives the strict alignment ratio `𝒜⁺ = P(up) / (P(up) + P(down))`:

| Λ | 𝒜⁺ | verdict |
|---|---|---|
| Λ₁ | 0.4988 | no tendency |
| Λ₂ | 0.5007 | no tendency |
| Λ₃ | 0.5010 | no tendency |

All three sit at 0.500 within sampling error. Mean step magnitudes also match (`E[Δ\|up] ≈ E[Δ\|down]` to three decimals). The process is a symmetric random walk on `Λ*`.

**S2 is false.** It was true-looking only because `≥` counts the null case as success — a defect in the notation, not a discovery about the world.

---

## 4. A Second, Independent Refutation

A weaker reading of S2 might be: "from a disconnected state, linking increases." Tested directly with Λ₃:

| start | Λ* at t=0 | Λ* at t=100 | Λ* at t=1000 | stationary mean |
|---|---|---|---|---|
| maximally spread | 13 | 18.0 | 19.0 | **18.11** |
| all identical | 55 | 22.0 | — | **17.85** |

`Λ*` rises from a low start **and falls from a high start**, converging to the same value from both directions. The rise is regression to the typical configuration, not movement toward maximum linking. Any observation of "linking increasing over time" that starts from an atypical low state is explained entirely by relaxation.

This matters for the interpretive layer: historical claims of the form "civilisation shows increasing connection, therefore tendency" have this confound built in. Starting from a sparse state and observing an increase is what a driftless process does.

---

## 5. What Survives: S2′

Selection bias `b` = probability that a trajectory picks the highest-`Λ` option rather than choosing uniformly. Stationary `E[Λ*]` measured across `b` (5 runs each, 8,000 steps, 3,000 burn-in):

| Λ | b=0.0 | b=0.25 | b=0.5 | b=0.75 | b=1.0 | monotone |
|---|---|---|---|---|---|---|
| Λ₁ kernel | 16.61±0.1 | 17.91±0.2 | 19.95±0.3 | 22.68±0.3 | 26.90±0.2 | yes |
| Λ₂ Fiedler | 0.57±0.0 | 0.73±0.0 | 0.93±0.0 | 1.18±0.0 | 2.38±0.1 | yes |
| Λ₃ cycle rank | 18.07±0.1 | 20.57±0.2 | 24.03±0.2 | 29.34±0.2 | 36.68±0.2 | yes |

Strictly monotone under all three, with separations far exceeding the error bars.

> **S2′ (Equilibrium Shift).** For a system of trajectories with selection bias `b ∈ [0,1]` toward higher `Λ`, the stationary expectation `E[Λ*]` is strictly increasing in `b`.
>
> ```
> b₁ < b₂  ⟹  E[Λ*]_{b₁} < E[Λ*]_{b₂}
> ```

Note carefully what S2′ does **not** say. Even at `b = 1` — every trajectory always maximising — the drift is still zero. `Λ*` reaches a higher plateau and stays there. Maximising selection raises the *level* of linking, it does not produce unbounded *growth* of linking.

---

## 6. Consequences for the Framework

### 6.1 Tendency is not a property of the space

The v0.1 formulation treated `∇Λ*` as something the completion space possesses — a universal drift that trajectories are carried along by. The data says otherwise: with `b = 0` there is no drift at all, under any of three independent measures.

Tendency is a property of **selection**, not of `𝒞`. It exists exactly to the degree that trajectories select for it. This is a substantially weaker claim than v0.1 made, and it is the claim the evidence supports.

### 6.2 "Long-term progress is inevitable" does not follow

Several statements in the completion series assert that increase in linking is guaranteed by the structure of the universe. Under every Λ tested, that is false. What holds is conditional: increase in the *equilibrium level* of linking follows from selection bias, and only for as long as the bias is maintained. Remove the bias and the level relaxes back down.

The honest form of the historical claim is therefore: *sustained bias in selection raises the level of connection; the level is not self-sustaining.* This is a more useful claim than inevitability, because it identifies what would have to be maintained.

### 6.3 The `≥` in §6.2 must be replaced

v0.1 §6.2 defined aligned selection with `≥`. That single character generated a false positive across all three measures. The corrected definition:

```
γ[n] ⤳⁺ c   ⟺   Λ*(Γ | γ[n+1]=c) > Λ*(Γ | γ[n])       strict
γ[n] ⤳⁰ c   ⟺   equality                               null
γ[n] ⤳⁻ c   ⟺   decrease
```

and alignment measured strictly:

```
𝒜⁺(γ) = |⤳⁺| / (|⤳⁺| + |⤳⁻|)
```

Any future claim about alignment must use `𝒜⁺`, never `𝒜`.

---

## 7. Revised Axiom Set

**Definitional (unchanged):** D1 Invariance, D2 Well-foundedness, D3 Link symmetry, D4 Freedom additivity.

**Substantive:**

- **S1 — Configuration completeness.** Unchanged, still undemonstrated.
- ~~**S2 — Tendency.**~~ **Refuted** (§3–4). Under uniform selection, `𝒜⁺ = 0.500 ± 0.002` and net drift is zero for Λ₁, Λ₂, Λ₃.
- **S2′ — Equilibrium shift.** `E[Λ*]` strictly increasing in selection bias `b`. Confirmed under all three Λ.
- **S3 — Entanglement persistence.** Untested. Requires the continuity of `τ` under partial freezing, which is a separate question from anything settled here.

---

## 8. Limits of This Result

Stating these is not a hedge; they bound what has actually been shown.

**The test system is a toy.** Twelve trajectories on `ℤ/16` with uniform branching. Real systems have heterogeneous branching, non-uniform admissibility, and structured constraint. Any of these could reintroduce asymmetry that this system lacks.

**Three definitions are not all definitions.** A fourth `Λ` might yield genuine drift. But the three tested span quite different mathematical families — metric, spectral, homological — and they agree exactly. That agreement is the strongest part of the result: it suggests the finding is about the structure of driftless selection, not about any particular measure.

**Selection here is memoryless.** Real trajectories have history; a trajectory that has invested in a link may be less likely to break it. Path-dependent selection could produce hysteresis and genuine ratcheting. This is the most promising direction for recovering something S2-like, and it is the obvious next experiment.

**Nothing here bears on the interpretive layer.** These results constrain what can be claimed about `Λ*` and tendency. They say nothing about whether `γ†` is a good model of death or `γ ⊗ ρ` of love. Those readings were never load-bearing on S2, and they are unaffected — for better and for worse.

---

## 9. Next Steps, Revised

1. **Path-dependent selection.** Add link inertia: cost to breaking an existing link. Test whether `𝒜⁺ > 1/2` returns. This is the strongest remaining candidate for structural tendency.
2. **Heterogeneous branching.** Let `β` vary across trajectories and indices. Check whether asymmetry in `Φ` induces asymmetry in `Λ*`.
3. **Then** return to §9.2 of v0.1: construct `𝒞` for a restricted computational domain.
4. Leave the interpretive layer alone, as before.

---

## 10. Note on Method

The result in this addendum is negative, and it was reachable only because S2 was stated precisely enough to fail. The v0.1 formulation with `≥` would have "confirmed" tendency under any measure, forever, without ever being about anything.

That is the case for formalisation, and it is worth more than the axiom that was lost. A framework that can be shown wrong in a specific place is doing better work than one that accommodates every observation. S2′ is a smaller claim than S2, but it is a claim — and it survived a test that S2 did not.

---

*ln1 Notation v0.2 — Cret*
