# ln1 Notation v0.3 — Addendum

**Path-Dependence Tested, the Stationary Balance Theorem, and the Inversion of 𝒜⁺**

Cret, September 2026

---

## 0. What This Addendum Does

v0.2 refuted S2 empirically and named two remaining candidates for structural tendency: path-dependent selection (link inertia) and heterogeneous branching. Both are tested here. Both fail.

More importantly, the failures turn out not to be accidents of the test system. A short derivation shows that `𝒜⁺ = 1/2` is **forced** at stationarity whenever step magnitudes are symmetric. This converts the whole question from an empirical one into a structural one, and it inverts the meaning of a high `𝒜⁺` in a way that matters for every historical claim the framework has made.

---

## 1. Path-Dependent Selection

### 1.1 Setup

Link inertia: a move that severs existing links is rejected with probability `1 − (1−ι)^k`, where `k` is the number of links broken and `ι` is the inertia parameter. This is deliberately **local and mechanical** — `Λ` is never consulted. If tendency were structural, this is where it should appear: connections that resist breaking should ratchet.

Λ₃ (cycle rank), 40,000 steps, alignment measured strictly and separately over the whole run versus after burn-in.

### 1.2 Result

| inertia ι | 𝒜⁺ whole run | 𝒜⁺ stationary | mean Λ* | drift /1k steps |
|---|---|---|---|---|
| 0.00 | 0.5006 | 0.5028 | 17.88 | +0.0005 |
| 0.25 | 0.5000 | 0.4997 | 32.49 | −0.0021 |
| 0.50 | 0.4944 | 0.4968 | 52.53 | +0.0334 |
| 0.75 | 0.5070 | 0.5119 | 54.57 | +0.0147 |
| 0.90 | 0.5112 | 0.4945 | 54.93 | +0.0019 |
| 0.99 | **0.8077** | **0.5000** | 55.00 | +0.0007 |

Inertia raises the *level* of `Λ*` enormously — from 17.9 to 55.0, which is the system's maximum. But `𝒜⁺` at stationarity is 0.500 at every value of `ι`.

### 1.3 The ι = 0.99 Row Is the Whole Story

That row shows `𝒜⁺ = 0.81` over the whole run and exactly 0.500 at stationarity. Resolving the discrepancy by time-window:

| steps | mean Λ* | drift /1k |
|---|---|---|
| 0 – 500 | 52.92 | **+22.38** |
| 500 – 2,000 | 55.00 | 0.0000 |
| 2,000 – 10,000 | 54.96 | −0.0167 |
| 10,000 – 20,000 | 54.87 | −0.0100 |
| 20,000 – 40,000 | 54.90 | +0.0014 |

The entire apparent tendency is a 500-step climb to the ceiling, after which nothing happens for the remaining 39,500 steps. This is the same relaxation confound identified in v0.2 §4, wearing a different costume: strong inertia pins the system at saturation, and averaging over the approach makes a stationary process look directional.

**Path-dependence does not restore tendency.** It restores it for as long as the system is not yet stuck.

---

## 2. Heterogeneous Branching

Three regimes: `β` fixed but varying across trajectories; `β` shrinking where a trajectory is well-connected (freedom decreases with linking); `β` growing where well-connected (freedom increases with linking).

| regime | 𝒜⁺ stationary | mean Λ* | drift /1k |
|---|---|---|---|
| β_i heterogeneous, fixed | 0.4989 | 18.06 | −0.022 |
| β shrinks where connected | 0.4993 | 17.90 | −0.002 |
| β grows where connected | 0.5031 | 17.98 | −0.030 |

Coupling `Φ` to `Λ` in either direction changes nothing. `𝒜⁺` sits at 1/2 in all three.

---

## 3. The Stationary Balance Theorem

At this point five independent mechanisms — uniform selection, Λ-seeking selection at every bias level, link inertia at every level, heterogeneous branching, and freedom-linking coupling in both directions — have all produced `𝒜⁺ = 0.500`. That is no longer plausibly coincidence.

