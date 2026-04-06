# FEMS Vehicle Charging Session Aggregator Challenge

## Purpose

This repository contains the take-home assignment for engineering candidates at eMotion Fleet. The challenge evaluates candidates' ability to design and build a data aggregation solution that consolidates information from multiple heterogeneous APIs — a common challenge in the Fleet and Energy Management System (FEMS) domain.

## What This Assignment Evaluates

- **Problem-solving**: Handling real-world data inconsistencies across multiple sources
- **Design decisions**: API architecture, data modeling, and component structure
- **Core concept understanding**: RESTful patterns, relational thinking, frontend architecture
- **Communication**: Documenting decisions and rationale clearly
- **Pragmatic engineering**: Delivering working software within time constraints

## Repository Structure

```
emotion-fleet-challenge/
├── README.md                      # This file
├── docs/
│   ├── ASSIGNMENT.md              # Main assignment instructions
│   ├── EVALUATION_CRITERIA.md     # How submissions are evaluated
│   └── API_DOCUMENTATION.md       # Mock API specifications
└── mock-apis/
    ├── ems-api/
    │   └── data.json              # Energy Management System data
    ├── fms-api/
    │   └── data.json              # Fleet Management System data
    └── power-provider-api/
        └── data.json              # Electric power provider data
```

## Getting Started

Candidates should begin by reading:

1. [`docs/ASSIGNMENT.md`](docs/ASSIGNMENT.md) — Assignment overview and requirements
2. [`docs/API_DOCUMENTATION.md`](docs/API_DOCUMENTATION.md) — Mock API specifications
3. [`docs/EVALUATION_CRITERIA.md`](docs/EVALUATION_CRITERIA.md) — Evaluation rubric

## Time Expectation

Candidates should still be asked to **timebox themselves to roughly 4-8 hours**, but the assignment as currently written will often take longer than that if a senior candidate fully implements both user journeys, adds role-appropriate tests, and writes the requested strategy documentation.

### Internal Calibration

| Track | With AI assistance | Without AI assistance | Longest parts |
|-------|--------------------|-----------------------|---------------|
| **Backend-heavy candidate** | ~6-10 hours | ~8-14 hours | Data normalization and identifier mapping, endpoint design, backend tests, plus a minimal UI or demo surface |
| **Frontend-heavy candidate** | ~8-12 hours | ~10-16 hours | App scaffolding, dashboard and history UI, API integration, state/filtering, plus the required strategy write-up |

In practice, the work that stretches the timebox is the combination of:

- Normalizing three data sources with different timestamps, units, identifiers, and status vocabularies
- Building both the primary track deliverable and a non-trivial opposite-stack surface area
- Writing the senior-level README and AI-usage documentation to a high standard

### If We Want This To Stay A True 4-8 Hour Exercise

The smallest cuts that still preserve evaluation quality are:

1. **Keep one core journey fully implemented and let the second be thinner.**
   For frontend candidates, prioritize a strong facility dashboard and allow a simpler history view. For backend candidates, prioritize strong aggregation contracts and allow a very thin frontend.
2. **Make tariff details explicitly non-core.**
   Current power consumption is useful, but tariff modeling adds little signal for the stated exercise.
3. **Reduce the required written strategy depth.**
   Keep testing, CI/CD, and monitoring as required topics, but make scaling and DX notes intentionally brief.
4. **Prefer depth over breadth in evaluation.**
   A well-prioritized submission with clear trade-offs is a better signal than a rushed attempt to implement every possible edge case.

## About eMotion Fleet

eMotion Fleet is a Tokyo-based startup building the infrastructure for commercial EV adoption across Japan and Asia. Our Fleet and Energy Management System (FEMS) integrates EV charging, telematics, and depot electrification to help logistics and transit operators decarbonize, cut operating costs, and maximize fleet uptime.

---

*For internal use: This assignment is maintained by the eMotion Fleet engineering team.*
