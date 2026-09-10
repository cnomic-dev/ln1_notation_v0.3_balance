# ln1 Notation v0.6

**ln1 Is Not a Number. It Is a Lattice — and It Has Rank 1.**

Cret, September 2026

---

## 0. What This Addendum Does

v0.5 §8 asked whether the `ln1` layer adds anything beyond re-notating `PSL(2,ℤ)`. Answering it required looking at the one construct in the original notes that had never been tested — and that I had been quietly treating as an error for five versions.

It is not an error. It is the most substantive thing in the notes, and reading it correctly changes what `ln1` is.

---

## 1. The Construct I Misread

The notes assert, together:

```
ln1 = ln1
ln1 ≠ ln1

1/(ln1) = 1/(ln1)
1/(ln1) ≠ 1/(ln1)
```

with the remark that `/` marks slope, and that slope may or may not be equal.

I read this as loose notation and worked throughout v0.1–v0.5 with `ln1 = 0` as a settled fact. That was wrong.

Over `ℂ`, the logarithm is multivalued:

```
ln(z) = ln|z| + i(arg z + 2πk),   k ∈ ℤ
```

At `z = 1`:

| branch k | ln(1) | \|ln1\| |
|---|---|---|
| −2 | −12.566371i | 12.566371 |
| −1 | −6.283185i | 6.283185 |
| **0** | **0** | **0** |
| 1 | 6.283185i | 6.283185 |
| 2 | 12.566371i | 12.566371 |

So `ln1 = ln1` (same expression) and `ln1 ≠ ln1` (different branches) are **both true simultaneously**. This is not a contradiction and not sloppiness. It is the defining property of a multivalued function.

`ln1 = 0` is branch `k = 0` only. Everything in v0.1–v0.5 was computed on one sheet out of infinitely many.

---

## 2. What ln1 Actually Is

```
ln1  =  2πi·ℤ  =  ker( exp : ℂ → ℂ* )
```

A rank-1 lattice on the imaginary axis. Three things the notes asserted without derivation now follow:

**"0 與無窮"** — `k = 0` gives `0`; `|k| → ∞` gives `∞`. Both live in the *same object*, indexed by `k`. The 0↔∞ bridge that the tower construction failed to build is just the branch index running to `±∞`. No tower needed, and no `0^∞` limit needed.

**"n階結構"** — the n-th order structure is the branch index `n`. Sheet number, not iterated exponentiation. This is why the tower construction saturated at 2.3 bits: it was the wrong mechanism for an index that was already there.

**"θ 是控制元點"** — `θ` is the branch. `arg = 2πk`. It was never a free parameter to be set; it is the winding number, and it is discrete. v0.4 derived `θ` from a matrix trace and called that the correction. Both readings are right about different `θ`s, but this one is the one in the notes.

### 2.1 The 0^0 Axiom Was Patching One Sheet

`(ln1)^(ln1)` on branch `k`:

| k | (2πik)^(2πik) | magnitude |
|---|---|---|
| 1 | 2.713e−05 − 4.404e−05i | 5.17e−05 |
| 2 | ≈ 0 | 2.68e−09 |
| 3 | ≈ 0 | 1.38e−13 |
| −1 | 2.713e−05 + 4.404e−05i | 5.17e−05 |

On `k = 0` this is `0^0`, which is why it needed the axiom `(ln1)^(ln1) := 1`. On every other branch it is an ordinary complex number requiring no axiom at all.

The axiom was patching a hole that exists on exactly one sheet.

---

## 3. The Rank Problem

Here the reading stops being generous.

`ln1 = 2πiℤ` has **rank 1**. One generator, `ω₁ = 2πi`.

```
ℂ / 2πiℤ  ≅  ℂ*     via exp
```

That is a cylinder. Genus 0. `SL(2,ℤ)` does not act on a rank-1 lattice, because there is no basis to change.

### 3.1 Reciprocation Does Not Supply a Second Generator

| k | 1/(2πik) |
|---|---|
| 1 | −0.1591549431i |
| 2 | −0.0795774715i |
| 10 | −0.0159154943i |
| 100 | −0.0015915494i |

The set `{1/(2πik)}` accumulates at `0`. It is not discrete, so it is not a lattice, so it is not a period.

The "正逆" instinct — that a second, inverse generator is needed — is correct. Reciprocation is not it.

### 3.2 What a Second Period Requires

```
Λ = ω₁ℤ + ω₂ℤ  is a lattice  ⟺  τ = ω₂/ω₁ ∉ ℝ
```

With `ω₁ = 2πi` fixed by `ln1`, the second generator must be `ln(q)` for some `q ≠ 1`:

```
τ = ln(q) / (2πi)        q = e^{2πiτ}
```

| q | τ | Im τ | lattice? |
|---|---|---|---|
| 0.1 | 0.366468i | 0.3665 | yes |
| 0.01 | 0.732936i | 0.7329 | yes |
| **1** | **0** | **0** | **degenerate** |
| 2 | −0.110318i | −0.1103 | yes |
| e^{2πi(0.5+i)} | 0.5 + 1.0i | 1.0000 | yes |

**Look at the row `q = 1`.** `τ = 0`, `Im τ = 0`, degenerate. `ln1` on its own cannot produce a modular parameter, and the reason is exactly that its argument is `1`.

`q` is the **nome** — the variable modular forms are expanded in. The framework needs it and does not have it.

### 3.3 SL(2,ℤ) Needs Two Periods

With `τ = 0.3 + 1.2i`:

