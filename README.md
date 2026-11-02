# Matroid prophet inequality: the exact constant C(B)

For every finite matroid, against the same almighty full-seed arrival-order
adversary, with one sample per element and seed budget 47|E|+27 bits, the
guaranteed fraction of the expected offline optimum is

$$C(B) = 5.1106085087308568\cdot 10^{-10},\qquad B=\left(\tfrac{261}{256}\right)^{256}\approx 142.9,$$

where C(B) is the closed form (5) of the bound-111 paper evaluated at the
rational $x=B$ in exact arithmetic. The exact numerator/denominator pair
(≈1900 digits each) is emitted by the certificate and stored verbatim in
[`exact_fraction.txt`](exact_fraction.txt) and [`result.json`](result.json).

This **exceeds the current listed value** $C_{141}\approx 5.1074889\cdot10^{-10}$
(bound-111 of `canghaimeng/openai-math-improvement`) by $6.108\cdot10^{-4}$
relative — and the bound-111 paper itself proves the theorem with exactly this
$C(B)$: *"Averaging (30) over phase proves (2) with $C(B)$… $C(B) > C(141) = C_{141}$."*
The listed value is the theorem's constant floored to the integer 141; this
repository evaluates the same closed form at the rational $x=B$ in exact
arithmetic. Nothing structural is new.

## What is whose

- **OpenAI** (One-Sample-Suffices preprint, commit `1581d4cb`): the
  construction (κ=164, ρ=93/256, h=3/4, t=23/2¹⁸, θ=261/256, L=256) and the
  structural prophet-inequality argument.
- **Ryan Shea** (`shea256/matroid-prophet-inequality`, commit `8cd13959`): the
  analysis constants (a, b, v, d, μ, ν), the scalar chain, and the earlier
  certificate C⋆.
- **Qiuyu Chen (Euler)** (`canghaimeng/openai-math-improvement`, bound-111):
  the conservative evaluation B > 141 (the current listed record), the exact
  scalar checker this file extends, and the paper's own statement that C(B)
  is larger.
- **MultiAgency / darkhipo** (this repository): the exact evaluation at
  x = B — one rational substitution in the published closed form — plus this
  certificate file. That is the entire contribution.

## The certificate

`check_scalar_B.py` (a derivative of bound-111's embedded `check_scalar.py`;
its supplement ZIP lives inside `paper.pdf`'s embedded-file streams) performs
19 exact-rational checks: every x-independent upstream check verbatim
(tilts, log lower bound, γ, ε, phase denominator, C₁₄₁ byte-exact
reproduction), plus the new ones (B exact, s(B) > 0, monotone gains,
C(B) > C₁₄₁ > C⋆). Runs in seconds with stdlib `fractions` only:

    python3 check_scalar_B.py

**Evidence level: arithmetic certificate on an inherited, unformalized
structural proof.** The scalar layer is exactly checked; the structure
(fixed-vector rule, exposure, hybrids, measurability) remains the prose of
the cited papers — as it does for every current row of this lane, none of
which carries Lean.
