# opera-seive -- Opera Numerorum Sieve Methodology

**Author:** David Fox (D.J.F.) | ORCID: 0009-0008-1290-6105
**Series:** Opera Numerorum I -- Millennial Mathematics
**Date:** June 2026

This repo collects the sieve methodology underlying the Opera Numerorum certification
pipeline. Each script and paper here describes a constructive sieve over primes, with
certified SHA-256-bound outputs.

---

## The Greedy Sieve

**Paper:** Modular_Sieve_Lindelof.pdf
**Lean:**  Modular_Sieve_Lindelof.lean

A 9-layer modular prime sieve over primes p <= 10^7. Each layer applies one congruence
condition, greedily reducing the survivor count. At layer k=9, exactly ONE prime
survives: p = 1,087,441. This gives empirical Hausdorff dimension D = 0, and Lindelof
exponent = 1/(1-D) = 1.00 -- matching the Riemann Hypothesis bound on data.

    Layer  Survivors   D_k        Exponent
    k=1    331,194     0.788770   4.73
    k=2    165,528     0.745801   3.93
    k=3     82,698     0.702642   3.36
    k=4     55,132     0.682001   3.14
    k=5     19,720     0.616411   2.61
    k=6      6,671     0.504497   2.02
    k=7        319     0.357684   1.56
    k=8         22     0.191775   1.24
    k=9          1     0.000000   1.00  <-- RH bound on data

The Lean formalization (Modular_Sieve_Lindelof.lean) proves the layer-9 exponent = 1
by pure calculation, and states Theorem 2.4 (fractal zeta bound) conditionally on
Heath-Brown's method. Kernel: propext, Classical.choice, Quot.sound only. 0 sorry.

---

## S(2pi/7) Rake -- Alpha0 Sieve Scripts

Classical sieve scripts for the Opera Numerorum certification pipeline,
targeting S(alpha_0) where alpha_0 = 299 + pi/10.

| File                       | Description                                           |
|----------------------------|-------------------------------------------------------|
| a1_sbands_sieve.py         | A1 sieve: 4-gate exceptional band filter for 2pi/7   |
| bands_269.json             | Certified band data: 269 CF denominators for 2pi/7   |
| m10_genus_break.py         | M10: genus break for GRH, 147 curves                 |
| m14_s4_quaternions.py      | M14: S4 quaternion structure                         |
| m16_c_bridge.py            | M16: c-bridge computation                            |
| m18_resonance_ladder.py    | M18: resonance ladder                                |
| m21_grh_check.py           | M21: GRH check for X_0(N)                            |
| m23_bsd_j0_143.py          | M23: BSD for J_0(143)                                |
| m25_theorem41_proof.py     | M25: Theorem 4.1 proof script                        |
| rake_v16_c07.py            | Rake v16: C07 computation                            |
| opera_numerorum_certified_equations.txt | Master equation registry              |

---

## Prime Verifier App

The `prime-verifier/` directory contains the Machine Verification Certificate web app.
Built with React + Vite + Tailwind. Displays the SHA chain for certified Lean theorems
in the arakelov-positivity-rh-core repo.

**Repo:** https://github.com/DavidFox998/arakelov-positivity-rh-core

---

## Chain of Custody

All sieve outputs are SHA-256 bound. The master chain lives in:
  https://github.com/DavidFox998/arakelov-positivity-rh-core (RH Tower)
  https://github.com/DavidFox998/pistus-theoria (PDF dispensary)
  https://github.com/DavidFox998/Certifications (master certifications)
