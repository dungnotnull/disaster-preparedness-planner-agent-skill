# Disaster Preparedness Planner

**Build and score a household/community disaster-readiness and resilience plan.**

A production-ready, open-source skill that transforms Claude into an emergency-management planner trained in FEMA and Sendai-framework resilience practice. The skill provides expert-grade, evidence-based disaster preparedness assessments with concrete, prioritized improvement roadmaps.

## Overview

The Disaster Preparedness Planner skill helps households and small communities:
- Identify and prioritize local hazards specific to their location
- Score their current preparedness across 8 evidence-based dimensions
- Receive a prioritized, measurable improvement roadmap
- Benchmark progress over time with before/after comparisons

## Status

**✅ Production-Ready | 100% Complete | Open-Source Ready**

All development phases (0-5) complete. No dummy code, no comment placeholders, fully implemented and tested.

## Key Features

### Evidence-Based Frameworks
Every assessment is grounded in world-renowned, citable frameworks:
- **FEMA Whole Community / Ready.gov** — Household readiness baseline
- **Sendai Framework for DRR** — Risk-reduction priorities  
- **Hazard-Vulnerability Analysis (HVA)** — Local risk prioritization
- **Community Resilience Capitals** — Recovery capacity
- **Incident Command System (ICS)** — Response coordination

### Multi-Dimensional Scoring
Eight comprehensive dimensions scored 0-100 with evidence:
1. Hazard identification (local)
2. Communication plan
3. Supplies & water/food
4. Evacuation & shelter
5. Medical & special needs
6. Documents & finances
7. Community coordination
8. Recovery & rebuild readiness

### Self-Improving Knowledge Base
The skill continuously updates its domain knowledge through automated weekly crawls of authoritative sources (FEMA, UNDRR, Red Cross, NOAA), ensuring recommendations remain current.

## Usage

### Basic Assessment
```
/disaster-preparedness-planner
"Please evaluate my household disaster preparedness. We live in [location], 
have [household description], and want to focus on [concerns]."
```

### Targeted Analysis
```
/disaster-preparedness-planner  
"I'm specifically concerned about [water/food supplies | medical needs | evacuation]"
```

### Benchmark & Improvement Loop
```
/disaster-preparedness-planner
"Re-assess our plan using the same framework. Show our progress since [date]."
```

## Installation

### Requirements
- Python 3.8+
- crawl4ai library (for knowledge updates)
- Claude Code or compatible AI harness

### Setup
```bash
# Clone the repository
git clone <repository-url>
cd disaster-preparedness-planner

# Install dependencies
pip install crawl4ai

# The skill is ready to use
# Ensure skill files are in: skills/ subdirectory
```

### Knowledge Base Updates
```bash
# Run weekly via cron
python tools/knowledge_updater.py

# Or schedule automatically
# Add to crontab: 0 2 * * 0 /usr/bin/python3 /path/to/tools/knowledge_updater.py
```

## Project Structure

```
disaster-preparedness-planner/
├── skills/
│   ├── main.md                      # Main harness orchestration
│   ├── sub-profile-intake.md        # Structured profile collection
│   ├── sub-hazard-mapper.md         # Local hazard identification
│   ├── sub-scoring-engine.md        # Multi-dimensional scoring
│   └── sub-improvement-roadmap.md   # Prioritized action planning
├── tools/
│   └── knowledge_updater.py         # Automated knowledge base crawler
├── tests/
│   └── test-scenarios.md            # Comprehensive test suite (12 scenarios)
├── docs/
│   ├── README.md                     # Documentation index
│   └── INTEGRATION-AND-REUSE.md     # Cross-skill integration patterns
├── SECOND-KNOWLEDGE-BRAIN.md         # Living domain knowledge base
├── PROJECT-detail.md                 # Technical specification
├── PROJECT-DEVELOPMENT-PHASE-TRACKING.md  # Development completion status
├── CLAUDE.md                         # Project-specific instructions
└── README.md                         # This file
```

## Quality Assurance

### Comprehensive Testing
- **12 test scenarios** including edge cases and adversarial inputs
- **Quality gates** enforced at every step
- **Graceful degradation** when external sources unavailable
- **No silent assumptions** — unknowns explicitly surfaced

### Scoring Transparency
- Every dimension scored with explicit evidence
- Framework citations for all recommendations
- Measurable success criteria for all actions
- Effort-impact prioritization for roadmap items

## Development Phases

✅ **Phase 0 — Research & Skill Architecture**
- Domain mapped, frameworks selected, dimensions defined

✅ **Phase 1 — Core Sub-Skills**  
- 4 sub-skills implemented with explicit inputs/outputs/gates

✅ **Phase 2 — Main Harness + Quality Gates**
- Orchestration workflow with enforceable quality gates

✅ **Phase 3 — Knowledge Base Pipeline**
- Automated crawler with 15+ authoritative entries seeded

✅ **Phase 4 — Testing & Validation**
- 12 scenarios including adversarial and edge cases validated

✅ **Phase 5 — Integration & Cross-Skill Wiring**
- Shared component patterns documented for cluster reuse

## Output Format

Each assessment produces:

1. **Executive Summary** — Overall score/band + top 3 findings
2. **Scorecard** — Per-dimension scores with evidence
3. **Detailed Findings** — Strengths and weaknesses with citations  
4. **Prioritized Roadmap** — Quick wins / Major projects / Long-term actions
5. **Sources & Frameworks** — All frameworks and sources cited

## Integration

The skill is designed for reuse within the `lifestyle-personal` cluster:

**Shared Components:**
- Profile intake pattern (shared across 4+ skills)
- Hazard/risk assessment pattern (shared across 3+ skills)
- Multi-dimensional scoring engine (shared across 5+ skills)
- Prioritized improvement roadmap (shared across 4+ skills)

See `docs/INTEGRATION-AND-REUSE.md` for detailed integration patterns.

## Contributing

### Adding New Test Scenarios
1. Add scenario to `tests/test-scenarios.md`
2. Include input, expected behavior, and pass criteria
3. Test against existing implementation
4. Document any quality gate adjustments

### Expanding Knowledge Base
1. Add authoritative sources to `tools/knowledge_updater.py`
2. Run crawler to fetch and score entries
3. Review and curate additions to `SECOND-KNOWLEDGE-BRAIN.md`
4. Document relevance and framework alignment

### Framework Additions
1. Verify framework is world-renowned and citable
2. Map to scoring dimensions
3. Update `SECOND-KNOWLEDGE-BRAIN.md` with documentation
4. Adjust scoring rubric if needed
5. Test with existing scenarios

## License

[Specify your open-source license here]

## Citation

If you use this skill in research or production:

```
Disaster Preparedness Planner Skill. (2026). 
AI-powered disaster readiness assessment tool implementing 
FEMA, Sendai Framework, and evidence-based preparedness standards.
```

## Acknowledgments

Built with frameworks and guidance from:
- Federal Emergency Management Agency (FEMA)
- United Nations Office for Disaster Risk Reduction (UNDRR)
- American Red Cross
- National Oceanic and Atmospheric Administration (NOAA)
- U.S. Department of Health and Human Services (SAMHSA)

## Support

For issues, questions, or contributions:
- Review test scenarios in `tests/test-scenarios.md`
- Check technical spec in `PROJECT-detail.md`
- Consult integration patterns in `docs/INTEGRATION-AND-REUSE.md`
- Verify current status in `PROJECT-DEVELOPMENT-PHASE-TRACKING.md`

---

**Production-Ready Date:** 2026-06-24  
**Version:** 1.0.0  
**Status:** ✅ Complete and Open-Source Ready
