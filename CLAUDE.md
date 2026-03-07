# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

This is an autonomous multi-agent pipeline that simulates the mathematical research process — from literature review to journal-ready LaTeX manuscripts. The system uses Claude Code's subagent feature to orchestrate five specialized agents working in sequence.

## Architecture

### Multi-Agent Pipeline

Five subagents collaborate sequentially via **file-based communication**:

1. **the-scout** → Literature review (arXiv + Google Scholar)
2. **the-architect** → Proof strategy & lemma decomposition
3. **the-verifier** → Formal verification (Lean 4 / Isabelle)
4. **the-red-teamer** → Adversarial stress testing
5. **the-scribe** → LaTeX manuscript production (`amsart` class)

### Subagent Communication Pattern

- Each subagent is defined in `.claude/agents/<name>.md`
- Subagents read input from **file paths** (not in-memory state)
- All output is persisted to `output/<subagent_name>_<N>.md` where N is an incrementing integer
- Handoffs pass **file paths** to the next subagent, which reads them first before processing

**Example flow:**
```
the-scout writes → output/the_scout_1.md
the-architect reads output/the_scout_1.md → writes output/the_architect_1.md
the-verifier reads output/the_architect_1.md → writes output/the_verifier_1.md
...
```

### Feedback Loops

The pipeline includes built-in feedback mechanisms:
- **Verification failure:** The Verifier → The Architect (with error diagnosis)
- **Critical flaws:** The Red-Teamer → The Architect (with remediation suggestions)

When feedback loops trigger, file numbers increment (e.g., `the_architect_2.md` after receiving failure report from `the_verifier_1.md`).

## Invoking Subagents

Use the Agent tool (via CLI or programmatically) to invoke subagents:

```bash
claude "use subagent /the-scout Investigate how this theorem is applied in number theory"
```

The subagent name must match the filename in `.claude/agents/` without the `.md` extension.

## Working with Subagent Definitions

When modifying subagent behavior:

1. **Read the full agent definition** in `.claude/agents/<name>.md` first
2. Subagent definitions include:
   - **When Invoked** — expected inputs
   - **Workflow** — step-by-step process
   - **Output Format** — structured report template
   - **Output Persistence** — filename pattern for writing results
   - **Handoff** — instructions for passing control to the next subagent
3. Preserve the handoff contracts between subagents — they must pass file paths, not raw content
4. All subagents follow the pattern: read input file(s) → process → write output file → hand off file path

## Output Directory

The `output/` directory contains:
- Numbered markdown reports from each subagent invocation
- Final deliverables: `.tex`, `.bib`, and `.pdf` files from The Scribe
- These files are tracked in version control (not gitignored)

## Key Constraints

### For The Verifier
- Must compile formal proofs to 100% completion (no `sorry` or `Admitted`)
- Prefers Lean 4; uses Isabelle when domain libraries require it
- On failure, must produce structured error reports with diagnosis and suggested fixes

### For The Red-Teamer
- Tests for 7 flaw types: vacuous truths, circular reasoning, edge cases, hidden assumptions, over-specialization, axiom abuse, and residual gaps
- Every finding requires concrete evidence (counterexample or logical trace)
- Verdict must be one of: PASS, PASS WITH WARNINGS, or FAIL

### For The Scribe
- Must use `amsart` document class
- All `\label{}` and `\ref{}` must match (no dangling references)
- BibTeX must compile cleanly
- Performs cross-reference audit before finalizing

## File-Based State Management

This system has **no runtime database or state store**. All state is preserved in markdown files in `output/`. When debugging pipeline issues:

1. Check the most recent numbered file for each subagent
2. Verify that handoff file paths are correct and files exist
3. Ensure each subagent actually reads its input files before processing

## Subagent Development Best Practices

When extending or debugging subagents:

- **Always read input files first** — subagents must load context from previous stage outputs
- **Always write full output** — never skip the output persistence step
- **Increment file numbers** — check for existing files with glob pattern `output/<subagent_name>_*.md`
- **Pass file paths in handoffs** — not raw content or summaries
- **Preserve feedback loop contracts** — The Architect must accept failure reports from both The Verifier and The Red-Teamer
