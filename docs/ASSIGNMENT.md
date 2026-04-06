# Take-Home Assignment: Vehicle Charging Session Aggregator

## Overview

Your task is to build a **Vehicle Charging Session Aggregator** that consolidates data from three different APIs into a unified interface. This mirrors real challenges at eMotion Fleet, where we integrate data from energy management systems, fleet management platforms, and utility providers.

The assignment tests your ability to:
- Design clean API contracts and application architecture
- Handle heterogeneous data sources with different formats and conventions
- Make pragmatic technical decisions and document your rationale
- Deliver working software within time constraints
- Show senior-level judgment about what to build now, what to document, and what to prioritize next

## Time Expectation

**4-8 hours** - This assignment is scoped for completion within a single working day.

You are encouraged to use AI tools (Copilot, Cursor, ChatGPT, Claude, etc.) to assist you. If you do, be prepared to document not only the tools you used, but also how you validated their output, how you structured your workflow, and how you used AI or agents for QA, testing, review, or iteration.

## Scenario

You are building a dashboard for fleet operators who manage electric vehicle charging at multiple depot facilities. They need to:

1. **Monitor facility status** - See real-time charger availability and power consumption across all facilities
2. **Review charging history** - Access historical charging session data for specific facilities

The challenge is that data comes from three separate systems, each with its own conventions:

| System | Data Provided | Quirks |
|--------|---------------|--------|
| **EMS API** (Energy Management System) | Facilities, chargers, charger status | UTC timestamps, kW units, UUID identifiers |
| **FMS API** (Fleet Management System) | Vehicles, charging sessions | JST timestamps, Wh units, prefixed string IDs |
| **Power Provider API** | Power consumption, tariff data | Unix timestamps, mixed units, numeric IDs |

Your job is to normalize and aggregate this data into a coherent experience.

## Deliverables

### Backend API

Build an API with **two endpoints**:

#### 1. Facility Status Endpoint

Returns aggregated status for all facilities, including:
- Facility information (name, location)
- Charger status summary (available, in-use, offline counts)
- Current power consumption

#### 2. Charging Session History Endpoint

Returns charging session history for a specific facility, including:
- Session details (vehicle, charger, duration, energy delivered)
- Support for basic filtering (e.g., by date range)

### Frontend Application

Build a web application with **two views**:

#### 1. Facility Status Dashboard

- Display all facilities with their current status
- Show charger availability breakdown per facility
- Show current power consumption per facility

#### 2. Charging Session History View

- Display charging sessions for a selected facility
- Show session details in a table format
- Include basic filtering capability

### Documentation

Your submission must include a **README** that documents:
- How to run your solution
- Your data normalization approach
- Key design decisions and trade-offs
- Your testing and regression strategy
- Your deployment and CI/CD approach
- Your monitoring, observability, and failsafe strategy
- Your performance and scaling considerations
- Your developer experience (DX) improvements or suggestions that would increase the efficacy of the wider team
- Anything you would do differently with more time

If you use AI tools or agents, include an `AI_USAGE.md` file or an equivalent README section that covers:
- Tools, models, and agents used
- Workflow notes, including any multi-agent approach
- `AGENTS.md`, `SKILLS.md`, prompt logs, or equivalent artifacts if you used them
- How AI or agents were used for QA, testing, code review, or documentation
- What you validated manually, corrected, or rejected

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
- We do expect you to document how you would test, deploy, monitor, scale, and improve the solution as a senior engineer

## Data Sources

The mock API data is provided in the `mock-apis/` directory:

- `mock-apis/ems-api/data.json` - Facilities and chargers
- `mock-apis/fms-api/data.json` - Vehicles and charging sessions
- `mock-apis/power-provider-api/data.json` - Power consumption and tariffs

See [`API_DOCUMENTATION.md`](API_DOCUMENTATION.md) for detailed specifications.

## What We're Looking For

### We DO evaluate:

- **API and interface design** - Are backend contracts and frontend flows clear, useful, and appropriately scoped?
- **Data handling** - How do you normalize inconsistent data?
- **Code organization** - Is your code readable, maintainable, and easy to extend?
- **Senior engineering judgment** - Do you show good thinking about testing, CI/CD, deployment, monitoring, resilience, and performance?
- **DX and team leverage** - Do you suggest improvements that would make the next engineer faster and increase the efficacy of the wider team?
- **Communication** - Can you explain decisions, trade-offs, and next steps clearly?

### What We Don't Expect You To Fully Implement Within The Timebox

- Complete production infrastructure or deployment automation, though your deployment and CI/CD strategy is evaluated
- Exhaustive automated test implementation, though your testing priorities and regression strategy are evaluated
- Brand-level visual design or marketing polish, though frontend-heavy candidates are evaluated on interface clarity, usability, and frontend execution quality
- Full scale hardening or benchmarking, though your performance assumptions and scaling strategy are evaluated
- Extra features beyond the core requirements unless they clearly strengthen the submission

## Optional Bonus

If you complete the core requirements with time to spare, consider:

- [ ] Role-appropriate automated tests or CI checks that cover meaningful risk beyond the happy path
- [ ] Monitoring, observability, or failure-handling mechanisms that make the system easier to trust
- [ ] Data freshness, synchronization, or refresh strategy where it meaningfully improves the solution
- [ ] Additional useful features that demonstrate product, operational, or system thinking

These are genuinely optional - a well-executed core submission without bonuses is preferred over a rushed submission that attempts everything.

## Submission

Submit by creating a **private repository** containing your solution. Grant access based on the role you completed:

- **Backend-heavy track** - `david.knapik@emotion-fleet.com` and `ivan.ordonez@emotion-fleet.com`
- **Frontend-heavy track** - `david.knapik@emotion-fleet.com` and `ihsan.engku@emotion-fleet.com`

Ensure your submission includes:

- [ ] All source code
- [ ] README with setup instructions, decision documentation, and senior-level strategy notes
- [ ] `AI_USAGE.md` or equivalent AI workflow documentation if AI tools or agents were used
- [ ] Any configuration needed to run locally

## Questions?

If anything is unclear, please reach out to `david.knapik@emotion-fleet.com`. Asking good questions is a positive signal.

---

Good luck! We look forward to reviewing your solution.
