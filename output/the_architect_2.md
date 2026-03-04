# The Architect Report (Revised): Fermat's Little Theorem -- Structural Blueprint for a Survey with Original Contribution

**Date:** 2026-03-03
**Iteration:** 2

---

### Input Sources

- `output/the_architect_1.md` (original blueprint, iteration 1)
- `output/the_verifier_1.md` (verification report identifying critical failures)
- `output/the_red_teamer_1.md` (stress-test report, verdict: VULNERABLE)

---

## Summary of Changes from Iteration 1

The first iteration had seven identified issues, three of them critical or blocking. This revision addresses all seven:

| Issue | Severity | Resolution |
|-------|----------|------------|
| 1. beta(theta) undefined | Critical | Pivoted away from claiming a novel closed-form formula. The conditional exponent result is now presented as EXPOSITORY context (known AGP framework), not as an original theorem. A numerical table is provided as illustration, with honest attribution. |
| 2. Harman calibration fails | Critical | Removed the false claim that beta(0.56) = 0.332. Harman's improvement is now correctly attributed to sieve-theoretic advances for structured moduli, not to a higher EH level. |
| 3. L5 definition drift | Major | Fixed. A single, consistent smoothness parameter is defined: the largest prime factor of (p-1) over all prime divisors p of n. |
| 4. Vacuous truth concern | Major | Added discussion of partial EH-type results. Also pivoted the original contribution to be unconditional (computational analysis does not depend on unproven hypotheses). |
| 5. Novelty deficit | Major | Major structural pivot. The original contribution is now a COMPUTATIONAL study (systematic analysis of Shallue-Webster data) plus PRECISE TESTABLE CONJECTURES, not the folklore "plug EH into AGP" exercise. The conditional exponent discussion is moved to the expository survey. |
| 6. L7 unfalsifiable | Moderate | Replaced the o(1) conjecture with a precise, testable prediction involving explicit log-factors. |
| 7. Larsen regime mismatch | Moderate | Corrected. Larsen's interval regime is now clearly distinguished from fixed-theta short intervals. |

Additionally:
- The proof assembly circularity is eliminated.
- Wright (2020) is explicitly discussed and the contribution is positioned relative to it.
- The Scout report's upper bound error (C(x) < x^{0.337}) is flagged and corrected.
- Harman's exponent is updated to the best known value of 0.3389.

---

## Paper Title (Revised)

**"Fermat's Little Theorem at 386: From Primality Testing to Carmichael Number Distribution, with Computational Investigations of Density and Smoothness"**

---

## Revised Narrative Arc

The paper is restructured into two clearly separated components:

**Part I (Sections 1-6): Expository Survey.** A comprehensive treatment of FLT and its consequences, from the foundational group theory through primality testing, cryptography, and the recent breakthroughs on Carmichael numbers. This part contains no original claims.

**Part II (Sections 7-8): Original Computational Contribution.** A systematic empirical analysis of the Shallue-Webster dataset of all 49,679,870 Carmichael numbers up to 10^{22}, extracting quantitative information about the smoothness profile of Carmichael number prime factors, the distribution of the number of prime factors, and the local density function. This analysis leads to precise, testable conjectures about the density of Carmichael numbers in short intervals, with explicit error terms (not just o(1)).

The key innovation in Part II is NOT a new theorem but a new dataset-driven analysis that:
(a) Provides the first systematic measurement of the "smoothness profile" of Carmichael number prime factors in a large dataset.
(b) Tests the predictions of both the Erdos conjecture and the Granville-Pomerance heuristic against empirical data.
(c) Formulates conjectures with explicit log-power error terms that can be tested against future tabulations.

This positions the paper as a substantive computational contribution within the tradition of computational analytic number theory (in the style of Shallue-Webster's own tabulation work, or Oliveira e Silva's prime gap computations).

---

## Section-by-Section Architecture

### Part I: Expository Survey

**Sections 1-6 remain essentially as in Iteration 1**, with the following corrections:

**Section 1: Introduction and Historical Context.** Unchanged.

**Section 2: Algebraic Foundations.** Unchanged. Theorems 2.1-2.6 as before.

**Section 3: Primality Testing.** Unchanged. Theorems 3.1-3.6 as before.

**Section 4: Cryptographic Applications.** Unchanged. Theorems 4.1-4.5 as before.

**Section 5: Carmichael Numbers -- Classical Theory and Recent Breakthroughs.** Modified:

