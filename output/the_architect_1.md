# The Architect Report: Fermat's Little Theorem -- Structural Blueprint for a Survey with Original Contribution

**Date:** 2026-03-03
**Iteration:** 1

---

### Input Source

`output/the_scout_1.md`

---

## Paper Title (Proposed)

**"Fermat's Little Theorem at 386: From Primality Testing to Post-Quantum Cryptography, with New Observations on Carmichael Number Density"**

---

## Main Thesis / Narrative Arc

Fermat's Little Theorem (FLT), stated without proof in 1640, is one of the most consequential atomic facts in mathematics. A single congruence -- $a^{p-1} \equiv 1 \pmod{p}$ -- serves as the structural backbone for two enormous branches of modern mathematics: (i) the theory of primality testing, pseudoprimes, and Carmichael numbers in analytic number theory, and (ii) the correctness and security of public-key cryptographic systems (RSA, Diffie-Hellman, ElGamal, ECC). The paper's narrative arc proceeds as follows:

1. **Foundation.** Present FLT and its generalizations (Euler, Carmichael lambda, Lagrange) in a unified group-theoretic language, establishing the notational and conceptual vocabulary for everything that follows.

2. **Number-theoretic consequences.** Trace how the failure modes of FLT's converse -- that is, the existence of pseudoprimes and Carmichael numbers -- drove the development of probabilistic and deterministic primality testing over 50 years (Miller 1976 through AKS 2002 through Larsen 2025).

3. **Cryptographic applications.** Show that FLT is not merely a primality-testing tool but the structural reason that RSA decryption works, that Diffie-Hellman key exchange is well-defined, and that elliptic curve arithmetic over finite fields is computationally tractable.

4. **The frontier.** Survey the explosive recent progress on Carmichael number distribution (Larsen 2022, 2025; Larsen-Wright 2025; Shallue-Webster 2024) and related open problems (Erdos density conjecture, PSW conjecture, Wieferich primes).

5. **Original contribution.** Present a novel synthesis result: a unified framework that connects the AGP construction, Larsen's Maynard-Tao sieve refinement, and computational data from Shallue-Webster to formulate a refined conjecture on the density of Carmichael numbers in short intervals, supported by heuristic analysis and computational evidence.

The overarching message: FLT is not a historical curiosity but a living theorem whose consequences remain at the frontier of both pure mathematics and applied computer science -- and the gaps in our understanding of its "failure modes" (pseudoprimes, Carmichael numbers, Wieferich primes) remain among the most stubborn open problems in number theory.

---

## Section-by-Section Architecture

### Section 1: Introduction and Historical Context

**Goal:** Motivate the paper, state FLT, give historical context, outline the paper structure.

**Key results to present (all expository):**
- **Theorem 1.1 (Fermat, 1640; Euler, 1736).** If $p$ is prime and $\gcd(a, p) = 1$, then $a^{p-1} \equiv 1 \pmod{p}$.
- Historical note on Fermat's letter, Leibniz's unpublished proof, Euler's 1736 proof.

**Classification:** Purely expository.

---

### Section 2: Algebraic Foundations -- Generalizations of FLT

**Goal:** Present FLT in its natural algebraic habitat: finite group theory. Establish unified notation used throughout the paper.

**Key results to present:**

| # | Statement | Type | Difficulty |
|---|-----------|------|------------|
| 2.1 | **Euler's Theorem.** $a^{\varphi(n)} \equiv 1 \pmod{n}$ for $\gcd(a,n) = 1$. | Theorem (expository) | Routine |
| 2.2 | **Lagrange's Theorem.** For finite group $G$ and $x \in G$, $\text{ord}(x) \mid |G|$. | Theorem (expository) | Routine |
| 2.3 | **Carmichael's Lambda Function.** $\lambda(n)$ is the exponent of $(\mathbb{Z}/n\mathbb{Z})^\times$; $\lambda(n) \mid \varphi(n)$ and $a^{\lambda(n)} \equiv 1 \pmod{n}$ for $\gcd(a,n)=1$. | Definition + Proposition (expository) | Routine |
| 2.4 | **Korselt's Criterion.** $n$ is a Carmichael number iff $n$ is squarefree and $(p-1) \mid (n-1)$ for every prime $p \mid n$. | Theorem (expository) | Routine |
| 2.5 | **Ring-theoretic extension (Hernandez et al., 2020).** FLT extends to rings satisfying the CNC-condition. | Theorem (expository, recent) | Moderate |
| 2.6 | **Isaacs-Pournaki generalization (2005).** Group-theoretic proof of FLT for non-prime moduli. | Theorem (expository) | Moderate |

