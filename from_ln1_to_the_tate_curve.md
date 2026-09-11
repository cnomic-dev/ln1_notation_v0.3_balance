# From ln1 to the Tate Curve

**An Exact Derivation in Five Steps**

Cret, September 2026

---

## Abstract

Two lines of an informal notation — that `ln1` is simultaneously equal and unequal to itself, and that the origin may be placed at a prime — determine, with no further input, the Tate curve `ℂ*/p^ℤ` with nome exactly `1/p`. This note gives the derivation, states precisely what it does and does not yield, and proves by Baker's theorem that no curve in the resulting family has complex multiplication.

Nothing here is new mathematics. The content is that a short informal notation determines a specific classical object exactly, and the derivation is five steps.

---

## 1. The Starting Notation

Two assertions, taken verbatim from the source notation:

```
(N1)    ln1 = ln1     and     ln1 ≠ ln1
(N2)    原點，表示0，可定位在質數2上
        the origin, representing 0, may be placed at the prime 2
```

(N1) reads as a contradiction under the assumption that `ln1` denotes a number. It does not.

---

## 2. Step One — ln1 Is a Set

Over `ℂ` the logarithm is multivalued:

```
ln(z) = ln|z| + i(arg z + 2πk),   k ∈ ℤ
```

At `z = 1`, `|z| = 1` and `arg z = 0`, so

```
ln(1) = 2πik,   k ∈ ℤ
```

| k | ln(1) |
|---|---|
| −1 | −6.28318530718i |
| 0 | 0 |
| 1 | 6.28318530718i |
| 2 | 12.5663706144i |

and `exp(2πik) = 1` for every `k` (verified to 25 digits).

So `ln1 = ln1` holds as an identity of expressions and `ln1 ≠ ln1` holds as a statement about branches. **(N1) is the definition of a multivalued function, stated correctly.**

```
ln1 = 2πi·ℤ = ker( exp : ℂ → ℂ* )
```

`ln1 = 0` is the principal branch, `k = 0`, and only that.

---

## 3. Step Two — It Has Rank 1, and That Is Not Enough

`2πiℤ` is a rank-1 lattice on the imaginary axis. Its quotient is

```
ℂ / 2πiℤ  ≅  ℂ*     (via exp)
```

a cylinder: genus 0. `SL(2,ℤ)` does not act, because a rank-1 lattice has no basis to change.

The real unit is not available either. Over `k ∈ [−200, 200]`,

```
min |2πik − 1| = 1.0,   attained at k = 0
```

`2πik` is purely imaginary for `k ≠ 0` and `0` otherwise, so `1` is never reached. Since `ln(e) = 1 + 2πik`, the constant `e` is **not** a value of this lattice. It is the generator of the other axis:

```
ℂ = ℝ·1 ⊕ ℝ·(2πi)
```

`e` and `2πi` are the two real generators of `ℂ`, and neither is derivable from the other. This is also the content of `e^{2πi} = 1` — the same statement as `ker(exp) = 2πiℤ`, written differently.

**A second, independent period is required.**

---

## 4. Step Three — The Prime Supplies It

A pair `ω₁, ω₂` spans a lattice iff `τ = ω₂/ω₁ ∉ ℝ`. Take `ω₂ = 2πi` from (N1) and, per (N2), `ω₁ = ln p`:

```
Λ_p = (ln p)·ℤ + 2πi·ℤ        τ_p = 2πi / ln p
```

| p | τ_p | Im τ_p |
|---|---|---|
| 2 | 9.064720284i | > 0 ✓ |
| 3 | 5.719201735i | > 0 ✓ |
| 5 | 3.903962532i | > 0 ✓ |
| 7 | 3.228918514i | > 0 ✓ |
| 13 | 2.449633280i | > 0 ✓ |

Every prime gives a genuine rank-2 lattice in the upper half plane.

**The degenerate case is exactly `p = 1`:** `ln 1 = 0`, `τ` undefined, lattice collapses. This is why (N1) alone cannot reach a modular parameter — its argument is `1`, the one value that fails — and why (N2)'s instruction to move the origin to a prime is load-bearing rather than cosmetic.

### 3.1 Equivalently: Change of Logarithm Base

```
log_b(z) = ln(z)/ln(b)    ⟹    ker(log_b) = (2πi/ln b)·ℤ
```

The period of `log` base `b` is `2πi/ln b = τ_b`. So *placing the origin at p* and *using logarithm base p* are the same operation. This also shows base change is not a free relabelling: different bases give different lattices, hence different curves.

---

## 5. Step Four — The Quotient Is the Tate Curve, with Nome Exactly 1/p

```
ℂ / Λ_p  ≅  ℂ* / p^ℤ
```

For `|p| ≠ 1` this is the Tate curve: an elliptic curve, genus 1, with `SL(2,ℤ)` acting on its period lattice.

Reduce `τ_p` to the fundamental domain by `S : τ ↦ −1/τ`:

```
S·τ_p = i·ln(p)/2π
```

| p | −1/τ_p | ln(p)/2π | agree |
|---|---|---|---|
| 2 | 0.110317800076i | 0.110317800076 | ✓ |
| 3 | 0.174849576283i | 0.174849576283 | ✓ |
| 13 | 0.408224369020i | 0.408224369020 | ✓ |

