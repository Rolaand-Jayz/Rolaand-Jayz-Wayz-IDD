# METHOD-0008 — Prototype Pathway

This document establishes a dedicated pathway for rapid proof-of-concept development within the RJW-IDD methodology. It enables speed and iteration while maintaining traceability so both AI agents and humans can distinguish between essential elements and flexible scaffolding.

> **When to Use:** For prototypes, spikes, feasibility studies, and experimental features. Not for production-ready changes—use METHOD-0002 pathways instead.

## 1. Entry Criteria

### When to Use the Prototype Path

Use this pathway when:

- **Proof of Concept (POC):** Validating a technical approach or architecture before committing to full implementation
- **Spike:** Time-boxed investigation to reduce uncertainty about a solution
- **Feasibility Study:** Determining if a capability is achievable within constraints
- **Experimental Features:** Exploring new functionality without production-grade requirements
- **Technology Evaluation:** Comparing frameworks, libraries, or approaches hands-on

### Distinction from Production Pathways

| Aspect | Prototype Path (METHOD-0008) | Production Paths (METHOD-0002) |
|--------|------------------------------|-------------------------------|
| **Goal** | Learn / Prove / Explore | Ship / Deploy / Maintain |
| **Time Horizon** | Days to weeks (max 4 weeks) | Variable (driven by scope) |
| **Quality Bar** | "Good enough to learn" | "Ready for users" |
| **Review** | Self-review acceptable | Peer review required (Medium+) |
| **Testing** | Smoke tests sufficient | Full coverage expected |
| **Documentation** | Inline comments + PROTO record | Full specifications and runbooks |
| **Exit** | Promote / Archive / Abandon | Release / Maintain |

### Time-Boxing Recommendations

| Prototype Type | Default Time-Box | Maximum Extension |
|----------------|------------------|-------------------|
| Quick spike | 2–3 days | 1 week |
| Standard POC | 1–2 weeks | 3 weeks |
| Complex feasibility | 2–3 weeks | 4 weeks |

**Hard Limit:** No prototype may exceed 4 weeks without a forced exit decision. If more time is needed, formally archive or promote the work and start fresh with a new PROTO record or full DEC-#### if promoting.

## 2. Lightweight Traceability

### PROTO Identifiers

Prototypes use `PROTO-####` identifiers (e.g., `PROTO-0001`, `PROTO-0002`). These are sequential within a project scope.

### Required Fields

Every prototype must capture:

| Field | Description | Example |
|-------|-------------|---------|
| **Intent Statement** | What are we trying to prove or learn? | "Validate that WebSocket-based architecture can handle 10K concurrent connections" |
| **Success Criteria** | How will we know if this worked? | "Sustain 10K connections with <100ms latency for 5 minutes" |
| **Time Limit** | When does this prototype expire? | "2024-12-15 (2 weeks from start)" |

### Optional but Encouraged

- Rough architecture notes or diagrams
- Known limitations and shortcuts
- Links to related evidence or decisions
- Stakeholder who requested the prototype

### PROTO Record Location

Store prototype records in `docs/prototypes/PROTO-####.md` using the template at `rjw-idd-methodology/templates/PROTO-template.md`.

## 3. Keep/Flex/Unknown Tagging System

Semantic tags help AI agents and humans distinguish between essential prototype elements and temporary scaffolding during code review and when promoting to production.

### Tag Definitions

| Tag | Variants | Meaning | Action on Promotion |
|-----|----------|---------|---------------------|
| **Keep** | `⟦keep⟧` or `[KEEP]` | Core to the proof-of-concept; essential for the prototype to function | Preserve and enhance to production quality |
| **Flex** | `⟦flex⟧` or `[FLEX]` | Scaffolding, shortcuts, or experimental approaches | Replace with production-grade implementation |
| **Unknown** | `⟦unknown⟧` or `[UNKNOWN]` | Uncertain whether essential; needs evaluation | Review during promotion; decide keep or replace |

### Usage Examples

**In Code Comments:**

```python
# ⟦keep⟧ Core connection pooling logic - proven to handle load
class ConnectionPool:
    def __init__(self, max_connections):
        self.pool = []  # ⟦flex⟧ Replace with thread-safe queue
        self.max = max_connections

    # ⟦unknown⟧ Retry logic may need adjustment for production
    def get_connection(self, retry=3):
        ...
```

