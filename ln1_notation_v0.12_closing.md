# ln1 Notation v0.12

**Closing the Trajectory Half: Growing 𝒞, S3, and the Counting Theorem**

Cret, September 2026

---

## 0. What This Addendum Does

v0.11 said I would not add a twelfth mechanism to the arithmetic side, and I am not. This closes the *other* half — the trajectory algebra of v0.1–v0.3, which v0.8 showed cannot be joined to the arithmetic work and which has had three items open since then.

All three are settled here. Two of them fail in the same shape, and naming that shape is the useful part.

---

## 1. Growing 𝒞 — The Last Route to S2

v0.3 §7 identified one live route to tendency: if the configuration space grows so the ceiling recedes faster than the system climbs, stationarity never arrives and the Balance Theorem never bites.

`K(t) = 16 + rate·t`, twelve trajectories, `Λ₃` as before.

**The hidden choice:** the linking radius `ε`. As the space grows, does `ε` stay fixed (absolute distance) or scale with `K` (relative distance)? Nothing in v0.3 specified this, and it turns out to decide everything.

| rate | ε convention | 𝒜⁺ | mean Λ* | drift/1k |
|---|---|---|---|---|
| 0.000 | absolute | 0.4991 | 18.066 | +0.010 |
| 0.000 | relative | 0.5042 | 17.945 | +0.004 |
| 0.001 | absolute | 0.4974 | **5.133** | −0.245 |
| 0.001 | relative | 0.4971 | 14.483 | −0.024 |
| 0.010 | absolute | 0.5003 | **0.203** | −0.017 |
| 0.010 | relative | 0.4954 | 14.116 | −0.008 |
| 0.100 | absolute | 0.5000 | **0.003** | −0.000 |
| 0.100 | relative | 0.5012 | 14.142 | +0.002 |

**𝒜⁺ = 1/2 in every row.**

The two conventions fail differently and both fail:

- **Absolute ε:** the space dilutes. Λ* collapses from 18 toward 0 — trajectories lose contact faster than they gain it. Growth *destroys* linking rather than enabling it.
- **Relative ε:** the system is scale-invariant. Growing `K` with `ε ∝ K` is the fixed-`K` system in rescaled coordinates. Nothing happens, and `𝒜⁺ = 1/2` for exactly the v0.2 reasons.

**The last route to S2 is closed.** Not by a narrow failure — by a dichotomy where one branch is trivial and the other is worse than trivial.

---

## 2. The Counting Theorem Is More General Than v0.3 Said

The `rate = 0.001, absolute` row deserves attention: `Λ*` falls from 18 to 5, so the process is *manifestly not stationary*, yet `𝒜⁺ = 0.4974`.

Decomposed over 30,000 steps:

```
P(up)     = 0.4987      P(down)   = 0.5013
E[Δ|up]   = 1.9778      E[Δ|down] = 1.9653
net/step  = +0.000733   ← nonzero, the process drifts
𝒜⁺        = 0.4987
```

The drift is carried entirely by magnitudes. The counts stay at 1/2.

