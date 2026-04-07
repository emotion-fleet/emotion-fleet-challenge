# Evaluation Criteria

This document outlines how submissions are evaluated. Understanding these criteria will help you prioritize your efforts during the assignment.

## Evaluation Philosophy

We evaluate candidates on their **ability to think through problems, make sound technical decisions, and suggest improvements that would increase the efficacy of the whole team**, not just their ability to produce working code. A submission with fewer features but clear reasoning, strong prioritization, and senior-level judgment is valued over a feature-complete submission with unclear structure or shallow trade-offs.

## Core Evaluation Areas

### 1. Product, API, and Interface Design (30%)

| Aspect | What We Look For |
|--------|------------------|
| **Endpoint structure** | Intuitive resource naming, useful response shapes, and clear contracts |
| **Interface design** | Clear information hierarchy, sensible user flows, and role-appropriate frontend execution |
| **Component or service architecture** | Logical boundaries, separation of concerns, and pragmatic abstractions |
| **Data flow** | Predictable fetching, state handling, and clear ownership of transformation logic |

**Questions we ask ourselves:**
- Would another developer understand how this system is meant to work?
- Is the API or UI structure easy to reason about and extend?
- Did the candidate make good trade-offs for the timebox and their track?

### 2. Data Normalization and Domain Correctness (25%)

| Aspect | What We Look For |
|--------|------------------|
| **Consistency** | Unified formats for timestamps, units, and identifiers across the required data sources |
| **Correctness** | Accurate timezone conversions, unit transformations, and ID mappings |
| **Edge cases** | Handling of missing data, null values, ongoing sessions, and ambiguous records |
| **Documentation** | Clear explanation of normalization strategy and assumptions |

**Questions we ask ourselves:**
- Did the candidate identify the meaningful inconsistencies in the data?
- Is the normalization logic centralized, explainable, and testable?
- Are edge cases handled gracefully rather than ignored?

### 3. Code Organization and Maintainability (25%)

| Aspect | What We Look For |
|--------|------------------|
| **Structure** | Logical file organization and clear module boundaries |
| **Readability** | Meaningful names, consistent style, and low accidental complexity |
| **Maintainability** | Code that would be easy to modify, debug, or extend |
| **Type safety** | Appropriate use of types (TypeScript for FE, type hints for Python) |

**Questions we ask ourselves:**
- Could a new team member navigate this codebase quickly?
- Is there unnecessary complexity or obvious code smell?
- Does the implementation feel intentional rather than scaffolded and unreviewed?

### 4. Quality Ownership, Delivery, and Communication (20%)

| Aspect | What We Look For |
|--------|------------------|
| **Testing and regression strategy** | Good prioritization of critical paths, failure modes, and regression risks |
| **Delivery strategy** | Practical thinking about CI/CD, deployment, verification, and release confidence |
| **Documentation quality** | Concise, useful explanations of decisions and trade-offs |
| **Communication** | Clear asynchronous communication and good prioritization under time pressure |

**Questions we ask ourselves:**
- Did the candidate show clear regression awareness?
- Is the delivery strategy pragmatic for the scope of the exercise?
- Can we understand what they built, what they skipped, and why?

## Role-Specific Emphasis

### Frontend-Heavy Candidates

We place additional emphasis on:
- Interface clarity and information hierarchy
- Frontend architecture and state management
- Usability, accessibility, and interaction quality
- Role-appropriate frontend testing strategy
- Clear integration with the API layer

### Backend-Heavy Candidates

We place additional emphasis on:
- API contract design and response modeling
- Data normalization boundaries and transformation logic
- Failure handling and backend maintainability
- Role-appropriate backend testing strategy
- Clear interfaces for frontend consumers

## Evaluation Tiers

### Strong Submission

- Core API and UI flows work correctly
- Data inconsistencies are handled thoughtfully and documented clearly
- Code is well-organized, readable, and maintainable
- Testing and delivery strategy is clear and appropriately prioritized
- Optional bonus items are not required for the submission to be considered strong

### Acceptable Submission

- Core functionality works with minor issues
- Some normalization or architectural gaps remain
- Code is functional but could be better organized
- Testing or delivery strategy is present but shallow or incomplete

### Weak Submission

- Core functionality is incomplete or broken
- Data inconsistencies are not meaningfully addressed
- Documentation is missing, minimal, or vague
- Code is difficult to follow or feels largely unexamined

## What We Don't Expect To Be Fully Implemented

To be explicit about what does not need to be fully built within the timebox:

| Not Fully Implemented | What We Still Evaluate |
|-----------------------|------------------------|
| **Production deployment pipeline** | We do evaluate delivery strategy and release thinking |
| **Exhaustive automated test suite** | We do evaluate testing priorities, regression coverage, and risk awareness |
| **Brand or marketing-level visual design** | For frontend-heavy candidates, we still evaluate interface clarity, usability, and execution quality |
| **Load testing or scale benchmarking** | We may discuss performance reasoning in the interview |
| **Optional features such as utility integration or date filtering** | We care more about disciplined prioritization than feature sprawl |

## Bonus Consideration

Optional bonus items can strengthen a submission, but **only if core requirements are solid**. A submission with excellent core execution and no bonuses will score higher than one with rushed core execution and attempted bonuses.

Bonus items that positively impact evaluation:
- Integrating the optional Power Provider API in a thoughtful way
- Adding optional date filtering where it meaningfully improves the experience
- Observability, failure-handling, or operational safeguards
- Additional useful features that demonstrate product or system thinking

## AI Tool Usage

Using AI tools is allowed. We may ask about how you used them, how you validated the output, and how AI influenced your testing, QA, or review process.

If you want to share that proactively, an `AI_USAGE.md` note is welcome but optional.

## Interview Follow-up

When time allows, we may also explore additional senior signals in the interview, such as:

- Monitoring, observability, and operational ownership
- Performance and scaling trade-offs
- Developer experience (DX) and maintainability improvements
- Suggestions that would improve the effectiveness of the wider team
- How AI tools or agents were orchestrated, validated, and used for QA

---

*We evaluate the whole picture - technical skills, product judgment, communication quality, and senior-level prioritization.*