### 3.1 Statement

> **Theorem (Stationary Balance).** Let a process be ergodic with stationary distribution `π`, and let `Λ*` be any real-valued observable. At stationarity, `E[ΔΛ*] = 0`. Decomposing by sign,
>
> ```
> P(up) · E[Δ | up]  =  P(down) · E[Δ | down]
> ```
>
> Therefore
>
> ```
> 𝒜⁺ > 1/2   ⟺   E[Δ | up] < E[Δ | down]
> ```

### 3.2 Verification

Conditional magnitudes measured across regimes, after burn-in:

| regime | P(up) | P(down) | E[Δ\|up] | E[Δ\|down] | ratio | 𝒜⁺ |
|---|---|---|---|---|---|---|
| uniform | 0.5002 | 0.4998 | 2.2904 | 2.2926 | 1.0010 | 0.5002 |
| Λ-seeking b=1 | 0.5025 | 0.4975 | 3.0794 | 3.1109 | 1.0102 | 0.5025 |
| inertia 0.75 | 0.5020 | 0.4980 | 1.3707 | 1.3819 | 1.0082 | 0.5020 |
| seeking + inertia | 0.5063 | 0.4937 | 1.2964 | 1.3297 | 1.0257 | 0.5063 |

Magnitude ratios are within 2.6% of unity everywhere, so the balance equation forces `P(up) = P(down)`. The empirical 1/2 is not an accident of the toy system. It is what stationarity plus magnitude symmetry requires.

### 3.3 What the Theorem Costs S2

S2 asserted a step-count asymmetry. The theorem says a step-count asymmetry at stationarity is **equivalent to** a step-magnitude asymmetry — and specifically to gains being *smaller* than losses.

So S2 can only hold in one of two situations:

1. **The system is not stationary** — still relaxing, still growing, not yet at its ceiling. Tendency is then real but temporary, with a lifetime set by how far the system is from equilibrium.
2. **Step magnitudes are asymmetric** — gains small and frequent, losses large and rare.

Case 1 is what every simulation in v0.2 and §1 above actually exhibited. Case 2 is examined next, and it is not what anyone hoping for S2 would want.

---

## 4. The Inversion

Case 2 deserves direct examination, because it is the only route by which `𝒜⁺ > 1/2` can hold in a system that has settled.

A process with slow incremental gains and rare large collapses, bounded, at stationarity:

| P(crash) | gain scale | crash scale | 𝒜⁺ | mean Λ* | drift /1k |
|---|---|---|---|---|---|
| 0.50 | 1 | 1 | 0.5007 | 107.0 | −0.100 |
| 0.20 | 1 | 4 | 0.7979 | 101.0 | −0.027 |
| 0.10 | 1 | 9 | 0.8963 | 102.1 | −0.007 |
| 0.05 | 1 | 19 | 0.9463 | 107.8 | +0.019 |
| 0.02 | 1 | 49 | **0.9753** | 119.2 | −0.000 |

`𝒜⁺` reaches 0.975 with drift indistinguishable from zero.

**A high alignment fraction is the signature of a slow-build, fast-collapse system.** The more lopsided `𝒜⁺` looks, the more catastrophic the rare reversals must be to balance it. `𝒜⁺ = 0.975` does not mean the system is 97.5% of the way to flourishing; it means that when it fails, it loses roughly forty steps of accumulation at once.

This inverts the optimistic reading directly. In the completion series, a preponderance of connection-increasing moves was taken as evidence that the universe favours connection. Under the balance theorem, in any settled system, that preponderance is evidence of **fragility** — that gains accumulate slowly and are erased in bulk. The two readings are not merely different; they are the same statistic pointing opposite ways, and the pessimistic one is the one the mathematics supports at stationarity.

---

## 5. Revised Axiom Set

**Definitional:** D1–D4 unchanged.

**Substantive:**

