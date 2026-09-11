# The Exact-Fraction Audit — Completion

**The Third Class: Algebraic Irrationals as Roots, Not Ratios**

Cret, September 2026

---

## 0. What Was Missing

The prior audit sorted every number in the project into two classes: exactly rational (the structural results) and provably transcendental (the coordinates). One kind of number fell through the gap — the "small linear form" near-misses from v0.8 and v0.11, which are neither.

This closes that gap and completes the audit.

---

## 1. The Comma Was Never a Decimal

v0.8 described `2¹⁹/3¹²` as a "small ε ≈ 0.0135." That description was already a decimal-flavoured way of stating an exact integer fact.

```
2¹⁹ = 524288
3¹² = 531441
comma = 3¹²/2¹⁹ = 531441/524288       (gcd = 1, already reduced)
```

This is a ratio of integers with no approximation anywhere in it. "Smallness" is a statement about how close this exact fraction sits to `1` — not a decimal awaiting reduction. My earlier phrasing obscured that the object was exact from the start.

---

## 2. The Exponents Are a Fraction Too: log₂3

Why 19 and 12 specifically? Because they are a convergent of `log₂3`:

```
log₂3 = 1.584962500721156        CF = [1; 1, 1, 2, 2, 3, 1, 5, 2, 23]
```

| convergent | comparison | error |
|---|---|---|
| 1 | 2¹ vs 3¹ | 0.585 |
| 3/2 | 2² vs 3³ | 0.085 |
| 8/5 | 2⁵ vs 3⁸ | 0.015 |
| **19/12** | **2¹² vs 3¹⁹** | **0.0016** |

`19/12` is the convergent of `log₂3` immediately preceding the comma. **This is not a coincidence to marvel at — it is the definition of a best rational approximation.** Every "surprisingly good" prime-power near-miss anywhere in this project is a continued-fraction convergent of some `log_p(q)`, by construction of the CF algorithm. The comma looks special because convergents are, by definition, unusually good; it is not special beyond that.

---

## 3. The t=47 Near-Miss, Done Exactly

v0.11 found that `ε²` (trace 2207, norm 1) sits within `2×10⁻⁷` of `ln 2207` and flagged it as a near-coincidence rather than an identity. Here is its actual exact form.

`ε²` is a root of `x² − 2207x + 1 = 0`:

```
discriminant = 2207² − 4 = 4870845 = 987²·5
             ⟹ √4870845 = 987√5

ε² = (2207 + 987√5) / 2
```

verified: `2207² − 4 = 4,870,845` and `987² × 5 = 4,870,845` — exact match.

**This is the correct generalisation of 分子分母 to a number that is algebraic but not rational: not a ratio of integers, but a root of an exact integer polynomial.** `ε²` is neither a fraction nor a decimal — it is a surd, stated completely by two integers (2207 and 987) and a square root. Nothing here is approximate.

---

## 4. The Complete Classification

Every number encountered across twelve versions of this project falls into exactly one of three classes, each with its own correct exact form:

| class | exact form | examples from this project |
|---|---|---|
| **rational** | `p/q` | nomes `1/p`, `ln ζₙ/2πi = j/n`, `ζ(−1) = −1/12`, `𝒜⁺ = 1/2` |
| **algebraic irrational** | root of an integer polynomial | `ε² = (2207+987√5)/2`; any fundamental unit of a real quadratic field |
| **transcendental** | continued fraction (exact as a process, not a single ratio) | `ln p / 2π`, `π`, `e`, `τ_p` |

The demand "express every decimal as numerator over denominator" is fully satisfiable — but only once it is understood as a demand for **the correct exact form for the kind of number in question**, not literally as a demand that everything be `p/q`. A transcendental number has no `p/q`; forcing one would misstate what kind of number it is. Its continued fraction is the exact and complete representation, realized as an infinite process rather than a terminating ratio.

---

## 5. Closing Note

With this, the fraction audit is complete: every number that appeared anywhere in versions v0.1 through v0.12, and in the write-up, now has a stated exact form appropriate to its type, and every prior appearance of an unreduced decimal (`ε ≈ 0.0135`, `2×10⁻⁷`) has been traced back to what it actually was.

The instruction turned out to be doing real evaluative work three times over: it separated structure from coordinate (prior audit), it explained why the "surprising" near-misses were not surprising (§2 here), and it supplied the right notion of exactness — polynomial root, not ratio — for the one class of number that a literal reading would have missed entirely.

---

*Cret, September 2026*
