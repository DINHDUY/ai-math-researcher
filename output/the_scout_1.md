# The Scout Report: Fermat's Little Theorem -- Applications in Number Theory and Cryptography

**Date:** 2026-03-03
**Topic:** Fermat's Little Theorem, its generalizations, applications in primality testing and cryptography, and associated open problems.

---

## 1. Statement, History, and Generalizations

### 1.1 Precise Statement

**Fermat's Little Theorem (FLT).** If $p$ is a prime and $\gcd(a, p) = 1$, then

$$a^{p-1} \equiv 1 \pmod{p}.$$

Equivalently, for any integer $a$: $a^p \equiv a \pmod{p}$.

### 1.2 Historical Origins

- **Pierre de Fermat** first stated the theorem in a letter to Frenicle de Bessy dated **1640**, without proof.
- **Gottfried Wilhelm Leibniz** gave an unpublished proof sometime before **1683**.
- **Leonhard Euler** provided the first published proof in **1736**, and later generalized the result.

### 1.3 Euler's Generalization

**Euler's Theorem.** For any modulus $n$ and any integer $a$ with $\gcd(a, n) = 1$:

$$a^{\varphi(n)} \equiv 1 \pmod{n},$$

where $\varphi(n)$ is Euler's totient function. When $n = p$ is prime, $\varphi(p) = p - 1$, recovering Fermat's Little Theorem.

### 1.4 Further Generalizations

