# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Repository Purpose

This repository contains a structured digital transformation practice library encoded as JSON, derived from industry best practice. It is designed to work with **Keleo Studio**, a Next.js application for authoring, composing, and visualizing practices based on the SEMAT practice language.

The library models enterprise digital transformation across four dimensions — strategy, technology, organization, and ethics — coordinated through a five-phase lifecycle.

## Content Structure

### Practices (in `practices/`)

Four domain practices, each defining Alphas, Activities, WorkProducts, Personas, and Narratives:

- **Strategic Transformation** — Digital strategy, business model innovation, servitization, customer value co-creation (Teece dynamic capabilities, Business Model Canvas, service-dominant logic)
- **Digital Technology and Data** — Composable infrastructure, data governance, platform ecosystems, cybersecurity (SMACIT, dual-backbone, data mesh, zero-trust, DevSecOps)
- **Organizational Transformation** — Leadership, digital culture, agile structures, innovation systems (Kotter dual operating system, ING squads/tribes, Haier Rendanheyi, three horizons)
- **Responsible Digital Practice** — Digital ethics, algorithmic accountability, workforce equity (Zuboff, Floridi, data feminism, GDPR, platform cooperativism)

One orchestration practice:

- **Digital Transformation Lifecycle** — Depends on all four domain practices. Defines a "Digital Transformation Journey" pattern with five phases: Sense and Strategize, Translate and Map, Co-Create the Runway, Deliver and Emerge, Feedback and Refactor. Contains no Alphas/Activities of its own; coordinates all 14 Alphas from the domain practices through progressive state targets per phase.

### Methods (in `methods/`)

- **Digital Transformation Foundations** — String-reference method composing all five practices against the "Digital Transformation Essentials" baseline
- **Digital Transformation Lifecycle (Embedded)** — Appears to be a work-in-progress staging artifact; currently identical to the lifecycle practice file

### Baseline (in `baseline/`)

The baseline practice **Digital Transformation Essentials** is referenced by all files but is not included in this repository. It defines the foundational Focuses, Alphas, ActivitySpaces, Competencies, and NarrativeTypes that practices extend. It must be available in Keleo Studio's practice library for method resolution.

## Aggregate Library Stats

- 14 Alphas across 4 domain practices
- 47 Activities, 25 WorkProducts, 13 Personas, 4 PersonaGroups
- 1 lifecycle pattern with 5 phases
- All files reference `baselinePracticeName: "Digital Transformation Essentials"`

## Relationship with Keleo Studio

**Keleo Studio location**: Typically at `../keleo-studio` relative to this repository.

### Validation

```bash
cd ../adoptionframework
node validate-schema.js path/to/practice.json       # Schema validation
node validate-full.js path/to/practice.json          # Schema + logical integrity
```

### Running Keleo Studio

```bash
cd ../adoptionframework
npm install
npm run dev
# Access at http://localhost:3000
```

## Key Schema Rules

When editing practice JSON files:

1. **Baseline reference**: Every practice must include `"baselinePracticeName": "Digital Transformation Essentials"`
2. **String references only**: Use exact string names when referencing elements; never embed full objects where a string is expected
3. **Alpha `contributesTo`**: New Alphas must declare `contributesTo` referencing a baseline or dependency Alpha
4. **Alpha states**: When redeclaring baseline Alphas, preserve state names and count (can enrich with checklists)
5. **`activitySpaceName`**: Activities must reference valid ActivitySpace names from the baseline
6. **Competency mapping**: Personas must have non-empty `competencies` arrays with exact baseline Competency name matches
7. **PersonaGroup hierarchy**: Activities reference PersonaGroups (not Personas) in `involves`
8. **Narratives**: Every Narrative requires both `name` AND `narrativeName` properties
9. **WorkProduct LODs**: Minimum 3 Levels of Detail per WorkProduct
10. **Practice element aliases**: `practiceElementAliases` are for human readability; all structural references use canonical baseline names

## Method Composition

Methods can use two formats:
- **String references** (compact): `baselinePracticeName` + `practiceNames` array — requires practice library for resolution
- **Full embedded objects**: `baselinePractice` + `practices` array — self-contained, portable

The presence of `practices`, `practiceNames`, or `baselinePractice` discriminates a Method from a Practice.

Practice dependencies declared via `practiceDependencyNames` are resolved recursively with cycle detection. Practices merge in array order; elements with the same `name` are merged, unique elements are added.
