# Data Hierarchy Standard

**Status:** Draft
**Version:** 0.1.0
**Working Group:** Data Hierarchy WG

---

## Overview

A standard hierarchical structure for organizing water utility data, adapted from ISA-95 for water industry needs.

## The Problem

Utilities organize data differently:
- Some use: `Facility > Equipment > Point`
- Others use: `Site > System > Asset > Tag`
- Others use: `Plant > Area > Unit > Device`

Software vendors can't build tools that work everywhere because every deployment requires custom hierarchy mapping.

## The Standard

### Hierarchy Levels

```
Enterprise
  └── Site
        └── Area
              └── Process Cell
                    └── Unit
                          └── Equipment Module
```

### Level Definitions

| Level | Description | Water Utility Example |
|-------|-------------|----------------------|
| **Enterprise** | The entire organization | Metro Water District |
| **Site** | A physical location/facility | North Treatment Plant |
| **Area** | A functional area within a site | Raw Water Pumping |
| **Process Cell** | A group of related units | High Service Pump Station |
| **Unit** | A single piece of equipment | Pump-01 |
| **Equipment Module** | Component of a unit | VFD-Pump-01 |

### Full Example

```
Metro Water District (Enterprise)
├── North Treatment Plant (Site)
│   ├── Raw Water Intake (Area)
│   │   └── Intake Screens (Process Cell)
│   │       ├── Screen-01 (Unit)
│   │       └── Screen-02 (Unit)
│   ├── Raw Water Pumping (Area)
│   │   └── Low Lift Pumps (Process Cell)
│   │       ├── Pump-01 (Unit)
│   │       │   ├── VFD-01 (Equipment Module)
│   │       │   └── Motor-01 (Equipment Module)
│   │       └── Pump-02 (Unit)
│   ├── Treatment (Area)
│   │   ├── Coagulation (Process Cell)
│   │   ├── Flocculation (Process Cell)
│   │   ├── Sedimentation (Process Cell)
│   │   └── Filtration (Process Cell)
│   └── Disinfection (Area)
│       └── Chlorination (Process Cell)
│           ├── ChlorineAnalyzer-01 (Unit)
│           └── ChlorinePump-01 (Unit)
└── South Distribution Center (Site)
    └── High Service Pumping (Area)
        └── Distribution Pumps (Process Cell)
            ├── Pump-01 (Unit)
            └── Pump-02 (Unit)
```

## Mapping to Systems

### SCADA/Historian Tag Structure

```
{Enterprise}.{Site}.{Area}.{ProcessCell}.{Unit}.{EquipmentModule}.{Point}

Example:
MetroWD.NorthWTP.RawWaterPumping.LowLiftPumps.Pump01.VFD01.Speed
MetroWD.NorthWTP.RawWaterPumping.LowLiftPumps.Pump01.VFD01.Current
MetroWD.NorthWTP.RawWaterPumping.LowLiftPumps.Pump01.Status
```

### GIS Feature Classes

| Hierarchy Level | GIS Representation |
|-----------------|-------------------|
| Enterprise | Organization boundary |
| Site | Facility polygon |
| Area | Functional zone |
| Unit | Point feature (equipment location) |

### CMMS Asset Hierarchy

The CMMS asset tree should mirror this hierarchy directly, enabling:
- Roll-up of maintenance costs by area/site
- Consistent work order routing
- Standardized reporting

## Water-Specific Adaptations

### Distribution System Extensions

For distribution networks, add:

| Level | Description | Example |
|-------|-------------|---------|
| **Pressure Zone** | Hydraulic zone | Zone-A (150-180 PSI) |
| **District** | Metered district | DMA-North-01 |

### Collection System Extensions

For wastewater, add:

| Level | Description | Example |
|-------|-------------|---------|
| **Sewershed** | Drainage area | Sewershed-Central |
| **Trunk** | Major conveyance | Main-Interceptor-01 |

## Implementation Guide

### Step 1: Map Existing Structure

Document your current hierarchy and map to the standard:

| Your Term | Standard Term |
|-----------|---------------|
| Plant | Site |
| Building | Area |
| System | Process Cell |
| Equipment | Unit |

### Step 2: Identify Gaps

- Missing levels? Add them.
- Extra levels? Map to closest standard level.
- Inconsistent naming? Standardize.

### Step 3: Implement Gradually

1. New projects use standard hierarchy
2. Existing systems maintain current structure
3. Add mapping layer for integration
4. Migrate during system upgrades

## Rationale

### Why ISA-95?

- **Proven**: Used in manufacturing for decades
- **Comprehensive**: Covers enterprise to device
- **Standardized**: International recognition
- **Tool support**: Many systems already support it

### Water-Specific Modifications

ISA-95 was designed for manufacturing. We adapted it by:
- Adding distribution/collection extensions
- Simplifying terminology for water context
- Providing water-specific examples

## Open Questions

- [ ] How to handle shared infrastructure between sites?
- [ ] Treatment of mobile assets (vehicles, portable equipment)?
- [ ] Integration with hydraulic model segmentation?

## References

- ISA-95.00.01: Enterprise-Control System Integration Part 1: Models and Terminology
- ISA-88: Batch Control
- IEC 62264: Enterprise-control system integration

---

**Feedback?** Open an [issue](../../../../issues) or join the [discussion](../../../../discussions).
