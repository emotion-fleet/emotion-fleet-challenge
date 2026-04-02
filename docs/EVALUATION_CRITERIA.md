# Evaluation Criteria

This document outlines how submissions are evaluated. Understanding these criteria will help you prioritize your efforts during the assignment.

## Evaluation Philosophy

We evaluate candidates on their **ability to think through problems and make sound technical decisions**, not just their ability to produce working code. A submission with fewer features but clear reasoning and clean implementation is valued over a feature-complete submission with unclear structure.

## Core Evaluation Areas

### 1. API and Component Design (30%)

| Aspect | What We Look For |
|--------|------------------|
| **Endpoint structure** | RESTful conventions, intuitive resource naming, appropriate HTTP methods |
| **Response design** | Consistent response shapes, appropriate data granularity, useful error responses |
| **Component architecture** | Logical component breakdown, separation of concerns, reusability where appropriate |
| **Data flow** | Clear data fetching patterns, appropriate state management |

**Questions we ask ourselves:**
- Would another developer understand this API without extensive documentation?
- Are components focused on single responsibilities?
- Is the data flow predictable and traceable?

### 2. Data Normalization Approach (25%)

| Aspect | What We Look For |
|--------|------------------|
| **Consistency** | Unified formats for timestamps, units, and identifiers across all data sources |
| **Correctness** | Accurate timezone conversions, unit transformations, ID mappings |
| **Edge cases** | Handling of missing data, null values, and ongoing sessions |
| **Documentation** | Clear explanation of normalization strategy in README |

**Questions we ask ourselves:**
- Did the candidate identify the data inconsistencies?
- Is the normalization logic centralized and testable?
- Are edge cases handled gracefully?

### 3. Code Organization and Quality (25%)

| Aspect | What We Look For |
|--------|------------------|
| **Structure** | Logical file organization, clear module boundaries |
| **Readability** | Meaningful names, appropriate comments, consistent style |
| **Maintainability** | Code that would be easy to modify or extend |
| **Type safety** | Appropriate use of types (TypeScript for FE, type hints for Python) |

**Questions we ask ourselves:**
- Could a new team member navigate this codebase quickly?
- Is there unnecessary complexity?
- Are there obvious code smells or anti-patterns?

### 4. Decision Documentation (20%)

| Aspect | What We Look For |
|--------|------------------|
| **Clarity** | Well-written README that explains the solution |
| **Rationale** | Explanation of key decisions and trade-offs |
| **Self-awareness** | Acknowledgment of limitations and potential improvements |
| **Communication** | Clear, concise, professional writing |

**Questions we ask ourselves:**
- Can we understand the candidate's thought process?
- Do they show awareness of trade-offs?
- Would they communicate well asynchronously?

## Evaluation Tiers

### ✅ Strong Submission

- Both endpoints work correctly with normalized data
- Both UI views display data appropriately
- README clearly explains approach and decisions
- Code is well-organized and readable
- Data inconsistencies are handled thoughtfully

### ⚠️ Acceptable Submission

- Core functionality works with minor issues
- Some data normalization gaps
- README present but lacks depth
- Code is functional but could be better organized

### ❌ Weak Submission

- Core functionality incomplete or broken
- Data inconsistencies not addressed
- Missing or minimal documentation
- Code is difficult to follow or poorly organized

## What We're NOT Evaluating

To be explicit about what won't affect your score:

| Not Evaluated | Why |
|---------------|-----|
| **Visual design** | We don't expect you to be a designer |
| **CSS polish** | Basic styling is fine |
| **Exhaustive tests** | Time constraints are understood |
| **Deployment** | Local execution is sufficient |
| **Performance optimization** | We're not testing at scale |
| **Feature completeness beyond requirements** | Focus on core requirements first |

## Bonus Consideration

Optional bonus items can strengthen a submission but **only if core requirements are solid**. A submission with excellent core execution and no bonuses will score higher than one with rushed core execution and attempted bonuses.

Bonus items that positively impact evaluation:
- Unit tests for data transformation logic
- Thoughtful error handling in the UI
- Additional useful features that demonstrate product thinking

## AI Tool Usage

Using AI tools is **encouraged and expected**. We will ask about your AI usage during the technical interview:

- What tools did you use?
- What prompts worked well?
- What did you have to correct or iterate on?
- What did you learn or verify through AI assistance?

Skilled use of AI tools is a positive signal. The ability to direct AI effectively and critically evaluate its output is valuable.

## Interview Follow-up

During the technical interview, expect questions such as:

- Walk us through your data normalization approach
- Why did you structure your API this way?
- What would you change with more time?
- How did you handle [specific edge case]?
- If you used AI, how did you validate its suggestions?

---

*We evaluate the whole picture — technical skills, problem-solving approach, communication quality, and decision-making process.*