- **Carmichael's Theorem:** $a^{\lambda(n)} \equiv 1 \pmod{n}$ for $\gcd(a,n)=1$, where $\lambda(n)$ is the Carmichael function (the exponent of the multiplicative group $(\mathbb{Z}/n\mathbb{Z})^\times$). Note $\lambda(n) \mid \varphi(n)$.
- **Group-theoretic formulation (Lagrange's Theorem):** For any finite group $G$ and element $x \in G$, $x^{|G|} = e$. FLT is the special case $G = (\mathbb{Z}/p\mathbb{Z})^\times$.
- **Matrix generalizations:** Congruences generalizing FLT have been proved for traces of powers of integer matrices (Arnold, Zarelua, and others).
- **Gaussian integer extensions:** FLT extends to Gaussian primes $\pi$: if $\pi \nmid \alpha$, then $\alpha^{N(\pi)-1} \equiv 1 \pmod{\pi}$.
- **Ring-theoretic extensions:** Hernandez, Hernandez Melo, and Tapia-Recillas (2020, arXiv:2012.06949) extended FLT to a class of rings satisfying the CNC-condition.

---

## 2. Prior Art Summary

### 2.1 Core References Table

| # | Reference | Year | Key Result | Relevance |
|---|-----------|------|------------|-----------|
| 1 | Euler, L. "Theorematum quorundam ad numeros primos spectantium demonstratio" | 1736 | First published proof of FLT | Foundational |
| 2 | Euler, L. "Theoremata circa residua ex divisione potestatum relicta" | 1763 | Proof of Euler's theorem ($a^{\varphi(n)} \equiv 1$) | Direct generalization |
| 3 | Korselt, A. "Probleme chinois" | 1899 | Korselt's criterion for Carmichael numbers | Structural characterization of pseudoprimes |
| 4 | Carmichael, R.D. "On composite numbers $P$ which satisfy..." | 1910 | First examples and study of absolute Fermat pseudoprimes | Definition of Carmichael numbers |
| 5 | Miller, G.L. "Riemann's hypothesis and tests for primality" | 1976 | Deterministic primality test assuming GRH | Connects FLT to Riemann Hypothesis |
| 6 | Rabin, M.O. "Probabilistic algorithm for testing primality" | 1980 | Miller-Rabin probabilistic primality test (error $\leq 4^{-k}$) | Most widely used FLT-based primality test |
| 7 | Rivest, R.L., Shamir, A., Adleman, L. "A method for obtaining digital signatures and public-key cryptosystems" | 1978 | RSA cryptosystem | FLT underpins RSA correctness |
| 8 | Diffie, W., Hellman, M. "New directions in cryptography" | 1976 | Diffie-Hellman key exchange | Relies on cyclic group structure from FLT |
| 9 | ElGamal, T. "A public key cryptosystem and a signature scheme based on discrete logarithms" | 1985 | ElGamal encryption and signatures | Uses multiplicative group structure mod $p$ |
| 10 | Pomerance, C., Selfridge, J.L., Wagstaff, S.S. "The pseudoprimes to $25 \cdot 10^9$" | 1980 | Extensive tabulation of pseudoprimes | Empirical foundation for pseudoprime theory |
| 11 | Alford, W.R., Granville, A., Pomerance, C. "There are infinitely many Carmichael numbers" | 1994 | $C(x) \geq x^{2/7}$ for large $x$ | Proved infinitude of Carmichael numbers |
| 12 | Agrawal, M., Kayal, N., Saxena, N. "PRIMES is in P" | 2002 | Deterministic polynomial-time primality test (AKS) | Resolved PRIMES in P unconditionally |
| 13 | Larsen, D. "Bertrand's postulate for Carmichael numbers" | 2022 | Carmichael number in $[x, x + x/(\log x)^C]$ for all $C > 1/2$ | Resolved Alford-Granville-Pomerance conjecture |
| 14 | Larsen, D. "Carmichael numbers in all possible arithmetic progressions" | 2025 | Every AP either contains infinitely many Carmichael numbers or none, with a simple criterion | Major structural advance |
| 15 | Larsen, D., Wright, T. "Carmichael numbers with a specified number of prime factors" | 2025 | For every sufficiently large $R$, there exists a Carmichael number with exactly $R$ prime factors | Advances toward Granville-Pomerance conjecture |
| 16 | Shallue, A., Webster, J. "Advances in tabulating Carmichael numbers" | 2024 | Tabulated all Carmichael numbers up to $10^{22}$ (49,679,870 total) | State-of-the-art computational enumeration |
| 17 | Isaacs, I.M., Pournaki, M.R. "Generalizations of Fermat's Little Theorem via Group Theory" | 2005 | Group-theoretic proof yielding FLT for non-prime moduli | Elegant generalization technique |
| 18 | Wagstaff, S.S. "Pseudoprimes and Fermat numbers" | 2024 | Strong pseudoprime bases for composite Fermat numbers | Recent contribution on pseudoprime structure |
| 19 | Fellini, Murty. "Wieferich primes in number fields and the conjectures of Ankeny-Artin-Chowla and Mordell" | 2025 | Connects Wieferich primes to AAC conjecture; infinitely many non-Wieferich primes under abc for number fields | Extends FLT-adjacent theory to number fields |
| 20 | Lucas, A. "Wieferich and Mersenne primes for function fields" | 2025 | Wieferich primes for Drinfeld modules; relation with Fermat equations | Function field analogue |
| 21 | Hernandez, Hernandez Melo, Tapia-Recillas. "Fermat's Little Theorem and Euler's Theorem in a class of rings" | 2020 | Extension of FLT to rings with CNC-condition | Algebraic generalization |
| 22 | Granville, A., Pomerance, C. "Two contradictory conjectures concerning Carmichael numbers" | 2001 | Analysis of Erdos vs. Pomerance conjectures on Carmichael number density | Highlights tension in the conjectural landscape |
| 23 | Harman, G. "On the number of Carmichael numbers up to $x$" | 2005 | Improved lower bound on $C(x)$ | Best known improvement over AGP lower bound |

### 2.2 Surveys and Textbooks

| # | Reference | Year | Scope |
|---|-----------|------|-------|
| S1 | Hardy, G.H., Wright, E.M. "An Introduction to the Theory of Numbers" | 1938 (6th ed. 2008) | Classical treatment of FLT, Euler's theorem, pseudoprimes |
| S2 | Crandall, R., Pomerance, C. "Prime Numbers: A Computational Perspective" | 2005 | Comprehensive treatment of primality testing algorithms |
| S3 | Katz, J., Lindell, Y. "Introduction to Modern Cryptography" | 2020 (3rd ed.) | RSA, DH, ElGamal with number-theoretic foundations |
| S4 | Washington, L.C. "Elliptic Curves: Number Theory and Cryptography" | 2008 (2nd ed.) | ECC over finite fields, FLT role in field arithmetic |
| S5 | Odlyzko, A. "Discrete logarithms in finite fields and their cryptographic significance" | 1985 | Seminal survey on DLP and cryptographic implications |

---

## 3. Number Theory Applications (Detailed)

### 3.1 Primality Testing

**Fermat Primality Test.** Given input $n$, choose random base $a$ with $1 < a < n$; if $a^{n-1} \not\equiv 1 \pmod{n}$, then $n$ is composite. The test fails on Carmichael numbers (which pass for all bases coprime to $n$).

**Miller-Rabin Test.** Strengthens the Fermat test by writing $n - 1 = 2^s \cdot d$ and checking both $a^d \equiv 1 \pmod{n}$ and $a^{2^r d} \equiv -1 \pmod{n}$ for some $0 \leq r < s$. Error probability $\leq 4^{-k}$ after $k$ rounds. No strong Carmichael numbers exist (Rabin-Monier, 1980).

**AKS Test.** Agrawal, Kayal, and Saxena (2002) proved PRIMES is in P via a deterministic polynomial-time algorithm. Best known complexity: $\tilde{O}(\log^6 n)$. Primarily of theoretical importance; Miller-Rabin dominates in practice.

**Gauss-Euler Primality Test.** Combined with Miller-Rabin (arXiv:2311.07048, 2023), achieves deterministic testing of all integers up to $2^{64}$ using only 6 bases.

### 3.2 Carmichael Numbers and Pseudoprimes

- **Korselt's Criterion:** $n$ is Carmichael iff $n$ is squarefree and $(p-1) \mid (n-1)$ for every prime $p \mid n$.
- **Smallest:** 561 = 3 * 11 * 17.
- **Infinitude:** Proved by Alford, Granville, Pomerance (1994). Lower bound: $C(x) \geq x^{2/7}$.
- **Upper bound:** $C(x) < x^{0.337}$ (Harman/Pomerance).
- **Short intervals:** Larsen (2022) proved Carmichael numbers exist in $[x, x + x/(\log x)^C]$ for any $C > 1/2$.
- **Arithmetic progressions:** Larsen (2025) showed every AP either contains infinitely many Carmichael numbers or none.
- **Tabulation:** Shallue and Webster (2024) enumerated all $\sim$49.7 million Carmichael numbers up to $10^{22}$.

### 3.3 Connection to Group Theory

$(\mathbb{Z}/p\mathbb{Z})^\times$ is a cyclic group of order $p - 1$. FLT is the statement that every element has order dividing $|G| = p - 1$. This perspective generalizes immediately:
- To $(\mathbb{Z}/n\mathbb{Z})^\times$ (Euler's theorem).
- To any finite group (Lagrange's theorem).
- To matrix groups, polynomial rings, and other algebraic structures.

---

## 4. Cryptography Applications (Detailed)

### 4.1 RSA Cryptosystem

**Setup:** Choose distinct primes $p, q$; let $n = pq$, $\varphi(n) = (p-1)(q-1)$. Choose $e$ with $\gcd(e, \varphi(n)) = 1$; compute $d \equiv e^{-1} \pmod{\varphi(n)}$.

**Correctness:** For any message $m$, $(m^e)^d = m^{ed} \equiv m \pmod{n}$. The proof uses:
1. Write $ed = 1 + k(p-1)(q-1)$.
2. By FLT: $m^{ed} = m \cdot (m^{p-1})^{k(q-1)} \equiv m \cdot 1 \equiv m \pmod{p}$ (when $\gcd(m,p) = 1$).
3. Similarly mod $q$.
4. By the Chinese Remainder Theorem: $m^{ed} \equiv m \pmod{n}$.

The case $p \mid m$ (or $q \mid m$) is handled separately and yields $m^{ed} \equiv 0 \equiv m \pmod{p}$.

### 4.2 Diffie-Hellman Key Exchange

Operates in the cyclic group $(\mathbb{Z}/p\mathbb{Z})^\times$ (or a subgroup of prime order $q \mid p-1$). FLT guarantees that:
- The group has order $p - 1$.
- Exponentiation is well-defined and periodic.
- Security reduces to the Discrete Logarithm Problem (DLP) in this group.

Safe primes $p = 2q + 1$ (where $q$ is also prime) are preferred so that the group structure resists the Pohlig-Hellman attack.

### 4.3 Digital Signatures (ElGamal, DSA)

- **ElGamal (1985):** Based on the DLP in $(\mathbb{Z}/p\mathbb{Z})^\times$. Signature verification uses the group law, which relies on FLT for its cyclic structure.
- **DSA (NIST, 1994):** A variant of ElGamal operating in a prime-order subgroup. FLT ensures the subgroup structure via $g^q \equiv 1 \pmod{p}$ where $q \mid p - 1$.

### 4.4 Elliptic Curve Cryptography (ECC)

FLT connects to ECC through:
1. **Finite field arithmetic:** Point operations on $E(\mathbb{F}_p)$ require computing multiplicative inverses in $\mathbb{F}_p$. By FLT, $a^{-1} \equiv a^{p-2} \pmod{p}$, enabling efficient inversion via fast exponentiation.
2. **Group structure:** The group $E(\mathbb{F}_p)$ has order $|E(\mathbb{F}_p)| = p + 1 - t$ (Hasse's theorem, $|t| \leq 2\sqrt{p}$), and the Elliptic Curve Discrete Logarithm Problem (ECDLP) provides security.
3. **Schoof's algorithm** for counting points on elliptic curves uses properties of Frobenius endomorphisms acting on $\ell$-torsion points, deeply connected to finite field theory.

### 4.5 Post-Quantum Considerations

Shor's algorithm (1994) breaks RSA, DH, and ECC in polynomial time on a quantum computer. All FLT-based cryptographic schemes are therefore vulnerable to quantum attacks. Post-quantum replacements (lattice-based, code-based, etc.) do not rely on FLT or the DLP.

---

## 5. Unsolved Gaps

### Gap 1: Asymptotic Density of Carmichael Numbers (Erdos's Conjecture)

**Status: WIDE OPEN.** Erdos (1956) conjectured $C(x) = x^{1-o(1)}$. The best unconditional lower bound remains $C(x) \geq x^{2/7}$ (Alford-Granville-Pomerance, 1994). The best upper bound is $C(x) < x^{0.337}$. The gap between the lower bound exponent ($\approx 0.286$) and the conjectured exponent (approaching 1) is enormous. Alford, Granville, and Pomerance showed that if primes are well-distributed in arithmetic progressions (a consequence of GRH), then $C(x) = x^{1-o(1)}$.

### Gap 2: Carmichael Numbers with Exactly $k$ Prime Factors

**Status: PARTIALLY RESOLVED.** The Granville-Pomerance conjecture states that for every $k \geq 3$, there exist infinitely many Carmichael numbers with exactly $k$ prime factors, and $C_k(x) = x^{1/k + o_k(1)}$. Larsen and Wright (2025) proved that for every sufficiently large $R$, a Carmichael number with exactly $R$ prime factors exists. The case of small $k$ (particularly $k = 3$) and the precise asymptotic density remain open.

### Gap 3: Wieferich Primes

**Status: WIDE OPEN.** Only two Wieferich primes are known: 1093 and 3511 (primes $p$ with $p^2 \mid 2^{p-1} - 1$). It is unknown whether infinitely many exist. Silverman (1988) showed the abc conjecture implies infinitely many non-Wieferich primes. Computational searches have verified no others exist below $6.7 \times 10^{15}$. Recent work (Fellini-Murty, 2025) connects number field analogues of Wieferich primes to the Ankeny-Artin-Chowla conjecture.

### Gap 4: The PSW Conjecture (Baillie-PSW Primality Test)

**Status: OPEN.** No composite number is known that is simultaneously a strong pseudoprime to base 2 and a Lucas pseudoprime with the standard parameter choice. A $620 prize stands for a counterexample or proof. No PSW challenge pseudoprimes with two or three prime factors exist up to $2^{80}$.

### Gap 5: Connection to the Generalized Riemann Hypothesis (GRH)

**Status: CONDITIONAL RESULTS ONLY.** Miller (1976) showed GRH implies a deterministic polynomial-time primality test. More broadly, GRH implies sharp bounds on the distribution of primes in arithmetic progressions, which would in turn resolve Erdos's conjecture on Carmichael numbers. The iterated Carmichael $\lambda$-function has normal order behavior that is provable under GRH but not unconditionally.

### Gap 6: Improving AKS Complexity

**Status: STALLED.** The best proven AKS complexity is $\tilde{O}(\log^6 n)$. A variant proposed by Agrawal-Kayal-Saxena would achieve $\tilde{O}(\log^3 n)$ if Agrawal's conjecture holds, but Lenstra and Pomerance provided heuristic evidence that Agrawal's conjecture is likely false. No new improvements have appeared since approximately 2005.

### Gap 7: Carmichael's Totient Conjecture

**Status: OPEN since 1907.** Carmichael conjectured that no value of Euler's totient function $\varphi$ is attained exactly once. Ford showed that if a counterexample exists, a positive proportion of integers are also counterexamples. Shannon, Shiue, He, and Saito (2025) explored special cases, but the general conjecture remains open.

---

## 6. Novelty Assessment

Fermat's Little Theorem itself is a completely settled classical result with multiple known proofs. Its direct generalizations (Euler's theorem, Lagrange's theorem) are likewise well-established. However, the landscape of *applications and consequences* of FLT contains several active and wide-open research fronts:

1. **The distribution of Carmichael numbers** remains one of the central open problems in analytic number theory, with the Erdos conjecture ($C(x) = x^{1-o(1)}$) unresolved and the gap between known bounds being very large. The recent work of Larsen (2022, 2025) and Larsen-Wright (2025) represents genuine breakthroughs but does not close the main asymptotic question.

2. **Wieferich primes** are among the most enigmatic objects in number theory. The finiteness or infinitude question is entirely open, and the connection to the abc conjecture makes this a problem at the frontier of arithmetic geometry.

3. **Post-quantum cryptography** has rendered FLT-based cryptosystems (RSA, DH, ElGamal, ECDSA) theoretically vulnerable, creating active research into replacement schemes, though the underlying number theory remains rich.

4. **Novel algebraic generalizations** of FLT to rings, function fields, and matrix settings continue to appear, though these are more incremental extensions than breakthrough directions.

A research program focusing on (a) the precise asymptotics of Carmichael number distribution, (b) the structure of pseudoprimes under combined Fermat-Lucas tests (PSW conjecture), or (c) Wieferich primes in number fields would be engaging genuinely open territory.

---

## 7. Recommended Problem Statement

**For a survey/expository paper:**

> Provide a unified treatment of Fermat's Little Theorem as a structural backbone for both analytic number theory (primality testing, pseudoprime distribution, Carmichael numbers) and public-key cryptography (RSA, Diffie-Hellman, elliptic curve cryptography). Synthesize recent advances -- particularly Larsen's results on Carmichael numbers in short intervals and arithmetic progressions (2022--2025), Shallue-Webster's computational tabulations (2024), and function field analogues of Wieferich primes (2025) -- and identify the key open problems: the Erdos density conjecture for Carmichael numbers, the PSW conjecture, and the finiteness of Wieferich primes.

**For an original research direction:**

> Investigate the gap between the unconditional lower bound $C(x) \geq x^{2/7}$ and the conjectured $C(x) = x^{1-o(1)}$ for the Carmichael number counting function, potentially leveraging Larsen's techniques involving Maynard-Tao sieve methods combined with the Alford-Granville-Pomerance framework. A concrete subproblem: can the exponent $2/7$ in the AGP lower bound be unconditionally improved?

---

## 8. Key Citations

### Foundational

```
@article{fermat1640,
  author  = {Pierre de Fermat},
  title   = {Letter to Fr\'{e}nicle de Bessy},
  year    = {1640},
  note    = {Statement of Fermat's Little Theorem (without proof)}
}

@article{euler1736,
  author  = {Leonhard Euler},
  title   = {Theorematum quorundam ad numeros primos spectantium demonstratio},
  journal = {Commentarii Academiae Scientiarum Petropolitanae},
  volume  = {8},
  pages   = {141--146},
  year    = {1736},
  note    = {First published proof of Fermat's Little Theorem}
}
```

### Primality Testing

```
@article{miller1976,
  author  = {Gary L. Miller},
  title   = {Riemann's hypothesis and tests for primality},
  journal = {Journal of Computer and System Sciences},
  volume  = {13},
  number  = {3},
  pages   = {300--317},
  year    = {1976}
}

@article{rabin1980,
  author  = {Michael O. Rabin},
  title   = {Probabilistic algorithm for testing primality},
  journal = {Journal of Number Theory},
  volume  = {12},
  number  = {1},
  pages   = {128--138},
  year    = {1980}
}

@article{aks2004,
  author  = {Manindra Agrawal and Neeraj Kayal and Nitin Saxena},
  title   = {{PRIMES} is in {P}},
  journal = {Annals of Mathematics},
  volume  = {160},
  number  = {2},
  pages   = {781--793},
  year    = {2004}
}
```

### Carmichael Numbers

```
@article{agp1994,
  author  = {W. R. Alford and Andrew Granville and Carl Pomerance},
  title   = {There are infinitely many {C}armichael numbers},
  journal = {Annals of Mathematics},
  volume  = {139},
  number  = {3},
  pages   = {703--722},
  year    = {1994}
}

@article{larsen2023,
  author  = {Daniel Larsen},
  title   = {Bertrand's postulate for {C}armichael numbers},
  journal = {International Mathematics Research Notices},
  volume  = {2023},
  number  = {15},
  pages   = {13072--13098},
  year    = {2023}
}

@article{larsen2025ap,
  author  = {Daniel Larsen},
  title   = {Carmichael numbers in all possible arithmetic progressions},
  journal = {arXiv preprint},
  note    = {arXiv:2504.09056},
  year    = {2025}
}

@article{larsenwright2025,
  author  = {Daniel Larsen and Thomas Wright},
  title   = {Carmichael numbers with a specified number of prime factors},
  journal = {arXiv preprint},
  note    = {arXiv:2510.16632},
  year    = {2025}
}

@article{shalluewebster2024,
  author  = {Andrew Shallue and Jonathan Webster},
  title   = {Advances in tabulating {C}armichael numbers},
  journal = {Research in Number Theory},
  volume  = {10},
  year    = {2024},
  doi     = {10.1007/s40993-024-00598-3}
}

@article{granvillepomerance2001,
  author  = {Andrew Granville and Carl Pomerance},
  title   = {Two contradictory conjectures concerning {C}armichael numbers},
  journal = {Mathematics of Computation},
  volume  = {71},
  number  = {238},
  pages   = {883--908},
  year    = {2001}
}
```

### Cryptography

```
@article{rsa1978,
  author  = {Ronald L. Rivest and Adi Shamir and Leonard Adleman},
  title   = {A method for obtaining digital signatures and public-key cryptosystems},
  journal = {Communications of the ACM},
  volume  = {21},
  number  = {2},
  pages   = {120--126},
  year    = {1978}
}

@article{diffiehellman1976,
  author  = {Whitfield Diffie and Martin E. Hellman},
  title   = {New directions in cryptography},
  journal = {IEEE Transactions on Information Theory},
  volume  = {22},
  number  = {6},
  pages   = {644--654},
  year    = {1976}
}

@inproceedings{elgamal1985,
  author    = {Taher ElGamal},
  title     = {A public key cryptosystem and a signature scheme based on discrete logarithms},
  booktitle = {Advances in Cryptology -- CRYPTO '84},
  pages     = {10--18},
  year      = {1985},
  publisher = {Springer}
}
```

### Wieferich Primes and Fermat Quotients

```
@article{fellini_murty2025,
  author  = {Fellini and M. Ram Murty},
  title   = {Wieferich primes in number fields and the conjectures of {A}nkeny--{A}rtin--{C}howla and {M}ordell},
  journal = {arXiv preprint},
  note    = {arXiv:2508.08472},
  year    = {2025}
}

@article{lucas2025,
  author  = {Alexis Lucas},
  title   = {Wieferich and {M}ersenne primes for function fields},
  journal = {arXiv preprint},
  note    = {arXiv:2512.08060},
  year    = {2025}
}
```

### Generalizations

```
@article{isaacs_pournaki2005,
  author  = {I. Martin Isaacs and M. R. Pournaki},
  title   = {Generalizations of {F}ermat's {L}ittle {T}heorem via group theory},
  journal = {American Mathematical Monthly},
  volume  = {112},
  pages   = {734--740},
  year    = {2005}
}

@article{hernandez2020,
  author  = {de Melo Hern\'{a}ndez and Hern\'{a}ndez Melo and Tapia-Recillas},
  title   = {Fermat's {L}ittle {T}heorem and {E}uler's {T}heorem in a class of rings},
  journal = {arXiv preprint},
  note    = {arXiv:2012.06949},
  year    = {2020}
}
```

---

## 9. Search Limitations

- **arXiv coverage:** Searches were performed via web search engines querying arXiv; some preprints may have been missed, particularly very recent ones (January--March 2026).
- **Paywalled journals:** Some results behind journal paywalls may not have appeared in search results.
- **Non-English literature:** The search was conducted in English only; relevant results in other languages may exist.
- **Scope:** The topic is extremely broad, spanning 400 years of mathematics. This report prioritizes results from the last 30 years with emphasis on 2020--2025 developments.

---

## 10. Handoff Note

This report is ready for handoff to **The Architect**. The recommended problem statement (Section 7) and key citations (Section 8) provide a complete foundation for structuring either an expository survey or an original research paper. The seven identified unsolved gaps (Section 5) offer concrete directions for novel contributions.

**File path:** `output/the_scout_1.md`