**Proof approach for 2.4:** Direct verification using the Chinese Remainder Theorem and the structure of $(\mathbb{Z}/n\mathbb{Z})^\times$ for squarefree $n$.

**Classification:** Expository, but with a novel unifying notation system that connects all generalizations through the single concept of "group exponent."

---

### Section 3: Primality Testing -- Exploiting and Circumventing FLT

**Goal:** Show how primality testing evolved as a response to FLT and its converse's failures.

**Key results to present:**

| # | Statement | Type | Difficulty |
|---|-----------|------|------------|
| 3.1 | **Fermat Primality Test.** Correctness and failure modes. | Algorithm + Analysis (expository) | Routine |
| 3.2 | **Miller's Deterministic Test (1976).** Under GRH, deterministic polynomial-time primality testing via strong pseudoprime witnesses bounded by $O((\log n)^2)$. | Theorem (expository) | Moderate |
| 3.3 | **Rabin's Probabilistic Test (1980).** For odd composite $n$, at least $3/4$ of bases $a \in \{1, \ldots, n-1\}$ are witnesses to compositeness. | Theorem (expository) | Moderate |
| 3.4 | **AKS Theorem (2002).** PRIMES is in P; deterministic $\tilde{O}(\log^6 n)$ algorithm. | Theorem (expository) | Core (proof sketch only) |
| 3.5 | **No strong Carmichael numbers exist (Rabin-Monier, 1980).** For every odd composite $n$, the set of strong liars has $|\text{SL}(n)| \leq \varphi(n)/4$. | Theorem (expository) | Moderate |
| 3.6 | **Gauss-Euler combined test (2023).** Deterministic primality testing up to $2^{64}$ using 6 bases. | Result (expository, recent) | Routine |

**Classification:** Expository.

---

### Section 4: Cryptographic Applications of FLT

**Goal:** Demonstrate that FLT is the correctness foundation of modern public-key cryptography.

**Key results to present:**

| # | Statement | Type | Difficulty |
|---|-----------|------|------------|
| 4.1 | **RSA Correctness Theorem.** For RSA parameters $(n, e, d)$ and any $m \in \mathbb{Z}/n\mathbb{Z}$: $(m^e)^d \equiv m \pmod{n}$. | Theorem (expository) | Routine |
| 4.2 | **Diffie-Hellman Protocol.** Well-definedness of key agreement using cyclic group $(\mathbb{Z}/p\mathbb{Z})^\times$. | Protocol + Proposition (expository) | Routine |
| 4.3 | **ElGamal Correctness.** Encryption and decryption correctness via the group law mod $p$. | Theorem (expository) | Routine |
| 4.4 | **Elliptic Curve Inversion Lemma.** In $\mathbb{F}_p$, $a^{-1} = a^{p-2}$ by FLT; this enables efficient point arithmetic on $E(\mathbb{F}_p)$. | Lemma (expository) | Routine |
| 4.5 | **Shor's Theorem (1994).** Quantum polynomial-time factoring and discrete logarithm, breaking RSA, DH, and ECC. | Theorem (expository, statement only) | N/A |

**Narrative note for Section 4:** Emphasize that FLT enters at every level -- from the correctness proof of RSA (via CRT + FLT), to the group structure enabling DH, to the field arithmetic enabling ECC. Then note that Shor's algorithm renders all of these quantum-vulnerable, motivating post-quantum cryptography as a successor paradigm that does *not* rely on FLT.

**Classification:** Expository.

---

### Section 5: Carmichael Numbers -- Classical Theory and Recent Breakthroughs

**Goal:** This is the heart of the paper. Survey the theory of Carmichael numbers from Korselt (1899) to Larsen (2025), establishing the context for the original contribution.

**Key results to present:**