**In Documentation:**

```markdown
## Architecture

### Message Queue [KEEP]
RabbitMQ handles message routing. Proven reliable in prototype load tests.

### Database Layer [FLEX]
Using SQLite for prototype speed. Must migrate to PostgreSQL for production.

### Caching Strategy [UNKNOWN]
Redis caching added for performance. Needs evaluation if essential or if
the main optimization was elsewhere.
```

**In PROTO Records:**

See Section 4 "Key Components" in the template for structured tagging.

### Tagging Guidelines

1. **Tag at the component level:** Tag functions, classes, or modules rather than individual lines
2. **Be honest about unknowns:** It's better to mark something `[UNKNOWN]` than guess wrong
3. **Update tags as you learn:** If you discover a `[FLEX]` item is actually essential, change it to `[KEEP]`
4. **Document rationale:** Brief notes explaining why something is tagged a certain way help during promotion

## 4. Relaxed Gates

### What Is NOT Required

In prototype mode, the following production-standard requirements are relaxed:

| Gate | Production Requirement | Prototype Allowance |
|------|------------------------|---------------------|
| **Peer Review** | Required (Medium+ risk) | Self-review acceptable |
| **Test Coverage** | Full coverage expected | Smoke tests sufficient |
| **Documentation** | Specs, runbooks, full docs | Inline comments + PROTO record |
| **Security Review** | Required for security-relevant | Not required unless handling real user data |
| **Performance Benchmarks** | Expected for affected areas | Not required unless performance is the thing being proven |
| **Full DEC Record** | Required (Medium+ risk) | PROTO record sufficient |
| **Evidence Harvesting** | Full research loop | Prior knowledge or quick research acceptable |

### What IS Still Required

Even in prototype mode, these remain mandatory:

| Requirement | Rationale |
|-------------|-----------|
| **PROTO decision record** | Ensures intent is captured; prevents drift |
| **Keep/Flex tagging** | Enables informed promotion decisions |
| **Time-box adherence** | Prevents prototypes from becoming shadow production systems |
| **Exit decision** | Every prototype must end with Promote, Archive, or Abandon |
| **Basic functionality** | Code should run and demonstrate the intended capability |
| **No real user data** | Unless explicitly authorized with proper consent handling |

### Security Exceptions

If the prototype must handle real user data or integrate with production systems:

- Security review IS required
- Data handling consent IS required
- Consider using the Low Risk production path (METHOD-0002 Section B) instead

## 5. Exit Options

Every prototype must conclude with one of three exit decisions documented in the PROTO record.

### Option 1: Promote to Production

**When to choose:** The prototype proved its hypothesis and the approach should be productionized.

**Process:**

1. Review all `[KEEP]`, `[FLEX]`, and `[UNKNOWN]` tags
2. Create a `DEC-####` decision record referencing the PROTO record as evidence
3. Initiate full METHOD-0002 pathway at appropriate risk level
4. Queue `[FLEX]` items for production-grade replacement
5. Evaluate `[UNKNOWN]` items and classify as keep or flex
6. Update PROTO record status to "Promoted" with link to DEC-####

**Traceability Chain:**

```text
PROTO-#### (evidence) → DEC-#### (decision) → Full METHOD-0002 execution
```

### Option 2: Archive

**When to choose:** The prototype provided valuable learnings but won't be productionized now (maybe later, different approach chosen, deprioritized).

**Process:**

1. Document learnings in PROTO record Section 6 "Exit Decision"
2. Capture what worked, what didn't, and why archiving vs promoting
3. Preserve code in a designated archive location or branch
4. Update PROTO record status to "Archived"
5. Ensure learnings are findable for future reference

**Code Preservation:**

- Option A: Move to `archived/prototypes/PROTO-####/` directory
- Option B: Tag with `archived-PROTO-####` git tag
- Option C: Document location in PROTO record; code stays in place but marked inactive

### Option 3: Abandon

**When to choose:** The prototype proved the approach doesn't work or is not worth pursuing.

**Process:**

1. Document why the approach failed in PROTO record Section 6
2. Capture lessons learned (negative knowledge is valuable)
3. Code may be deleted (no preservation requirement)
4. Update PROTO record status to "Abandoned"

**Value of Abandonment:** A well-documented abandonment prevents others from repeating failed experiments. Always capture *why* the approach was abandoned.

