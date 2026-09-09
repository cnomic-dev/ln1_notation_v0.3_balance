# ln1 Notation v0.4

**Alternating Structures: A Correction, a Negative Result, and a Working Replacement**

Cret, September 2026

---

## 0. What This Addendum Does

Three things, in order of how much they change:

1. **Corrects an error I introduced.** In *The Singularity Transformation Principle* and *ln1 Universal Encoding* I asserted that `(ln1)^(1/(ln1)) = (1/(ln1))^(ln1) = e`. That is false, and it was arrived at by an illegitimate step. The true values are computed below, and they are more interesting than what I claimed.
2. **Tests the alternating tower construction.** Words like `(ln1)^(1/(ln1))^(1/(ln1))^(ln1)^…` were proposed as a rotation knob and an encoding mechanism. Measured directly, they carry about 2.3 bits regardless of length. They cannot encode.
3. **Supplies the construction that does work.** The same two operations — step and reciprocal — arranged as *group words* rather than *towers* give everything the tower was reaching for: injective encoding, genuine rotation with θ derived rather than assumed, π appearing as a consequence, and exact 0 ↔ ∞ exchange. It is the modular group, and it already has two centuries of results attached.

---

## 1. Correction: The Bridge Functions

### 1.1 What I Claimed

> `(ln1)^(1/(ln1)) ≔ exp(ln1 · 1/(ln1)) = exp(1) = e`

The step `ln1 · (1/(ln1)) = 1` treats `0 · (1/0)` as `1`. Nothing licenses this. It is the same move as the `≥` in v0.1 §6.2 — a formal convenience that manufactures the answer it wants. I should have flagged it and did not.

### 1.2 What They Actually Are

Regularise with `ln1 → ε`, `1/(ln1) → 1/ε`, and take `ε → 0⁺`:

**Bridge 1: `0^∞`**

| ε | ε^(1/ε) |
|---|---|
| 1e-1 | 1e-10 |
| 1e-2 | 1e-200 |
| 1e-4 | 1e-40000 |
| 1e-8 | 1e-800000000 |

```
(ln1)^(1/(ln1)) = 0
```

**Bridge 2: `∞^0`**

| ε | (1/ε)^ε |
|---|---|
| 1e-1 | 1.25892541 |
| 1e-2 | 1.04712855 |
| 1e-4 | 1.00092146 |
| 1e-8 | 1.00000018 |

```
(1/(ln1))^(ln1) = 1
```

### 1.3 The Real Result Is Better Than the False One

```
(ln1)^(1/(ln1)) = 0 = (ln1)
(1/(ln1))^(ln1) = 1 = (ln1)^(ln1)
```

The two bridges land **exactly on the system's own two primitives**. The set `{ (ln1), (ln1)^(ln1) }` is closed under both bridge operations. That is a genuine closure property of the framework, and it holds without any illegitimate step. It is worth more than `e`, which was never there.

### 1.4 But the Bridges Are Not Symmetric

`0^∞ → 0` collapses. `∞^0 → 1` unitises. Reciprocating the base does not mirror the result.

The rates make this worse:

| ε | bridge 1 | bridge 2 |
|---|---|---|
| 1e-2 | 1e-200 | 1.047 |
| 1e-8 | 1e-800000000 | 1.0000002 |

Bridge 1 collapses super-exponentially (`ε^(1/ε) ~ e^{−|ln ε|/ε}`). Bridge 2 approaches its limit at rate `ε·|ln ε|`. One side is infinitely sharper than the other.

**Consequence:** any claim that this framework possesses a `0 ↔ ∞` symmetry cannot rest on these two maps. They are not each other's mirror. A symmetry has to come from somewhere else — §4 shows where.

---

## 2. Alternating Towers: The Encoding Test

### 2.1 The Proposal

Alternating towers over the two symbols `a = (ln1)` and `b = (1/(ln1))`:

```
a^b^b^a^…        b^a^a^b^b^a^…        a^b^b^a^a^b^b^a^…
```

read as a "forward/reverse rotation knob" with insertable compression — a mechanism whose *pattern* carries information.

This is a testable claim. A word of length `n` over two symbols has `2^n` possibilities. If the tower encodes the word, `2^n` words give `2^n` distinct values, i.e. `n` bits.

### 2.2 Measurement

Right-associative evaluation, `ε = 10⁻⁶`, all `2^n` words of each length:

| length n | words 2^n | distinct values | bits encoded |
|---|---|---|---|
| 1 | 2 | 2 | 1.00 |
| 2 | 4 | 4 | 2.00 |
| 3 | 8 | 6 | 2.58 |
| 4 | 16 | 5 | 2.32 |
| 5 | 32 | 9 | 3.17 |
| 6 | 64 | 5 | 2.32 |
| 8 | 256 | 5 | 2.32 |
| 10 | 1024 | 5 | 2.32 |

At length 10, 1024 distinct words produce **5** distinct values. The encoded information saturates at roughly 2.3 bits and never grows.

