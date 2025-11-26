# Asset Naming Convention

**Status:** Draft
**Version:** 0.1.0
**Working Group:** Asset Naming WG

---

## Overview

A unified naming convention for water utility assets that works across GIS, CMMS, SCADA, historians, and other systems.

## The Problem

Every utility names assets differently:
- GIS: `Pump_001`
- CMMS: `P-WTP-01`
- SCADA: `MainSt_Pump_1`
- Historian: `Site1.Area2.PMP001`

Integrating systems requires expensive custom mapping for every project.

## The Standard

### Naming Schema

```
{Utility}.{Site}.{System}.{AssetType}-{Sequence}
```

### Components

| Component | Description | Example |
|-----------|-------------|---------|
| Utility | Organization identifier | `CityWater`, `MetroWD` |
| Site | Physical location/facility | `NorthWTP`, `MainPS` |
| System | Process system | `RawWaterPumping`, `Disinfection` |
| AssetType | Equipment category | `Pump`, `Valve`, `Tank` |
| Sequence | Unique identifier | `01`, `02`, `A1` |

### Examples

```
CityWater.NorthWTP.RawWaterPumping.Pump-01
CityWater.NorthWTP.RawWaterPumping.Pump-02
CityWater.NorthWTP.Disinfection.ChlorineAnalyzer-01
CityWater.MainPS.HighService.Pump-01
CityWater.MainPS.HighService.VFD-01
```

### Standard Asset Types

| Type Code | Description |
|-----------|-------------|
| `Pump` | Centrifugal, submersible, etc. |
| `Valve` | Gate, butterfly, check, etc. |
| `Tank` | Storage tanks, reservoirs |
| `Meter` | Flow meters, level sensors |
| `Analyzer` | Water quality instruments |
| `VFD` | Variable frequency drives |
| `Motor` | Electric motors |
| `Blower` | Aeration blowers |

## Implementation Notes

### Transitioning from Existing Names

1. Create a mapping table from legacy names to standard names
2. Implement as an alias layer - don't rename in source systems immediately
3. Use standard names for all new assets
4. Migrate gradually as systems are upgraded

### System-Specific Considerations

**GIS**
- Store standard name in a dedicated field
- Maintain legacy name for historical reference

**SCADA**
- Tag naming may have character limits - use abbreviations consistently
- Document abbreviation mappings

**CMMS**
- Asset hierarchy should match naming hierarchy
- Work order references should use standard names

## Rationale

### Why This Format?

- **Hierarchical**: Reflects physical organization
- **Human-readable**: Operators can understand at a glance
- **Machine-parseable**: Easy to split and query
- **Extensible**: Works for any asset type
- **Proven**: Based on ISA-95 and existing utility practices

### Why Not UUIDs?

UUIDs are useful for database keys but:
- Not human-readable
- Don't convey meaning
- Harder to debug and troubleshoot

The standard name provides meaning; use UUIDs internally if needed.

## Open Questions

- [ ] Should site codes be standardized across regions?
- [ ] How to handle assets that span multiple systems?
- [ ] Versioning for renamed assets?

## References

- ISA-95: Enterprise-Control System Integration
- ISO 14224: Petroleum and natural gas industries - Collection and exchange of reliability and maintenance data

---

**Feedback?** Open an [issue](../../../../issues) or join the [discussion](../../../../discussions).