### Forced Exit at Time-Box Expiry

When a prototype reaches its time-box limit without a natural exit:

1. **Stop work immediately** — no extensions without new PROTO
2. **Conduct rapid assessment:**
   - Did we learn what we intended?
   - Is the path forward clear?
   - What's the confidence level?
3. **Choose exit option** based on current state
4. **If more time truly needed:** Archive current PROTO, create new PROTO-#### with fresh time-box

## 6. AI Agent Guidance

### Working Within Prototype Mode

AI agents operating in prototype mode have increased autonomy and reduced verification overhead:

**Increased Autonomy:**

- Self-review acceptable without human sign-off for each change
- Can iterate rapidly without per-change documentation
- May use experimental approaches and shortcuts
- Can declare success/failure based on objective criteria

**Reduced Verification:**

- Smoke tests sufficient (happy path + basic error handling)
- Inline comments acceptable instead of full documentation
- Performance optimization not required unless proving performance
- Security hardening not required unless handling real data

**Still Required:**

- Maintain PROTO record with current status
- Tag components with Keep/Flex/Unknown
- Adhere to time-box limits
- Escalate if scope changes significantly
- Respect hard constraints (no real user data without authorization)

### Interpreting Tags When Working on Promoted Code

When an AI agent encounters promoted prototype code (indicated by reference to a PROTO-#### in the DEC-#### record):

**For `[KEEP]` tagged code:**

- Preserve the core logic and approach
- May refactor for production quality
- May add error handling, logging, tests
- Do NOT change the fundamental approach without new decision

**For `[FLEX]` tagged code:**

- This is explicitly marked for replacement
- Production-grade implementation expected
- Review PROTO record for context on why this was temporary
- Use standard METHOD-0002 approach for the replacement

**For `[UNKNOWN]` tagged code:**

- Stop and evaluate before modifying
- Determine if this is actually essential (reclassify to KEEP)
- Or if it can be replaced (reclassify to FLEX)
- Document the classification decision in the DEC-#### record
- Then proceed based on new classification

### Trust Level Adjustments for Prototype Work

Prototype mode does not change an agent's trust level, but it does adjust how that trust is applied:

| Trust Level | Standard Mode | Prototype Mode |
|-------------|---------------|----------------|
| Level 0 | All actions require approval | PROTO-scoped actions may batch for approval |
| Level 1 | Pre-approved categories only | All prototype work is pre-approved within scope |
| Level 2 | Autonomous with post-hoc review | Autonomous; review at prototype exit |
| Level 3 | Strategic participation | May approve PROTO records and exit decisions |

### Prototype Workflow Summary for Agents

```text
1. Receive prototype assignment (or propose one)
2. Draft PROTO-#### record with intent, criteria, time-box
3. Work iteratively toward success criteria
   - Tag components as KEEP/FLEX/UNKNOWN as you build
   - Self-review; iterate quickly
   - Document surprises and learnings
4. Assess against success criteria at midpoint
5. At time-box end or completion:
   - Evaluate against success criteria
   - Recommend exit decision with rationale
   - If promoting: identify DEC-#### pathway and risk level
6. Update PROTO record with exit decision
```

## 7. Companion Assets

- `METHOD-0001` — Core methodology principles
- `METHOD-0002` — Phase checklists (production pathways)
- `METHOD-0003` — Role handbook
- `METHOD-0004` — AI agent workflows
- `METHOD-0006` — Agent trust and autonomy framework
- `templates/PROTO-template.md` — Prototype decision record template

## 8. Method Adoption Steps

1. Create `docs/prototypes/` directory in your project for PROTO records
2. Copy `PROTO-template.md` as starting point for first prototype
3. Ensure team understands Keep/Flex/Unknown tagging conventions
4. Establish maximum time-box policy (recommend 4-week hard limit)
5. Define archive location for completed prototypes
6. Add prototype exit reviews to regular governance cadence
7. Train AI agents on prototype mode expectations (reference this document)

## 9. Related Documentation

- `governance/METHOD-0002-phase-driver-checklists.md` — Production pathways (Quick Start references this document)
- `operations/METHOD-0004-ai-agent-workflows.md` — Full agent workflow including prototype mode
- `operations/METHOD-0006-agent-trust-and-autonomy.md` — Trust framework for agents
- `templates/PROTO-template.md` — Template for prototype records
