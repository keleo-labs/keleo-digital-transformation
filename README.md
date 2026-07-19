# Digital Transformation Practice Library

A structured practice library for enterprise digital transformation, encoded as JSON for use with [Keleo Studio](https://github.com/keleo-labs/keleo-studio). Derived from industry best practice.

## What This Library Contains

The library models digital transformation across four interdependent dimensions, coordinated through a five-phase lifecycle:

### Domain Practices (`practices/`)

| Practice | Focus | Key Frameworks |
|----------|-------|----------------|
| **Strategic Transformation** | Digital strategy, business model innovation, servitization, customer value co-creation | Teece dynamic capabilities, Business Model Canvas, Furr & Shipilov disruption, service-dominant logic |
| **Digital Technology and Data** | Composable infrastructure, data governance, platform ecosystems, cybersecurity | SMACIT, dual-backbone architecture, data mesh, zero-trust, DevSecOps |
| **Organizational Transformation** | Leadership capability, digital culture, agile structures, innovation systems | Kotter dual operating system, ING squads/tribes/chapters, Haier Rendanheyi, three horizons |
| **Responsible Digital Practice** | Digital ethics, algorithmic accountability, workforce equity | Zuboff surveillance capitalism, Floridi soft/hard ethics, data feminism, GDPR |

### Lifecycle Orchestration (`practices/`)

**Digital Transformation Lifecycle** coordinates all 14 Alphas from the domain practices through five phases:

1. **Sense and Strategize** — Baseline assessment and strategic awareness
2. **Translate and Map** — Strategic translation to actionable plans
3. **Co-Create the Runway** — Collaborative foundation building
4. **Deliver and Emerge** — Scaled delivery with emergent innovation
5. **Feedback and Refactor** — Outcome measurement and strategic re-entry

### Composed Methods (`methods/`)

**Digital Transformation Foundations** — A complete method composing all five practices against the "Digital Transformation Essentials" baseline, providing an end-to-end framework for organizational digital transformation.

## Library at a Glance

- **14 Alphas** — Digital Strategy, Business Model, Customer Value Delivery, Digital Infrastructure, Data Capital, Platform Ecosystem, Digital Security, Transformation Leadership, Organizational Capability, Digital Culture, Innovation Capability, Responsible Digital Governance, Algorithmic Accountability, Digital Workforce Equity
- **47 Activities** across 4 domain practices
- **25 WorkProducts** including strategy documents, architecture blueprints, governance frameworks, and maturity assessments
- **13 Personas** in 4 PersonaGroups — from Chief Digital Officer to Algorithmic Accountability Analyst
- **1 Lifecycle Pattern** with 5 phases mapping progressive state targets for all Alphas

## Directory Structure

```
├── baseline/          # Baseline practice files (kernel ontology)
├── methods/           # Composed methods (multiple practices)
└── practices/         # Domain practices and lifecycle orchestration
```

**Note**: The baseline practice "Digital Transformation Essentials" is referenced by all files but is not stored in this repository. It must be available in Keleo Studio's practice library for method resolution.

## Getting Started

### Prerequisites

- [Keleo Studio](https://github.com/keleo-labs/keleo-studio) (typically cloned at `../adoptionframework`)
- The "Digital Transformation Essentials" baseline loaded in Keleo Studio

### Validation

```bash
cd ../adoptionframework
node validate-schema.js path/to/practice.json       # Schema validation
node validate-full.js path/to/practice.json          # Schema + logical integrity checks
```

### Visualization

```bash
cd ../adoptionframework
npm install
npm run dev
# Open http://localhost:3000
```

Import practice files via the Library page, then use:
- **Practice Author** to edit practices
- **Method Builder** to compose methods
- **Flow Visualizer** to view Kanban pattern boards

## License

Licensed under the [Apache License 2.0](LICENSE).
