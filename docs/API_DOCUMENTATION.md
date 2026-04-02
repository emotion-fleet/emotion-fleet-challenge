# Mock API Documentation

This document describes the three mock APIs that serve as data sources for the assignment. Each API has intentionally different conventions to simulate real-world integration challenges.

## Data Files Location

```
mock-apis/
├── ems-api/
│   └── data.json          # Energy Management System
├── fms-api/
│   └── data.json          # Fleet Management System
└── power-provider-api/
    └── data.json          # Electric Power Provider
```

Load these JSON files directly in your application — no need to run mock servers.

---

## EMS API (Energy Management System)

**File:** `mock-apis/ems-api/data.json`

The EMS manages charging infrastructure at depot facilities.

### Conventions

| Aspect | Convention |
|--------|------------|
| **Timestamps** | ISO 8601, UTC timezone (e.g., `"2026-04-01T08:00:00Z"`) |
| **Power units** | Kilowatts (kW) |
| **Energy units** | Kilowatt-hours (kWh) |
| **Identifiers** | UUID format (e.g., `"f47ac10b-58cc-4372-a567-0e02b2c3d479"`) |
| **Naming** | snake_case |

### Data Structure

```json
{
  "api_version": "1.0",
  "generated_at": "2026-04-01T09:00:00Z",
  "facilities": [
    {
      "facility_id": "uuid",
      "name": "string",
      "location": {
        "address": "string",
        "latitude": "number",
        "longitude": "number"
      },
      "total_capacity_kw": "number",
      "chargers": [
        {
          "charger_id": "uuid",
          "model": "string",
          "max_power_kw": "number",
          "status": "AVAILABLE | IN_USE | OFFLINE | MAINTENANCE",
          "current_power_kw": "number | null",
          "last_status_update": "ISO 8601 UTC timestamp"
        }
      ]
    }
  ]
}
```

### Charger Status Values

| Status | Description |
|--------|-------------|
| `AVAILABLE` | Charger is ready for use |
| `IN_USE` | Charger is actively charging a vehicle |
| `OFFLINE` | Charger is not communicating |
| `MAINTENANCE` | Charger is under maintenance |

---

## FMS API (Fleet Management System)

**File:** `mock-apis/fms-api/data.json`

The FMS tracks vehicles and their charging sessions.

### Conventions

| Aspect | Convention |
|--------|------------|
| **Timestamps** | String format with JST timezone (e.g., `"2026-04-01 17:00:00 JST"`) |
| **Energy units** | Watt-hours (Wh) |
| **Identifiers** | Prefixed strings (e.g., `"VH-001"`, `"CS-20260401-001"`) |
| **Naming** | camelCase |

### Data Structure

```json
{
  "apiVersion": "2.1",
  "generatedAt": "2026-04-01 18:00:00 JST",
  "vehicles": [
    {
      "vehicleId": "string (VH-XXX format)",
      "licensePlate": "string",
      "model": "string",
      "batteryCapacityWh": "number",
      "currentBatteryPercent": "number | null",
      "status": "available | charging | in_transit | offline"
    }
  ],
  "chargingSessions": [
    {
      "sessionId": "string (CS-YYYYMMDD-XXX format)",
      "vehicleId": "string (VH-XXX format)",
      "chargerIdentifier": "string",
      "facilityRef": "string",
      "startTime": "JST timestamp string",
      "endTime": "JST timestamp string | null",
      "energyDeliveredWh": "number",
      "maxPowerW": "number",
      "status": "completed | in_progress | failed | interrupted"
    }
  ]
}
```

### Notes

- `endTime` is `null` for sessions that are currently in progress
- `chargerIdentifier` uses a different format than EMS charger IDs — you'll need to map these
- `facilityRef` uses yet another identifier format for facilities

### Vehicle Status Values

