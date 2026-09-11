# ln1 Notation v0.11

**The Prime Curve Family: Nome 1/p, Accumulating at the Cusp, Never CM**

Cret, September 2026

---

## 0. What This Addendum Does

v0.10 established that choosing a logarithm base is choosing the nome, so there is one curve per prime. That makes `{τ_p}` a family, and a family has a shape. This addendum works out what the shape is.

The result has one clean piece and one hard negative. The clean piece closes a loop that has been open since v0.7. The negative is proved with Baker's theorem and it is decisive about where this family sits in arithmetic geometry.

---

## 1. The Nome Is Exactly 1/p

```
τ_p = 2πi / ln p          reduced by S:   S·τ_p = i·ln(p)/(2π)
```

| p | Im τ_p | height ln p/2π | q = e^{2πiτ} |
|---|---|---|---|
| 2 | 9.064720 | 0.110318 | **0.5000000000** |
| 3 | 5.719202 | 0.174850 | **0.3333333333** |
| 5 | 3.903963 | 0.256150 | **0.2000000000** |
| 7 | 3.228919 | 0.309701 | **0.1428571429** |
| 13 | 2.449633 | 0.408224 | **0.0769230769** |
| 1009 | 0.908406 | 1.100829 | 0.0009910803 |

At `τ = i·h` with `h = ln(p)/2π`, the nome is `q = e^{−2πh} = 1/p`, **exactly**.

> **Origin at the prime p ⟺ logarithm base p ⟺ nome q = 1/p.**

Three separate lines in the notes, now provably one operation. The Tate curve is `ℂ*/p^ℤ`, and the height in the fundamental domain is `ln(p)/2π`.

This is the cleanest statement the framework has produced. It is small, but it is exact and it is derived rather than asserted.

---

## 2. The Family Accumulates at the Cusp

`τ_p = 2πi/ln p → 0` as `p → ∞`, which is a cusp. After reduction, `S·τ_p = i·ln(p)/2π → i∞`, the standard cusp of the fundamental domain.

So the primes march up the imaginary axis, and `q = 1/p → 0`.

Counting in the height coordinate:

```
N(T) = #{p : ln(p)/2π ≤ T} = π(e^{2πT}) ~ e^{2πT}/(2πT)
```

| T | e^{2πT} | N(T) | e^{2πT}/(2πT) | ratio |
|---|---|---|---|---|
| 0.30 | 6.6 | 3 | 3.49 | 0.859 |
| 0.40 | 12.3 | 5 | 4.91 | 1.018 |
| 0.50 | 23.1 | 9 | 7.37 | 1.222 |
| 0.70 | 81.3 | 22 | 18.49 | 1.190 |

This is the prime number theorem rewritten in the height coordinate. No new content — but it fixes the density of the family, and the exponential shape is what the next section is about.

---

## 3. The Analogy That Is Real, and the One That Is Not

Exponential-over-linear growth is also the shape of the **prime geodesic theorem**: on the modular surface, `#{closed geodesics of length ≤ L} ~ e^L/L`, the exact analogue of PNT. This analogy is genuine and classical — it is what the Selberg zeta function is for.

But the `τ_p` are not geodesics. A closed geodesic comes from a hyperbolic `γ` with `|tr γ| = t`, and its length is `L = 2·arccosh(t/2)`:

| \|tr\| | L | nearest ln p | gap |
|---|---|---|---|
| 3 | 1.9248473002 | ln 7 = 1.945910 | 0.021063 |
| 5 | 3.1335984739 | ln 23 = 3.135494 | 0.001896 |
| 7 | 3.8496946005 | ln 47 = 3.850148 | 0.000453 |
| 47 | 7.6993892010 | ln 2207 = 7.699389 | **0.000000** ← |

### 3.1 That Last Row Is Not an Identity

At six decimals it reads as exact. At twenty-five it does not:

```
ε²        = 2206.999546896146215177927
L = ln ε² = 7.699389200953655159964143
ln 2207   = 7.699389406256736399942537
difference= 2.05e−07
```

`ε²` has trace `t²−2 = 2207` and norm 1, so it is `2207` minus a small correction, and 2207 happens to be prime. It is a near-coincidence, not an identity — the same small-linear-form-in-logarithms phenomenon as v0.8's Pythagorean comma, appearing yet again.

I am flagging this because at the precision I first printed it, it looked like a discovery. That is the characteristic failure mode in this area and it caught me in my own table.

**Conclusion:** geodesic lengths are `2 log((t+√(t²−4))/2)` — logs of fundamental units of real quadratic fields. Logs of primes are a different set. The PNT ↔ prime-geodesic analogy is real; "primes are geodesics" is not an identification. The `τ_p` are points in the upper half plane.

---

## 4. No Prime Curve Has Complex Multiplication

This is the hard negative, and it is a theorem rather than a measurement.

CM requires `τ` imaginary quadratic. Here `τ_p = i·ln(p)/2π`, so CM would need `ln(p)/π` algebraic — equivalently a nonzero algebraic relation

```
α·ln p + β·(2πi) = 0,    α, β algebraic, not both zero
```

But `2πi = log(1)` and `ln p = log(p)` are both logarithms of **algebraic** numbers. Baker's theorem says a nonvanishing algebraic linear form in logarithms of algebraic numbers cannot equal zero. So no such relation exists.

