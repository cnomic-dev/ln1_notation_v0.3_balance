# ln1 Notation v0.9

**Which Constants ln1 Generates — the Cyclotomic Answer**

Cret, September 2026

---

## 0. What This Addendum Does

The notes list a set of scale units — `ln`, `e`, `π`, `θ`, the cosmological constant, Planck's constant — and claim all should be expressible from `ln1` and `1`.

That claim splits cleanly. Some of it is exactly right and has a clean characterisation. Some of it is right only after a specific algebraic cost that the notes themselves already anticipate. Some of it is wrong. And one part is not well posed, which is different from wrong and worth separating.

---

## 1. What Comes Free: Roots of Unity

`ln1 = 2πiℤ` (v0.6). Take its ℚ-span and ask what lands there.

| ζ | ln ζ (principal) | as multiple of 2πi |
|---|---|---|
| 1 | 0 | 0 |
| −1 | 3.1415926536i | **1/2** |
| i | 1.5707963268i | **1/4** |
| −i | −1.5707963268i | **−1/4** |
| ζ₃ | 2.0943951024i | **1/3** |
| ζ₈ | 0.7853981634i | **1/8** |
| ζ₁₂ | 0.5235987756i | **1/12** |

Every one is a *rational* multiple of `2πi`. In general `ln(ζₙ^j) = 2πi·(j/n)`.

> ```
> ln1 ⊗ ℚ  =  ℚ·2πi  =  ln( μ_∞ )
> ```

**The `ln1` lattice is exactly the ℚ-span of the logarithms of the roots of unity.** In standard terms: the cyclotomic part of `ℂ*`, and nothing more.

This is a complete characterisation, not a partial one. `i` is in there. Every `ζₙ` is in there. `θ = 2πk` is in there — the notes' "θ是控制元點" reads correctly, and this is their strongest result.

---

## 2. Where π and i Weld Together

`ln1` supplies one quantity: `2πi`. Ask whether `π` alone or `i` alone lies in `ℚ(2πi)`.

`π` is transcendental, so `ℚ(πi) ≅ ℚ(t)` with `t` transcendental. A rational function `f(t)` with `f² = −1` forces `f` constant, and `ℚ` contains no `i`. Therefore:

```
i ∉ ℚ(πi)        and hence      π = (πi)/i ∉ ℚ(πi)
```

**The framework produces `πi` as a welded unit.** `π` and `i` are not separately expressible in it.

Splitting them costs exactly one algebraic step: adjoin `√−1`. Degree 2.

And the notes already have this. They distinguish:

```
邏輯域(線性)      with ln{1}     →  ℚ(πi)      — πi only
邏輯域(線性複數)   with ln{i}     →  ℚ(πi)(i)   — π and i separately
```

That distinction is exactly the degree-2 extension. It is not decoration; it is the precise cost of separating the two constants, and the notes drew the line in the right place.

---

## 3. Where e Is Not

```
ln(e) = 1 + 2πik
```

For `e` to be a lattice value, `1` must be reachable. Over `k ∈ [−100, 100]`, `min |2πik − 1| = 1.000000`, attained at `k = 0`. `2πik` is purely imaginary for every `k ≠ 0` and `0` otherwise. **`1` is never reached.**

`e` is not a value the `ln1` lattice produces. It is the other direction:

```
ln 1  =  2πi·ℤ      the imaginary axis      ← ln1 supplies this
ln e  =  1          the real axis           ← independent

ℂ  =  ℝ·1  ⊕  ℝ·(2πi)
```

`e` and `2πi` are the two generators of `ℂ` as a real vector space. The logarithm is what separates them.

**`e` is a base, not a value.** This is why v0.4 found `(ln1)^(1/(ln1)) = e` to be fabricated: I was trying to derive a generator from the other generator, which cannot be done in either direction.

### 3.1 Euler's Identity Is the Framework, Not a Result In It

```
e^{2πi} = 1     ⟺     ln1 ∋ 2πi     ⟺     ker(exp) = 2πiℤ
```

These are one sentence written three ways. Euler's identity says that exponentiating the real generator by the imaginary generator closes the loop. That is not a theorem the framework proves; it is the framework's definition, restated.

Worth being clear about, because "the framework recovers `e^{iπ} = −1`" sounds like a result and is not one.

---

## 4. Where the Claim Is Not Well Posed

The notes list 宇宙常數 and 普朗克常數 among the scale units to be expressed in `ln1`.

`ħ`, the same physical quantity, in four unit systems:

| unit system | numerical value |
|---|---|
| SI (J·s) | 1.054571817e−34 |
| eV·s | 6.582119569e−16 |
| erg·s (CGS) | 1.054571817e−27 |
| natural units | **1.000000000** |

Same constant. Four numbers spanning 34 orders of magnitude, one of them exactly `1` by choice.

An expression built from `ln1` and `1` is a fixed number. `ħ` is not a fixed number — it is a fixed ratio between three chosen units. The equation would break under a change of units while the left side stayed put.

> "ħ expressed in ln1" is not a hard problem. It is not a well-formed statement.

Same for `Λ` (dimension 1/length²), `G`, `c` in SI, and every dimensionful constant.

