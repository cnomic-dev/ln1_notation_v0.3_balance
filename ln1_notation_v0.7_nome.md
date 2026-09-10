# ln1 Notation v0.7

**The Prime 2 as Nome, Multiplicativity Recovered, and Where the Framework Actually Sits**

Cret, September 2026

---

## 0. What This Addendum Does

v0.6 ended with one testable proposal: read "原點可定位在質數2上" as supplying the second period, rather than as a labelling convention. It is tested here. It works, and it works better than I expected — it also resolves the v0.5 Multiplicativity Obstruction, by a route that shows why that obstruction was self-inflicted.

Then it places the result honestly, which is the less comfortable half.

---

## 1. The Prime as Nome

`ln1` supplies `ω₂ = 2πi`. Read the prime as supplying `ω₁ = ln q`:

```
Λ = (ln q)·ℤ + 2πi·ℤ        τ = ω₂/ω₁ = 2πi / ln q
```

| q | τ | Im τ |
|---|---|---|
| 2 | 9.064720i | 9.064720 |
| 3 | 5.719202i | 5.719202 |
| 5 | 3.903963i | 3.903963 |
| 7 | 3.228919i | 3.228919 |
| 11 | 2.620292i | 2.620292 |
| 13 | 2.449633i | 2.449633 |

Every prime gives a genuine rank-2 lattice, and every one lands in the upper half plane. **The rank problem is solved from inside the notes.** No constant is imported; the second period is the thing the notes already put at the origin.

### 1.1 What the Quotient Is

```
ℂ / (ln q·ℤ + 2πi·ℤ)  ≅  ℂ* / q^ℤ
```

For `|q| ≠ 1` this is the **Tate curve** — an elliptic curve, genus 1, with `SL(2,ℤ)` acting on its period lattice. This is a standard classical object, not an invention.

Contrast with v0.6: `ln1` alone gave `ℂ*`, genus 0, no group action. Adding the prime raises the genus by one and turns the modular group on.

### 1.2 The Degenerate Case Is Exactly q = 1

`q = 1` gives `τ = 0`, `Im τ = 0`. The lattice collapses. This is why five versions of work on `ln1` alone could not reach anything modular: the argument of the logarithm was `1`, and that is precisely the degenerate value.

The notes' instruction to place the origin at a prime, not at 1, was doing real work.

---

## 2. Multiplicativity, Recovered

v0.5 proved that `PSL(2,ℤ)` cannot carry `(ℕ, ×)` — no free abelian subgroup of rank ≥ 2. That proof stands. But look at the reciprocal of the modular parameter:

```
1/τ_n = ln(n) / 2πi
1/τ_{mn} = ln(mn)/2πi = (ln m + ln n)/2πi = 1/τ_m + 1/τ_n
```

| m | n | 1/τ_m | 1/τ_n | sum | 1/τ_mn |
|---|---|---|---|---|---|
| 2 | 3 | 0.110318 | 0.174850 | 0.285167 | 0.285167 |
| 4 | 9 | 0.220636 | 0.349699 | 0.570335 | 0.570335 |
| 6 | 10 | 0.285167 | 0.366468 | 0.651635 | 0.651635 |
| 8 | 9 | 0.330953 | 0.349699 | 0.680653 | 0.680653 |

Exact for all `m, n` — **with no coprimality condition**, unlike the Hecke route in v0.5 which only worked when `gcd(m,n) = 1`.

```
ln : (ℕ, ×) → (ℂ/2πiℤ, +)
```

is an injective monoid homomorphism. This is the multiplicative encoding the framework was after for five versions.

### 2.1 Why the Obstruction Was Self-Inflicted

```
v0.5:  PSL(2,ℤ) has no free abelian subgroup of rank ≥ 2.
v0.7:  (ℝ, +) has one of countably infinite rank, spanned by {ln p}.
```

`{ln p : p prime}` is ℚ-linearly independent, by unique factorisation. The infinite rank that `PSL(2,ℤ)` structurally could not have is sitting in the additive reals, and the logarithm is the map to it.

The obstruction was never that arithmetic is hard to encode. It was that I had gone looking for it in a group whose operation was wrong. The framework's own primitive — the logarithm — does it directly, and does it because converting multiplication to addition is what logarithms are for.

That is embarrassing in a specific way worth recording: v0.4 and v0.5 spent two versions in `PSL(2,ℤ)` because I introduced `S` and `T` and then treated the group as though the framework had produced it. The framework's actual content was the log, which was in the first line of the notes.

---

## 3. Where This Lands: Linear Forms in Logarithms

The encoding is faithful. Does it bite on anything?

For `a + b = c` with `a ≪ b`:

```
b/c = 1 − a/c    ⟹    Λ = ln(b/c) ≈ −a/c
```

and `ln(b/c)` is a ℤ-linear combination of `ln p` over the primes dividing `b` and `c`.

| (a,b,c) | Λ = ln(b/c) | −a/c | quality |
|---|---|---|---|
| (1, 8, 9) | −0.117783035656 | −0.111111111111 | 1.2263 |
| (1, 48, 49) | −0.020619287203 | −0.020408163265 | 1.0412 |
| (1, 4374, 4375) | −0.000228597555 | −0.000228571429 | 1.5679 |
| (1, 512, 513) | −0.001951220131 | −0.001949317739 | 1.3176 |
| (2, 3¹⁰·109, 23⁵) | −0.000000310735506659 | −0.000000310735459561 | 1.6299 |

Agreement to ten significant figures, from `ln(1−x) = −x − x²/2 − ⋯`.

### 3.1 The Best-Known Triple, Explicitly

