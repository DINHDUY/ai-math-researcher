# The "Autonomous Math Researcher"

The production of a mathematical research paper is a unique blend of creative problem-solving and rigorous logical construction. Unlike many laboratory sciences, the "experiment" happens entirely through deduction, often taking months or even years to move from a "hunch" to a published theorem.

Here is the full workflow, from the initial spark of an idea to the final publication.

---

## Phase 1: Problem Selection & Investigation

Before a single word is typed, a mathematician must find a "gap" in the mathematical landscape.

* **Identifying the Conjecture:** The researcher selects a mathematical statement (conjecture) whose truth is unknown. This often comes from reading existing literature or attending seminars.
* **The "Coffee & Chalkboard" Stage:** This is the non-linear process of testing small cases, looking for counterexamples, and searching for a logical path.
* **Collaboration:** Most modern math research is collaborative. Professors often use digital whiteboards or tools like **Miro** or **Graspable Math** to brainstorm synchronously.

---

## Phase 2: Drafting the Proof (The "Informal" Stage)

Once a researcher believes they have a proof, they move from "discovery" to "verification."

* **Filling the Gaps:** A proof that "works" in one's head often has "holes" when written down. This stage involves meticulous checking of every lemma and corollary.
* **The LaTeX Standard:** Almost all math papers are written in **LaTeX**. It is the industry standard because it handles complex symbols ($e^{i\pi} + 1 = 0$) and bibliography management (BibTeX) with precision.
* **Drafting Style:** Mathematicians often "write in spirals"—drafting the introduction, then a section of the proof, then returning to the introduction to refine definitions based on what they discovered during the proof.

---

## Phase 3: The Preprint & Community Feedback

In mathematics, sharing work *before* formal publication is a critical cultural norm.

* **The arXiv Submission:** Before submitting to a journal, mathematicians upload their paper to **arXiv.org**. This "timestamps" the discovery to prevent being "scooped" and makes the work immediately available to the global community.
* **Informal Peer Review:** After the arXiv post, the author might receive emails from colleagues pointing out typos, suggesting simpler proofs, or noting missing citations.
* **Refining:** The author updates the arXiv version (e.g., "v2") based on this feedback before approaching a journal.

---

## Phase 4: Formal Submission & Peer Review

The formal "Publishing" phase is notoriously slow in mathematics, often taking **6 to 24 months**.

| Step | Action |
| --- | --- |
| **Journal Selection** | The author chooses a journal based on the paper's "reach" (e.g., *Annals of Mathematics* for ground-breaking work vs. specialized journals). |
| **The Editor's Desk** | An editor performs a "sanity check." If the paper looks interesting and relevant, they send it to "referees" (anonymous experts). |
| **The Referee Process** | Referees do not just check for "good writing"; they must verify the **logical correctness** of the math. This is a grueling, line-by-line audit. |
| **The Decision** | The author receives one of three results: **Accept**, **Revision Required** (most common), or **Reject**. |

---

## Phase 5: Publication & Beyond

Once the math is verified and the logic is deemed sound, the paper moves to production.

* **Copyediting:** Journal editors check for grammar and style, though they rarely touch the math itself.
* **The Final Version:** The "Version of Record" is published in the journal.
* **Archiving:** The author usually updates the arXiv page with a link to the official published version, ensuring the "pre-print" remains open-access for those without journal subscriptions.

---

## Subagents

### # Subagent: The Scout

**Objective:** Contextualize the problem and prevent "reinventing the wheel."

* **Input:** User Research Topic / Conjecture.
* **Tools:** `arXiv_API`, `Google_Scholar_Search`.
* **Scratchpad:** Maintain a list of "Prior Art" and "Unsolved Gaps."
* **Handoff:** If a unique gap is found, pass `Problem_Statement` + `Citations` to **The Architect**.

---

### # Subagent: The Architect

**Objective:** Generate the high-level logical strategy (The "Aha!" moment).

* **Input:** `Problem_Statement` from **The Scout**.
* **Process:** 1.  Break the main conjecture into smaller, manageable **Lemmas**.
2.  Write an informal proof sketch in plain English.
* **Handoff:** Pass `Informal_Sketch` to **The Verifier**.

---

### # Subagent: The Verifier (Formal Logic)

**Objective:** Ensure the logic isn't just "plausible," but mathematically certain.

* **Input:** `Informal_Sketch`.
* **Process:** 1.  Attempt to translate the English steps into **Lean 4** or **Isabelle** code.
2.  Run the code in a kernel.
* **Loop Trigger:** If code fails to compile, send `Error_Logs` back to **The Architect** with the message: *"Logic broken at Step 3; re-evaluate the assumption of X."*
* **Handoff:** On 100% compilation success, pass `Verified_Code` to **The Red-Teamer**.

---

### # Subagent: The Red-Teamer (The Critic)

**Objective:** Find the "hidden" flaws the Verifier might have missed (e.g., vacuous truths or circular reasoning).

* **Input:** `Verified_Code` + `Informal_Sketch`.
* **Process:** 1.  Search for "Trivial Cases" (e.g., what happens if $n=0$ or $p=2$?).
2.  Check for "Circular Logic" (did the Architect assume the conclusion in Lemma 2?).
* **Handoff:** If it passes the "Stress Test," pass the full "Verified Bundle" to **The Scribe**.

---

### # Subagent: The Scribe (LaTeX Production)

**Objective:** Polish the raw logic into a journal-ready manuscript.

* **Input:** `Verified Bundle` (Math + Citations).
* **Constraints:** Use `amsart` document class. Ensure all `\label{}` and `\ref{}` commands match.
* **Handoff:** Final `.tex` file and `.pdf` to the User.