| Status | Description |
|--------|-------------|
| `available` | Vehicle is at depot, not charging |
| `charging` | Vehicle is currently charging |
| `in_transit` | Vehicle is on a route |
| `offline` | Vehicle is not reporting |

### Session Status Values

| Status | Description |
|--------|-------------|
| `completed` | Session finished normally |
| `in_progress` | Session is ongoing |
| `failed` | Session encountered an error |
| `interrupted` | Session was stopped early |

---

## Power Provider API

**File:** `mock-apis/power-provider-api/data.json`

The power provider supplies electricity consumption and tariff data.

### Conventions

| Aspect | Convention |
|--------|------------|
| **Timestamps** | Unix timestamp in seconds (e.g., `1711958400`) |
| **Power units** | Kilowatts (kW) |
| **Energy units** | Kilowatt-hours (kWh) |
| **Identifiers** | Numeric IDs and facility reference codes |
| **Naming** | camelCase |

### Data Structure

```json
{
  "version": "3.0",
  "exportTimestamp": 1711962000,
  "consumptionRecords": [
    {
      "recordId": "number",
      "facilityCode": "string (DEPOT-XXX-X format)",
      "timestampUnix": "number (Unix seconds)",
      "periodMinutes": "number",
      "powerKw": "number",
      "energyKwh": "number",
      "tariffCategory": "peak | standard | off_peak"
    }
  ],
  "tariffs": [
    {
      "tariffId": "number",
      "category": "peak | standard | off_peak",
      "pricePerKwh": "number (JPY)",
      "validFrom": "number (Unix timestamp)",
      "validTo": "number (Unix timestamp) | null"
    }
  ],
  "facilityMappings": [
    {
      "facilityCode": "string",
      "contractId": "string",
      "maxContractedPowerKw": "number"
    }
  ]
}
```

### Tariff Categories

| Category | Typical Hours (JST) | Description |
|----------|---------------------|-------------|
| `peak` | 13:00-16:00 | Highest rates |
| `standard` | 08:00-13:00, 16:00-22:00 | Normal rates |
| `off_peak` | 22:00-08:00 | Lowest rates |

---

## Cross-Reference Mapping

The three APIs use different identifiers for the same entities. Here's how they relate:

### Facility Identifiers

| EMS API | FMS API | Power Provider |
|---------|---------|----------------|
| `facility_id` (UUID) | `facilityRef` (string) | `facilityCode` (string) |

The mapping is provided in each data file. For example:
- EMS: `"f47ac10b-58cc-4372-a567-0e02b2c3d479"`
- FMS: `"FACILITY-TKY-ALPHA"`
- Power: `"DEPOT-TKY-A"`

### Charger Identifiers

| EMS API | FMS API |
|---------|---------|
| `charger_id` (UUID) | `chargerIdentifier` (string) |

Example mapping:
- EMS: `"c1a2b3c4-d5e6-4f7a-8b9c-0d1e2f3a4b5c"`
- FMS: `"CHG-TKY-01"`

---

## Data Challenges Summary

Your solution needs to handle these inconsistencies:

| Challenge | Details |
|-----------|---------|
| **Timezone normalization** | Convert JST strings and Unix timestamps to a consistent format |
| **Unit conversion** | Handle kW/W and kWh/Wh differences |
| **ID mapping** | Join data across different identifier formats |
| **Null handling** | Handle missing `endTime`, `currentBatteryPercent`, etc. |
| **Status normalization** | Unify different status naming conventions |
| **Case conventions** | Handle snake_case vs camelCase field names |

---

## Example: Joining Data

To display a facility's status with current power consumption, you would need to:

1. Load facility from EMS API (get `facility_id`)
2. Find matching `facilityRef` in FMS API sessions
3. Find matching `facilityCode` in Power Provider consumption records
4. Normalize all timestamps to a common format
5. Aggregate charger statuses from EMS
6. Sum energy delivered from FMS sessions (converting Wh to kWh)
7. Get current power reading from Power Provider

This is the core challenge of the assignment.