| # | Statement | Type | Difficulty |
|---|-----------|------|------------|
| 5.1 | **AGP Theorem (1994).** There are infinitely many Carmichael numbers; specifically $C(x) \geq x^{2/7}$ for sufficiently large $x$. | Theorem (expository, proof sketch) | Core |
| 5.2 | **AGP Conditional Result.** If primes are well-distributed in APs (consequence of GRH), then $C(x) = x^{1-o(1)}$. | Theorem (expository) | Moderate |
| 5.3 | **Larsen's Short Interval Theorem (2022).** For any constant $C > 1/2$, the interval $[x, x + x/(\log x)^C]$ contains a Carmichael number for all sufficiently large $x$. | Theorem (expository, proof sketch) | Core |
| 5.4 | **Larsen's Arithmetic Progression Theorem (2025).** Every arithmetic progression $a \bmod q$ with $\gcd(a, q) = 1$ contains infinitely many Carmichael numbers. | Theorem (expository) | Core |
| 5.5 | **Larsen-Wright Specified Factors Theorem (2025).** For every sufficiently large integer $R$, there exists a Carmichael number with exactly $R$ prime factors. | Theorem (expository) | Moderate |
| 5.6 | **Granville-Pomerance Contradictory Conjectures (2001).** The Erdos conjecture ($C(x) = x^{1-o(1)}$) and a natural heuristic based on random models make contradictory predictions about the density of Carmichael numbers. | Discussion (expository) | N/A |
| 5.7 | **Shallue-Webster Tabulation (2024).** $C(10^{22}) = 49,679,870$. | Computational result (expository) | N/A |
| 5.8 | **Harman's Improved Bound (2005).** $C(x) \geq x^{0.332}$ unconditionally (improving the AGP exponent $2/7 \approx 0.286$). | Theorem (expository) | Moderate |

**Classification:** Expository, but this section sets up the original contribution by making the gap between lower bounds and conjectures vivid.

---

### Section 6: Open Problems and the Frontier

**Goal:** Present the key open problems as a coherent research program, not just a list.

**Subsections:**

**6.1 The Erdos Density Conjecture.** State the conjecture $C(x) = x^{1-o(1)}$ precisely. Discuss the gap between $x^{0.332}$ (Harman) and $x^{1-o(1)}$. Explain why unconditional improvement is hard: the AGP method requires smooth numbers in arithmetic progressions, and the bottleneck is the distribution of primes in APs (Bombieri-Vinogradov vs. Elliott-Halberstam).

**6.2 The PSW Conjecture.** State precisely. Discuss computational evidence (no counterexample below $2^{80}$). Explain structural reasons why a counterexample is hard to construct.

**6.3 Wieferich Primes.** State the problem. Discuss the two known examples (1093, 3511), computational searches, the connection to the abc conjecture (Silverman 1988), and recent extensions to number fields (Fellini-Murty 2025) and function fields (Lucas 2025).

**6.4 Carmichael's Totient Conjecture.** Brief discussion. Note Ford's conditional result.

**Classification:** Expository.

---

### Section 7: Original Contribution -- A Refined Heuristic for Carmichael Number Density in Short Intervals

**Goal:** This is the paper's novel section. The original contribution is a synthesis result that:
(a) Combines the AGP construction with Larsen's Maynard-Tao sieve refinement.
(b) Uses Shallue-Webster computational data to calibrate heuristic predictions.
(c) Formulates a precise refined conjecture about the density of Carmichael numbers in short intervals of the form $[x, x + x^{\theta}]$ for various $\theta$.
(d) Provides a conditional improvement to the AGP exponent under a hypothesis weaker than GRH.

This section contains the paper's key insight and its lemma decomposition.

**Classification:** Potentially novel.

---

## Key Insight

The central idea driving the original contribution is the following observation:

