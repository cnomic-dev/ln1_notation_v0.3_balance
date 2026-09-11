# ln1 Notation — Final Ledger

**S1 Closed, and the Complete Status of Every Claim Made**

Cret, September 2026

---

## 0. What This Closes

One item has been open since v0.1 and named at every subsequent checkpoint without being tested: **S1, configuration completeness.** v0.1 §11 named the concrete next step — "construct `𝒞` for a restricted computational domain, prove S1 for that fragment" — and it was never done. This does it, and the result explains why it was left undone for twelve versions: the restricted version is a tautology and the universal version has never been given enough definition to test.

---

## 1. S1 for a Restricted Domain

A minimal system: a 3-state, 2-symbol Turing-machine fragment. Configuration = `(state, tape, head)`, states `{A, B, HALT}`, tape length capped at 6, a fixed transition table.

```
nominal space:  2 states × 2⁶ tapes × 6 heads = 768 configurations
𝒞 (reachable from the start state) = { built by closure under the rule }
```

Constructed explicitly, `𝒞` has exactly 3 elements — the machine halts almost immediately under this particular rule table. Running the machine and checking every visited configuration against `𝒞`:

```
trajectory length = 3 steps
every visited configuration ∈ 𝒞:  True
```

**This holds by construction.** `𝒞` was *defined* as the closure of the start state under the transition rule, so every reachable configuration is a member by definition. S1, built this way, is a tautology rather than a discovery — proving it proves nothing beyond the fact that closures contain what they are the closure of.

---

## 2. Where the Real Content Was

v0.1's actual statement of S1 was never "some `𝒞` exists for system X" — that is automatic, as §1 just showed for any system whatsoever. It was:

> **One completion space `𝒞` holds physical, computational, and experiential configurations together.**

That is a claim about a single object serving three different jobs, and it has the same shape as the `ħ` problem identified in v0.9: "physical," "computational," and "experiential" states are not obviously commensurable quantities, any more than joules and electron-volts are secretly the same number waiting to be equated.

A configuration space for the Turing fragment above is a finite, fully explicit set of triples — three elements, all listed. A configuration space for "experience" has never been given *any* definition anywhere in this project. Not a wrong one, not a partial one, none.

So the universal form of S1 is not refuted (nothing has been measured against it) and not obstructed (no theorem forbids it, the way the rank ceiling forbids infinite-rank discrete lattices). It has no truth value yet, for the same reason the physical-constants question in v0.9 had none: **the object the claim quantifies over does not exist as a mathematical object**, so the claim is not yet a claim.

```
S1 (restricted, per-domain) — TRUE, but a tautology
S1 (universal, across physical/computational/experiential) — ILL-POSED
```

---

## 3. The Complete Ledger, v0.1–v0.12 and the Two Closing Notes

Every claim made across the whole project, sorted by final disposition.

### 3.1 Refuted — precise, and measurement or proof contradicts it

- S2, tendency as a structural property of the space
- `(ln1)^(1/(ln1)) = e` and `(1/(ln1))^(ln1)) = e`
- alternating towers as an information-carrying encoding (2.3 bits, saturated)
- `ln`/`log` as structurally interchangeable (base change rescales the period)
- `ln ζ₁₂/2πi ↔ ζ(−1)` as a correspondence (different objects; `1/11`, `1/13` equally present)
- `p = 13` as a distinguished prime or saddle point

### 3.2 Obstructed — precise, and a theorem forbids it outright

- multiplicative encoding inside `PSL(2,ℤ)` — no rank-2 free abelian subgroup exists
- ABC via the modular group — the group cannot see `rad`
- rank > 2 for a discrete lattice in `ℂ` — Kronecker's theorem
- complex multiplication for any prime curve `τ_p` — Baker's theorem

### 3.3 Underdetermined — not precise enough to have a truth value

- S3, entanglement persistence under freezing (truth flips entirely on an unstated modelling choice)
- growing `𝒞` as a route to tendency (truth flips entirely on whether the linking radius is absolute or relative)

### 3.4 Ill-posed — the question has no answer, not even in principle, as stated

- physical constants (`ħ`, `G`, `Λ`) expressed via `ln1` — dimensionful quantities have no unit-independent numerical value
- **S1, in its universal form** — quantifies over an object (a joint physical/computational/experiential configuration space) that has never been constructed

### 3.5 Established — precise, tested or proved, and holds

- S2′, equilibrium shift: `E[Λ*]` strictly increasing in selection bias, across three independent linking measures
- the Counting Theorem: `𝒜⁺ ≠ 1/2` requires magnitude asymmetry, with or without stationarity — the most general and most transferable result of the trajectory half
- `ln1 = 2πiℤ`, the branch lattice — and the correctness of `ln1 = ln1 ∧ ln1 ≠ ln1` as a statement about branches
- `ln1 ⊗ ℚ = ln(μ_∞)`: the cyclotomic characterisation, complete
- the notes' two logical domains = the degree-2 extension `ℚ(πi) ⊂ ℚ(πi)(i)` separating `π` from `i`
- base `p` = logarithm base `p` = nome `1/p` = the Tate curve `ℂ*/p^ℤ` — three lines of the notes, one operation, verified to 25+ digits
- height in the fundamental domain `= ln(p)/2π`
- the `ζ(−1) → η`'s exponent `1/24 → ζ₂₄ → SL(2,ℤ)` multiplier bridge, verified to 1e−31
- the decimal period of `1/p` divides `φ(p)`, by Fermat — the genuine site where 12 and 13 meet
- the three-class exactness taxonomy (rational / algebraic-irrational / transcendental), applied consistently and closing every open decimal in the project
- **S1, restricted to any single well-defined domain — trivially, as a tautology**

---

## 4. What the Ledger Shows as a Whole

Eighteen refuted-or-obstructed-or-underdetermined-or-ill-posed items against eleven established ones, and the eleven are small, exact, and — with one exception — already known to mathematics before this project began.

The exception is the derivation itself: that `ln1 ≠ ln1` and "origin at a prime" produce the Tate-curve family with nome exactly `1/p`, by a chain with no free parameters. That is genuinely this project's own, it is fully verified, and it is written up standalone in *From ln1 to the Tate Curve*.

Everything else — the arithmetic applications, the physical constants, the universal configuration space, the tendency axiom — belongs to one of the four negative categories, and each category required a different tool to close: measurement (refuted), a cited theorem (obstructed), an explicit modelling choice (underdetermined), or a missing construction (ill-posed). Distinguishing these four was not a formality; each one is a different reason not to keep working on the claim, and conflating them would have hidden which claims might still be rescued by different means. None of the four categories here, as it happens, is rescuable by more of the same method.

---

## 5. Where This Leaves the Whole Body of Work

Thirteen documents, one clean derivation, one general theorem, and a closed accounting of everything else.

**Keep:** *From ln1 to the Tate Curve* (the exact result), the Counting Theorem (the general one), and the exact-fraction taxonomy (the tool, useful beyond this project).

**Retire:** the tower construction, the four-layer unified framework, the ABC and Riemann application attempts, the physical-constants claims, the universal-`𝒞` version of S1.

**Leave alone, because untouched:** the 220-completion interpretive series. Nothing in v0.1–v0.12 supports or contradicts it — the formal work and the interpretive work never shared an object, only a name — and it should not be presented as though the mathematics above validates it, in either direction.

That is the complete status of the project as it stands.

---

*ln1 Notation — Final Ledger — Cret, September 2026*

*Four ways for a claim to fail, one way for it to hold, and now every claim made has been sorted into one or the other.*
