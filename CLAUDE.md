# Claude Code Instructions - Water Utility Ontology

This file contains specific instructions for Claude Code when working on this project.

## Project Overview

**Water Utility Ontology** - Open-source standards for water utility data integration and AI readiness. This repository contains semantic standards, naming conventions, data hierarchies, and visualization guidelines for the water industry.

## GitHub Configuration

**IMPORTANT**: This project uses a dedicated GitHub account. Always use these settings:

- **GitHub Organization**: Founder-Evolve
- **Repository**: water-utility-ontology
- **Full URL**: https://github.com/Founder-Evolve/water-utility-ontology
- **SSH Remote**: git@github-founder-evolve:Founder-Evolve/water-utility-ontology.git

### SSH Configuration

This project uses a project-specific SSH key configured with the host alias `github-founder-evolve`. The git remote is configured to use this alias automatically.

**Do NOT use**:
- The default `github.com` host for push/pull operations
- Other GitHub accounts (mikeskarl, joeblack47, etc.)

### Git Commands

When working with this repo, git operations will automatically use the correct credentials via the SSH host alias.

```bash
# These will work correctly:
git push origin main
git pull origin main

# The remote is configured as:
# origin -> git@github-founder-evolve:Founder-Evolve/water-utility-ontology.git
```

## Repository Structure

```
water-utility-ontology/
├── README.md                  # Main repository overview
├── CONTRIBUTING.md            # Contribution guidelines
├── LICENSE                    # CC BY 4.0
├── CLAUDE.md                  # This file
├── docs/
│   └── standard-template.md   # Template for new standards
├── standards/
│   ├── asset-naming/          # Asset naming convention
│   ├── data-hierarchy/        # ISA-95 adaptation for water
│   └── scada-visualization/   # Colors, symbols, layouts
└── examples/                  # Implementation examples
```

## Standards Development Workflow

1. **Draft** - Create new standard in `standards/{name}/README.md`
2. **Review** - Open PR for community feedback
3. **Pilot** - Test at participating utilities
4. **Stable** - Merge and tag release

## Commit Message Format

```
type: short description

Optional longer description

Co-Authored-By: Claude <noreply@anthropic.com>
```

Types: `feat`, `fix`, `docs`, `style`, `refactor`

## Related Projects

- **Evolvewater Website**: /Users/mkarl/1Code/1Evolve/ (separate repo, uses joeblack47 account)
- Standards page references this repo at: https://github.com/Founder-Evolve/water-utility-ontology

## License

CC BY 4.0 - All contributions must be compatible with this license.