```
⟹ ln(p)/π is transcendental for every prime p
⟹ no τ_p is imaginary quadratic
⟹ no prime curve has complex multiplication
⟹ j(τ_p) is transcendental for every prime p
```

The near-misses are only density:

| p | ln p / π | nearest a√d/b | gap |
|---|---|---|---|
| 2 | 0.220635600152652 | √7/12 | 1.6e−04 |
| 13 | 0.816448738040769 | √6/3 | 4.8e−05 |

Rationals times square roots are dense in `ℝ`. Density is not equality, and Baker forbids equality.

### 4.1 What This Costs

CM is where the arithmetic in this area lives. Singular moduli `j(τ)` are algebraic integers; class fields of imaginary quadratic fields are generated explicitly by them; Kronecker's Jugendtraum is the whole programme. Every bit of it requires `τ` imaginary quadratic.

The prime curves are provably never in that class. So:

- no singular moduli
- no explicit class field theory
- no reciprocity
- `j(τ_p)` transcendental throughout

**The family `{τ_p}` is a path of Tate curves accumulating at the cusp with no extra arithmetic structure at any point.** In a landscape where the arithmetic content is concentrated at the CM points, this family provably avoids all of them.

That is a sharper negative than v0.5's and v0.8's, because it is not "we have not found a route" — it is "Baker's theorem forbids the route."

---

## 5. Where This Leaves the Framework

Combining v0.7 through v0.11:

| what the framework produces | status |
|---|---|
| `ln1 = 2πiℤ`, branch lattice | ✅ correct, exact |
| roots of unity, `θ` as winding number | ✅ correct, complete characterisation |
| base p = nome 1/p = Tate curve `ℂ*/p^ℤ` | ✅ correct, exact, three lines unified |
| height `ln(p)/2π`, family at the cusp | ✅ correct |
| rank ceiling at 2, one prime per curve | ✅ theorem (v0.8) |
| multiplicativity via `ln` | ✅ correct, and standard |
| ABC contact via linear forms in logs | ⚠️ real, and it is Baker's 1966 theory |
| CM, singular moduli, class fields | ❌ **provably unreachable** |
| Riemann | ❌ no route |
| ABC proof | ❌ no route |

The framework consistently produces *correct* objects. It has not once produced a *new* one, and it now has a theorem saying it cannot reach the part of the territory where the arithmetic is.

---

## 6. My Assessment, Stated Plainly

Eleven versions is enough to say something about the whole rather than the parts.

**The framework is internally sound and externally redundant.** Every structural instinct in the notes has decoded to a real object: the branch lattice, the winding number, the nome, the degree-2 extension separating π from i. That is a remarkable hit rate for notes written without this machinery in view, and it says something real about the quality of the underlying intuition.

But every object it decodes to was already there, and the two hardest questions it was aimed at — ABC and Riemann — are now blocked by three separate theorems: the rank ceiling (v0.8), the multiplicativity obstruction (v0.5), and the CM obstruction (v0.11). These are not gaps. They are proofs that the routes do not exist.

**What I would do with this:** treat it as a completed piece of work rather than a stalled one. What you have is a derivation, from `ln1 ≠ ln1` and "origin at a prime," of the Tate curve family with nome `1/p` — clean, exact, and yours. That is a real thing to have written down. It is not a route to the conjectures, and the versions above say why with proofs rather than with discouragement.

**What I would not do:** add a twelfth mechanism. The pattern across v0.4, v0.5, v0.6, v0.8, and v0.11 is that each new mechanism runs into a theorem, and the theorems are getting more fundamental rather than less. That is the signature of a genuine boundary, not of insufficient cleverness.

The trajectory half (v0.1–v0.3) remains a separate and untouched question, and v0.8 showed it cannot be joined to this one.

---

## 7. Ledger, Complete

**Refuted:** S2 as structural tendency; both bridges equal `e`; alternating towers as encoding; multiplicative encoding in `PSL(2,ℤ)`; ABC via the group; the framework reaching `PSL(2,ℤ)`; `e` derivable from `ln1`; physical constants in `ln1` (ill-posed); `ln`/`log` structurally interchangeable; the `1/12` ↔ `1/12` correspondence; `p = 13` as a saddle point; **CM for any prime curve** (v0.11).

**Established:** S2′; the Stationary Balance Theorem and the `𝒜⁺` inversion; `{0,1}` closed under both bridges; the Multiplicativity Obstruction; `ln1 = 2πiℤ` and the vindication of `ln1 ≠ ln1`; the prime as second period; multiplicativity via `ln`; the rank ceiling and the arithmetic–geometry dichotomy; `ln1 ⊗ ℚ = ln μ_∞`; the two logical domains as the degree-2 extension; base change = nome; the `ζ(−1) → 1/24 → ζ₂₄ → SL(2,ℤ)` bridge; **nome = 1/p exactly, height = ln(p)/2π, family accumulating at the cusp** (v0.11).

**Open:** growing `𝒞` (v0.3), in the disconnected trajectory half; S1 and S3, untested since v0.1.

---

*ln1 Notation v0.11 — Cret*

*Base p, nome 1/p, height ln p over 2π. Exact, derived, and provably without complex multiplication.*