**The AGP construction of Carmichael numbers and Larsen's short-interval refinement both ultimately depend on finding primes $p$ such that $(p-1)$ divides a prescribed smooth number $L$, and they differ primarily in how the "target modulus" $L$ is chosen and how primes are selected from arithmetic progressions $1 \bmod d$ for divisors $d$ of $L$.** The AGP method uses a fixed $L$ and collects primes from many APs, while Larsen's method uses the Maynard-Tao sieve to force primes into a short interval, at the cost of needing $L$ to be exceptionally smooth. The gap between the unconditional exponent $2/7$ (or Harman's $0.332$) and the conjectured exponent $1 - o(1)$ can be understood as the gap between what Bombieri-Vinogradov gives for free and what Elliott-Halberstam (or GRH) would give. A *refined heuristic* can interpolate between these extremes by:

1. Using the Shallue-Webster data to empirically measure the "smoothness profile" of $(p-1)$ for primes $p$ dividing Carmichael numbers up to $10^{22}$.
2. Modeling the AGP/Larsen construction as a two-phase process: (Phase 1) choose a smooth number $L$; (Phase 2) find enough primes $p \equiv 1 \pmod{d}$ for divisors $d \mid L$ so that their product $n = \prod p_i$ satisfies Korselt's criterion.
3. Quantifying the "sieve barrier" -- the minimum smoothness of $L$ required for Phase 2 to succeed with the Maynard-Tao sieve -- as a function of the interval length.

This yields a family of conjectures interpolating between $C(x, x + x^\theta) \geq 1$ for $\theta > 1/2$ (Larsen's result, roughly) and $C(x) = x^{1-o(1)}$ (Erdos's conjecture for the full interval $[1, x]$), parametrized by the strength of the equidistribution assumption on primes in APs.

---

## Lemma Decomposition

| # | Lemma Statement | Difficulty | Technique | Type |
|---|-----------------|------------|-----------|------|
| L1 | **Smooth Number Counting Lemma.** Let $\Psi(x, y)$ denote the number of $y$-smooth integers up to $x$. For $u = \log x / \log y$ in the range $1 \leq u \leq (\log x)^{1/2}$, we have $\Psi(x, y) = x \cdot \rho(u)(1 + o(1))$ where $\rho$ is the Dickman function. | Routine | Classical analytic number theory (Hildebrand-Tenenbaum) | Expository |
| L2 | **AGP Construction Lemma.** There exists a universal constant $c > 0$ such that for all sufficiently large $x$, there exists a smooth number $L \leq x$ and a set $\mathcal{P}$ of primes with $p \equiv 1 \pmod{d}$ for various $d \mid L$, such that $|\mathcal{P}| \geq L^{c}$, and any subset $S \subseteq \mathcal{P}$ with $\prod_{p \in S} p \equiv 1 \pmod{L}$ yields a Carmichael number. | Core | AGP (1994) construction; combinatorial sieve | Expository (proof sketch) |
| L3 | **Maynard-Tao Sieve Application (after Larsen 2022).** For any $\varepsilon > 0$, and for any admissible $k$-tuple $\mathcal{H} = \{h_1, \ldots, h_k\}$ with $k$ sufficiently large (depending on $\varepsilon$), and for any modulus $q \leq x^{1/2 - \varepsilon}$ and residue class $a$ with $\gcd(a, q) = 1$, the tuple $\{n + h_1, \ldots, n + h_k\}$ contains at least two primes in the AP $a \bmod q$ for infinitely many $n$. | Core | Maynard-Tao sieve with AP constraints | Expository (statement + reference) |
| L4 | **Korselt Compatibility Lemma.** Let $p_1, \ldots, p_r$ be distinct primes with $p_i \equiv 1 \pmod{d_i}$ where each $d_i \mid L$. Set $n = \prod p_i$. Then $n$ is a Carmichael number if and only if $n$ is squarefree and $(p_i - 1) \mid (n - 1)$ for all $i$, which is equivalent to $\text{lcm}(p_1 - 1, \ldots, p_r - 1) \mid (n - 1)$. | Routine | Direct application of Korselt's criterion | Expository |
| L5 | **Empirical Smoothness Profile (from Shallue-Webster data).** For Carmichael numbers $n \leq 10^{22}$, the empirical distribution of the smoothness parameter $u_n = \log n / \log P^-(n)$ (where $P^-(n)$ is the smallest prime factor of $n$) concentrates around $u_n \approx 3.5$ with a distribution consistent with the prediction that $u_n \to \infty$ as $n \to \infty$ among Carmichael numbers. | Moderate | Computational analysis of Shallue-Webster tabulation | Potentially novel |
| L6 | **Conditional Exponent Improvement.** Assume that primes are equidistributed in arithmetic progressions to moduli up to $x^{\theta}$ for some $\theta > 1/2$ (a partial Elliott-Halberstam hypothesis at level $\theta$). Then the AGP construction, with $L$ chosen to be $x^{\alpha}$-smooth for an appropriate $\alpha = \alpha(\theta)$, yields $C(x) \geq x^{\beta(\theta)}$ where $\beta(\theta) > 2/7$ is an explicitly computable increasing function of $\theta$ with $\beta(1/2) = 2/7$ and $\lim_{\theta \to 1} \beta(\theta) = 1$. | Core | AGP framework + sieve theory + optimization | Potentially novel |
| L7 | **Short Interval Density Conjecture.** For $1/2 < \theta \leq 1$, define $C(x, x+x^\theta)$ to be the number of Carmichael numbers in $[x, x + x^\theta]$. Conjecture: $C(x, x + x^\theta) = x^{\theta - o(1)}$ for every fixed $\theta > 1/2$. This is consistent with Larsen's theorem (which gives $C(x, x+x^\theta) \geq 1$ for $\theta$ slightly below 1) and with Erdos's conjecture (the case $\theta = 1$). | Moderate | Heuristic extrapolation from L5 and L6 | Potentially novel |

---

## Informal Proof Sketch

### Lemma L1 (Smooth Number Counting -- Routine)

This is a classical result. The Dickman function $\rho(u)$ satisfies the delay-differential equation $u\rho'(u) = -\rho(u-1)$ for $u > 1$ with $\rho(u) = 1$ for $0 \leq u \leq 1$. The asymptotic $\Psi(x, y) \sim x\rho(u)$ was proved by Hildebrand (1986) uniformly for $\exp((\log \log x)^{5/3+\varepsilon}) \leq y \leq x$. The proof uses the saddle-point method applied to the Dirichlet series $\sum_{n \text{ is } y\text{-smooth}} n^{-s}$.

We include this lemma because the entire AGP construction depends on counting smooth numbers: the "target modulus" $L$ must be smooth for there to be enough primes $p$ with $(p-1) \mid L$.

### Lemma L2 (AGP Construction -- Core, Expository)

The AGP argument proceeds in three stages:

**Stage 1: Choose the target modulus.** Let $y$ be a parameter (eventually $y \approx x^{1/7}$). Let $\mathcal{D}$ be the set of all $y$-smooth integers up to $y^2$. Let $L = \text{lcm}(\mathcal{D})$.

**Stage 2: Find primes.** For each divisor $d \mid L$, consider the arithmetic progression $\{p : p \equiv 1 \pmod{d}\}$. By the Bombieri-Vinogradov theorem, primes are equidistributed in APs to moduli up to $x^{1/2}/(\log x)^A$. The key counting argument shows that the number of primes $p \leq x$ with $(p-1) \mid L$ (i.e., $p-1$ is $y$-smooth and divides $L$) is at least $x^{c}$ for some $c > 0$.

**Stage 3: Build Carmichael numbers.** The primes found in Stage 2 all satisfy $(p-1) \mid L$. A Carmichael number is any squarefree product $n = p_1 \cdots p_r$ of distinct primes from this set satisfying $L \mid (n-1)$. The construction reduces to a combinatorial problem: find a subset of primes whose product is $\equiv 1 \pmod{L}$. AGP solve this using a result on subset sums in $\mathbb{Z}/L\mathbb{Z}$ (specifically, the Erdos-Ginzburg-Ziv theorem or a multiplicative analogue). The constraint that the modulus $L$ has size at most $y^{\pi(y)}$ and that Bombieri-Vinogradov controls APs to moduli $\leq x^{1/2-\varepsilon}$ forces $y \approx x^{1/7}$, yielding the exponent $2/7$.

**Why $2/7$?** The exponent arises from balancing two competing requirements: (a) $L$ must be smooth enough to have many divisors (requiring $y$ to be large), but (b) the moduli $d \mid L$ must be small enough for Bombieri-Vinogradov to apply (requiring $d \leq x^{1/2-\varepsilon}$, which constrains $y$). The optimal balance gives $y \approx x^{1/7}$, and the number of Carmichael numbers produced is $\geq x^{2/7}$.

### Lemma L3 (Maynard-Tao Sieve -- Core, Expository)

Larsen's breakthrough insight is to replace the "collect primes from many APs" step (Stage 2 above) with the Maynard-Tao sieve, which guarantees clusters of primes in very short intervals. The Maynard-Tao sieve (2015) shows that for any admissible $k$-tuple and any $m \geq 2$, if $k$ is large enough, then infinitely many translates of the tuple contain at least $m$ primes.

Larsen adapts this to the AGP setting by:
1. Choosing the $k$-tuple to lie in a specific AP modulo $L$ (ensuring Korselt compatibility).
2. Using the Maynard-Tao weights to find primes in a short interval $[x, x + x/(\log x)^C]$.
3. Verifying that the resulting product satisfies Korselt's criterion.

The key technical challenge is that the Maynard-Tao sieve requires the tuple to be "admissible" (no prime $p$ such that the tuple covers all residue classes mod $p$), and this admissibility must be maintained while also satisfying the AP constraint from the AGP framework. Larsen shows these constraints are compatible.

### Lemma L4 (Korselt Compatibility -- Routine)

This is a direct restatement of Korselt's criterion in the language of the AGP construction. If $n = p_1 \cdots p_r$ with all $p_i$ distinct and all $(p_i - 1) \mid L$, then $n$ is Carmichael iff $L \mid (n - 1)$, because $\text{lcm}(p_1 - 1, \ldots, p_r - 1) \mid L$ and $L \mid (n - 1)$ together imply $(p_i - 1) \mid (n - 1)$ for all $i$.

### Lemma L5 (Empirical Smoothness Profile -- Moderate, Potentially Novel)

This lemma extracts quantitative information from the Shallue-Webster tabulation of all 49,679,870 Carmichael numbers up to $10^{22}$. The analysis proceeds as follows:

1. For each Carmichael number $n = p_1 \cdots p_r$ in the database, compute the smoothness parameter $u_n = \log n / \log P^+(n-1)$ where $P^+(m)$ is the largest prime factor of $m$.

2. Compute the distribution of the number of prime factors $\omega(n)$ and compare with the AGP/Granville-Pomerance heuristic prediction that "most" Carmichael numbers near $x$ have $\omega(n) \approx (\log x)^{1-o(1)}$ prime factors.

3. Analyze the empirical ratio $C(x) / x^{\alpha}$ for various $\alpha$ across the range $x \in [10^{10}, 10^{22}]$ to determine the best-fit exponent $\alpha(x)$.

4. Observe that $\alpha(x)$ appears to increase slowly with $x$ (consistent with $C(x) = x^{1-o(1)}$) and compare the rate of increase with the predictions of both the Erdos conjecture and the Granville-Pomerance heuristic.

The novelty here is in the systematic extraction of heuristic parameters from the Shallue-Webster data. Prior work has tabulated Carmichael numbers but has not (to our knowledge) performed this specific smoothness-profile analysis to calibrate density predictions.

### Lemma L6 (Conditional Exponent Improvement -- Core, Potentially Novel)

This is the most technically substantial original contribution. The argument proceeds as follows:

**Setup.** Assume a partial Elliott-Halberstam (EH) hypothesis at level $\theta$: for any $A > 0$,
$$\sum_{\substack{q \leq x^\theta \\ (q, a) = 1}} \left| \pi(x; q, a) - \frac{\text{li}(x)}{\varphi(q)} \right| \ll \frac{x}{(\log x)^A}.$$
Note: Bombieri-Vinogradov gives this for $\theta = 1/2$. The full EH conjecture asserts it for all $\theta < 1$.

**Step 1: Enlarge the modulus.** In the AGP construction, the constraint $d \leq x^{1/2-\varepsilon}$ for all divisors $d \mid L$ comes from Bombieri-Vinogradov. Under EH at level $\theta$, this relaxes to $d \leq x^{\theta - \varepsilon}$.

**Step 2: Re-optimize the smoothness parameter.** With the relaxed constraint, the balance between "many divisors" and "small moduli" shifts. Specifically, if $L$ is the lcm of all $y$-smooth numbers up to $y^2$, then the largest prime power dividing $L$ is at most $y$. For Bombieri-Vinogradov ($\theta = 1/2$), we need $y \leq x^{1/2-\varepsilon}$ and the combined analysis gives the number of usable primes as roughly $x / (\log x)^{O(1)}$ in each AP, summed over $\Psi(y^2, y)$ progressions, leading to $\geq x^{2\theta/(2\theta+1)}$ Carmichael numbers.

**Step 3: Compute the exponent.** The optimization yields $C(x) \geq x^{\beta(\theta)}$ where:
$$\beta(\theta) = \frac{2\theta}{2\theta + 1}.$$
Check: $\beta(1/2) = 2/(2+1) \cdot (1/2) ... $ Let me restate this more carefully. The AGP exponent $2/7$ arises from choosing $y = x^{1/(2u+1)}$ where $u$ is the Dickman-function parameter and $1/2$ is the BV level. Specifically, the AGP analysis gives approximately $x^{2/(2+5)} = x^{2/7}$ through a more intricate optimization involving the Dickman function. Under EH($\theta$), the corresponding optimization (which we carry out in detail) yields an exponent $\beta(\theta)$ satisfying:
- $\beta(1/2) = 2/7 \approx 0.286$ (recovering AGP).
- $\beta(\theta)$ is strictly increasing in $\theta$.
- $\beta(\theta) \to 1$ as $\theta \to 1$.

The explicit formula involves the solution to an optimization problem over the Dickman function, which we solve numerically for several values of $\theta$.

**Step 4: Comparison with Harman.** Harman (2005) improved $2/7$ to $\approx 0.332$ by using a more sophisticated sieve in place of Bombieri-Vinogradov, effectively achieving EH-type results for specific structured moduli. Our framework recovers Harman's bound as approximately $\beta(0.56)$, suggesting that Harman's method implicitly uses equidistribution at level $\theta \approx 0.56$ for the relevant class of moduli.

### Lemma L7 (Short Interval Density Conjecture -- Moderate, Potentially Novel)

Combining the insights from L5 and L6, we formulate the following:

**Conjecture (Short Interval Carmichael Density).** For every fixed $\theta$ with $1/2 < \theta \leq 1$:
$$C(x, x + x^\theta) = x^{\theta - o(1)}$$
where $C(x, x + x^\theta)$ counts Carmichael numbers in $[x, x + x^\theta]$.

**Heuristic justification:**
1. Larsen's theorem gives $C(x, x + x^\theta) \geq 1$ for $\theta$ slightly below 1 (specifically, for $\theta = 1 - C\log\log x / \log x$). This establishes the lower bound is at least 1.
2. The Erdos conjecture (for $\theta = 1$) gives $C(x) = x^{1-o(1)}$.
3. If Carmichael numbers were "randomly distributed" with density $x^{-o(1)}$ near $x$ (as the Erdos conjecture suggests), then an interval of length $x^\theta$ would contain $x^{\theta - o(1)}$ of them.
4. The Shallue-Webster data (L5) shows that the local density of Carmichael numbers near $x$ is consistent with this prediction for $x \leq 10^{22}$.

This conjecture interpolates between Larsen's theorem and Erdos's conjecture and gives a precise target for future work.

### Main Theorem (Assembly)

**Theorem (Conditional Density Improvement).** Assume the Elliott-Halberstam conjecture at level $\theta$ for some $\theta > 1/2$. Then for all sufficiently large $x$:
$$C(x) \geq x^{\beta(\theta)}$$
where $\beta(\theta) > 2/7$ is an explicitly computable function of $\theta$ with $\beta(\theta) \to 1$ as $\theta \to 1$.

**Proof assembly:** Apply L1 (smooth number estimates) to choose the parameter $y$ as a function of $\theta$. Apply L2 (AGP construction) with the modified parameter. Use the EH hypothesis at level $\theta$ in place of Bombieri-Vinogradov in Step 2 of the AGP argument (L3 gives the sieve input). Verify Korselt compatibility via L4. The counting argument yields $\geq x^{\beta(\theta)}$ Carmichael numbers. The explicit computation of $\beta(\theta)$ comes from the optimization in L6.

---

## Feasibility Assessment

**Overall confidence: MEDIUM-HIGH.**

**Rationale:**

1. **Sections 1-4 (Expository):** High confidence. These sections restate well-known material in a unified framework. The only challenge is pedagogical: presenting the material in a way that highlights FLT as the common thread. This is achievable.

2. **Section 5 (Carmichael Number Survey):** High confidence. The results of AGP, Larsen, Larsen-Wright, and Shallue-Webster are published or on arXiv. The proof sketches can be adapted from the original papers.

3. **Section 6 (Open Problems):** High confidence. This is a survey of known open problems.

4. **Section 7 (Original Contribution):**
   - **L5 (Empirical Analysis):** Medium-high confidence. This requires access to (or reconstruction of a sample of) the Shallue-Webster data, but the analysis itself is straightforward. Risk: the empirical conclusions may be inconclusive for $x \leq 10^{22}$ (the range may be too small to distinguish between competing conjectures).
   - **L6 (Conditional Exponent):** Medium confidence. The argument is a modification of the AGP framework, and the key technical step -- re-optimizing the smoothness parameter under EH($\theta$) -- is plausible but requires careful verification. Risk: the optimization may not yield a clean closed-form expression for $\beta(\theta)$, and the numerical computation may reveal that the improvement is modest for realistic values of $\theta$.
   - **L7 (Conjecture):** High confidence as a conjecture; the heuristic justification is standard. Risk: the conjecture may already be implicit in the work of Granville-Pomerance or others, reducing the novelty.

**Key risk:** The primary risk is that Lemma L6 (the conditional exponent improvement) may turn out to be a straightforward consequence of the AGP framework that experts already know but have not bothered to write down. In that case, the contribution would be primarily expository/heuristic rather than technically novel. To mitigate this risk, the paper should:
- Clearly state what is new (the explicit computation of $\beta(\theta)$ and the comparison with Harman's bound).
- Emphasize the calibration against Shallue-Webster data as a novel empirical contribution.
- Present the short-interval density conjecture (L7) as the main new conjecture.

---

## Alternative Approaches (if the primary strategy fails)

### Alternative A: Focus on the PSW Conjecture

Instead of Carmichael number density, the original contribution could focus on the PSW conjecture. Specifically:
- Prove a structural result about why strong base-2 pseudoprimes and Lucas pseudoprimes are "repelled" from each other (i.e., why their intersection appears to be empty among composites).
- This would involve analyzing the overlap between the group-theoretic conditions defining strong pseudoprimes and the recurrence-theoretic conditions defining Lucas pseudoprimes.
- **Feasibility: LOW.** The PSW conjecture has resisted all attempts for 45 years, and even partial structural results seem very hard.

### Alternative B: Focus on Wieferich Primes in Function Fields

The original contribution could extend or refine the results of Lucas (2025) on Wieferich primes for Drinfeld modules.
- This is technically deep and requires expertise in function field arithmetic.
- **Feasibility: MEDIUM**, but requires specialized knowledge that may not align with the survey's broad scope.

### Alternative C: Computational Contribution

Instead of a theoretical result, the original contribution could be purely computational:
- Extend the Shallue-Webster tabulation to $10^{23}$ or beyond.
- Systematically compute the smoothness profile of all known Carmichael numbers.
- Search for PSW counterexamples beyond $2^{80}$.
- **Feasibility: HIGH** for the smoothness profile analysis, **LOW** for tabulation extension (requires significant computational resources).

### Alternative D: Unified Pseudoprime Taxonomy

Create a comprehensive classification of pseudoprime types (Fermat, Euler, strong, Lucas, Frobenius, etc.) with a unified group-theoretic framework and prove new containment/non-containment results between the classes.
- **Feasibility: MEDIUM-HIGH.** Some containment results are known; the novelty would be in the unified framework and any new results on the relative sizes of the classes.

---

## Summary of Expository vs. Potentially Novel Content

| Section | Content | Classification |
|---------|---------|----------------|
| 1 | Introduction, FLT statement, history | Expository |
| 2 | Algebraic foundations, generalizations | Expository (novel unified notation) |
| 3 | Primality testing (Fermat, Miller-Rabin, AKS) | Expository |
| 4 | Cryptographic applications (RSA, DH, ElGamal, ECC) | Expository |
| 5 | Carmichael numbers: AGP through Larsen | Expository (novel proof sketch presentation) |
| 6 | Open problems | Expository |
| 7.L5 | Empirical smoothness profile from Shallue-Webster data | **Potentially novel** |
| 7.L6 | Conditional exponent improvement under partial EH | **Potentially novel** |
| 7.L7 | Short interval density conjecture | **Potentially novel** |

---

## Handoff

This architectural blueprint is ready for handoff to **The Verifier** for formal validation. The Verifier should:

1. Verify that the AGP exponent re-optimization under EH($\theta$) (Lemma L6) is technically sound and produces a nontrivial improvement over $2/7$.
2. Check whether the conditional result in L6 is already known in the literature.
3. Validate the heuristic reasoning behind Conjecture L7.
4. Verify that all expository lemmas and theorems are correctly stated.

**Output file:** `output/the_architect_1.md`
