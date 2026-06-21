# opera-seive — Opera Numerorum Testing Methods

**`github.com/DavidFox998/opera-seive`**  
Author: David J. Fox · Aberdeen, WA · Series: Opera Numerorum / Battle Plan v1.6

Testing methods, datasets, CSV outputs, and certified verification scripts
for the exceptional prime program S(2π/7) and the RH chain.

---

## What This Repository Contains

| File | Type | Description |
|------|------|-------------|
| `rake_v16_c07.py` | Python | S(2π/7) Rake v1.6 + Lemma G0.3 + C07 Arakelov fix |
| `rake_v16_c07.out` | Output | Certified stdout — SHA-256 bound in file |
| `bands_269.json` | JSON | Machine-readable band certificate — 269 bands |
| `traces_143.csv` | CSV | Prime trace data for X₀(143) |
| `m9_grh_all.csv` | CSV | GRH verification data — M9 all-prime sweep |
| `a1_sbands_sieve.py` | Python | A1 supplementary bands sieve — α = 2π/7, 4-condition gate |
| `opera_numerorum_certified_equations.txt` | Text | Certified equation manifest — all Opera Numerorum modules |
| `m10_genus_break.py` | Python | M10 genus breakpoint computation |
| `m14_s4_quaternions.py` | Python | M14 — 600-cell S₄ quaternion sweep, 120 vertices |
| `m16_c_bridge.py` | Python | M16 — c-bridge computation |
| `m18_resonance_ladder.py` | Python | M18 — resonance ladder |
| `m21_grh_check.py` | Python | M21 — GRH zero check |
| `m23_bsd_j0_143.py` | Python | M23 — BSD J₀(143) verifier |
| `m25_theorem41_proof.py` | Python | M25 — Theorem 4.1 descent proof |

---

## The Rake Methodology — S(2π/7)

The **Rake v1.6** tests every prime p up to the search bound against four conditions:

```
Condition 1  Primality           Miller-Rabin (deterministic ≤ 3.3×10²⁴)
Condition 2  Diophantine         CF best-approximator to 2π/7: dist(h)·h < 1
Condition 3  Lemma G0.3         Galois residue gate: 3^h mod 7 ∈ {3, 5, 6}
Condition 4  C07 Arakelov fix   arakelov_term(genus=13) = 24 > 0
```

### Result

```
BANDS = [127, 414679]
```

Both bands pass all four conditions.
Both have h ≡ 7 (mod 12).

The 269-band structure encodes the CF-denominators of α = 2π/7 that survive all four gates.
`bands_269.json` is the machine-readable certificate of this structure.

---

## CSV Data

### `traces_143.csv` — Prime Trace Data
Riemann zero trace data for X₀(143). Columns:
- `prime` — prime p
- `a_p` — Hecke eigenvalue a_p(f₁₄₃)
- `trace` — trace of Frobenius at p

### `m9_grh_all.csv` — GRH Verification Sweep
All-prime GRH verification for X₀(143), 199, 311 up to the M9 search bound. Columns:
- `N` — conductor
- `p` — prime
- `zero_real` — Re(ρ) of nearest zero
- `status` — PASS / FLAG

---

## Lean Chain Binding

The sieve output binds directly to the formal Lean proof:

```
rake_v16_c07.py  →  bands_269.json
                         ↓
C01_Arakelov.lean : arakelovSelfIntersection (X₀ 143) = 24   [BRICK, 0 sorry]
C07_RH.lean       : uses ArakelovPositivity_X0_143 as hypothesis gate
```

- [`rh-core-c01-c07`](https://github.com/DavidFox998/rh-core-c01-c07) — the Lean chain
- [`rh-p5-bridge-14`](https://github.com/DavidFox998/rh-p5-bridge-14) — P5-Bridge-14 extension

---

## Certification

| File | SHA-256 |
|------|---------|
| `rake_v16_c07.py` | `1fc3e7811ef5dacadacef1e09ecec9e1ac547edb7d8bf7b4c734a34c4c87b3b7` |
| `rake_v16_c07.out` (stdout) | `f45b8e0acc1389303922b82fdb683605094610475e496936932935a24fd61acd` |
| `bands_269.json` | see `rake_v16_c07.out` |

All scripts: Python 3 · no external dependencies beyond standard library and `sympy` for primality.

---

## Author

David J. Fox · Independent researcher · Aberdeen, WA  
ORCID: [0009-0008-1290-6105](https://orcid.org/0009-0008-1290-6105)  
Archive: [pistus-theoria](https://github.com/DavidFox998/pistus-theoria) · [morningstar-project](https://github.com/DavidFox998/morningstar-project)
