# Test Scenarios — Disaster Preparedness Plan (household/community)

These scenarios validate the harness, scoring, gates, and graceful degradation. Minimum 5; adversarial and edge cases included.

## Scenario 1: Full assessment
- **Input:** User submits a complete disaster preparedness plan artifact and asks for a full evaluation
- **Expected behavior:** Score every dimension with evidence, highlight hazard identification and communication plan findings, deliver a prioritized roadmap
- **Frameworks expected in output:** FEMA Whole Community / Ready.gov preparedness, Sendai Framework for Disaster Risk Reduction
- **Quality gates checked:** every dimension scored with evidence; roadmap items measurable.
- **Pass criteria:** output contains a scorecard, evidence per dimension, and a prioritized roadmap; no silent assumptions.
## Scenario 2: Targeted concern
- **Input:** User reports a specific weakness in supplies & water/food
- **Expected behavior:** Diagnose the supplies & water/food issue against the named framework and return focused, measurable fixes
- **Frameworks expected in output:** FEMA Whole Community / Ready.gov preparedness, Sendai Framework for Disaster Risk Reduction
- **Quality gates checked:** every dimension scored with evidence; roadmap items measurable.
- **Pass criteria:** output contains a scorecard, evidence per dimension, and a prioritized roadmap; no silent assumptions.
## Scenario 3: Benchmark / improvement loop
- **Input:** User wants to compare a revised version against a prior baseline
- **Expected behavior:** Re-score against the same rubric, show the before/after delta per dimension, and update the roadmap
- **Frameworks expected in output:** FEMA Whole Community / Ready.gov preparedness, Sendai Framework for Disaster Risk Reduction
- **Quality gates checked:** every dimension scored with evidence; roadmap items measurable.
- **Pass criteria:** output contains a scorecard, evidence per dimension, and a prioritized roadmap; no silent assumptions.

## Scenario 4: Incomplete input (edge case)
- **Input:** User provides only a vague one-line description with no artifact.
- **Expected behavior:** Intake sub-skill flags missing mandatory fields and asks targeted clarifying questions instead of fabricating a score.
- **Pass criteria:** No score is produced from assumptions; unknowns are explicitly listed.

## Scenario 5: Offline / sources unavailable (graceful degradation)
- **Input:** A normal request, but WebSearch/WebFetch are unavailable.
- **Expected behavior:** Skill falls back to SECOND-KNOWLEDGE-BRAIN.md and clearly states the limitation and reduced confidence.
- **Pass criteria:** Output explicitly signals the degraded mode and still cites internal frameworks.

## Scenario 6: Conflicting user constraints (adversarial)
- **Input:** User specifies mutually exclusive constraints: "minimal budget (<$100)" but "complete professional-grade supplies for 6-month duration."
- **Expected behavior:** Scoring engine acknowledges the conflict, presents trade-offs transparently, and offers tiered alternatives rather than fabricating an impossible solution.
- **Pass criteria:** No silent assumption resolution; explicit conflict identification; multiple pathway options presented with realistic cost estimates.

## Scenario 7: Extreme multi-hazard location (edge case)
- **Input:** User location subject to 7+ hazard types (coastal Florida: hurricane, storm surge, flood, tornado, wildfire, extreme heat, pandemic) with high recurrence intervals.
- **Expected behavior:** Hazard mapper ranks all hazards by likelihood×severity matrix, identifies compounding and cascading effects, and prioritizes top-tier hazards without ignoring lower-tier but still significant risks.
- **Pass criteria:** All hazards acknowledged; prioritization rationale explicit; compounding effects addressed; no generic advice.

## Scenario 8: Multi-generational household with special needs (complexity)
- **Input:** Household includes: elderly with dementia, child with Type 1 diabetes, mobility-impaired adult requiring electric medical equipment, and non-English-speaking members.
- **Expected behavior:** Intake captures all special needs without prompting cascade; scoring weights medical/evacuation dimensions higher; roadmap addresses each special need with specific, measurable actions.
- **Pass criteria:** No generic advice; every special need addressed; evacuation plans include equipment and medication requirements; communication plan addresses language access.

## Scenario 9: Framework applicability question (edge case)
- **Input:** User explicitly questions: "Does Sendai Framework even apply to household-level planning, or is it just for governments?"
- **Expected behavior:** Skill explains the framework's origin and scope, demonstrates household-level applicability with concrete examples, and transparently acknowledges when framework guidance is extrapolated vs directly applicable.
- **Pass criteria:** Clear explanation of framework scope and limitations; concrete household-level examples provided; no overclaim of framework authority.

## Scenario 10: Post-disaster recovery only (partial scope)
- **Input:** User states: "I'm fine on preparedness—just need recovery and rebuild planning."
- **Expected behavior:** Intake flags scope limitation, confirms user doesn't want full assessment, scoring focuses on Recovery & rebuild readiness dimension with deep analysis, roadmap prioritizes recovery-specific actions.
- **Pass criteria:** Scope limitation explicitly acknowledged; other dimensions not forced; recovery dimension scored with evidence; roadmap focused on recovery actions.

## Scenario 11: Apartment/renter constraints (environment edge case)
- **Input:** User in high-rise rental unit with no storage space, no control over building modifications, landlord restrictions, and shared common areas.
- **Expected behavior:** Intake captures all constraints; scoring acknowledges limitations; roadmap provides renter-appropriate alternatives (portable kits, community coordination, negotiated modifications); no homeowner-centric advice.
- **Pass criteria:** Storage constraints explicitly addressed; renter-appropriate alternatives provided; building-level coordination included; no advice requiring property ownership.

## Scenario 12: Very low-resource, high-vulnerability profile (extreme case)
- **Input:** User reports: zero budget, no vehicle, social isolation, disability, unstable housing, food insecurity.
- **Expected behavior:** Scoring doesn't penalize for lack of resources; roadmap prioritizes no-cost actions (community connections, emergency alerts, documentation consolidation), identifies available assistance programs, avoids recommendations requiring unattainable resources.
- **Pass criteria:** Resource constraints never result in lower preparedness scores; roadmap focuses on achievable actions; assistance programs identified; no unrealistic recommendations.

