# Water Utility Ontology

**Open-source standards for water utility data integration and AI readiness.**

[![License: CC BY 4.0](https://img.shields.io/badge/License-CC%20BY%204.0-lightgrey.svg)](https://creativecommons.org/licenses/by/4.0/)
[![Status: Draft](https://img.shields.io/badge/Status-Draft-yellow.svg)]()

---

## The Problem

Every water utility invents their own way to name assets, structure data, and visualize operations. A pump might be:
- `P-001` in SCADA
- `Pump_MainSt_1` in GIS
- `EQ-4521` in CMMS

This fragmentation costs the industry billions:
- Integration projects take **months instead of weeks**
- AI solutions require **custom data mapping** for every deployment
- Operators **can't transfer skills** between utilities
- Vendors must **rebuild** for every customer

## The Solution

A shared ontology - common vocabulary, naming conventions, and data structures - that lets:
- Systems speak the same language
- Tools work across utilities
- Knowledge transfer freely
- AI become affordable and scalable

## Standards

| Standard | Status | Description |
|----------|--------|-------------|
| [Asset Naming](./standards/asset-naming/) | Draft | Unified naming convention across all systems |
| [Data Hierarchy](./standards/data-hierarchy/) | Draft | ISA-95 adapted for water utilities |
| [SCADA Visualization](./standards/scada-visualization/) | Draft | Standard colors and HMI layouts |

### Coming Soon
- Water Quality Data Model
- Work Order Schema
- Integration Patterns (SCADA-to-GIS, CMMS-to-Historian)
- Energy Management Standards

## Quick Start

### For Utilities
1. Review the [standards](./standards/) that apply to your needs
2. Pilot implementation on a new project or system
3. Share feedback via [Issues](../../issues)

### For Vendors
1. Review standards for integration targets
2. Map your product's data model to the ontology
3. Document compliance in your materials

### For Contributors
1. Join the [discussion](../../discussions)
2. Review open [issues](../../issues) and [pull requests](../../pulls)
3. See [CONTRIBUTING.md](./CONTRIBUTING.md) for guidelines

## Why This Matters

```
Without Standards                    With Standards
─────────────────                    ──────────────

  SCADA ──?──┐                         SCADA ────┐
             │                                   │
  GIS ───?───┼──?── AI                 GIS ──────┼──── AI
             │      (expensive)                  │      (affordable)
  CMMS ──?───┘                         CMMS ─────┘

  6 months integration               2 weeks integration
  $500K per utility                  $50K per utility
  Custom everything                  Reusable everywhere
```

## Governance

This is a community-driven initiative:
- **No vendor ownership** - standards remain independent
- **Open development** - all discussions and decisions are public
- **Practitioner-led** - working groups are run by utility professionals
- **Free to use** - CC BY 4.0 license, no fees or membership required

## Get Involved

- **Website**: [evolvewater.ai/standards](https://evolvewater.ai/standards.html)
- **Discussions**: [GitHub Discussions](../../discussions)
- **Issues**: [Report problems or suggest improvements](../../issues)
- **Join**: [Become a founding member](https://evolvewater.ai/join.html)

## License

This work is licensed under [Creative Commons Attribution 4.0 International (CC BY 4.0)](https://creativecommons.org/licenses/by/4.0/).

You are free to:
- **Share** - copy and redistribute the material
- **Adapt** - remix, transform, and build upon the material for any purpose

Under the following terms:
- **Attribution** - give appropriate credit and indicate if changes were made

---

**Built by utilities, for utilities.**