- **5.1 (AGP Theorem):** As before, C(x) >= x^{2/7} for sufficiently large x.
- **5.2 (AGP Conditional):** As before, under GRH implies C(x) = x^{1-o(1)}.
- **5.3 (Larsen Short Interval):** CORRECTED statement. Larsen (2022) shows C(x, x + x/(log x)^C) >= 1 for any constant C > 1/2, for all sufficiently large x. The interval length here is x/(log x)^C = x^{1 - C log log x / log x}, which tends to x (NOT of the form x^theta for fixed theta < 1). This is a "Bertrand's postulate" for Carmichael numbers.
- **5.4 (Larsen AP):** As before.
- **5.5 (Larsen-Wright):** As before.
- **5.6 (Granville-Pomerance):** As before.
- **5.7 (Shallue-Webster):** As before.
- **5.8 (Harman's Improved Bound):** CORRECTED. The best known unconditional lower bound is C(x) >= x^{0.3389} (Harman, improving from x^{2/7} through a series of papers using his sieve method for structured moduli).
- **5.9 (Wright's Conditional Density, NEW):** Wright (2020), "A Conditional Density for Carmichael Numbers," proves that under the Heath-Brown conjecture on least primes in APs, C(x) >> x^{1-R} where R = (2+o(1)) log log log log x / log log log x. This is a much stronger conditional result than the simple "plug EH into AGP" interpolation. The paper positions this as the state of the art for conditional results, noting that the Heath-Brown conjecture is implied by EH-type hypotheses but is weaker than the full EH.
- **5.10 (AGP Conditional Exponent under Partial EH, NEW EXPOSITORY).** We present, as an expository remark (NOT an original result), the observation that under EH(theta) for theta > 1/2, the AGP framework yields C(x) >= x^{beta(theta)} for an exponent beta(theta) that is an increasing function of theta with beta(1/2) = 2/7 and beta(theta) -> 1 as theta -> 1. We explain the qualitative structure of the optimization (see the Expository Remark below) and note that this interpolation is a routine consequence of the AGP framework, already implicit in AGP (1994) and superseded by Wright's (2020) conditional result.

**CORRECTION to the Scout Report:** The Scout report claims "the best upper bound is C(x) < x^{0.337}." This is an error. The value 0.337 (or more precisely 0.3389) is a LOWER bound exponent (Harman's result). The best known upper bounds on C(x) are of the form C(x) = O(x * exp(-c(log x)^{1/3})) for some constant c > 0 (or similar subexponential bounds), which are much smaller than x^{0.337} for large x but much larger than x^{2/7}. There is no known upper bound of the form C(x) <= x^{alpha} for any fixed alpha < 1.

**Section 6: Open Problems.** Modified slightly:
- 6.1 (Erdos Density Conjecture): Add discussion of the gap between the lower bound x^{0.3389} (Harman) and x^{1-o(1)} (conjectured).
- 6.2 (PSW Conjecture): As before.
- 6.3 (Wieferich Primes): As before.
- 6.4 (Carmichael's Totient Conjecture): As before.
- 6.5 (Short Interval Density, NEW): Explicitly state as an open problem: for fixed theta in (1/2, 1), is it true that C(x, x + x^theta) -> infinity? Note that Larsen's result does NOT answer this, as Larsen's intervals have length x/(log x)^C = x^{1-o(1)}, not x^theta for fixed theta < 1.

---

### Part II: Original Contribution

**Section 7: Computational Analysis of Carmichael Number Distribution**

This section is entirely restructured. The original contribution is now purely computational and conjectural, with no false claims of novel theorems.

**Section 8: Precise Conjectures**

Contains testable conjectures arising from the computational analysis.

---

## Expository Remark: The AGP Exponent Under Partial EH

Before presenting the original contribution, we include (in Section 5.10) the following expository discussion of the conditional exponent, with full attribution.

**Expository Remark (AGP Exponent Under EH(theta)).** In the AGP (1994) framework, the exponent 2/7 in the lower bound C(x) >= x^{2/7} arises from optimizing a construction that depends on the level of distribution of primes in arithmetic progressions. The Bombieri-Vinogradov theorem provides level of distribution theta = 1/2 (i.e., equidistribution of primes in APs to moduli up to x^{1/2-epsilon}). Under a partial Elliott-Halberstam hypothesis EH(theta) asserting equidistribution to moduli up to x^{theta-epsilon}, the AGP optimization can be re-run with relaxed constraints, yielding a larger exponent.

**Qualitative structure of the optimization.** In the AGP construction:
- Choose a smoothness parameter y = x^{alpha}, where alpha <= theta - epsilon (the EH constraint: all moduli d arising from y-smooth numbers must satisfy d <= x^{theta-epsilon}).
- The number of "usable" primes p <= x (those with (p-1) being y-smooth) is approximately S ~ pi(x) * rho(1/alpha), where rho is the Dickman function.
- The combinatorial assembly (finding subset products congruent to 1 modulo L) requires S to exceed a certain threshold depending on L = lcm of y-smooth numbers.
- The resulting Carmichael number count is C(x) >> x^{f(alpha)}, where f(alpha) is determined by the Dickman function and the size of L.
- Optimizing f(alpha) subject to alpha <= theta yields beta(theta) = max_{alpha <= theta} f(alpha).

The optimization is a calculus problem involving the Dickman function rho(u) and is not expected to have a clean closed-form solution. The AGP paper itself does not give a closed-form formula for the exponent 2/7 but rather derives it through a detailed asymptotic analysis.

**Known anchor points.** The following values of beta(theta) are known or can be inferred:

| theta | Source | beta(theta) | Notes |
|-------|--------|-------------|-------|
| 1/2 | AGP (1994), unconditional via BV | 2/7 = 0.2857 | The original AGP result |
| ~0.55 (effective) | Harman (2005-2008), unconditional | 0.3389 | Harman achieves this NOT by assuming EH(0.55) but by proving stronger-than-BV results for the specific structured moduli in the AGP construction, using his sieve method. The "effective theta" of 0.55 is a rough heuristic comparison, not a rigorous equivalence. |
| 1 - epsilon (all epsilon > 0) | AGP (1994) Theorem 4, conditional on GRH | 1 - o(1) | The full conditional result |

**Why this is not novel.** AGP (1994) Theorem 4 already identifies the BV barrier and shows that stronger equidistribution gives better exponents. Wright (2020) gives a quantitatively superior conditional result under the weaker Heath-Brown conjecture. The interpolation "plug EH(theta) into AGP" is a standard exercise that has likely been considered by every expert in this area. We include this discussion for completeness but do not claim it as original.

**Important clarification on Harman's method.** Harman's improvement from 2/7 to 0.3389 does NOT come from assuming a higher level of distribution in the Elliott-Halberstam sense. Rather, Harman's sieve provides better-than-BV equidistribution results for the specific class of smooth moduli that arise in the AGP construction. This is a fundamentally different kind of input: Harman proves an unconditional result by exploiting the structure of the moduli, rather than assuming a general equidistribution hypothesis. Any framework that claims to "recover Harman's bound as beta(0.55)" must carefully distinguish between the abstract EH level and the effective level achieved by sieve methods for structured moduli.

---

## Key Insight (Revised)

The central idea driving the ORIGINAL contribution (Part II) is:

**The Shallue-Webster tabulation of all 49,679,870 Carmichael numbers up to 10^{22} provides a sufficiently large and complete dataset to test, for the first time, fine-grained quantitative predictions about the internal structure of Carmichael numbers -- not just their counting function C(x), but the joint distribution of their prime factorizations, the smoothness properties of (p-1) for their prime factors p, and their local density in intervals of various lengths.**

Existing computational studies of Carmichael numbers have focused on:
(i) Counting C(x) at specific thresholds (Pinch, Shallue-Webster).
(ii) Searching for Carmichael numbers with specific properties (e.g., few prime factors).

What has NOT been done systematically (to our knowledge) is:
(a) Measuring the distribution of the "smoothness defect" of Carmichael numbers: for a Carmichael number n = p_1 * ... * p_r, how does max_i P^+(p_i - 1) (the largest prime factor among all (p_i - 1)) compare to n?
(b) Testing whether the empirical ratio C(x)/x^{alpha(x)} stabilizes or drifts, and if drifting, at what rate.
(c) Computing the empirical density of Carmichael numbers in intervals [x, x + x^theta] for various fixed theta and comparing with heuristic predictions.
(d) Measuring the correlation between the number of prime factors omega(n) and the size n among Carmichael numbers, and comparing with the Granville-Pomerance prediction.

These measurements lead to precise, testable conjectures with explicit error terms.

---

## Lemma Decomposition (Revised)

The lemma structure is now divided into:
- **Expository Lemmas (E1-E4):** Required for the survey sections. All are standard results.
- **Computational Propositions (C1-C4):** The original contribution. These are empirical findings from the Shallue-Webster data analysis.
- **Conjectures (J1-J2):** Precise, testable conjectures arising from the computational analysis.

### Expository Lemmas

| # | Lemma Statement | Difficulty | Technique | Section |
|---|-----------------|------------|-----------|---------|
| E1 | **Smooth Number Counting.** For u = log x / log y in [1, (log x)^{1/2}], Psi(x,y) = x * rho(u) * (1+o(1)) where rho is the Dickman function. | Routine | Hildebrand-Tenenbaum | 5.1 |
| E2 | **AGP Construction.** There exists c > 0 such that C(x) >= x^c for all sufficiently large x. Specifically, C(x) >= x^{2/7}. | Core (expository) | AGP (1994) | 5.1 |
| E3 | **Larsen Short Interval.** For any constant C > 1/2, the interval [x, x + x/(log x)^C] contains a Carmichael number for all sufficiently large x. | Core (expository) | Maynard-Tao sieve + AGP | 5.3 |
| E4 | **Korselt's Criterion.** n > 1 composite is Carmichael iff n is squarefree and (p-1) | (n-1) for every prime p | n. | Routine | CRT | 5.1 |

### Computational Propositions (Original)

| # | Proposition Statement | Difficulty | Technique | Section |
|---|----------------------|------------|-----------|---------|
| C1 | **Smoothness Profile of Carmichael Prime Factors.** For each Carmichael number n = p_1 * ... * p_r in the Shallue-Webster dataset (n <= 10^{22}), define the smoothness parameter s(n) = max_{i=1}^{r} log(P^+(p_i - 1)) / log(n), where P^+(m) denotes the largest prime factor of m. The empirical distribution of s(n) is unimodal with median approximately [TO BE COMPUTED] and is consistent with s(n) -> 0 as n -> infinity among Carmichael numbers. | Moderate | Computational analysis | 7.1 |
| C2 | **Effective Exponent Function.** Define alpha(x) = log C(x) / log x. Using the Shallue-Webster counts at thresholds x = 10^k for k = 10, 11, ..., 22, we compute alpha(x) and observe that alpha(x) increases monotonically from alpha(10^{10}) ~ [VALUE] to alpha(10^{22}) ~ [VALUE]. The rate of increase is consistent with alpha(x) = 1 - A / (log log x)^B for explicit constants A, B determined by least-squares fit. | Moderate | Computational analysis + regression | 7.2 |
| C3 | **Prime Factor Count Distribution.** For Carmichael numbers n <= 10^{22}, the distribution of omega(n) = number of distinct prime factors has mean approximately [VALUE] and is compared with the Granville-Pomerance heuristic prediction that "typical" Carmichael numbers near x have omega(n) ~ (log x)^{1-epsilon}. | Moderate | Computational analysis | 7.3 |
| C4 | **Short Interval Density.** For each threshold x = 10^k (k = 15, 16, ..., 22) and each theta in {0.5, 0.6, 0.7, 0.8, 0.9}, compute the empirical count C(x, x + x^theta) from the Shallue-Webster data and compare with the heuristic prediction C(x, x + x^theta) ~ C(x) * x^{theta-1}. | Moderate | Computational analysis | 7.4 |

**Note on [VALUES]:** The bracketed values [TO BE COMPUTED], [VALUE] indicate quantities that require running the actual computation on the Shallue-Webster dataset. The propositions are stated here with the structure of what will be measured; the specific numerical results will be filled in during the writing phase (by The Scribe) after the computational analysis is performed.

### Conjectures (Original)

| # | Conjecture Statement | Basis | Testability | Section |
|---|---------------------|-------|-------------|---------|
| J1 | **Refined Erdos Conjecture with Explicit Rate.** C(x) = x / exp((A + o(1)) * (log x)^{1/3} * (log log x)^{2/3}) for an explicit constant A > 0, where the o(1) is bounded by |o(1)| <= B / (log log x)^{1/3} for an explicit constant B. | Data from C2, Granville-Pomerance heuristic | TESTABLE: predicts C(10^{25}), C(10^{30}) to within a factor | 8.1 |
| J2 | **Short Interval Density with Explicit Error.** For fixed theta in (1/2, 1), C(x, x + x^theta) >= x^theta / exp(D * (log x)^{1/3}) for an explicit constant D > 0 and all sufficiently large x. | Data from C4, heuristic extension of Erdos conjecture | TESTABLE: makes predictions for future tabulations | 8.2 |

---

## Informal Proof Sketch (Revised)

### Expository Lemmas

**E1 (Smooth Number Counting).** Classical. The Dickman function rho(u) satisfies u*rho'(u) = -rho(u-1) for u > 1 with rho(u) = 1 for 0 <= u <= 1. Hildebrand (1986) proved Psi(x,y) ~ x*rho(u) uniformly for exp((log log x)^{5/3+epsilon}) <= y <= x using the saddle-point method. We include this because the AGP construction and all Carmichael density arguments rest on smooth number estimates.

**E2 (AGP Construction).** The proof has three stages: (1) Choose a smooth modulus L as the lcm of y-smooth numbers, with y ~ x^{1/7}. (2) Using the Bombieri-Vinogradov theorem, count primes p <= x with (p-1) | L; by smooth number estimates, there are >> x^{2/7} such primes. (3) Using a combinatorial argument (a multiplicative analogue of Erdos-Ginzburg-Ziv), find subsets of these primes whose product is 1 mod L, yielding Carmichael numbers by Korselt's criterion. The exponent 2/7 arises from optimizing the smoothness parameter y subject to the BV constraint y <= x^{1/2-epsilon}. We present a detailed proof sketch following AGP (1994) and Granville's exposition in "Primes in Intervals of Bounded Length."

**E3 (Larsen Short Interval).** Larsen (2022) replaces Stage 2 of the AGP argument with the Maynard-Tao sieve, which guarantees clusters of primes satisfying congruence conditions in short intervals. The key technical innovation is showing that the admissibility conditions of the Maynard-Tao sieve are compatible with the congruence constraints from the AGP framework. The interval length x/(log x)^C (for C > 1/2) is determined by the Maynard-Tao sieve's reach.

**IMPORTANT:** Larsen's interval [x, x + x/(log x)^C] has length x^{1-o(1)} as x -> infinity. For no fixed theta < 1 does Larsen's result imply C(x, x + x^theta) >= 1. The question of whether every interval [x, x + x^theta] for fixed theta in (1/2, 1) contains a Carmichael number for sufficiently large x remains open.

**E4 (Korselt's Criterion).** Direct proof via CRT. If n = p_1 * ... * p_r is squarefree with (p_i - 1) | (n - 1) for all i, then for any a with gcd(a, n) = 1, write a^{n-1} mod p_i. Since ord_{p_i}(a) | (p_i - 1) and (p_i - 1) | (n-1), we get a^{n-1} = 1 mod p_i for all i. By CRT, a^{n-1} = 1 mod n. Conversely, if n is Carmichael and p | n, then taking a to be a generator of (Z/pZ)*, we get ord(a) = p-1 divides n-1.

### Computational Propositions

**C1 (Smoothness Profile).** For each Carmichael number n = p_1 * ... * p_r in the dataset, we compute:
- The factorization of each (p_i - 1).
- P^+(p_i - 1), the largest prime factor of (p_i - 1), for each i.
- s(n) = max_i log(P^+(p_i - 1)) / log(n), the normalized smoothness defect.

The quantity s(n) measures how far the Carmichael number's prime factors are from being "perfectly smooth" (s(n) = 0 would mean all (p_i - 1) have only bounded prime factors relative to n). In the AGP construction, the primes are chosen with (p-1) being y-smooth where y = x^{1/7}, so s(n) ~ 1/7 for AGP-constructed Carmichael numbers. If "wild" Carmichael numbers (not arising from AGP-type constructions) exist in abundance, they might have different smoothness profiles.

The computation requires: (a) Access to the Shallue-Webster data (or a representative sample), (b) Factoring (p_i - 1) for each prime factor p_i of each Carmichael number in the dataset. For the dataset up to 10^{22}, the prime factors p_i are at most 10^{22}, and (p_i - 1) is at most 10^{22}, so factorization is feasible using standard methods (trial division, Pollard rho, ECM).

**C2 (Effective Exponent).** The Shallue-Webster tabulation gives C(10^k) for k = 3, 4, ..., 22. We compute alpha(10^k) = log C(10^k) / log(10^k) = log C(10^k) / (k * log 10). We then fit the model alpha(x) = 1 - A / (log log x)^B using least-squares regression on the data points.

Known data points from Shallue-Webster (2024) and earlier tabulations:

| x | C(x) | alpha(x) |
|---|------|----------|
| 10^3 | 1 | 0.000 |
| 10^6 | 43 | 0.272 |
| 10^9 | 646 | 0.312 |
| 10^{12} | 8241 | 0.326 |
| 10^{15} | 105,212 | 0.335 |
| 10^{18} | 1,401,644 | 0.341 |
| 10^{21} | 20,138,200 | 0.347 |
| 10^{22} | 49,679,870 | 0.350 |

The trend alpha(x) increasing slowly with x is consistent with alpha(x) -> 1 (Erdos conjecture) but the rate of increase is extremely slow. Fitting alpha(x) = 1 - f(x) and analyzing the functional form of f(x) is the core of this proposition.

**C3 (Prime Factor Count).** For each Carmichael number in the dataset, compute omega(n). Tabulate the distribution of omega(n) as a function of n's magnitude. Compare with:
- The AGP prediction: omega(n) should grow with log(n).
- The Granville-Pomerance heuristic: omega(n) ~ (log n)^{1-o(1)} for "typical" Carmichael numbers near x.
- The empirical finding of Pinch and others: small Carmichael numbers tend to have omega(n) = 3 (the minimum possible).

**C4 (Short Interval Density).** Using the complete Shallue-Webster dataset, for each x = 10^k and theta in {0.5, 0.6, 0.7, 0.8, 0.9}, count exactly how many Carmichael numbers lie in [x, x + x^theta]. Compare with the "uniform distribution" heuristic: if Carmichael numbers near x have density approximately C(x)/x = x^{alpha(x)-1}, then the expected count in [x, x + x^theta] is approximately x^{theta + alpha(x) - 1}.

### Conjectures

**J1 (Refined Erdos Conjecture with Explicit Rate).** The heuristic basis for this conjecture is the Granville-Pomerance analysis (2001), which considers two competing models for Carmichael number density:
- **Erdos's model:** Based on smooth number heuristics, predicts C(x) = x^{1-o(1)} with the o(1) term vanishing like 1/(log log x) or similar.
- **Pomerance's model:** Based on a random model of prime factorizations, predicts C(x) = x * exp(-c * (log x * log log x)^{1/2}), which is much sparser.

The computational data (C2) should allow us to distinguish between these models, or at least to determine which one better fits the data for x <= 10^{22}. The conjecture J1 proposes a specific functional form calibrated to the data.

IMPORTANT: The range x <= 10^{22} may be too small to definitively distinguish between the Erdos and Pomerance models, since both predict very similar counts at this scale. The conjecture should be accompanied by a discussion of this limitation and an indication of what range of x would be needed to discriminate.

**J2 (Short Interval Density with Explicit Error).** This replaces the unfalsifiable "C(x, x+x^theta) = x^{theta - o(1)}" from Iteration 1. The new conjecture has:
- An explicit lower bound (not just existence), of the form x^theta / exp(D * (log x)^{1/3}).
- A specific constant D that can be estimated from the data.
- Predictions for C(10^{25}, 10^{25} + 10^{25*theta}) that can be checked against future tabulations.

The key distinction from Iteration 1's L7: this is a LOWER BOUND conjecture (which is the natural direction for a density conjecture), it has an explicit error term (not o(1)), and it is calibrated against data rather than derived from a hand-waving heuristic.

---

## Main Results Assembly (Revised, Non-Circular)

The paper's original results are:

**Computational Result A (from C1, C2, C3).** A systematic empirical analysis of the Shallue-Webster dataset yields:
- The smoothness profile of Carmichael number prime factors (C1).
- The effective exponent function alpha(x) and its rate of growth (C2).
- The distribution of omega(n) among Carmichael numbers (C3).

These are empirical findings, not theorems. They require no proof, only correct computation.

**Computational Result B (from C4).** Empirical density measurements of Carmichael numbers in short intervals [x, x + x^theta] for various x and theta. This is the first systematic study of short-interval Carmichael density using a complete dataset.

**Conjecture J1.** A precise conjecture on C(x) with explicit error terms, calibrated against the data.

**Conjecture J2.** A precise conjecture on C(x, x + x^theta) with explicit error terms, testable against future tabulations.

**Assembly (no circularity):** C1 provides structural data about Carmichael numbers. C2 provides the counting data. C3 provides distributional data. C4 provides short-interval data. J1 is formulated by fitting a model to C2's data, informed by the Granville-Pomerance heuristic framework. J2 is formulated by combining C4's data with the model from J1. Each component is independent and self-contained. No component is a restatement of another.

---

## Feasibility Assessment

**Overall confidence: HIGH for the computational work, MEDIUM for the conjectures.**

| Component | Confidence | Rationale |
|-----------|------------|-----------|
| Sections 1-6 (Survey) | HIGH | All expository. Verified in Iteration 1. |
| C1 (Smoothness Profile) | MEDIUM-HIGH | Requires access to Shallue-Webster data and factoring p_i - 1. Factorization is feasible for p_i <= 10^{22}. The main risk is data access: if the raw factorizations of Carmichael numbers are not published (only counts), we may need to recompute from the Carmichael numbers themselves, which is more expensive. |
| C2 (Effective Exponent) | HIGH | The data C(10^k) is published. The computation is a straightforward regression. |
| C3 (Prime Factor Count) | MEDIUM-HIGH | Similar to C1: requires the factorizations, which are feasible. |
| C4 (Short Interval Density) | HIGH | Requires only the ordered list of Carmichael numbers, not their factorizations. |
| J1 (Refined Erdos Conjecture) | MEDIUM | The conjecture may be underdetermined by data in the range x <= 10^{22}. The Erdos and Pomerance models may not be distinguishable at this scale. |
| J2 (Short Interval Conjecture) | MEDIUM | Same concern: the range may be too small for reliable extrapolation. |

**Key risks:**

1. **Data access.** The Shallue-Webster paper tabulates counts but may not publish the full list of Carmichael numbers with their factorizations. If only counts at powers of 10 are available, C1 and C3 would need to be scaled down to a sample. Mitigation: the Carmichael numbers themselves are deterministic (a function of the primality of certain numbers), and for a sample up to 10^{15} or 10^{16}, recomputation is feasible.

2. **Range limitation.** The range x <= 10^{22} contains only ~50 million Carmichael numbers. While this is large enough for distributional analysis, it may not be large enough to extrapolate the rate at which alpha(x) -> 1. The paper must be honest about this limitation.

3. **Novelty.** The computational analysis (C1-C4) is not technically deep, but it fills a genuine gap in the literature: no one has systematically analyzed the smoothness profile or short-interval density of Carmichael numbers at this scale. The novelty lies in the specific measurements and the calibrated conjectures, not in new theoretical techniques.

---

## Alternative Approaches (if the computational pivot fails)

If the Shallue-Webster data is not accessible or the analysis yields inconclusive results:

### Alternative A: Unified Pseudoprime Taxonomy

Create a comprehensive classification of pseudoprime types (Fermat, Euler, strong, Lucas, Frobenius, etc.) with:
- A unified group-theoretic/ring-theoretic framework.
- Precise containment relations between classes (with proofs or counterexamples).
- Quantitative comparisons of the counting functions for each class.
- New observations about the overlap (or lack thereof) between Fermat pseudoprimes and Lucas pseudoprimes (relevant to the PSW conjecture).

**Feasibility: MEDIUM-HIGH.** Some containment results are known (e.g., every Carmichael number is a Fermat pseudoprime to every coprime base). The novelty would be in the unified framework and any new quantitative comparisons.

### Alternative B: Expository-Only Paper

If no original contribution can be credibly claimed, the paper could be positioned as a purely expository/pedagogical contribution:
- A comprehensive survey of FLT and its modern descendants.
- Aimed at advanced undergraduates or beginning graduate students.
- The "contribution" is the pedagogical synthesis, not a new result.
- This is a legitimate category of mathematical publication (e.g., Monthly articles, Notices surveys).

**Feasibility: HIGH.** The survey content (Sections 1-6) is already solid.

### Alternative C: Computational Extension

Extend the Shallue-Webster tabulation or conduct new computations:
- Tabulate Carmichael numbers to 10^{23} (requires significant computational resources).
- Systematically search for PSW counterexamples beyond 2^{80}.
- Compute statistics about Carmichael numbers that are also strong pseudoprimes to specific bases.

**Feasibility: MEDIUM** (depends on computational resources).

---

## Positioning Relative to Wright (2020)

Wright (2020), "A Conditional Density for Carmichael Numbers," proves under the Heath-Brown conjecture on least primes in arithmetic progressions that C(x) >> x^{1-R} where R = (2+o(1)) * log log log log x / log log log x. This is the strongest conditional density result for Carmichael numbers.

Our paper's relationship to Wright (2020):

1. **We do not compete with Wright's conditional theorem.** Wright's result is a conditional THEOREM (proved rigorously under an explicit hypothesis). Our J1 is a CONJECTURE (supported by data but not proved under any hypothesis). These are complementary, not competing, contributions.

2. **We provide empirical evidence that Wright's conditional result may be unconditionally true** (or close to it). If our data analysis in C2 shows that alpha(x) is increasing at a rate consistent with Wright's bound (i.e., the gap 1 - alpha(x) decreases like log log log x / log log x), that would be evidence that the Heath-Brown conjecture is "morally" true even if not proved.

3. **Our conjectures are more precise than Wright's conditional bound.** Wright gives a rate of convergence in terms of iterated logarithms; our J1 proposes a specific functional form calibrated to data. These conjectures could inform future theoretical work.

4. **We cite Wright prominently** as state-of-the-art for conditional results and explain how the AGP framework, Wright's conditional improvement, and Harman's unconditional improvement form a hierarchy of results.

---

## Discussion of Partial EH-Type Results (Addressing Issue 4)

The Elliott-Halberstam conjecture at level theta > 1/2 is unproven for any theta > 1/2 in full generality. However, several partial results exist:

1. **Bombieri-Friedlander-Iwaniec (1986, 1989).** Proved EH-type results for SPECIFIC structured sums of primes in APs, not for the full sum. These results were crucial for Zhang's (2014) proof of bounded gaps between primes.

2. **Polymath 8b (2014).** Achieved an effective level of distribution beyond 1/2 for specific combinatorial applications (bounded gaps), using a modified BV approach.

3. **Maynard (2020).** Proved that primes have level of distribution 1/2 + 1/34 = 0.529... for a restricted class of exponential sums.

4. **Harman's sieve (2005-2008).** For the specific class of smooth moduli arising in the AGP construction, Harman proves better-than-BV equidistribution, unconditionally. This is the mechanism behind the improvement from 2/7 to 0.3389.

For our paper: the conditional exponent discussion (Section 5.10) is purely expository and does not require EH to be proven. The original contribution (Part II) is entirely unconditional, based on analysis of existing data.

---

## Summary of Classification

| Section | Content | Classification | Novel? |
|---------|---------|----------------|--------|
| 1 | Introduction, FLT, history | Expository | No |
| 2 | Algebraic foundations | Expository | No |
| 3 | Primality testing | Expository | No |
| 4 | Cryptographic applications | Expository | No |
| 5 | Carmichael numbers: AGP through Larsen | Expository | No |
| 5.10 | Conditional exponent under partial EH | Expository remark | No (folklore) |
| 6 | Open problems | Expository | No |
| 7.C1 | Smoothness profile analysis | Computational | **Yes** |
| 7.C2 | Effective exponent function | Computational | **Yes** |
| 7.C3 | Prime factor count distribution | Computational | **Partially** (extends Pinch's earlier work) |
| 7.C4 | Short interval density measurements | Computational | **Yes** |
| 8.J1 | Refined Erdos conjecture | Conjecture | **Yes** (if genuinely new formulation) |
| 8.J2 | Short interval density conjecture | Conjecture | **Yes** |

---

## Handoff

This revised architectural blueprint addresses all seven issues identified in the verification and stress-test reports:

1. beta(theta) is no longer claimed as an original result; it is presented as an expository remark with honest attribution.
2. The Harman calibration claim is removed.
3. The smoothness parameter is defined consistently as max_i P^+(p_i - 1) / log(n).
4. Partial EH results are discussed; the original contribution is unconditional.
5. The novelty is now computational analysis + precise conjectures, not a folklore theorem.
6. The conjectures have explicit error terms, not just o(1).
7. Larsen's interval regime is correctly distinguished from fixed-theta intervals.

The blueprint is ready for handoff to **The Verifier** for formal validation of the revised structure.

**Output file:** `F:/Users/DTRAN/SDD/math-paper-author/output/the_architect_2.md`
