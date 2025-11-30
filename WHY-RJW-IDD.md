# Why RJW-IDD? — The Case for Disciplined AI Development

> **TL;DR:** "Vibe coding" — asking an AI to "make it work" without context or structure — leads to unmaintainable chaos. RJW-IDD (Intelligence Driven Development) provides the missing structure: **Context, Traceability, and Trust**.

## 1. The Problem: The "Vibe Coding" Trap

In the age of AI coding assistants, it's tempting to fall into "Vibe Coding":
1.  **Prompt:** "Make me a snake game."
2.  **Result:** Code that works... mostly.
3.  **Prompt:** "Add multiplayer."
4.  **Result:** The AI rewrites half the code, breaking the single-player mode, changing variable names, and introducing new, unverified libraries.

### The Consequences
*   **Amnesia:** The AI forgets *why* previous decisions were made.
*   **Drift:** The codebase loses coherence as different "vibes" (prompts) pull it in different directions.
*   **Black Boxes:** Humans can't review the logic because it's buried in thousands of lines of generated code without a paper trail.
*   **Fragility:** Changes are made blindly, often breaking downstream dependencies that the AI didn't "see" in its limited context window.

## 2. The Solution: RJW-IDD

**Rolaand Jayz Wayz – Intelligence Driven Development** is a methodology designed to treat AI not as a magic wand, but as a **junior engineer that needs clear specs**.

### Core Pillars

#### A. Context is King (The "Living Context")
Instead of relying on the AI's training data or short-term memory, we maintain a **Living Tech Context**.
*   **Before:** AI guesses what libraries to use.
*   **RJW-IDD:** AI reads `TECH-CONTEXT.md`, sees we use `pytest` and `flask`, and generates code that fits *perfectly* into the existing slot.

#### B. Traceability (The "Paper Trail")
Every line of code exists because a **Decision** was made and a **Spec** was written.
*   **DEC-####**: Records *why* we chose Option A over Option B.
*   **SPEC-####**: Defines *what* exactly needs to be built.
*   **Code**: Implements the Spec.
*   **Result:** If code breaks, we don't just patch it; we fix the Spec and the Decision that led to it.

#### C. Trust through Verification
We don't trust the AI's "vibe". We trust its **Evidence**.
*   **Harvesters**: Tools that gather raw data (logs, docs) to prove assumptions.
*   **Audits**: Checkpoints where humans verify that the AI followed the process.
*   **Behavioral Contracts**: Agents explicitly agree to "stop and ask" when risks are high (see `METHOD-0006`).

## 3. The Workflow: From Chaos to Order

1.  **Discovery**: We don't write code yet. We ask questions. We gather evidence. We make decisions (`DEC-####`).
2.  **Specification**: We define the solution in natural language (`SPEC-####`). Humans review this. It's English, not Python, so anyone can understand it.
3.  **Execution**: The AI translates the approved Spec into Code. Because the Spec is clear, the Code is correct.
4.  **Verification**: We verify the output against the Spec, not just "does it run?".

## 4. Human-First Design

This repository is designed for **Humans** first, AI second.
*   **Readable Artifacts**: Documents start with Summaries. Decisions explain trade-offs.
*   **Navigable Structure**: You shouldn't need `grep` to find the architecture decision.
*   **Clear Paths**: Whether you're fixing a typo or re-architecting the backend, there is a clear, risk-appropriate path for you (`METHOD-0007`).

---
*Stop coding on vibes. Start coding with intelligence.*
