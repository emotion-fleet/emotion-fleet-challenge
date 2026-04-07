# Mock API Documentation

This document describes the mock APIs that serve as data sources for the assignment.

The **required core** of the exercise uses:
- EMS API
- FMS API

An optional **Power Provider API** is also included if you want extra depth after completing the core requirements.

## Data Files Location

```
mock-apis/
├── ems-api/
│   └── data.json          # Required: Energy Management System
├── fms-api/
│   └── data.json          # Required: Fleet Management System
└── power-provider-api/
    └── data.json          # Optional bonus: Electric Power Provider
```

Load these JSON files directly in your application - no need to run mock servers.

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
      "external_refs": {
        "fms_facility_ref": "string",
        "power_provider_code": "string"
      },
      "chargers": [
        {
          "charger_id": "uuid",
          "external_ref": "string",
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

- `chargerIdentifier` uses a different format than EMS charger IDs - you will need to map these
- `facilityRef` uses a different identifier format for facilities
- In this mock data, `status` is the source of truth for session state. Do not rely on `endTime == null` alone to mean "in progress"

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

## Optional Bonus API: Power Provider

**File:** `mock-apis/power-provider-api/data.json`

The power provider supplies electricity consumption and tariff data. This data set is **optional** and can be used if you want to extend the facility status view beyond charger-side load.

### Conventions

| Aspect | Convention |
|--------|------------|
| **Timestamps** | Unix timestamp in seconds |
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

---

## Cross-Reference Mapping

### Required Core Mapping

The core assignment requires joining EMS and FMS records.

#### Facility Identifiers

| EMS API | FMS API |
|---------|---------|
| `facility_id` (UUID) | `facilityRef` (string) |

The EMS data includes an `external_refs.fms_facility_ref` field to help with this mapping.

#### Charger Identifiers

| EMS API | FMS API |
|---------|---------|
| `charger_id` (UUID) | `chargerIdentifier` (string) |

The EMS data includes an `external_ref` field on each charger to help with this mapping.

### Optional Bonus Mapping

If you use the Power Provider API, you will also need to map EMS facilities to utility `facilityCode` values via `external_refs.power_provider_code`.

---

## Data Challenges Summary

### Required Core Challenges

| Challenge | Details |
|-----------|---------|
| **Timezone normalization** | Convert UTC and JST timestamps to a consistent format |
| **Unit conversion** | Handle kW/W and kWh/Wh differences |
| **ID mapping** | Join EMS and FMS data across different identifier formats |
| **Null handling** | Handle missing `endTime`, `currentBatteryPercent`, and similar fields |
| **Status normalization** | Interpret and present status values consistently |
| **Case conventions** | Handle snake_case vs camelCase field names |

### Optional Bonus Challenges

| Challenge | Details |
|-----------|---------|
| **Unix timestamps** | Normalize Power Provider timestamps if you use that API |
| **Third-system mapping** | Join utility `facilityCode` values to EMS facilities |
| **Utility-side power data** | Distinguish charger-side load from utility-side consumption if you choose to surface both |

---

## Example: Core Join

To display a facility's status and charging history using the required APIs, you would typically:

1. Load facilities and chargers from EMS
2. Map EMS facility and charger references to FMS `facilityRef` and `chargerIdentifier`
3. Normalize UTC and JST timestamps to a common format
4. Aggregate charger statuses from EMS
5. Sum `current_power_kw` values from EMS chargers to derive current charging load
6. Join FMS charging sessions and vehicles to build facility history

If you use the optional Power Provider API, you can extend this by joining facility codes and adding utility-side consumption data.
