# The Exact-Fraction Audit

**Applying 所有小數用分子分母表示 to Every Result**

Cret, September 2026

---

## 0. What This Does

The source notation contains an instruction:

> 所有小數點、以及有無窮循環小數的需要分子分母表達，才能完美表達無窮循環小數
> *All decimals, and repeating decimals in particular, must be expressed as numerator over denominator in order to be expressed perfectly.*

Applied literally to every numerical result in this project, this does something I did not expect: **it sorts the work cleanly into what survived and what did not.** That sort is the content of this note.

---

## 1. Class I — Exactly Rational

The demand is fully met. These are exact, not approximations.

| result | exact fraction | decimal |
|---|---|---|
| nome q, base 2 | **1/2** | 0.500000000000000 |
| nome q, base 3 | **1/3** | 0.333333333333333 |
| nome q, base 5 | **1/5** | 0.200000000000000 |
| nome q, base 7 | **1/7** | 0.142857142857143 |
| nome q, base 13 | **1/13** | 0.076923076923077 |
| nome q, base 101 | **1/101** | 0.009900990099010 |
| ln i / 2πi | **1/4** | 0.250000000000000 |
| ln(−1) / 2πi | **1/2** | 0.500000000000000 |
| ln ζ₁₂ / 2πi | **1/12** | 0.083333333333333 |
| ln ζ₂₄ / 2πi | **1/24** | 0.041666666666667 |
| ζ(−1) | **−1/12** | −0.083333333333333 |
| η exponent = −ζ(−1)/2 | **1/24** | 0.041666666666667 |
| 𝒜⁺ under symmetric steps | **1/2** | 0.500000000000000 |

Note what these are: nomes, cyclotomic indices, a special value, the counting constant. **Every structural result of the project is in this column.**

### 1.1 Repeating Decimals Are Exactly Fractions

Here the notes are straightforwardly right, and there is more in it than the notes claimed.

| nome 1/p | decimal | period | φ(p) | period \| φ(p) |
|---|---|---|---|---|
| 1/3 | 0.33… | 1 | 2 | yes |
| 1/7 | 0.142857142857… | 6 | 6 | yes |
| 1/11 | 0.0909… | 2 | 10 | yes |
| **1/13** | **0.076923076923…** | **6** | **12** | **yes** |
| 1/17 | 0.0588235294117647… | 16 | 16 | yes |
| 1/19 | 0.0526315789473684… | 18 | 18 | yes |
| 1/23 | 0.0434782608695652… | 22 | 22 | yes |
| 1/101 | 0.00990099… | 4 | 100 | yes |

The period of the nome `1/p` is `ord_p(10)`, and it divides `φ(p) = p − 1` by Fermat's little theorem.

**This is where 13 and 12 actually meet.** v0.10 identified the only genuine `13 ↔ 12` relation as the field degree `[ℚ(ζ₁₃):ℚ] = φ(13) = 12`. Writing the nome as a fraction makes the same fact visible directly: `1/13` has decimal period 6, and `6 | 12`.

Not the `ζ(−1) = −1/12` coincidence, which v0.10 refuted. This one — and it was hiding in the fraction the whole time.

---

## 2. Class II — Provably Irrational

The demand cannot be met, and that is a theorem rather than a shortfall.

| quantity | decimal | why no fraction exists |
|---|---|---|
| ln 2 | 0.693147180559945286 | Lindemann |
| ln 2 / 2π (height of p=2) | 0.110317800076325800 | Baker |
| ln 13 / 2π (height of p=13) | 0.408224369020384392 | Baker |
| τ₂ = 2π / ln 2 | 9.064720283654388311 | Baker |
| π | 3.141592653589793116 | Lindemann, 1882 |
| e | 2.718281828459045091 | Hermite, 1873 |
| j(τ_p) | — | transcendental, v0.11 §6 |

A fraction `p/q` equal to any of these would contradict a theorem. These are not "not yet expressed as fractions."

