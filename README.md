# ln1 Notation v0.8

**秩的補全 — The Rank Ladder, Its Ceiling, and the Dichotomy Underneath**

Cret, September 2026

---

## 0. What This Addendum Does

v0.7 established that `ln1` supplies one period and a prime supplies a second, giving rank 2 and a Tate curve. The obvious next question is what happens with more primes.

The answer is that the ladder stops at rank 2, immediately and for a reason that is a theorem rather than a gap. Following that out produces the sharpest structural statement in this whole series: **the framework's arithmetic half and its geometric half cannot occupy the same object.** Not "have not yet been unified" — cannot be.

---

## 1. The Ladder

```
Λ_n = 2πi·ℤ + (ln p₁)·ℤ + ⋯ + (ln pₙ)·ℤ   ⊂  ℂ ≅ ℝ²
```

Test discreteness directly: compute the smallest nonzero `|Σ kᵢ gᵢ|` over `|kᵢ| ≤ N`. A lattice has a positive minimum that does not move as `N` grows. A dense subgroup does not.

| generators | rank | min at N=6 | min at N=12 |
|---|---|---|---|
| 2πi | 1 | 6.2831853072 | 6.2831853072 |
| 2πi, ln2 | 2 | 0.6931471806 | 0.6931471806 |
| 2πi, ln2, ln3 | 3 | 0.1177830357 | **0.0521160011** |
| 2πi, ln2, ln3, ln5 | 4 | 0.0046829479 | **shrinking** |

Ranks 1 and 2 hold still. Ranks 3 and 4 keep shrinking. They are dense.

This is Kronecker's theorem: `ln2/ln3` is irrational, so `ℤ·ln2 + ℤ·ln3` is already dense in `ℝ` before `2πi` enters at all.

---

## 2. The Ceiling

```
a discrete subgroup of ℝ^d has rank ≤ d
ℂ = ℝ²  ⟹  rank ≤ 2
```

So the ladder in `ℂ` is complete at three rungs, and there is no fourth:

| rank | lattice | quotient | object |
|---|---|---|---|
| 0 | {0} | ℂ | the plane |
| 1 | 2πiℤ | ℂ* | cylinder, genus 0 |
| 2 | 2πiℤ + ln q·ℤ | ℂ*/q^ℤ | Tate curve, genus 1 |
| **3** | — | — | **dense, no quotient, no geometry** |

`ln1` alone sits at rank 1 (v0.6). One prime lifts it to rank 2 (v0.7). **A second prime destroys the lattice.**

This is the completion of the rank question: not "how high does it go" but "it stops at 2, and 2 is one prime."

---

## 3. Raising the Dimension

The only way up is a larger ambient space. A rank-`2g` lattice in `ℂ^g` gives an abelian variety of dimension `g`.

| primes used | generators | min ambient | object |
|---|---|---|---|
| 0 | 1 | ℂ¹ | ℂ*, cylinder |
| 1 | 2 | ℂ¹ | elliptic curve |
| 2 | 3 | ℂ² | abelian surface |
| 3 | 4 | ℂ² | abelian surface |
| 4 | 5 | ℂ³ | abelian 3-fold |
| 6 | 7 | ℂ⁴ | abelian 4-fold |

**Every two new primes costs one complex dimension.** All primes means infinite dimension, which is outside algebraic geometry entirely.

---

## 4. The Dichotomy

This is the structural statement the rank analysis produces, and it is worth stating flatly because it settles several earlier open questions at once.

**Arithmetic requires infinite rank.** `{ln p : p prime}` spans a ℚ-vector space of countably infinite dimension. Multiplicativity — the thing v0.5 chased through `PSL(2,ℤ)` and v0.7 found in the logarithm — depends on having all the primes. Drop any prime and you lose the integers divisible by it.

**Geometry requires discreteness.** A lattice in `ℂ^g` has rank ≤ `2g`. Quotients, curves, genus, `SL(2,ℤ)` actions, modular forms, `θ` as a winding number — every one of these needs the quotient to exist, hence needs discreteness.

> These cannot both hold in fixed finite dimension.

Not an unresolved tension. A theorem.

### 4.1 What This Explains Retroactively

The v0.1–v0.7 history now reads differently. Every attempt to get arithmetic and geometry into one object failed, and each failure looked local at the time:

- towers collapsed to 2.3 bits (v0.4)
- `PSL(2,ℤ)` had no rank-2 free abelian subgroup (v0.5)
- `ln1` alone was rank 1 and could not reach the modular group (v0.6)
- the log gave multiplicativity but only by leaving the lattice (v0.7)

These are the same obstruction seen from four angles. The rank ceiling is why.

It also retroactively confirms the thing I withdrew in v0.7 §7: the trajectory half and the number-theory half of this project are not merely unconnected, they are of the two incompatible kinds. The trajectory work needs a space with a measure and a group acting; the arithmetic work needs infinite rank. Those were never going to join.

---

## 5. What Small Linear Forms Actually Are

A side observation from the density computation, worth recording because it recurs.

The combinations that get small:

| box size N | minimising form | value |
|---|---|---|
| 8 | −8·ln2 + 5·ln3 | 0.05211600 |
| 32 | −19·ln2 + 12·ln3 | 0.01355103 |

