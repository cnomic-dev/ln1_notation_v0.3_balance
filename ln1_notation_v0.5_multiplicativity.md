# ln1 Notation v0.5

**The Multiplicativity Obstruction, and Where the Arithmetic Actually Lives**

Cret, September 2026

---

## 0. What This Addendum Does

v0.4 §8.2 named one decidable question and said it should be settled before anything more was built on the word encoding:

> Does the word for `m·n` relate to the words for `m` and `n`? If not, the number-theoretic applications do not follow.

It is settled. The answer is no, and not because a cleverer encoding is needed — there is a structural obstruction that rules out every possible encoding. This kills the ABC application outright and moves the Riemann application to a different object.

The obstruction also identifies exactly what was missing, which turns out to be a single number.

---

## 1. The Naive Encoding

Under `n ↦ T^n`:

| m | n | T^m · T^n | T^(m+n) | T^(m·n) |
|---|---|---|---|---|
| 2 | 3 | T^5 | T^5 | T^6 |
| 3 | 5 | T^8 | T^8 | T^15 |
| 4 | 7 | T^11 | T^11 | T^28 |

`T^m · T^n = T^(m+n)`, always. The group law is addition. Multiplication is not represented.

This much is obvious. The real question is whether some *other* encoding could do better.

---

## 2. The Obstruction

### 2.1 What Would Be Required

A useful multiplicative encoding is a monoid homomorphism

```
ψ : (ℕ_{>0}, ×) → PSL(2,ℤ)
```

injective on primes. Since `(ℕ, ×)` is the free commutative monoid on the primes, the image would have to contain infinitely many pairwise-commuting elements of infinite order — a free abelian subgroup of rank ≥ 2 at minimum.

### 2.2 What PSL(2,ℤ) Actually Has

Brute-force search over all words of length ≤ 10 for elements commuting with the hyperbolic element `TTST = [[2,1],[1,1]]`:

| word | matrix | \|tr\| |
|---|---|---|
| SS | [[1,0],[0,1]] | 2 (identity) |
| TTST | [[2,1],[1,1]] | 3 |
| STTSTS | [[1,−1],[−1,2]] | 3 |
| TTSTTTST | [[5,3],[3,2]] | 7 |
| STTSTTTSTS | [[2,−3],[−3,5]] | 7 |

Five distinct elements, and every one is a power of `TTST` or its conjugate-inverse. `[[5,3],[3,2]] = [[2,1],[1,1]]²`.

This is the standard fact for `PSL(2,ℤ) ≅ ℤ/2 * ℤ/3`: **the centraliser of an infinite-order element is infinite cyclic.** Free products have this property; it is not an accident of the search depth.

### 2.3 The Conclusion

> **Multiplicativity Obstruction.** In `PSL(2,ℤ)`, any set of pairwise-commuting infinite-order elements lies in a single cyclic subgroup. Hence no free abelian subgroup of rank ≥ 2 exists, and no monoid homomorphism from `(ℕ, ×)` distinguishing two or more primes exists.

No encoding scheme can fix this. It is a property of the group, not of the choice of `ψ`.

---

## 3. Consequence for ABC

ABC is the tension between an additive constraint and a multiplicative one:

```
a + b = c          additive
c vs rad(abc)      multiplicative
```

In the word encoding, the additive side is free:

| (a,b,c) | T^a·T^b | T^c | rad(abc) | quality log c / log rad | ABC hit |
|---|---|---|---|---|---|
| (1, 8, 9) | T^9 | T^9 | 6 | 1.2263 | yes |
| (5, 27, 32) | T^32 | T^32 | 30 | 1.0190 | yes |
| (1, 4374, 4375) | T^4375 | T^4375 | 210 | 1.5679 | yes |
| (2, 3, 5) | T^5 | T^5 | 30 | 0.4732 | no |
| (1, 2, 3) | T^3 | T^3 | 6 | 0.6131 | no |

Every row satisfies `T^a · T^b = T^c` exactly. High-quality triples and worthless ones are indistinguishable in the group. The group law is satisfied identically by all triples, so it carries zero bits about which ones matter.

**The modular group gives ABC no purchase.** The entire content of ABC is in `rad`, and `rad` is multiplicative, and multiplicativity is not in the group.

The proposed mechanism in *ln1 Universal Encoding* §11 — that coprimality corresponds to "slope incompatibility" and this bounds `c` — has no support. Coprimality is a multiplicative property; the group cannot see it.

---

## 4. What Was Missing: One Number

The obstruction points directly at its own cause.

The only natural multiplicative map on matrices is the determinant:

```
det(AB) = det(A) · det(B)
```

`SL(2,ℤ)` is *defined* by `det = 1`. The group was built by discarding the one thing that carries multiplication.

### 4.1 The Fix

Leave the group. Work in the monoid `M₂(ℤ)⁺` of integer matrices with positive determinant. Then

```
det : M₂(ℤ)⁺ → (ℕ, ×)
```

is a surjective monoid homomorphism, and multiplication is carried exactly. The obstruction in §2 does not apply because `M₂(ℤ)⁺` is not a group — no inverses, no centraliser argument.

### 4.2 What This Produces

Classify determinant-`n` matrices modulo `SL(2,ℤ)`. Standard representatives `[[a,b],[0,d]]` with `ad = n`, `0 ≤ b < d`:

| n | # cosets | σ₁(n) |
|---|---|---|
| 1 | 1 | 1 |
| 2 | 3 | 3 |
| 4 | 7 | 7 |
| 6 | 12 | 12 |
| 9 | 13 | 13 |
| 12 | 28 | 28 |

The count is the divisor sum. These cosets are the **Hecke operators** `T_n`.

### 4.3 Multiplicativity Recovered

