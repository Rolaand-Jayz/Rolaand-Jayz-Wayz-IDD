# Rolaand Jayz Wayz – Coding with Natural Language: Intelligence Driven Development (RJW-IDD)

> **A disciplined methodology for AI-assisted software development** — no code, just the pure method and templates for the artefacts you create when applying it.

## 🗺️ Start Here

Welcome. If you are new to RJW-IDD, follow this path:

1.  **Understand the "Why":** Read [**WHY-RJW-IDD.md**](./WHY-RJW-IDD.md) to understand why "vibe coding" fails and how this method fixes it.
2.  **Explore the Method:**
    *   **Core Principles:** [METHOD-0001](./rjw-idd-methodology/core/METHOD-0001-principles.md)
    *   **Streamlined Operations:** [METHOD-0007](./rjw-idd-methodology/operations/METHOD-0007-streamlined-operations.md) (How to get work done fast)
    *   **Agent Trust:** [METHOD-0006](./rjw-idd-methodology/operations/METHOD-0006-agent-trust-and-autonomy.md) (How to work with AI agents)
3.  **Use the Templates:** When you do work, copy the templates from [`rjw-idd-methodology/templates/`](./rjw-idd-methodology/templates/).

---

## 📂 Repository Map

### Core Documents (`rjw-idd-methodology/`)

*   **`core/`**: The fundamental laws of the method.
    *   `METHOD-0001`: Principles.
    *   `METHOD-0002`: The detailed "Checklists" for high-risk work.
    *   `METHOD-0003`: Roles & Responsibilities.
*   **`operations/`**: How to execute.
    *   `METHOD-0004`: AI Agent Workflows.
    *   `METHOD-0005`: Production Support.
    *   `METHOD-0006`: **Agent Trust & Autonomy** (NEW).
    *   `METHOD-0007`: **Streamlined Operations** (NEW).
*   **`templates/`**: **Copy these to start working.**
    *   `TECH-CONTEXT-template.md`: **Crucial.** The living brain of your tech stack.
    *   `DEC-LITE-template.md`: For most day-to-day decisions.
    *   `PROJECT-DEC-template.md`: For big architectural choices.
    *   `AGENT-TRUST-template.md`: To promote/demote AI agents.

### Documentation (`docs/`)
*   `change-log.md`: The history of this methodology itself.

---

## 🚀 Quick Start Guide

### 1. Setup Your Project
Copy the `rjw-idd-methodology` folder into your project root.

### 2. Initialize Context
Create `docs/TECH-CONTEXT.md` using the [template](./rjw-idd-methodology/templates/TECH-CONTEXT-template.md). Fill in your current stack.

### 3. Choose Your Path (from METHOD-0007)

*   **Small Fix?** → **Pathway B (Low Risk)**
    *   Check `TECH-CONTEXT.md`.
    *   Write a failing test.
    *   Fix it.
    *   Update Change Log.
*   **New Feature?** → **Pathway C (High Risk)**
    *   Create a `DEC-####` decision record.
    *   Write a `SPEC-####`.
    *   Update `TECH-CONTEXT.md` if adding libs.
    *   Implement & Verify.

---

## 🤝 Contributing
See [CONTRIBUTING.md](./CONTRIBUTING.md) for how to propose changes to this methodology.