```
(a, b, c) = (2, 3¹⁰·109, 23⁵) = (2, 6436341, 6436343)

Λ = +10·ln 3  − 5·ln 23  + 1·ln 109
  = −0.000000310735506659

support = {3, 23, 109},   height max|eᵢ| = 10,   quality = 1.629912
```

A ℤ-linear form in three of the infinitely many independent generators, sitting within `3·10⁻⁷` of zero.

Baker's theorem bounds from below how small such a form can be:

```
|Σ eᵢ ln pᵢ|  >  exp( −C(n) · ∏ ln pᵢ · ln max|eᵢ| )
```

ABC forces it small; Baker forbids it from being too small. The gap between those two bounds *is* effective ABC.

**So the framework's log layer does see `rad`** — the prime support of the linear form is exactly the radical, and the number of terms is what Baker's constant depends on. v0.5 was right that `PSL(2,ℤ)` cannot see `rad`; v0.7 shows the log can.

---

## 4. The Honest Placement

This is where the intellectual honesty has to come in, because the result above is real and the temptation to overclaim it is strong.

**Linear forms in logarithms is Baker's theory, from 1966.** The S-unit equation approach to ABC is standard Diophantine machinery. It yields *weak* effective ABC — bounds far too large to approach the conjecture, and known to be far from it for structural reasons that are themselves well studied.

So the honest statement of what happened across seven versions:

> The framework's log structure is real mathematics, arrived at by a route that was its own, and it lands in a place that was already occupied fifty years ago.

That is a substantially better outcome than the tower route (2.3 bits, refuted) or the group route (structurally obstructed, refuted). Those were wrong. This is right and not new.

Whether "right and not new" is worth having depends on what the framework is for. As a proof strategy for ABC, no — it arrives at machinery whose limits are known. As a conceptual organisation that reaches Baker's setting from `0 = ln1` and "origin at a prime," it is coherent and it is yours. Those are different claims and should not be conflated.

---

## 5. Corrected Structural Map

| structure | lives in | mechanism | status |
|---|---|---|---|
| branch index, "n階" | `2πiℤ` | sheets of `ln` | ✅ v0.6 |
| θ, rotation | `arg = 2πk` | winding number | ✅ v0.6 |
| 0 ↔ ∞ | `k → ±∞` | same object, one index | ✅ v0.6 |
| second period | `ln q`, q prime | the origin at 2 | ✅ v0.7 |
| genus 1, `SL(2,ℤ)` acts | Tate curve `ℂ*/q^ℤ` | rank-2 lattice | ✅ v0.7 |
| **multiplication** | `ln : (ℕ,×) → (ℂ/2πiℤ,+)` | the logarithm itself | ✅ v0.7 |
| infinite rank | `{ln p}` ℚ-independent | unique factorisation | ✅ v0.7 |
| ABC contact | small linear forms in logs | Baker / S-units | ⚠️ real but standard |
| ABC proof | — | — | ❌ no route |
| Riemann | — | — | ❌ no route shown |

---

## 6. The Ledger, v0.1–v0.7

**Refuted:** S2 as structural tendency (v0.2–v0.3); both bridges equal `e` (v0.4); alternating towers as encoding (v0.4); multiplicative encoding in `PSL(2,ℤ)` (v0.5); ABC via the group (v0.5); the framework reaching `PSL(2,ℤ)` at all (v0.6).

**Established:** S2′ equilibrium shift (v0.2–v0.3); Stationary Balance Theorem and the `𝒜⁺` inversion (v0.3); `{0,1}` closed under both bridges (v0.4); Multiplicativity Obstruction (v0.5); `ln1 = 2πiℤ` and the vindication of `ln1 ≠ ln1` (v0.6); **the prime as second period, Tate curve, and multiplicativity via `ln`** (v0.7).

**Open:** growing `𝒞` (v0.3); S1 and S3, untested since v0.1; whether anything in the framework distinguishes it from Baker's setting.

---

## 7. What I Would Do Next, and What I Would Not

**Would not:** pursue ABC through this. The machinery it reaches has known limits, and those limits are not a matter of insufficient effort.

**Would:** check whether the *choice of prime* matters. Each prime `q` gives a different `τ_q`, hence a different Tate curve, hence a different `j`-invariant. The notes say the origin "可隨意調整位置" — freely adjustable. If that freedom is real, the framework is claiming all these curves are equivalent, which is false (they have different `j`). If it is not free, then the choice of 2 is load-bearing and the notes should say why 2 specifically.

That is a sharp, answerable question about the notes rather than about mathematics, and it decides whether §1 is a structure or a convention.

**Would also:** note that the trajectory-algebra half of this project (v0.1–v0.3, `Λ`, `𝒜⁺`, the balance theorem) is entirely disconnected from the number-theory half (v0.4–v0.7). Nothing links them. The unified-framework document I wrote earlier asserted a four-layer hierarchy connecting them; that assertion has no support and I should not have made it. They are two separate investigations that share a name.

---

## 8. Note on Method

Seven versions. The pattern that emerged:

Every construct in the notes that I dismissed as an error turned out to be load-bearing (`ln1 ≠ ln1`, the origin at 2). Every construct I supplied to "fix" the framework turned out to be a detour (`e`, `S` and `T`, the four-layer hierarchy). The notes were more right than my corrections, and specifically right in the places that looked most wrong.

The reverse also held: every claim in the notes that made a *quantitative* promise — towers encoding information, slope incompatibility bounding ABC — failed on measurement, and failed decisively.

The distinction seems to be between structural intuitions, which were good, and mechanical proposals, which were not. That is a useful thing to know going forward about where to spend checking effort.

---

*ln1 Notation v0.7 — Cret*

*The multiplication was in the logarithm the whole time. It took two versions inside the wrong group to notice.*