| m | n | gcd | \|T_m\| | \|T_n\| | product | \|T_mn\| | holds |
|---|---|---|---|---|---|---|---|
| 2 | 3 | 1 | 3 | 4 | 12 | 12 | yes |
| 4 | 9 | 1 | 7 | 13 | 91 | 91 | yes |
| 7 | 11 | 1 | 8 | 12 | 96 | 96 | yes |
| 8 | 9 | 1 | 15 | 13 | 195 | 195 | yes |
| 4 | 6 | 2 | 7 | 12 | 84 | 60 | no |
| 6 | 10 | 2 | 12 | 18 | 216 | 168 | no |

Multiplicative exactly when `gcd(m,n) = 1`. This is the definition of a multiplicative arithmetic function, and it is why Euler products exist:

```
Σ σ₁(n) n^{−s} = ζ(s) · ζ(s−1)
```

which factors over primes. **This is where ζ enters.** Not through group elements — through operators indexed by determinant, one per prime.

---

## 5. Corrected Structural Map

| structure | lives in | mechanism |
|---|---|---|
| addition | `PSL(2,ℤ)` | `T^m · T^n = T^{m+n}` |
| encoding, depth = precision | words in `⟨S,T⟩` | continued fractions |
| rotation, θ | trace of the word | `θ = 2 arccos(\|tr\|/2)` |
| 0 ↔ ∞ exchange | `S(z) = −1/z` | exact involution, `S² = I` |
| **multiplication** | **`det` on `M₂(ℤ)⁺`** | **not available in the group** |
| primes, Euler products | Hecke operators `T_p` | one operator per prime |

Everything v0.4 established about the group stands. What v0.5 adds is that the group is the *additive and geometric* half of the picture only, and the arithmetic half requires leaving it.

---

## 6. Honest Status of the Two Conjectures

### 6.1 ABC

**Dead in this framework, as currently posed.** The additive side is free in the group and the multiplicative side is absent from it. Any ABC approach through Hecke operators would need to express `rad` in terms of them, and `rad` is not a Hecke eigenvalue of anything standard — it is not even multiplicative in the strong sense (`rad(p^k) = p` for all `k`, so it loses all exponent information, which is precisely what ABC is about).

I would not pursue this. The obstruction is not a gap to be filled; it is a mismatch between what the machinery does and what the problem needs.

### 6.2 Riemann

**Not dead, but not supported either, and further away than v0.4 suggested.**

The one structural fact worth keeping: `ζ(s)ζ(s−1)` arises as the Dirichlet series of `σ₁`, which arises from Hecke coset counts. So there is a genuine route from `M₂(ℤ)⁺` to `ζ`. That much is classical and correct.

What does *not* follow, and what I overstated in v0.4 §7:
- The `S` ↔ `s ↦ 1−s` correspondence. Both are involutions with a fixed structure, but the functional equation's involution acts on the *spectral parameter* `s`, while `S` acts on the *upper half plane* `z`. These are different spaces. The coincidence of order 2 is not evidence.
- Any statement that zeros of `ζ` correspond to identifiable group elements. Nothing here produces that.

The honest position: the framework arrives at a place where `ζ` genuinely lives, by a route that is mathematically sound. It has not arrived at any statement about `ζ`'s zeros, and the distance between those two things is the entire difficulty of the Riemann hypothesis.

---

## 7. What Survives Across v0.1–v0.5

Five versions in, this is the ledger.

**Refuted:**
- S2, tendency as a structural property (v0.2, v0.3)
- `(ln1)^(1/(ln1)) = e` and `(1/(ln1))^(ln1) = e` (v0.4)
- alternating towers as an encoding — 2.3 bits, saturated (v0.4)
- multiplicative encoding in `PSL(2,ℤ)` (v0.5)
- the ABC application (v0.5)

**Established:**
- S2′, equilibrium shift under selection bias, across three linking measures (v0.2, v0.3)
- the Stationary Balance Theorem, and the inversion of `𝒜⁺` (v0.3)
- `{0, 1}` closed under both bridge maps (v0.4)
- word encoding in `⟨S,T⟩`: injective, depth = precision, CF-exact (v0.4)
- `θ` derived from trace, `π` from element orders (v0.4)
- the Multiplicativity Obstruction (v0.5)
- multiplicativity via `det` and Hecke operators (v0.5)

**Open:**
- growing `𝒞` as the last route to tendency (v0.3 §7)
- whether the `ln1` encoding has any content beyond re-deriving `⟨S,T⟩`
- S1 and S3, still untested since v0.1

The refuted column is longer than the established one. That is what happens when claims are stated precisely enough to check, and it is the right outcome — each refutation removed a direction that would have consumed effort indefinitely.

---

## 8. The Question I Would Ask Next

Not a next step in the programme, but the question the programme now has to face.

Every structure the `ln1` notation has been shown to produce — `S` and `T`, words, traces, continued fractions — is `PSL(2,ℤ)`, arrived at under different names. The framework's own vocabulary (`0 = ln1`, towers, `n`-th order reciprocal structures, `θ` as control) either mapped onto something already in that group, or failed on measurement.

So: **does the `ln1` layer add anything, or is it a re-notation of the modular group?**

This is answerable. Find one statement expressible in `ln1` notation that is (a) about `⟨S,T⟩`, (b) true, and (c) not a standard modular-group fact. If such a statement exists, the layer is doing work. If every `ln1` statement about the group is either standard or false, the layer is a change of names — which has value for intuition and none for proof.

I do not know the answer. But three of the five versions here ended in refutation, and the survivors were all things the modular group already knew. That is the pattern to check against.

---

*ln1 Notation v0.5 — Cret*

*The group carries addition and geometry. Arithmetic needed the determinant, and the group had set it to 1.*
