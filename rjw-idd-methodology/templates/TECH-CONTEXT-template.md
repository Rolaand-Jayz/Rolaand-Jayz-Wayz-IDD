# TECH-CONTEXT — Living Tech Stack & Context

> **Usage Instructions:**
> 1. **Read before planning:** The AI Agent MUST read this document before generating any plan to understand the current technical constraints, patterns, and decisions.
> 2. **Reference during implementation:** Ensure code changes align with the "Current Architecture & Patterns" section.
> 3. **Update after changes:** If a plan introduces a new library, changes a pattern, or deprecates a component, the AI Agent MUST update this document.
>    - **Do not create a new file.**
>    - **Do not delete history.** Add a new entry to the "Context Evolution Log" and update the "Current" sections.

## 1. Current Architecture & Patterns

### 1.1 Core Technology Stack
| Component | Technology | Version | Justification/Notes |
|-----------|------------|---------|---------------------|
| Language | Python | 3.10+ | Standard for AI/ML workflows. |
| Testing | Pytest | Latest | Standard testing framework. |
| Linter | Flake8 | Latest | Code quality enforcement. |
| **[Add Category]** | **[Tech]** | **[Ver]** | **[Notes]** |

### 1.2 Architectural Principles
- **Principle 1**: [e.g., Modular Design - components should be loosely coupled]
- **Principle 2**: [e.g., Traceability - every code change links to a Spec/Dec]

### 1.3 Coding Standards & Patterns
- **Naming**: [e.g., snake_case for functions, PascalCase for classes]
- **Error Handling**: [e.g., Use custom exceptions defined in `errors.py`]
- **Documentation**: [e.g., Google style docstrings required]

## 2. Active Technical Constraints
*   **Constraint A**: [e.g., Must run offline]
*   **Constraint B**: [e.g., No external database dependencies]

---

## 3. Context Evolution Log

> **Instructions:** When changing the stack or patterns, add a new row to the top of this table. "Impact" should describe what existing code needs to be updated or refactored.

| Date | Change Description | Rationale | Impact / Migration Steps | Agent ID |
|------|--------------------|-----------|--------------------------|----------|
| YYYY-MM-DD | Initial Context Creation | Project initialization | N/A | [Agent/Human] |
