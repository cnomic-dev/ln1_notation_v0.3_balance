# ln1 Notation v0.10

**Base Change Is the Nome — and the Two 1/12's Are Not the Same 1/12**

Cret, September 2026

---

## 0. What This Addendum Does

Two claims to check.

The first — that `ln` and `log` are freely interchangeable — turns out to be false in an interesting way, and the way it fails collapses two separate moves in the notes into one.

The second — that `ln ζ₁₂ = 2πi/12` and `ζ(−1) = −1/12` correspond, with `p = 13` a prime saddle point — does not hold. But there is a genuine bridge nearby, it is classical, and it lands on 24 rather than 12. Separating the real one from the numerological one is most of the work here.

---

## 1. Base Change Moves the Lattice

```
log_b(z) = ln(z) / ln(b)     ⟹     log_b(1) = 2πi·k / ln b
```

So the kernel is not `2πiℤ` but `(2πi/ln b)·ℤ`.

| base b | period 2πi/ln b |
|---|---|
| 2 | 9.064720i |
| 3 | 5.719202i |
| 5 | 3.903963i |
| 7 | 3.228919i |
| 10 | 2.728753i |
| e | 6.283185i |

Compare v0.7's table of `τ_q = 2πi/ln q`. **They are the same numbers.**

> The period of `log` base `b` is exactly `τ_b`, the modular parameter obtained in v0.7 by "putting the origin at a prime."

So the notes' two separate moves —

```
原點可定位在質數 2 上
ln 與 log 可交替轉換使用
```

— are **one move**. Changing the logarithm base *is* choosing the nome. That is a genuine unification of two lines in the notes that I had been treating independently, and it is worth having.

### 1.1 The Consequence Is That Base Change Is Not Free

Different bases give different lattices, hence different Tate curves, hence different `j`-invariants. `log₂` and `log₃` are not two notations for one object; they are two objects.

So "可交替轉換使用" is true as an *algebraic* statement — every `log_b` is `ln` divided by a constant — and false as a *structural* one. Dividing by `ln b` rescales the period, and the period is the whole content.

`ln` is canonical among the bases because it is the unique one whose real generator is `1`. Any other base has a real generator of `ln b ≠ 1`, and then the two axes are not normalised against each other.

### 1.2 It Also Answers v0.7 §7

That open question was whether "可隨意調整位置" (freely adjustable origin) is a structure or a convention. It is a structure: each base gives a different curve with a different `j`. The freedom is real freedom of choice, not a freedom of relabelling — you are picking which curve to work on, and the choice is consequential.

---

## 2. The Two 1/12's

### 2.1 They Have Different Origins

**(a) `ln ζ₁₂ = 2πi·(1/12)`**

The `1/12` here is `j/n` with `n = 12` — a cyclotomic index. Nothing distinguishes it:

```
ln ζ₁₁ = 2πi·(1/11) = 0.5711986643i
ln ζ₁₂ = 2πi·(1/12) = 0.5235987756i
ln ζ₁₃ = 2πi·(1/13) = 0.4833219467i
```

`ζ₁₂` appeared in the v0.9 table only because it was one of the examples I picked. `1/13` is equally present and equally unremarkable. If I had listed `ζ₇` and `ζ₉` instead, no `1/12` would have appeared at all.

**(b) `ζ(−1) = −1/12`**

Verified: `ζ(−1) = −0.0833333333333333333` by analytic continuation.

This is a special value of a specific function at a specific point. It carries a sign, and the sign is negative. The series `1+2+3+⋯` diverges — partial sums are 55, 5050, 500500 — and `−1/12` is not its sum. It is the value the continuation takes at `s = −1`, joined to the series by a procedure rather than by an equality.

**Same digits, different objects.** A cyclotomic index and a special value. Identifying them directly is numerology, and the `1/11` and `1/13` rows are the reason: they show the `12` in (a) has no privileged status.

### 2.2 Where 13 Actually Meets 12

There is one real relation, and it is not the one proposed:

```
φ(11) = 10   ⟹  [ℚ(ζ₁₁) : ℚ] = 10
φ(13) = 12   ⟹  [ℚ(ζ₁₃) : ℚ] = 12
φ(17) = 16   ⟹  [ℚ(ζ₁₇) : ℚ] = 16
```

`ℚ(ζ₁₃)` has degree 12 over `ℚ` because `φ(13) = 12`. That is genuine, and it is the reason 12 sits near 13 at all.

But this 12 is a **field degree**. It is a third distinct 12:

| 12 | what it is |
|---|---|
| `φ(13) = 12` | a field degree |
| `ζ(−1) = −1/12` | a special value |
| `ln ζ₁₂ = 2πi/12` | a cyclotomic index |