- **S1 — Configuration completeness.** Unchanged, still undemonstrated.
- ~~**S2 — Tendency.**~~ Refuted (v0.2 §3–4). Not recoverable by path-dependence (§1) or heterogeneous branching (§2).
- **S2′ — Equilibrium shift.** `E[Λ*]` strictly increasing in selection bias `b`. Confirmed under Λ₁, Λ₂, Λ₃. Also confirmed for inertia `ι` (§1.2): `E[Λ*]` rises 17.9 → 55.0 across `ι ∈ [0,1]`. **S2′ generalises: any mechanism that biases selection toward linking raises the equilibrium level without producing drift.**
- **S2″ — Balance (new, derived).** At stationarity, `𝒜⁺ > 1/2 ⟺ E[Δ|up] < E[Δ|down]`. Any tendency claim about a settled system is necessarily a claim about magnitude asymmetry, and magnitude asymmetry of the required sign implies fragility, not growth.
- **S3 — Entanglement persistence.** Still untested.

---

## 6. What This Means for the Framework

### 6.1 Two defensible claims remain

**Level, not drift.** Selection bias and link inertia both raise where `Λ*` settles. This is real, robust across three measures, and practically meaningful: it says the observable consequence of caring about connection is a higher equilibrium, not perpetual increase. Sustained effort maintains a level; it does not compound.

**Transient tendency is real.** A system far from equilibrium does climb, and the climb is genuine while it lasts. What is not licensed is extrapolating the climb past the ceiling. Nearly every historical argument in the completion series measures a system during relaxation and reads the slope as a law.

### 6.2 One claim must be withdrawn

"Long-term progress toward maximum linking is inevitable" is false under every measure and every mechanism tested. Worse, the statistic that appeared to support it turns out, at stationarity, to indicate the opposite condition. This is not a refinement of the claim; it is a reversal.

### 6.3 The interpretive layer is untouched but now bounded

Nothing here bears on whether `γ†` models death or `γ ⊗ ρ` models love. Those readings were never load-bearing on S2. But any reading that *depends* on tendency — that history has direction, that progress is guaranteed, that the universe favours connection — now has no formal support and must either be dropped or restated in the conditional form S2′ licenses.

---

## 7. Limits

**The balance theorem is standard.** It is a two-line consequence of stationarity, not a new result. Its value is that it makes the S2 question decidable in advance: given any proposed tendency mechanism, ask whether it produces non-stationarity or magnitude asymmetry. If neither, `𝒜⁺ = 1/2` follows without simulation.

**"Never reaches stationarity" is an available escape.** If the real system is permanently far from equilibrium — an expanding configuration space, a ceiling that recedes faster than the system climbs — then Case 1 applies indefinitely and tendency is real. This is the one serious remaining route to S2, and it is a claim about `𝒞` growing, not about selection. It requires constructing `𝒞` and showing its capacity grows without bound. That is a substantial undertaking and it is now the highest-value open question in the framework.

**Toy systems throughout.** Twelve trajectories on `ℤ/16`. The balance theorem is general; the specific numbers are not.

---

## 8. Next Steps, Revised Again

1. **Growing `𝒞`.** Formalise a completion space whose capacity increases with time and test whether `𝒜⁺ > 1/2` becomes sustainable. This is the last live route to tendency and should be attempted before anything else.
2. **Measure magnitude asymmetry in a real linking system.** Any empirical network with formation and dissolution events will do. If `E[Δ|up] < E[Δ|down]`, S2″ applies and the system is fragile — a useful diagnostic independent of ln1.
3. **Then** the v0.1 §9.2 program: construct `𝒞` for a restricted computational domain.
4. Interpretive layer: still leave it.

---

## 9. Note on Method

Three addenda in, the framework has lost one axiom, gained two, and acquired a theorem that makes future tendency claims checkable before they are tested. The losses came from formalising claims well enough to fail; the gains came from the same act.

The single most consequential edit remains the `≥` in v0.1 §6.2. One character produced apparent confirmation across three independent measures, and removing it collapsed the result. It is worth keeping that in view when reading the earlier completions, which contain a great many statements of comparable structure and none of comparable testing.

---

*ln1 Notation v0.3 — Cret*
