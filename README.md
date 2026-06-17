# Opera Numerorum -- opera-seive

**S(2pi/7) Rake Methodology, Lean Chain Bindings, Certificates**

Author: David Fox | Series: Opera Numerorum / Battle Plan v1.6

## Contents

| File | Description |
|------|-------------|
| `rake_v16_c07.py` | S(2pi/7) Rake v1.6 + Lemma G0.3 + C07 Arakelov Fix |
| `rake_v16_c07.out` | Certified stdout (SHA256 bound in file) |
| `bands_269.json` | Machine-readable band certificate |

## Result

**BANDS = [127, 414679]**

Both pass four conditions:
1. Primality (Miller-Rabin, deterministic <= 3.3e24)
2. Diophantine: CF best-approximator to 2pi/7 (`dist(h)*h < 1`)
3. Lemma G0.3: Galois residue gate (`3^h mod 7 in {3,5,6}`)
4. C07 Arakelov fix: `arakelov_term(genus=13) = 24 > 0`

Both bands: `h == 7 mod 12`.

## Lean Chain Binding

- `C01_Arakelov.lean`: `arakelovSelfIntersection (X0 143) = 24` [proved, no sorry]
- `C07_RH.lean`: uses `ArakelovPositivity_X0_143 : 0 < 24` as hypothesis gate
- Repo: [DavidFox998/rh-core-c01-c07](https://github.com/DavidFox998/rh-core-c01-c07)

## Certification

| File | SHA256 |
|------|--------|
| `rake_v16_c07.py` | `1fc3e7811ef5dacadacef1e09ecec9e1ac547edb7d8bf7b4c734a34c4c87b3b7` |
| stdout | `f45b8e0acc1389303922b82fdb683605094610475e496936932935a24fd61acd` |

Date: 2026-06-04