The **height** of `p` in the fundamental domain is `ln(p)/2π`.

The nome at that point:

| p | q = e^{2πiτ} | 1/p | agree |
|---|---|---|---|
| 2 | 0.5 | 0.5 | ✓ |
| 3 | 0.3333333333333333 | 0.3333333333333333 | ✓ |
| 5 | 0.2 | 0.2 | ✓ |
| 7 | 0.1428571428571429 | 0.1428571428571429 | ✓ |
| 13 | 0.07692307692307692 | 0.07692307692307692 | ✓ |
| 101 | 0.009900990099009901 | 0.009900990099009901 | ✓ |

```
q = e^{2πiτ}|_{τ = i·ln(p)/2π} = e^{−ln p} = 1/p        exactly
```

> **Result.** Origin at the prime `p` ⟺ logarithm base `p` ⟺ nome `q = 1/p` ⟺ the Tate curve `ℂ*/p^ℤ`, at height `ln(p)/2π` in the fundamental domain.

Three separate lines of the source notation are one operation.

As `p → ∞`, `τ_p → 0` and the height `→ ∞`: the family marches up the imaginary axis and accumulates at the cusp. Counting in the height coordinate, `N(T) = π(e^{2πT}) ~ e^{2πT}/2πT`, which is the prime number theorem in this coordinate.

---

## 6. Step Five — No Curve in the Family Has Complex Multiplication

Complex multiplication requires `τ` imaginary quadratic. Here `τ_p = i·ln(p)/2π`, so CM would require `ln(p)/π` algebraic, equivalently a relation

```
α·ln p + β·(2πi) = 0,   α, β algebraic, not both zero
```

Both `2πi = log(1)` and `ln p = log(p)` are logarithms of algebraic numbers. **Baker's theorem** states that a nonvanishing algebraic linear form in logarithms of algebraic numbers is nonzero. No such relation exists.

```
⟹ ln(p)/π is transcendental for every prime p
⟹ no τ_p is imaginary quadratic
⟹ no curve in the family has complex multiplication
⟹ j(τ_p) is transcendental for every prime p
```

Near-misses are only density — rationals times square roots are dense in `ℝ`, and density is not equality.

### 5.1 What This Excludes

CM points are where the arithmetic in this area is concentrated: singular moduli are algebraic integers, class fields of imaginary quadratic fields are generated explicitly, and Kronecker's Jugendtraum is that theory. All of it requires `τ` imaginary quadratic.

The family `{τ_p}` provably contains no such point. It is a path of Tate curves accumulating at the cusp with no extra arithmetic structure anywhere along it.

---

## 7. What This Does and Does Not Give

**Gives, exactly:**

- `ln1 = 2πiℤ`, the branch lattice, with `ln1 ⊗ ℚ = ln(μ_∞)` — the ℚ-span of logarithms of roots of unity, and nothing else
- `θ` as the branch index `2πk`: a winding number, discrete, derived rather than posited
- `i`, `−1`, every `ζₙ` free, since `ln ζₙ = 2πi·(j/n)`
- `πi` as a welded unit; separating `π` from `i` costs exactly one degree-2 extension, `√−1`
- base `p` = nome `1/p` = the Tate curve, exactly, with height `ln(p)/2π`

**Does not give:**

- `e`, or the real unit `1` — the second generator, not derivable from the first
- `ln p` for any prime, from `ln1` alone — each prime is an independent period
- rank above 2 in `ℂ`: a discrete subgroup of `ℝ²` has rank ≤ 2, so a second prime destroys the lattice (`ℤ·ln2 + ℤ·ln3` is already dense in `ℝ`)
- complex multiplication, by §6
- any dimensionful physical constant — `ħ` takes four different numerical values in four unit systems, so the question has no answer rather than a hard one

**The rank ceiling is the binding constraint.** Arithmetic needs infinite rank (`{ln p}` is ℚ-linearly independent). Geometry needs discreteness (rank ≤ 2 per complex dimension). These cannot both hold in fixed finite dimension. One prime per curve is not a limitation of the derivation; it is the maximum.

---

## 8. Status

Every step above is classical. Multivaluedness of `log` is elementary; the Tate curve is standard; Baker's theorem is 1966. Nothing in this note is new mathematics, and the derivation should not be read as claiming otherwise.

What the note establishes is narrower and, I think, still worth recording: **a two-line informal notation determines a specific classical object exactly, by a five-step derivation with no free parameters.** The nome comes out as `1/p` on the nose. That is a real fact about the notation, and it is the kind of thing that is easy to assert loosely and hard to pin down, so pinning it down has some value.

It is also the boundary. The family it produces avoids, provably, the part of the landscape where arithmetic content lives. Routes from here to the ABC conjecture or the Riemann hypothesis are blocked by three separate theorems — the rank ceiling, the absence of a multiplicative encoding in `PSL(2,ℤ)`, and the CM obstruction above. Those are not gaps awaiting more work.

---

## Verification

All numerical claims were checked to 30 significant digits: the branch values of `ln(1)`; `exp(2πik) = 1`; `min|2πik − 1| = 1`; `Im τ_p > 0` for the listed primes; `−1/τ_p = i·ln(p)/2π`; and `q = 1/p` for `p ∈ {2,3,5,7,13,101}`. Every check passed.

---

*Cret, September 2026*