Three different objects with the same numeral. And `13` is not distinguished among primes here — `φ(p) = p−1` for every prime, so every prime has this property. There is no saddle point at 13.

---

## 3. The Bridge That Is Real

The instinct that `ζ(−1)` connects to roots of unity is **correct**. The connection exists, it is classical, and it runs through the Dedekind eta function.

```
η(τ) = q^{1/24} ∏_{n≥1} (1 − qⁿ),      q = e^{2πiτ}
```

Where does `1/24` come from?

```
ζ(−1)     = −0.0833333333333333333
−ζ(−1)/2  =  0.0416666666666666667
1/24      =  0.0416666666666666667
```

The exponent is `−ζ(−1)/2`. **The `1/12` enters `η` as `1/24`.**

### 3.1 The Multiplier Is a 24th Root of Unity

At `τ = 0.3 + 1.1i`:

```
η(τ+1)/η(τ)  = 0.96592582628907 + 0.25881904510252i
e^{2πi/24}   = 0.96592582628907 + 0.25881904510252i
difference   = 1.1e−31
```

Exactly a primitive 24th root of unity.

```
ζ(−1) = −1/12   →   exponent 1/24   →   ζ₂₄ ∈ μ_∞
```

**This is the genuine link between the special value and the cyclotomic world of v0.9.** Not `ζ₁₂` — `ζ₂₄`, and the factor of 2 is not negotiable.

### 3.2 And S Acts Too

```
η(−1/τ)      = 0.799617382906 − 0.0444507197496i
√(−iτ)·η(τ)  = 0.799617382906 − 0.0444507197496i
difference   = 4.9e−31
```

`η` is a modular form of weight 1/2 with a 24th-root multiplier system, and both generators `S` and `T` act on it — the same `S` and `T` from v0.4.

So the chain is:

```
ζ(−1) = −1/12  →  η's exponent 1/24  →  ζ₂₄  →  multiplier system  →  SL(2,ℤ)
```

Every arrow is a theorem. This is the correspondence the intuition was reaching for, and it is better than the proposed one because it actually holds.

---

## 4. The Symmetry-Breaking Instinct

Not wrong about the family of idea, wrong about the mechanism.

The same `1/24` fixes the critical dimension of the bosonic string:

```
D − 2 = 24     ⟹     D = 26
```

and it arises from ζ-regularising `Σn` — the same regularisation that gives `−1/12`. The cancellation is an **anomaly cancellation**, which is a symmetry statement, and the theory is inconsistent away from `D = 26`.

So "symmetry breaking / phase transition" is the right neighbourhood for where `1/24` appears. But:

- the mechanism is anomaly cancellation in a specific quantum theory, not a phase transition in the statistical-mechanics sense
- the number is 24
- no prime plays any role, and 13 in particular plays none

The instinct located the right region of mathematics. The specific identification did not survive.

---

## 5. Ledger Update

**Refuted (v0.10):**
- `ln` and `log` freely interchangeable — false structurally; base change rescales the period
- `ln ζ₁₂ = 2πi/12` ↔ `ζ(−1) = −1/12` — different objects, and `1/11`, `1/13` are equally present
- `p = 13` as a prime saddle point — no basis; `φ(p) = p−1` holds for every prime

**Established (v0.10):**
- **base change = choice of nome**: `period(log_b) = τ_b`, collapsing two lines of the notes into one operation
- **v0.7 §7 answered**: the origin's adjustability is structural, not conventional — different bases give different curves with different `j`
- **the real bridge**: `ζ(−1) = −1/12` → `η`'s exponent `1/24` → primitive 24th root of unity → the `SL(2,ℤ)` multiplier system, verified to 1e−31

---

## 6. Note on Method

The v0.7 §8 asymmetry holds for a fifth and sixth time, and now in both directions within a single message.

**Structural claim, correct:** "ln 與 log 可交替轉換" pointed at something real — base change *is* the nome — and unified two separate moves in the notes. I would not have found that connection on my own; it came from the claim.

**Numerical claim, false:** the `1/12` ↔ `1/12` identification. And the way it fails is instructive: the `12` in the cyclotomic column was an artefact of which examples I happened to tabulate in v0.9. Had I listed different roots of unity, the coincidence would not have been visible to notice.

That is the specific hazard with `1/12`: it appears in enough places that a coincidence is nearly guaranteed, and the ones that matter (the `η` exponent) are separated from the ones that do not (a cyclotomic index) only by tracing where each came from. Digits agreeing is not evidence. The provenance is the evidence, and here the provenance says 24.

---

*ln1 Notation v0.10 — Cret*

*Changing the base is choosing the curve. And the 1/12 that matters shows up as 1/24.*
