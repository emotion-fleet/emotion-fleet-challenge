# FEMS Vehicle Charging Session Aggregator Challenge

## Purpose

This repository contains the take-home assignment for engineering candidates at eMotion Fleet. The challenge evaluates candidates' ability to design and build a data aggregation solution that consolidates information from multiple heterogeneous APIs - a common challenge in the Fleet and Energy Management System (FEMS) domain.

The core exercise uses two required data sources:
- EMS API
- FMS API

An optional Power Provider API is also included if candidates want extra depth after completing the core solution.

## What This Assignment Evaluates

- **Problem-solving**: Handling real-world data inconsistencies across multiple sources
- **Design decisions**: API architecture, data modeling, and component structure
- **Core concept understanding**: RESTful patterns, relational thinking, and frontend architecture
- **Communication**: Explaining decisions, trade-offs, and next steps clearly
- **Pragmatic engineering**: Delivering strong signal within a constrained timebox

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
    │   └── data.json              # Required: Energy Management System data
    ├── fms-api/
    │   └── data.json              # Required: Fleet Management System data
    └── power-provider-api/
        └── data.json              # Optional bonus: Electric power provider data
```

## Getting Started

Candidates should begin by reading:

1. [`docs/ASSIGNMENT.md`](docs/ASSIGNMENT.md) - Assignment overview and requirements
2. [`docs/API_DOCUMENTATION.md`](docs/API_DOCUMENTATION.md) - Mock API specifications
3. [`docs/EVALUATION_CRITERIA.md`](docs/EVALUATION_CRITERIA.md) - Evaluation rubric

## Time Expectation

This assignment is designed to be completed in **4-8 hours**. AI tools are allowed, and candidates may be asked about how they used them during the technical interview.

## About eMotion Fleet

eMotion Fleet is a Tokyo-based startup building the infrastructure for commercial EV adoption across Japan and Asia. Our Fleet and Energy Management System (FEMS) integrates EV charging, telematics, and depot electrification to help logistics and transit operators decarbonize, cut operating costs, and maximize fleet uptime.

---

*For internal use: This assignment is maintained by the eMotion Fleet engineering team.*