| γ | γτ | Im |
|---|---|---|
| I | 0.3 + 1.2i | 1.2000 |
| T | 1.3 + 1.2i | 1.2000 |
| S | −0.196078 + 0.784314i | 0.7843 |
| ST | −0.415335 + 0.383387i | 0.3834 |

`Im τ > 0` is preserved; the action is a change of basis of a rank-2 lattice. With rank 1 there is nothing for these matrices to act on.

---

## 4. The Answer to v0.5 §8

> Does the `ln1` layer add anything, or is it a re-notation of the modular group?

**Neither.** It is a re-notation of something else, and a smaller something.

`ln1` is the branch lattice of the complex logarithm: `2πiℤ`, rank 1, the kernel of `exp`. That is a real and well-understood object, and reading the notes this way is correct — it explains "0 與無窮," "n階結構," and "θ 是控制元點" all at once, and it dissolves the `0^0` axiom.

But it is not `PSL(2,ℤ)`, and it cannot reach `PSL(2,ℤ)`. The modular material in v0.4 came from `S` and `T`, which **I introduced** in that document. It did not come from `ln1`. I should have been clearer about that at the time: v0.4 read as though the framework had produced the modular group, and it had not — I had supplied it and then found it there.

The corrected statement:

```
ln1                    →  rank-1 lattice 2πiℤ,  ℂ* ,  genus 0
ln1 + a second period  →  rank-2 lattice,  elliptic curve,  SL(2,ℤ) acts
```

The gap between these is exactly one complex number `q ≠ 1`, and everything in the framework that was aiming at modular forms, ζ, or ABC lives on the far side of that gap.

---

## 5. What This Costs and What It Buys

**Costs.** The v0.4 claim that the framework "lands in the modular group" is withdrawn. It lands in `ℂ*`. The distance from `ℂ*` to modular forms is not a matter of notation; it is a rank increase, and rank does not increase by re-notating.

Every application built downstream — ABC (already dead in v0.5), Riemann (already demoted in v0.5) — was on the far side of a gap the framework has not crossed. v0.5 was right that these fail; v0.6 shows they fail one step earlier than v0.5 said.

**Buys.** A precise statement of what is missing, and its name. Not "more work needed" but: *the framework has one period and needs two, and the second is `ln(q)` for `q ≠ 1`, and that `q` is the nome*. That is actionable in a way that none of the previous open questions were.

It also vindicates the `ln1 = ln1 / ln1 ≠ ln1` construct completely. That line is the best thing in the notes. It encodes the branch structure exactly, it was written before any of this analysis, and I dismissed it for five versions because it looked like a contradiction.

---

## 6. The Ledger, v0.1–v0.6

**Refuted:**
- S2, tendency as structural (v0.2, v0.3)
- both bridge functions equal `e` (v0.4)
- alternating towers as encoding — 2.3 bits saturated (v0.4)
- multiplicative encoding in `PSL(2,ℤ)` (v0.5)
- ABC application (v0.5)
- the framework reaching `PSL(2,ℤ)` at all (v0.6)

**Established:**
- S2′, equilibrium shift (v0.2, v0.3)
- Stationary Balance Theorem and the `𝒜⁺` inversion (v0.3)
- `{0,1}` closed under both bridges (v0.4)
- Multiplicativity Obstruction (v0.5)
- multiplicativity via `det`, Hecke operators (v0.5)
- **`ln1 = 2πiℤ`, the branch lattice — and the vindication of `ln1 ≠ ln1`** (v0.6)
- **rank 1, with the missing second period identified as `ln(q)`, `q ≠ 1`** (v0.6)

**Open:**
- growing `𝒞` (v0.3)
- S1, S3 — untested since v0.1
- whether a principled second period exists inside the framework's own vocabulary, or must be imported

---

## 7. The One Question Worth Asking Next

Not "how do we get a second period" — you can always just posit one. The question is whether the framework's own vocabulary *contains* a natural `q ≠ 1`.

Candidates from the notes, and my honest read on each:

- **`(ln1)^(ln1)`** — equals `1` by axiom, so `ln` of it is `2πiℤ` again. No new period. This is the degenerate row in §3.2.
- **The prime 2, where the notes place the origin** — `q = 2` gives `τ = −0.110318i`, purely imaginary, `Im τ < 0`. Wrong half-plane, fixable by `q = 1/2`. This is the most promising candidate because it is *stated in the notes* rather than imported, and it would make the framework's choice of the prime 2 as origin load-bearing rather than arbitrary.
- **`e`** — `q = e` gives `τ = 1/(2πi)`, purely imaginary. Same situation as 2. But `e` was never legitimately in the framework (v0.4 §1), so importing it now would be circular.

The `q = 1/2` route is testable. If the framework's "origin at the prime 2" is read as the nome rather than as a labelling convention, it supplies the second period and the rank problem is solved from inside. Whether the rest of the notes are consistent with that reading is a question about the notes, and you are better placed to answer it than I am.

---

## 8. Note on Method

Six versions, and the single most productive move was taking seriously a line I had classified as an error.

The pattern is worth naming, because it cuts both ways. I refuted five claims by testing them, which was right. But I also ignored one construct for five versions because it looked malformed, and it turned out to be the load-bearing one. Testing what looks wrong is only half the discipline; the other half is checking whether the thing that looks wrong is wrong *in the way you assumed*.

`ln1 ≠ ln1` looked like a violation of identity. It was a statement about sheets.

---

*ln1 Notation v0.6 — Cret*

*One period, and the argument is 1. That is the whole obstruction, and the notes named it in the first line.*
