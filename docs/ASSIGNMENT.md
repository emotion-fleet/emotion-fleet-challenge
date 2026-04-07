# Take-Home Assignment: Vehicle Charging Session Aggregator

## Overview

Your task is to build a **Vehicle Charging Session Aggregator** that consolidates data from two different APIs into a unified interface. This mirrors real challenges at eMotion Fleet, where we integrate data across systems with different conventions and constraints.

The assignment tests your ability to:
- Design clean API contracts and application architecture
- Handle heterogeneous data sources with different formats and conventions
- Make pragmatic technical decisions and document your rationale
- Deliver working software within time constraints
- Show senior-level judgment about what to build now, what to leave optional, and what to prioritize next

## Time Expectation

**4-8 hours** - This assignment is scoped for completion within a single working day.

You are welcome to use AI tools (Copilot, Cursor, ChatGPT, Claude, etc.) while working on the assignment. We may ask about your workflow, validation process, and how you used AI during the interview. If you want to share an `AI_USAGE.md` note, you may, but it is optional.

## Scenario

You are building a dashboard for fleet operators who manage electric vehicle charging at multiple depot facilities. They need to:

1. **Monitor facility status** - See current charger availability and charging load across facilities
2. **Review charging history** - Access historical charging session data for specific facilities

The core challenge comes from two required systems with different conventions:

| System | Data Provided | Quirks |
|--------|---------------|--------|
| **EMS API** (Energy Management System) | Facilities, chargers, charger status | UTC timestamps, kW units, UUID identifiers |
| **FMS API** (Fleet Management System) | Vehicles, charging sessions | JST timestamps, Wh units, prefixed string IDs |

An optional **Power Provider API** is also included in the repository if you want to extend the exercise further, but it is not required for the core solution.

## Deliverables

### Backend API

Build an API with **two endpoints**:

#### 1. Facility Status Endpoint

Returns aggregated status for all facilities, including:
- Facility information (name, location)
- Charger status summary (available, in-use, offline counts)
- Current charging load

#### 2. Charging Session History Endpoint

Returns charging session history for a specific facility, including:
- Session details (vehicle, charger, duration, energy delivered)
- Date-range filtering is optional if you have extra time

### Frontend Application

Build a web application with **two views**:

#### 1. Facility Status Dashboard

- Display all facilities with their current status
- Show charger availability breakdown per facility
- Show current charging load per facility

#### 2. Charging Session History View

- Display charging sessions for a selected facility
- Show session details in a table format
- Filtering is optional if you have extra time

### Documentation

Your submission must include a **README** that documents:
- How to run your solution
- Your data normalization approach
- Your testing and regression strategy
- Your delivery strategy (CI/CD and deployment)
- What you would do with more time

If you use AI tools or agents and want to share more context, an `AI_USAGE.md` file or equivalent README note is welcome but optional.

## Technical Requirements

### For Backend Candidates

| Requirement | Specification |
|-------------|---------------|
| **API Framework** | Python with FastAPI (required) |
| **Frontend** | Any framework of your choice (or minimal HTML/JS) |

### For Frontend Candidates

| Requirement | Specification |
|-------------|---------------|
| **Frontend Framework** | React with Next.js (required) |
| **API Layer** | Any language/framework of your choice |

### For All Candidates

- Use the provided mock API data files as your data source
- You may load the JSON files directly - no need to build actual mock servers
- No database required - in-memory data handling is acceptable
- No deployment is required for the submission itself - local execution is sufficient
- The required core uses the EMS and FMS data sets
- The Power Provider API is available as an optional extension if you want extra depth

## Data Sources

The mock API data is provided in the `mock-apis/` directory:

### Required

- `mock-apis/ems-api/data.json` - Facilities and chargers
- `mock-apis/fms-api/data.json` - Vehicles and charging sessions

### Optional Bonus

- `mock-apis/power-provider-api/data.json` - Utility-side power consumption and tariff data

See [`API_DOCUMENTATION.md`](API_DOCUMENTATION.md) for detailed specifications.

## What We're Looking For

### We DO evaluate:

- **API and interface design** - Are backend contracts and frontend flows clear, useful, and appropriately scoped?
- **Data handling** - How do you normalize inconsistent data?
- **Code organization** - Is your code readable, maintainable, and easy to extend?
- **Quality ownership** - Do you write role-appropriate tests and show clear regression awareness?
- **Delivery judgment** - Do you show practical thinking about CI/CD and deployment?
- **Communication** - Can you explain decisions, trade-offs, and next steps clearly?

### Additional Senior Signals We May Explore In The Interview

- Monitoring, observability, and failsafe thinking
- Performance and scaling considerations
- Developer experience (DX) and team leverage
- How you used AI tools, agents, validation, and QA workflows

### What We Don't Expect You To Fully Implement Within The Timebox

- Complete production infrastructure or deployment automation
- Brand-level visual design or marketing polish, though frontend-heavy candidates are still evaluated on interface clarity and usability
- Full scale hardening or benchmarking
- Extra features beyond the core requirements unless they clearly strengthen the submission

## Optional Bonus

If you complete the core requirements with time to spare, consider:

- [ ] Integrating the optional Power Provider API into facility status
- [ ] Adding date-range filtering to the session history endpoint or UI
- [ ] Adding observability, failure-handling, or operational safeguards
- [ ] Adding useful product features that clearly strengthen the submission

These are genuinely optional - a well-executed core submission without bonuses is preferred over a rushed submission that attempts everything.

## Submission

Submit by creating a repository containing your solution and follow the submission channel instructions provided with this assignment.

Ensure your submission includes:

- [ ] All source code
- [ ] README with setup instructions and decision documentation
- [ ] Any configuration needed to run locally

## Questions?

If anything is unclear, please contact us.

---

Good luck! We look forward to reviewing your solution.