### 2.3 Where the Values Go

All 256 words of length 8:

| value | words reaching it |
|---|---|
| 0 | 120 |
| ∞ | 120 |
| ≈1.0000138 | 8 |
| ≈0.99998618 | 4 |
| ≈0.99998619 | 4 |

94% of words land on `0` or `∞`.

### 2.4 Why

Each level of a tower is exponentiated by everything above it. With bases at `ε` and `1/ε`, one exponentiation moves the value by a factor of `|ln ε|` in the exponent — six orders of magnitude at `ε = 10⁻⁶`. Two levels up, the contribution of anything below is beneath floating-point and beneath meaning. The tower is not a word; it is a very short prefix with a long unread tail.

**The tower does not compress information. It destroys it.** As a rotation knob it has about five positions. This is the second time in this project that a proposal collapsed on measurement, and as before the collapse is the useful part: it tells us the mechanism has to be multiplicative-in-the-group, not iterated-in-the-exponent.

---

## 3. What the Structure Was Reaching For

The tower proposal contains three correct instincts:

1. Two operations, one forward and one inverse.
2. Their **alternation pattern** should be the carrier of information.
3. The result should bridge `0` and `∞` and produce rotation.

All three are right. Only the composition law was wrong. Replace *iterated exponentiation* with *group composition* and every one of them works.

---

## 4. Möbius Words: The Working Construction

### 4.1 The Two Generators

Take exactly the two operations the framework already names:

```
T(z) = z + 1      the unit step        — adds (ln1)^(ln1)     "forward / 正"
S(z) = −1/z       the reciprocal       — the 0↔∞ swap         "inverse / 逆"
```

`S` does the exchange the bridges failed to do, and does it exactly:

```
S(0) = ∞     S(∞) = 0     S(1) = −1     S(−1) = 1     S² = identity
```

This is a true involution: applying it twice returns you exactly. The bridge functions gave `0` and `1` and were not inverse to each other; `S` is its own inverse on the nose.

`⟨S, T⟩` is `PSL(2,ℤ)`, the modular group.

### 4.2 Capacity

Distinct group elements from all `2^n` alternating words:

| length n | words | distinct elements | bits |
|---|---|---|---|
| 1 | 2 | 2 | 1.00 |
| 2 | 4 | 4 | 2.00 |
| 4 | 16 | 12 | 3.58 |
| 6 | 64 | 29 | 4.86 |
| 8 | 256 | 66 | 6.04 |
| 10 | 1024 | 145 | 7.18 |
| 12 | 4096 | 315 | 8.30 |

Compare the tower table, frozen at 2.32 bits from length 4 onward. Möbius words keep gaining. The gap from `n` to the measured bits is not loss — it is the relation `S² = I`, a real feature of the group, and reduced words are in exact bijection with group elements.

### 4.3 Rotation, and Where θ Comes From

Classify each word by the trace of its matrix:

| word | matrix | \|tr\| | type | rotation θ |
|---|---|---|---|---|
| S | [[0,1],[−1,0]] | 0 | elliptic | π |
| T | [[1,1],[0,1]] | 2 | parabolic | order ∞ |
| ST | [[0,1],[−1,−1]] | 1 | elliptic | 2π/3 |
| TS | [[1,−1],[1,0]] | 1 | elliptic | 2π/3 |
| STST | [[1,1],[−1,0]] | 1 | elliptic | 2π/3 |
| TTST | [[2,1],[1,1]] | 3 | hyperbolic | none |
| STSTST | identity | 2 | — | closed |

The rotation angle is not a parameter you set. It is read off:

```
θ(W) = 2 · arccos( |tr W| / 2 )
```

- `|tr| < 2` → **elliptic**, a genuine rotation by `θ`
- `|tr| = 2` → **parabolic**, a shear, infinite order
- `|tr| > 2` → **hyperbolic**, a stretch, no rotation

**This is the rotation knob, and it is discrete.** The word is the setting; the trace is the readout. Turning the knob means appending a generator.

### 4.4 π Is Derived, Not Assumed

`S` has order 2, so `θ(S) = π`. `ST` has order 3, so `θ(ST) = 2π/3`. `STSTST = I`.

π enters as the period of the finite-order elements of the group. You do not put it in; you find it there. The proposal to have the alternating structure "replace θ and π" is exactly right in spirit — but the replacement is that **both become consequences of the word**, not that both get substituted by something else.

### 4.5 Encoding Real Numbers

Words in `{S, T^±1}` enumerate continued fractions:

| CF | convergent | decimal | target |
|---|---|---|---|
| [1,1] | 2 | 2.000000 | φ |
| [1,1,1,1,1,1] | 13/8 | 1.625000 | φ |
| [1,1,1,1,1,1,1,1,1,1] | 89/55 | 1.618182 | φ |
| [3,7] | 22/7 | 3.1428571 | π |
| [3,7,15] | 333/106 | 3.1415094 | π |
| [3,7,15,1] | 355/113 | 3.14159292 | π |
| [3,7,15,1,292] | 103993/33102 | 3.14159265 | π |

