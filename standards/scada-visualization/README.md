# SCADA Visualization Standard

**Status:** Draft
**Version:** 0.1.0
**Working Group:** SCADA Visualization WG

---

## Overview

Standard color codes, symbology, and HMI layout guidelines for water utility SCADA systems.

## The Problem

Every utility creates their own SCADA visual language:
- Is red "alarm" or "running"?
- Does green mean "open" or "closed"?
- Where are alarms displayed?

New operators spend months learning each utility's conventions. Hiring from other utilities means retraining from scratch.

## The Standard

### Color Coding

#### Equipment Status Colors

| Color | Hex | RGB | Meaning |
|-------|-----|-----|---------|
| **Green** | `#22C55E` | 34, 197, 94 | Running / Operating normally |
| **Red** | `#DC2626` | 220, 38, 38 | Alarm / Fault / Requires attention |
| **Yellow** | `#EAB308` | 234, 179, 8 | Warning / Degraded performance |
| **Gray** | `#6B7280` | 107, 114, 128 | Off / Stopped / Out of service |
| **Blue** | `#3B82F6` | 59, 130, 246 | Manual mode / Local control |
| **White** | `#FFFFFF` | 255, 255, 255 | Unknown / Communication failure |

#### Valve Position Colors

| Color | Meaning |
|-------|---------|
| **Green** | Open |
| **Red** | Closed |
| **Yellow** | Transitioning / Partial |
| **Gray** | Unknown / Offline |

#### Process Values

| Condition | Color |
|-----------|-------|
| Normal | Green or Black text |
| High warning | Yellow background |
| High alarm | Red background |
| Low warning | Yellow background |
| Low alarm | Red background |

### Symbology

#### Pumps

```
Running:        Stopped:        Fault:
  ┌───┐           ┌───┐          ┌───┐
  │ ▶ │  GREEN    │ ▶ │  GRAY    │ ▶ │  RED
  └───┘           └───┘          └───┘
```

#### Valves

```
Open:           Closed:         Transitioning:
  │               │               │
 ─┼─  GREEN      ─╳─  RED       ─┼─  YELLOW
  │               │               │
```

#### Tanks/Reservoirs

- Show level as percentage fill
- Color band: Green (normal), Yellow (warning), Red (alarm)
- Display numeric level value

### HMI Layout Guidelines

#### Screen Hierarchy

1. **Overview** - System-wide status, major alarms
2. **Area** - Functional area (e.g., Raw Water Pumping)
3. **Detail** - Individual equipment control

#### Standard Screen Elements

| Element | Location | Purpose |
|---------|----------|---------|
| Title bar | Top | Screen name, timestamp |
| Navigation | Left or top | Access to other screens |
| Alarms | Top or right | Active alarm summary |
| Main content | Center | Process graphic |
| Status bar | Bottom | System status, user info |

#### Alarm Presentation

**Alarm Banner Requirements:**
- Always visible on all screens
- Most critical alarms at top
- Show: Time, Tag, Description, Priority
- Color-coded by priority

**Alarm Priority Colors:**

| Priority | Color | Response Time |
|----------|-------|---------------|
| Critical | Red | Immediate |
| High | Orange | < 5 minutes |
| Medium | Yellow | < 30 minutes |
| Low | Blue | When convenient |

### Layout Templates

#### Pump Station Overview

```
┌─────────────────────────────────────────────────────┐
│  NORTH PUMP STATION              12:45:32  11/26/24 │
├─────────────────────────────────────────────────────┤
│ ┌─────────────────────────────────────────────────┐ │
│ │            ALARM: High wet well (PS-01)         │ │
│ └─────────────────────────────────────────────────┘ │
│                                                     │
│   SUCTION          PUMPS           DISCHARGE        │
│                                                     │
│   ┌─────┐      ┌───┐  ┌───┐      ┌─────┐          │
│   │     │      │ ▶ │  │ ▶ │      │     │          │
│   │ 75% │─────│ P1 │──│ P2 │─────│     │          │
│   │     │      └───┘  └───┘      │     │          │
│   └─────┘      GREEN  GRAY       └─────┘          │
│   Wet Well     RUN    STOP       Discharge        │
│                                                     │
│   Level: 7.5 ft   Flow: 1,250 GPM   Press: 65 PSI │
│                                                     │
├─────────────────────────────────────────────────────┤
│  [Overview] [Trends] [Alarms] [Settings]           │
└─────────────────────────────────────────────────────┘
```

#### Treatment Process Overview

```
┌─────────────────────────────────────────────────────┐
│  TREATMENT OVERVIEW              12:45:32  11/26/24 │
├─────────────────────────────────────────────────────┤
│                                                     │
│  RAW WATER → COAG → FLOC → SED → FILT → DISINFECT │
│     │         │      │      │     │        │       │
│   [OK]      [OK]   [OK]  [WARN]  [OK]    [OK]     │
│                                                     │
│  ┌─────────────────────────────────────────────────┐
│  │ SEDIMENTATION - WARNING                         │
│  │ Basin 2 sludge blanket high (4.2 ft)           │
│  └─────────────────────────────────────────────────┘
│                                                     │
│  Turbidity In: 12 NTU    Turbidity Out: 0.08 NTU  │
│  Flow: 15.2 MGD          Cl2 Residual: 2.1 mg/L   │
│                                                     │
└─────────────────────────────────────────────────────┘
```

## Implementation Guide

### Step 1: Audit Current Screens

Document existing color usage and compare to standard.

### Step 2: Create Mapping

| Current | Standard | Action |
|---------|----------|--------|
| Red = Running | Green = Running | Change |
| Green = Alarm | Red = Alarm | Change |

### Step 3: Update Templates

Modify HMI templates to use standard colors.

### Step 4: Migrate Gradually

- New screens use standard
- Update existing screens during maintenance
- Train operators on changes

## Rationale

### Why These Colors?

- **Green = Good**: Universal association
- **Red = Bad**: Universal alarm color
- **Yellow = Caution**: Industry standard for warnings
- **Gray = Inactive**: Neutral, non-attention-grabbing

### Accessibility

Colors chosen for:
- Sufficient contrast (WCAG AA)
- Distinguishable for common color blindness
- Clear meaning even in grayscale

## Open Questions

- [ ] Handling of legacy color schemes during transition?
- [ ] Dark mode / night shift color variants?
- [ ] Animation standards (blink rates, etc.)?

## References

- ISA-101: Human Machine Interfaces
- EEMUA 201: Process Plant Alarm Systems
- ASM Consortium: Effective Operator Display Design

---

**Feedback?** Open an [issue](../../../../issues) or join the [discussion](../../../../discussions).
