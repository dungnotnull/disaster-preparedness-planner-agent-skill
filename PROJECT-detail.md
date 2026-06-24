# PROJECT-detail.md — Disaster Preparedness Plan (household/community)

## Executive Summary
`disaster-preparedness-planner` turns Claude into an emergency-management planner trained in FEMA and Sendai-framework resilience practice. It runs a research-first harness that intakes the user's case, binds it to named world-renowned frameworks, scores it on 8 dimensions, and returns a prioritized improvement roadmap with effort/impact. The skill is self-improving: `tools/knowledge_updater.py` continuously refreshes its knowledge base from authoritative sources.

## Problem Statement
Households and small communities are unprepared for likely local hazards. They need a hazard-specific readiness plan scored for completeness and recovery capacity.

## Target Users & Use Cases
- Primary: practitioners and non-experts who need an expert-grade, evidence-based assessment of their disaster preparedness plan (household/community) artifact.
- Trigger examples:
  - User says: "Full assessment" → skill score every dimension with evidence, highlight hazard identification and communication plan findings, deliver a prioritized roadmap
  - User says: "Targeted concern" → skill diagnose the supplies & water/food issue against the named framework and return focused, measurable fixes
  - User says: "Benchmark / improvement loop" → skill re-score against the same rubric, show the before/after delta per dimension, and update the roadmap

## Harness Architecture
```
intake/requirements
    │  profile-intake → hazard-mapper → scoring-engine → improvement-roadmap → synthesis
    ▼
[named frameworks] → [multi-dimensional scoring] → [prioritized roadmap] → [quality/compliance gates] → DELIVERABLE
```

## Evaluation Frameworks (world-renowned, citable)
- **FEMA Whole Community / Ready.gov preparedness** — Household readiness baseline
- **Sendai Framework for Disaster Risk Reduction** — Risk-reduction priorities
- **Hazard-Vulnerability Analysis (HVA)** — Local risk prioritization
- **Community resilience capitals model** — Recovery capacity
- **Incident Command System (ICS) basics** — Response coordination

## Scoring Dimensions
1. Hazard identification (local)
2. Communication plan
3. Supplies & water/food
4. Evacuation & shelter
5. Medical & special needs
6. Documents & finances
7. Community coordination
8. Recovery & rebuild readiness

## Full Sub-Skill Catalog
### `sub-profile-intake`
- **Purpose:** Collect a complete, normalized profile before any analysis so downstream scoring is grounded in real inputs, not assumptions.
- **Inputs:** Free-form user description, uploaded artifacts, answers to clarifying questions
- **Outputs:** Normalized profile object (JSON-like) with goals, constraints, current state, and explicit unknowns flagged
- **Tools:** Read, WebSearch
- **Quality gate:** All mandatory fields captured or explicitly marked 'unknown'; no silent assumptions.
### `sub-hazard-mapper`
- **Purpose:** Anchor the plan to real local risks (flood, quake, wildfire, etc.) rather than a generic checklist.
- **Inputs:** Location, environment, history
- **Outputs:** Ranked local hazard list with likelihood/severity
- **Tools:** Read, WebSearch, WebFetch
- **Quality gate:** At least the top three location-specific hazards identified with rationale.
### `sub-scoring-engine`
- **Purpose:** Produce a transparent, dimension-by-dimension score (0-100 or band) with evidence for every sub-score.
- **Inputs:** Normalized profile, selected framework + rubric
- **Outputs:** Per-dimension scores, weighted total, strengths, and ranked weaknesses each tied to evidence
- **Tools:** Read, WebSearch
- **Quality gate:** Every dimension has a numeric score AND a one-line evidence/justification; no unscored dimension.
### `sub-improvement-roadmap`
- **Purpose:** Convert weaknesses into a sequenced, effort/impact-ranked action plan the user can execute.
- **Inputs:** Scored weaknesses, user constraints
- **Outputs:** Prioritized roadmap (Quick wins / Major projects / Long-term) with effort, impact, and success metric per item
- **Tools:** Read, Write
- **Quality gate:** Every recommendation has effort, impact, and a measurable success criterion.

## Skill File Format Specification
Each skill file uses YAML frontmatter (`name`, `description`) followed by: Role & Persona, Workflow (Harness Flow), Sub-skills Available, Tools, Output Format, Quality Gates. `skills/main.md` is the harness entry point and invokes the sub-skills above in order.

## E2E Execution Flow
1. Parse the user request and uploaded artifact(s).
2. Run intake/requirements sub-skill; flag unknowns (no silent assumptions).
3. (No safety gate for this cluster.)
4. Select governing framework(s) and rubric.
5. Score every dimension with cited evidence.
6. Generate the prioritized roadmap (effort/impact + success metric).
7. Run quality/devil's-advocate review.
8. Synthesize the final professional deliverable; pass all quality gates before display.

## SECOND-KNOWLEDGE-BRAIN Integration
- Sources: FEMA / Ready.gov, UNDRR Sendai Framework, Red Cross preparedness, NOAA hazard data
- ArXiv categories: physics.soc-ph
- Search queries: "disaster preparedness household resilience", "hazard vulnerability analysis", "community emergency planning"
- Append format: dated entries with Title, Authors, Year, Venue, DOI/Link, Relevance.

## Supporting Tools Spec
`tools/knowledge_updater.py`: crawl4ai → fetch → parse → score (recency × relevance) → dedupe (URL/DOI hash) → append to `SECOND-KNOWLEDGE-BRAIN.md`. Schedule: weekly cron.

## Quality Gates (must all pass before output)
- Every scored dimension has evidence.
- At least one named framework cited.
- Roadmap items each have effort, impact, and a measurable success metric.
- Devil's-advocate review passed.

## Test Scenarios
1. **Full assessment** — Input: User submits a complete disaster preparedness plan artifact and asks for a full evaluation → Expected: Score every dimension with evidence, highlight hazard identification and communication plan findings, deliver a prioritized roadmap
2. **Targeted concern** — Input: User reports a specific weakness in supplies & water/food → Expected: Diagnose the supplies & water/food issue against the named framework and return focused, measurable fixes
3. **Benchmark / improvement loop** — Input: User wants to compare a revised version against a prior baseline → Expected: Re-score against the same rubric, show the before/after delta per dimension, and update the roadmap

## Key Design Decisions
1. Scoring is always bound to named, citable frameworks — never ad hoc.
2. Intake forbids silent assumptions; unknowns are surfaced.
3. Roadmap is effort/impact-ranked and measurable.
4. Knowledge base is self-updating for trend alignment.
5. Devil's-advocate review is mandatory before output.