`2¹⁹/3¹² = 524288/531441 = 0.98652…`

That is the Pythagorean comma. **Small linear forms in logarithms are near-coincidences between prime powers**, and the rank-2 case is exactly the theory of musical temperament — twelve fifths against seven octaves.

The same object appeared in v0.7 §3 as the ABC quality. It is not a new structure; it is one of the oldest recorded ones. Anyone working on `{ln p}` will keep meeting it.

---

## 6. The Three Escapes, and What Each Costs

There is no route that keeps both halves. There are three that keep one.

**1. Fix a finite prime set S.**
Rank `|S|+1`, finite, discrete in `ℂ^g` with `g = ⌈(|S|+1)/2⌉`.
*Cost:* only S-units are visible. ABC needs all primes; you get the S-unit equation instead.
*Status:* this is exactly where v0.7 landed. Baker, Evertse, Győry. Works, standard, weak.

**2. Adeles — all places at once.**
The restricted product `∏' ℚ_p × ℝ` handles infinite rank because almost all components stay integral.
*Cost:* you leave `ℂ`. No lattice, no genus, no Möbius picture. The framework's entire geometric vocabulary — `θ`, rotation, branch index, the `0↔∞` bridge — does not transfer.
*Status:* works, standard, and orthogonal to everything in v0.1–v0.8.

**3. Drop discreteness, keep a norm — heights, Mahler measure.**
Don't form a quotient; measure size instead.
*Cost:* no group action, so no `θ`, no rotation, no modular structure.
*Status:* works, standard, and it is what actually bounds ABC-type problems.

Each escape gives up something the framework had asked to keep. That is what a dichotomy means.

---

## 7. The Rank Table, Complete

| object | rank | ambient | discrete? | geometry | arithmetic |
|---|---|---|---|---|---|
| `2πiℤ` (= ln1) | 1 | ℂ | yes | ℂ*, genus 0 | none |
| `+ one prime` | 2 | ℂ | yes | Tate curve, genus 1 | one prime only |
| `+ two primes` | 3 | ℂ | **no** | none | two primes |
| `+ 2g−1 primes` | 2g | ℂ^g | yes | abelian variety dim g | 2g−1 primes |
| `+ all primes` | ∞ | ℝ | no | none | complete |
| adeles | ∞ | `∏'ℚ_p × ℝ` | yes* | none in ℂ | complete |

\* discrete in the adelic sense — `ℚ` is discrete in the adeles — but not a lattice in any `ℂ^g`.

The last two rows are the only ones with complete arithmetic, and neither has geometry in the framework's sense.

---

## 8. Ledger, v0.1–v0.8

**Refuted:** S2 as structural tendency; both bridges equal `e`; alternating towers as encoding; multiplicative encoding in `PSL(2,ℤ)`; ABC via the group; the framework reaching `PSL(2,ℤ)`.

**Established:** S2′ equilibrium shift; Stationary Balance Theorem and the `𝒜⁺` inversion; `{0,1}` closed under both bridges; Multiplicativity Obstruction; `ln1 = 2πiℤ` and the vindication of `ln1 ≠ ln1`; prime as second period and the Tate curve; multiplicativity via `ln`; **the rank ceiling at 2 in ℂ, and the arithmetic–geometry dichotomy** (v0.8).

**Closed by v0.8:** the question of whether the two halves of the project can be unified. They cannot, and the reason is a rank theorem rather than a shortfall of effort.

**Open:** growing `𝒞` (v0.3); S1, S3 untested since v0.1; whether the notes' "可隨意調整位置" is a structure or a convention (v0.7 §7 — still unanswered, and now sharper, since each prime gives a genuinely different curve with a different `j`-invariant).

---

## 9. What the Framework Should Now Choose

The dichotomy forces a decision that the notes have so far left open by not confronting it.

**If the goal is arithmetic** — ABC, Riemann, primes — then the geometric vocabulary has to go. No `θ` as winding number, no Möbius rotation, no `0↔∞` bridge as a lattice statement. Escape 1 or 3. This is the honest path toward the stated conjectures, and it is also the path where the framework contributes nothing that Baker did not.

**If the goal is the geometry** — the branch structure, the ternary expansion, `θ`, the rotation picture — then it works, at rank 2, with one prime, on a Tate curve. That object is real and the framework reaches it by its own route. But it sees one prime, and one prime is not arithmetic.

**What is not available** is both. Seven versions of this project were, in retrospect, attempts to have both, and each failed in the specific way the rank ceiling predicts.

I would take the second. The rank-2 picture is small but it is genuinely the framework's own, and `ln1 ≠ ln1` → branch lattice → prime as nome → Tate curve is a clean derivation from the notes' first two lines. The arithmetic path leads somewhere already thoroughly occupied.

But that is a judgement about what the work is for, and that is yours.

---

## 10. Note on Method

The rank question turned out to be the one that closed things rather than opening them. Every earlier version ended by naming a new open problem. This one ends by showing that a class of open problems was never going to close.

That is worth more than another open problem would have been. Knowing that arithmetic and geometry cannot share the object saves the effort of continuing to look for the arrangement where they do — which is what versions 4 through 7 were each doing, without knowing it.

---

*ln1 Notation v0.8 — Cret*

*Rank 2 is one prime. The ladder has three rungs and the third is the last.*