Note what these are: heights, moduli, coordinates. **Every quantity that is merely a measured position is in this column.**

---

## 3. The Sort This Performs

```
EXACT (rational)      the structure    q = 1/p,  j/n,  ζ(−1),  1/24,  1/2
INEXACT (irrational)  the coordinates  ln p,  ln p/2π,  τ_p,  j(τ_p)
```

Every result that survived twelve versions of testing is in the first column. Every number that is a position rather than a result is in the second.

**The demand for exactness is a filter that keeps exactly the results and discards exactly the measurements.** That is a better argument for the instruction than the notes gave for it, and I would not have found it without applying the instruction literally.

---

## 4. What Class II Gets Instead

Irrationals have no single `p/q`, but they have an exact representation as a *process*: the continued fraction, whose convergents are exact fractions.

**Height of p = 2:** `ln2/2π = 0.110317800076326`, CF `[0; 9, 15, 2, 4, 1, 1, 1, 1]`

| convergent | value | error |
|---|---|---|
| 15/136 | 0.110294117647059 | 2.4e−05 |
| 31/281 | 0.110320284697509 | 2.5e−06 |
| 139/1260 | 0.110317460317460 | 3.4e−07 |
| 309/2801 | 0.110317743662978 | 5.6e−08 |

**Height of p = 13:** `ln13/2π = 0.408224369020384`, CF `[0; 2, 2, 4, 2, 6, 2, 1, 2]`

| convergent | value | error |
|---|---|---|
| 9/22 | 0.409090909090909 | 8.7e−04 |
| 20/49 | 0.408163265306122 | 6.1e−05 |
| 129/316 | 0.408227848101266 | 3.5e−06 |
| 278/681 | 0.408223201174743 | 1.2e−06 |

**τ₂ = 2π/ln2:** CF `[9; 15, 2, 4, 1, 1, 1, 1, 2]` — the tail of the height's CF, as it must be, since `τ₂ = 1/(height)`.

### 4.1 And This Closes a Loop

By v0.4, a continued fraction **is** a word in `⟨S, T⟩`, with word length equal to precision.

So the notes' demand for numerator-over-denominator, applied to irrationals, lands exactly on the word encoding — which is the thing the notes were reaching for with the alternating tower construction, and which the towers failed to be (2.3 bits, saturated).

The instruction and the failed mechanism were aimed at the same target. The instruction reaches it.

---

## 5. The Complete Exact Statement of the Main Result

With every decimal removed:

> For a prime `p`, let `Λ_p = (ln p)·ℤ + 2πi·ℤ` and `τ_p = 2πi / ln p`.
>
> Then `ℂ/Λ_p ≅ ℂ*/p^ℤ` is the Tate curve, its height in the fundamental domain is `ln(p)/2π`, and its nome is
>
> ```
> q = 1/p
> ```
>
> exactly, with no decimal appearing anywhere in the statement. The decimal expansion of `q` repeats with period `ord_p(10)`, which divides `p − 1`.
>
> No `τ_p` is imaginary quadratic (Baker), so no curve in the family has complex multiplication and `j(τ_p)` is transcendental for every `p`.

The heights `ln(p)/2π` are irrational and appear only as coordinates. The result itself — `q = 1/p` — is a fraction.

---

## 6. What the Instruction Is Actually For

Read as a demand about notation, "express all decimals as fractions" is either trivial (for rationals) or impossible (for irrationals).

Read as a demand about *results*, it is a discipline: **a result that cannot be stated without a decimal is not yet a result.** It is a measurement, and measurements are positions rather than facts.

By that standard the project has produced a small number of genuine results — `q = 1/p`, `ln ζₙ/2πi = j/n`, `𝒜⁺ = 1/2`, `η`'s exponent `1/24` — and a large number of measurements. The proportion is roughly what twelve versions of refutation would suggest.

The notes' instruction, applied to the notes' own project, is the sharpest evaluative tool in it.

---

*Cret, September 2026*

*Every result of this work is a fraction. Everything that needed a decimal was a coordinate.*