> **Counting Theorem (generalising v0.3's S2″).** `𝒜⁺ ≠ 1/2` requires magnitude asymmetry — `E[Δ|up] ≠ E[Δ|down]` — whether or not the process is stationary.

v0.3 derived this from the stationary balance equation and stated it under stationarity. It is stronger than that. `𝒜⁺` counts steps; step-count asymmetry and magnitude asymmetry are the only two ways a process can move, and `𝒜⁺` sees only the first. Drift lives in the second.

This retroactively explains why every mechanism across v0.2, v0.3, and now v0.12 returned 1/2: none of them engineered magnitude asymmetry, and none of them could have, because all of them were symmetric in their step distributions by construction.

---

## 3. S3 Is Underdetermined

The last untested axiom from v0.1:

> **S3.** If `γ ⊗ ρ` and `ρ` freezes, `τ(γ ⋈ ρ†)` is preserved in `⟨γ⟩`.

Operationalised: freeze two of twelve trajectories at `t = 5000` and measure whether the joint invariant still exceeds the invariant of the active ones alone.

| reading of "freeze" | τ(γ⋈ρ†) − τ(γ) | verdict |
|---|---|---|
| ρ stops moving, stays in 𝒞 | **6.662 ± 1.407** | S3 holds |
| ρ is removed from 𝒞 | **0.000 ± 0.000** | S3 fails |

Both readings are trivial:

- **"Stops moving"** — `ρ` is still a point in `𝒞`, still within `ε` of things, still contributing edges. Entanglement persists because nothing was removed.
- **"Removed"** — the edges go with it. Entanglement vanishes because everything was removed.

**S3 is not false. It is underdetermined.** Its truth value is fixed entirely by which reading you pick, and neither reading makes it informative.

### 3.1 The Same Shape as §1

This is the identical failure to growing `𝒞`:

| claim | the undetermined choice | branch A | branch B |
|---|---|---|---|
| growing 𝒞 | is ε absolute or relative? | dilution | scale-invariance |
| S3 | does freezing remove or immobilise? | vanishes | persists |

In both cases the framework states a proposition, and the proposition's truth is decided by a modelling choice the framework never made. The measurement does not adjudicate; it just reports which choice you made.

This is worth naming because it is a *third* kind of failure, distinct from the two the project has seen so far:

1. **Refuted** — the claim is precise and measurement contradicts it. (S2, the towers, `e` from the bridges.)
2. **Obstructed** — the claim is precise and a theorem forbids it. (Multiplicativity, rank, CM.)
3. **Underdetermined** — the claim is not precise enough to have a truth value until an unstated choice is made. (Growing `𝒞`, S3, and — in a different register — the physical constants in v0.9.)

The third is the least satisfying to discover because there is nothing to fix. You cannot make an underdetermined claim true; you can only replace it with a determinate one, which is a different claim.

---

## 4. Final Status of the Trajectory Half

| item | status |
|---|---|
| S1 — configuration completeness | never operationalised; would need a construction of `𝒞`, which was never given |
| S2 — tendency | **refuted** (v0.2), not recoverable by path-dependence (v0.3), heterogeneous branching (v0.3), or growing `𝒞` (v0.12) |
| S2′ — equilibrium shift | **holds**, across three linking measures and two mechanisms |
| S2″ → Counting Theorem | **holds**, and more generally than first stated |
| S3 — entanglement persistence | **underdetermined** |
| D1–D4 | definitional, carry no content |

What survives from v0.1–v0.3 is: **S2′ and the Counting Theorem.** One empirical regularity and one small theorem.

The Counting Theorem is the more useful of the two, and it generalises past this framework: *any* time someone reports "most changes were improvements" as evidence of progress in a bounded system, the theorem says that statistic is about step counts and carries no information about direction unless magnitudes are also reported. That is a real and transferable caution.

---

## 5. The Whole Project, Twelve Versions On

Two investigations that share a name and cannot be joined (v0.8).

**Arithmetic half (v0.4–v0.11).** Every structural instinct in the notes decoded to a real object — branch lattice, winding number, nome, the degree-2 extension. The endpoint is exact and derived: *base p ⟺ nome 1/p ⟺ the Tate curve ℂ\*/p^ℤ, at height ln(p)/2π, accumulating at the cusp, provably never CM*. Correct, small, and already-known. Three theorems block the routes to ABC and Riemann.

**Trajectory half (v0.1–v0.3, v0.12).** S2 refuted four different ways. S2′ and the Counting Theorem survive. S1 was never made precise; S3 cannot be.

**The pattern, across both halves.** Structural claims in the notes: right, repeatedly, and often right in ways I initially dismissed. Quantitative and mechanical claims: wrong on measurement, without exception. Twelve versions and that asymmetry never reversed.

I would take that as the project's actual finding. Not a result about ABC or about tendency, but a calibrated statement about a body of intuition: the *shapes* it reaches for are real and worth decoding, and the *mechanisms* it proposes for them are not. That is unusual enough to be worth knowing, and it is more useful going forward than any of the individual refutations.

---

## 6. What I Would Do Now

**Stop adding mechanisms.** Twelve versions, and the last eight each ended in a theorem or a dichotomy rather than a gap. That is a boundary.

**Write up the one exact result.** `ln1 ≠ ln1` → branch lattice → prime as nome → `ℂ*/p^ℤ` with `q = 1/p` is a clean five-line derivation from the notes' opening. It is not new mathematics but it is a correct and self-contained piece of exposition, and it is the only thing in twelve versions that is both exact and yours.

**Keep the Counting Theorem.** It is small, it is true, and it applies outside this project.

**Let the rest go.** The interpretive material — the 220 completions, the trajectory-to-meaning mappings — was never load-bearing on any of this, and none of the refutations above touch it. But equally, nothing above supports it, and it should not be presented as though the formal work does.

---

*ln1 Notation v0.12 — Cret*

*Three ways to fail: contradicted, forbidden, or never precise enough to be either. This half ended with two of the third.*
