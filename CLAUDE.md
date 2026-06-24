# CLAUDE.md — Disaster Preparedness Plan (household/community)

**Skill name:** `disaster-preparedness-planner`
**Tagline:** Build and score a household/community disaster-readiness and resilience plan.
**Source idea:** #105 (cluster: `lifestyle-personal`)
**Current phase:** Phase 4 — Testing & Validation (initial build complete)

## Problem This Skill Solves
Households and small communities are unprepared for likely local hazards. They need a hazard-specific readiness plan scored for completeness and recovery capacity.

## Harness Flow Summary
1. **sub-profile-intake** → Collect a complete, normalized profile before any analysis so downstream scoring is grounded in real inputs, not assumptions.
2. **sub-hazard-mapper** → Anchor the plan to real local risks (flood, quake, wildfire, etc.) rather than a generic checklist.
3. **sub-scoring-engine** → Produce a transparent, dimension-by-dimension score (0-100 or band) with evidence for every sub-score.
4. **sub-improvement-roadmap** → Convert weaknesses into a sequenced, effort/impact-ranked action plan the user can execute.
5. **main (synthesis)** → assemble the scored deliverable + prioritized roadmap and run final quality gates.

## Gates
No safety/compliance gate applies to this cluster; standard quality gates still apply.

## Sub-skills
- `skills/sub-profile-intake.md` — Structured intake of location, household composition, and local hazards plus goals, constraints, and context.
- `skills/sub-hazard-mapper.md` — Identify and rank the most likely local hazards.
- `skills/sub-scoring-engine.md` — Multi-dimensional scoring of the preparedness plan against the selected framework.
- `skills/sub-improvement-roadmap.md` — Prioritized improvement roadmap for the preparedness with effort/impact.

## Tools Required
WebSearch, WebFetch, Read, Write, Bash

## Knowledge Sources
- [FEMA / Ready.gov](https://www.ready.gov)
- [UNDRR Sendai Framework](https://www.undrr.org)
- [Red Cross preparedness](https://www.redcross.org)
- [NOAA hazard data](https://www.noaa.gov)

ArXiv / research categories crawled: physics.soc-ph

## Supporting Tools
- `tools/knowledge_updater.py` — crawl4ai pipeline that refreshes `SECOND-KNOWLEDGE-BRAIN.md` weekly from the sources above.

## Active Development Tasks
- [x] Scaffold deliverables and sub-skills
- [x] Define scoring dimensions against named frameworks
- [ ] Expand `SECOND-KNOWLEDGE-BRAIN.md` with first crawl batch
- [ ] Add 3 more adversarial test scenarios
- [ ] Wire shared cluster sub-skills for reuse

## Reference Docs
- `PROJECT-detail.md` — full technical spec
- `PROJECT-DEVELOPMENT-PHASE-TRACKING.md` — phase roadmap
- `SECOND-KNOWLEDGE-BRAIN.md` — living domain knowledge base
