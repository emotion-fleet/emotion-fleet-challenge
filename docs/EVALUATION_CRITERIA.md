# Evaluation Criteria

This document outlines how submissions are evaluated. Understanding these criteria will help you prioritize your efforts during the assignment.

## Evaluation Philosophy

We evaluate candidates on their **ability to think through problems, make sound technical decisions, and suggest improvements that would increase the efficacy of the whole team**, not just their ability to produce working code. A submission with fewer features but clear reasoning, strong prioritization, and senior-level judgment is valued over a feature-complete submission with unclear structure or shallow trade-offs.

## Core Evaluation Areas

### 1. Product, API, and Interface Design (25%)

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

### 2. Data Normalization and Domain Correctness (20%)

| Aspect | What We Look For |
|--------|------------------|
| **Consistency** | Unified formats for timestamps, units, and identifiers across all data sources |
| **Correctness** | Accurate timezone conversions, unit transformations, and ID mappings |
| **Edge cases** | Handling of missing data, null values, ongoing sessions, and ambiguous records |
| **Documentation** | Clear explanation of normalization strategy and assumptions |

**Questions we ask ourselves:**
- Did the candidate identify the meaningful inconsistencies in the data?
- Is the normalization logic centralized, explainable, and testable?
- Are edge cases handled gracefully rather than ignored?

### 3. Code Organization and Maintainability (20%)

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

### 4. Senior Engineering Strategy (20%)

| Aspect | What We Look For |
|--------|------------------|
| **Testing and regression strategy** | Good prioritization of critical paths, failure modes, and regression risks |
| **Deployment and CI/CD approach** | Practical thinking about environments, pipelines, rollout, and verification |
| **Monitoring and failsafes** | Thoughtful observability, alerting, and graceful degradation ideas |
| **Performance and scale reasoning** | Awareness of likely bottlenecks, trade-offs, and future scaling concerns |

**Questions we ask ourselves:**
- Does the candidate think like someone who has to own this in production?
- Did they distinguish what must be implemented now from what should be planned next?
- Would their strategy reduce regressions and operational surprises for the team?

### 5. DX, Communication, and Team Efficacy (15%)

| Aspect | What We Look For |
|--------|------------------|
| **Developer experience** | Clear local setup, useful scripts, and maintainable workflows |
| **Documentation quality** | Concise, practical explanations of decisions and trade-offs |
| **Team leverage** | Suggestions that would improve handoff quality, onboarding, or delivery speed for the broader team |
| **AI collaboration quality** | Thoughtful use of AI tools or agents, with evidence of validation and ownership |

**Questions we ask ourselves:**
- Would this submission make the next engineer faster rather than slower?
- Does the candidate communicate clearly and asynchronously?
- Do they suggest improvements that would increase the efficacy of the wider team?

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
- Senior-level strategy is present for testing, deployment, monitoring, performance, and DX
- AI usage is documented clearly and validated critically if AI was used

### Acceptable Submission

- Core functionality works with minor issues
- Some normalization or architectural gaps remain
- Code is functional but could be better organized
- Strategy is present but shallow, incomplete, or not well-prioritized

### Weak Submission

- Core functionality is incomplete or broken
- Data inconsistencies are not meaningfully addressed
- Documentation is missing, minimal, or vague
- Code is difficult to follow or feels largely unexamined
- Senior engineering strategy is absent or superficial

## What We Don't Expect To Be Fully Implemented

To be explicit about what does not need to be fully built within the timebox:

| Not Fully Implemented | What We Still Evaluate |
|-----------------------|------------------------|
| **Production deployment pipeline** | We do evaluate deployment and CI/CD strategy |
| **Brand or marketing-level visual design** | For frontend-heavy candidates, we still evaluate interface clarity, usability, and execution quality |
| **Load testing or scale benchmarking** | We do evaluate performance assumptions, bottleneck awareness, and mitigation ideas |
| **Feature completeness beyond requirements** | We care more about disciplined prioritization than feature sprawl |

## Bonus Consideration

Optional bonus items can strengthen a submission, but **only if core requirements are solid**. A submission with excellent core execution and no bonuses will score higher than one with rushed core execution and attempted bonuses.

Bonus items that positively impact evaluation:
- Monitoring, observability, alerting, or failure-recovery measures
- Data freshness, synchronization, or refresh mechanisms where they materially improve the solution
- Additional useful features that demonstrate product, operational, or system thinking

## AI Tool Usage

Using AI tools and agentic workflows is **encouraged and expected**. We evaluate not only whether you used AI, but how deliberately and critically you used it.

Strong AI usage documentation explains:
- What tools, models, agents, or workflows you used
- How tasks were decomposed, including any multi-agent workflow
- `AI_USAGE.md`, `AGENTS.md`, `SKILLS.md`, prompt logs, or equivalent artifacts if used
- How AI or agents were used for QA, regression testing, code review, or documentation
- What outputs you corrected, rejected, or independently verified
- How you evaluated agent quality, reliability, and trustworthiness

Skilled use of AI is a positive signal when paired with critical validation, clear ownership, and good engineering judgment.

## Interview Follow-up

During the technical interview, expect questions such as:

- Walk us through your architecture and data normalization approach
- Why did you choose to implement some things and document others?
- What regression risks concern you most, and how would you catch them in CI/CD?
- How would you deploy, monitor, and operate this in production?
- What DX changes would most improve the next engineer's experience?
- What suggestions would you make to increase the effectiveness of the wider team?
- If you used AI or agents, how did you orchestrate, evaluate, and validate their output?
- How did you use AI or agents for QA or testing, and where did you decide not to trust them?

---

*We evaluate the whole picture - technical skills, product judgment, communication quality, AI collaboration, and the ability to improve team efficacy over time.*