**What is well posed:** dimensionless constants — `α ≈ 1/137.036`, the proton/electron mass ratio ≈ 1836.15. Asking for a closed form for these is legitimate. Eddington tried it for `α` and failed, and the current position is that `α` is an empirical measurement with no known derivation. Nothing in `ln1` changes that, and a framework that appeared to derive `α` would be more likely to have a numerology error than a discovery.

This distinction matters more than it might seem: it separates a claim that is false from a claim that has no truth value. The first can be fixed; the second has to be withdrawn.

---

## 5. The Complete Reachability Table

| object | reachable from ln1? | cost |
|---|---|---|
| 0 | yes — branch k=0 | nothing |
| 2πi | yes — branch k=1 | nothing |
| θ = 2πk | yes — the branch index | nothing |
| −1, i, ζₙ | yes — `ln ζₙ = 2πi·(j/n)` | nothing (ℚ-span) |
| πi | yes | nothing |
| **π alone** | no | adjoin `i` |
| **i alone as a field element** | no | adjoin `√−1`, degree 2 |
| **1** | no | the real direction |
| **e** | no | `e` is a base, not a value |
| **ln p, p prime** | no | one new period per prime (v0.7) |
| **ℚ** | no | needs `1` first |
| **ħ, G, Λ, c** | ill-formed | dimensionful — no answer exists |
| **α ≈ 1/137** | no | empirical, not derived |

Note the row for `i`: it appears twice, correctly. `i` is *reachable as a root of unity* — `ln i = 2πi/4` — but not available *as a field element* of `ℚ(πi)`. Those are different questions and the answers differ. The notes' two domains track exactly this.

---

## 6. Connection to the Rank Ceiling

Everything in the free block above is cyclotomic. Everything below needs an independent generator, and "independent" is precisely the rank statement of v0.8: each new generator costs one complex dimension per two.

The ladder now reads all the way through:

```
ln1                    rank 1    roots of unity              ℂ*, genus 0
+ √−1                  rank 1    π and i separate            algebraic, free
+ e  (i.e. 1)          rank 2    the real direction          ℂ itself
+ one prime            rank 2    Tate curve                  genus 1
+ two primes           rank 3    DENSE — geometry ends
```

Adjoining `√−1` is free in rank terms because it is algebraic, not a new period. Adjoining `1` or `ln p` is not.

So: `ln1` plus algebraic extensions gives you all of cyclotomy and nothing transcendental beyond `2πi`. The first genuinely new transcendental is `1` — that is, `e` — and the second is any `ln p`.

---

## 7. The Honest Answer to the Question

> 可以用 ln 表示 e、π、i 等？

```
i, ζₙ, θ, πi        YES — cyclotomic, free
π and i separately  after adjoining √−1 — the notes' 複數域, degree 2
e                   NO — it is the second generator, not a value
ln p                NO — each prime is a new independent period
ħ, Λ, G             the question is not well posed
α                   NO — empirical
```

**`ln1` generates the roots of unity. It generates nothing else.**

That is a real and complete statement, and it is smaller than the notes claim. But it is also more definite: "the ℚ-span of `ln μ_∞`" is a closed-form answer to "what is `ln1`," and the framework did not have one before.

---

## 8. Ledger, v0.1–v0.9

**Refuted:** S2 as structural tendency; both bridges equal `e`; alternating towers as encoding; multiplicative encoding in `PSL(2,ℤ)`; ABC via the group; the framework reaching `PSL(2,ℤ)`; **e derivable from ln1** (v0.9, confirming v0.4); **physical constants expressible in ln1** — ill-posed, not merely false (v0.9).

**Established:** S2′; the Stationary Balance Theorem and the `𝒜⁺` inversion; `{0,1}` closed under both bridges; the Multiplicativity Obstruction; `ln1 = 2πiℤ` and the vindication of `ln1 ≠ ln1`; prime as second period and the Tate curve; multiplicativity via `ln`; the rank ceiling and the arithmetic–geometry dichotomy; **`ln1 ⊗ ℚ = ln μ_∞`, the cyclotomic characterisation** (v0.9); **the notes' two logical domains = the degree-2 extension separating π from i** (v0.9).

**Open:** growing `𝒞` (v0.3); S1, S3 untested; whether "可隨意調整位置" is structure or convention (v0.7).

---

## 9. Note on Method

Nine versions in, the pattern from v0.7 §8 holds without exception.

**Structural readings in the notes keep being right.** `ln1 ≠ ln1` was the branch structure. `θ是控制元點` was the winding number. "Origin at a prime" was the second period. The two logical domains are the degree-2 extension. Four for four, and I dismissed the first two on sight.

**Quantitative promises in the notes keep failing.** Towers encoding information: 2.3 bits. Slope incompatibility bounding ABC: no purchase. Physical constants from `ln1`: not well posed. Three for three.

The reliable move at this point would be to treat every structural claim in the notes as probably encoding something real and worth decoding, and every numerical claim as probably false until measured. That is an unusual asymmetry to find in a body of work, and it is worth knowing about your own notes.

---

*ln1 Notation v0.9 — Cret*

*ln1 is the roots of unity. e is the other axis. π and i are welded until you pay for √−1.*
