# Take-Home Assignment: Vehicle Charging Session Aggregator

## Overview

Your task is to build a **Vehicle Charging Session Aggregator** that consolidates data from three different APIs into a unified interface. This mirrors real challenges at eMotion Fleet, where we integrate data from energy management systems, fleet management platforms, and utility providers.

The assignment tests your ability to:
- Design clean API contracts and application architecture
- Handle heterogeneous data sources with different formats and conventions
- Make pragmatic technical decisions and document your rationale
- Deliver working software within time constraints

## Time Expectation

**4-8 hours** — This assignment is scoped for completion within a single working day.

You are encouraged to use AI tools (Copilot, Cursor, ChatGPT, Claude, etc.) to assist you. If you do, be prepared to discuss your process during the technical interview — including the prompts you used, how you iterated, and what you learned.

## Scenario

You are building a dashboard for fleet operators who manage electric vehicle charging at multiple depot facilities. They need to:

1. **Monitor facility status** — See real-time charger availability and power consumption across all facilities
2. **Review charging history** — Access historical charging session data for specific facilities

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
- Anything you would do differently with more time

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
- You may load the JSON files directly — no need to build actual mock servers
- No database required — in-memory data handling is acceptable
- No deployment required — local execution is sufficient

## Data Sources

The mock API data is provided in the `mock-apis/` directory:

- `mock-apis/ems-api/data.json` — Facilities and chargers
- `mock-apis/fms-api/data.json` — Vehicles and charging sessions
- `mock-apis/power-provider-api/data.json` — Power consumption and tariffs

See [`API_DOCUMENTATION.md`](API_DOCUMENTATION.md) for detailed specifications.

## What We're Looking For

### We DO evaluate:

- **API design** — Are your endpoints well-structured and intuitive?
- **Data handling** — How do you normalize inconsistent data?
- **Code organization** — Is your code readable and maintainable?
- **Decision-making** — Can you explain your technical choices?
- **Problem-solving** — How do you handle edge cases and ambiguity?

### We DON'T evaluate:

- Visual design or CSS polish
- Exhaustive test coverage
- Production-ready deployment
- Performance optimization for scale

## Optional Bonus

If you complete the core requirements with time to spare, consider:

- [ ] Unit tests for critical data transformation logic
- [ ] Error states and loading indicators in the UI
- [ ] Additional filtering or sorting capabilities
- [ ] Data refresh or polling mechanism

These are genuinely optional — a well-executed core submission without bonuses is preferred over a rushed submission that attempts everything.

## Submission

Submit your solution as instructed by your recruiter. Ensure your submission includes:

- [ ] All source code
- [ ] README with setup instructions and decision documentation
- [ ] Any configuration needed to run locally

## Questions?

If anything is unclear, please reach out to your recruiting contact. We're happy to clarify requirements — asking good questions is a positive signal.

---

Good luck! We look forward to reviewing your solution.