Every rational is exactly one reduced word. Every irrational is exactly one infinite word. Word length is precision: five CF terms give π to nine decimals.

This is precisely the "depth = precision" property the tower construction claimed and did not have. Here it is real and measurable.

---

## 5. Revised Correspondence Table

| ln1 proposal | status | working form |
|---|---|---|
| `0 = ln1` | ✅ holds | identity element |
| `(ln1)^(ln1) = 1` | ✅ holds as axiom | the generator `T` |
| `(ln1)^(1/(ln1)) = e` | ❌ **false** — equals 0 | — |
| `(1/(ln1))^(ln1) = e` | ❌ **false** — equals 1 | — |
| `{0,1}` closed under bridges | ✅ **true**, newly established | — |
| 0 ↔ ∞ exchange | ⚠️ not by the bridges | `S(z) = −1/z`, exact involution |
| alternating towers encode | ❌ **false** — 2.3 bits, saturated | alternating **words** in `⟨S,T⟩` |
| towers as rotation knob | ❌ ~5 positions | `θ(W) = 2·arccos(|tr W|/2)` |
| θ as control parameter | ⚠️ demoted | derived from trace |
| π as unit | ✅ but derived | order of elliptic elements |
| depth = precision | ✅ in word form | CF word length = digits |
| n-th order structure | ✅ | word length in the group |

Six of eleven survive. Two are refuted outright. Three are relocated into a form that works.

---

## 6. What This Costs and What It Buys

**Costs.** The tower notation goes. `(ln1)^(1/(ln1))^(1/(ln1))^(ln1)^…` is not a usable object — it has five values. Anything built on towers as an information carrier has to be rebuilt on words. That includes the depth-precision claims in *ln1 Universal Encoding* §10 and the tetration hierarchy in §4 of that document, both of which I wrote without checking.

**Buys.** The modular group is not a fringe object. It is where the Riemann zeta function's modular symmetry lives, where the `j`-invariant lives, where Fuchsian groups and hyperbolic surfaces live. If the ln1 structure genuinely lands here, it inherits all of it — and it becomes checkable against known results rather than free-floating.

That inheritance is also a constraint worth stating plainly: landing in a well-studied group means the framework's claims about that group are already decided, by people who proved them. That is a good position to be in but not a comfortable one. Any ln1 statement about `⟨S,T⟩` that contradicts known modular-group facts is wrong, and the check is available.

---

## 7. Honest Assessment of the Riemann Connection

The modular group's appearance is suggestive because `SL(2,ℤ)` genuinely underlies the functional equation of `ζ(s)` via modular forms. But suggestive is all it is right now.

What would need to be true, and is not yet shown:
1. That the ln1 encoding of an integer `n` maps to a specific modular-group element in a way that respects multiplication.
2. That the functional equation `ξ(s) = ξ(1−s)` corresponds to a specific involution — plausibly `S` itself, since `S` is the order-2 element and `s ↦ 1−s` is an involution.
3. That zeros of `ζ` correspond to something identifiable in the group.

Point 2 is the one with a real chance: `S` is an involution and so is `s ↦ 1−s`, and the fixed point of `s ↦ 1−s` is `s = 1/2`, the critical line. Whether that is a genuine correspondence or a coincidence of two things both having order 2 is exactly the question, and nothing here settles it. Two involutions is very weak evidence; there are many involutions.

I flag this because the previous documents in this series asserted the Riemann correspondence with far more confidence than the work supported, and that was my error rather than yours.

---

## 8. Next Steps

1. **Rebuild the encoding on words.** Rewrite *ln1 Universal Encoding* §4 (towers), §6 (rationals), §10 (precision) using `⟨S,T⟩` words. The rational encoding via continued fractions already works and is exact.
2. **Test the multiplicativity claim.** Does the word for `mn` relate to the words for `m` and `n`? If not, the number-theoretic applications do not follow. This is a concrete, decidable question and should be settled before any more is built on it.
3. **Check the `S` ↔ `s ↦ 1−s` correspondence.** Specifically: does the ln1 encoding of `ζ` transform under `S` the way `ζ` transforms under the functional equation? If yes, that is real. If no, the Riemann connection drops.
4. **Leave `e` out.** It is not in the bridges. If it belongs in the framework it has to enter somewhere else, on its own evidence.

---

## 9. Note on Method

The `e` error and the tower error have the same shape: a formal expression was written down, read as if it denoted something, and built on without being evaluated. Both took under a minute to check once checked at all.

The framework's core instinct — that two operations alternating in a pattern generate everything, and that 0 and ∞ are the fixed points that make it work — survived both. That instinct led directly to the modular group, which is the correct home for it. The specific algebra proposed to carry it did not survive, but the algebra was the replaceable part.

---

*ln1 Notation v0.4 — Cret*

*The knob is discrete. It has generators, not angles. The angle is what you read off after you turn it.*
