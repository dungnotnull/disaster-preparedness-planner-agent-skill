# Integration & Cross-Skill Wiring — Disaster Preparedness Planner

## Lifestyle-Personal Cluster Context

The `disaster-preparedness-planner` skill belongs to the broader `lifestyle-personal` cluster, which includes skills focused on improving personal and household outcomes through structured planning and assessment.

## Shared Sub-Skills for Reuse

### 1. Profile Intake Pattern
**Shared across:** disaster-preparedness-planner, financial-planner, career-coach, wellness-assessor

**Reusable component:** Structured intake of user profile data including:
- Location and environmental context
- Household composition and dependencies
- Resource constraints (budget, time, access)
- Goals and risk tolerance
- Current state assessment

**Normalization schema:**
```json
{
  "location": {
    "type": "string",
    "constraints": ["urban", "suburban", "rural", "remote"]
  },
  "household": {
    "size": "number",
    "composition": ["adults", "children", "seniors", "special_needs"],
    "structure": ["single-family", "multi-family", "apartment", "other"]
  },
  "resources": {
    "budget_range": "string",
    "time_availability": "string",
    "access_constraints": ["mobility", "language", "technology"]
  },
  "goals": ["string"],
  "constraints": ["string"],
  "current_state": {
    "existing_preparations": ["string"],
    "identified_gaps": ["string"]
  },
  "unknowns": ["string"]
}
```

**Quality gate:** All mandatory fields captured or explicitly marked 'unknown'; no silent assumptions.

### 2. Hazard/Risk Assessment Pattern
**Shared across:** disaster-preparedness-planner, travel-safety-advisor, climate-risk-assessor, insurance-planner

**Reusable component:** Local risk identification and prioritization including:
- Environmental hazard mapping
- Likelihood × severity matrix
- Historical frequency analysis
- Climate trend projections

**Assessment schema:**
```json
{
  "location": "string",
  "hazards": [
    {
      "type": "string",
      "likelihood": "number (0-1)",
      "severity": "number (0-10)",
      "priority_score": "number",
      "evidence": "string",
      "recurrence_interval": "string",
      "seasonality": ["string"],
      "cascading_effects": ["string"]
    }
  ],
  "confidence_level": "string"
}
```

**Quality gate:** At least the top three location-specific hazards identified with rationale.

### 3. Multi-Dimensional Scoring Engine
**Shared across:** disaster-preparedness-planner, financial-health-check, wellness-assessor, career-fit-analyzer

**Reusable component:** Transparent, evidence-based scoring across multiple dimensions:
- Per-dimension scores (0-100 or band)
- Weighted total calculation
- Evidence citation per dimension
- Strength and weakness identification

**Scoring schema:**
```json
{
  "framework": "string",
  "dimensions": [
    {
      "name": "string",
      "score": "number (0-100)",
      "band": "string (A-F or 1-5)",
      "evidence": "string",
      "framework_reference": "string",
      "strengths": ["string"],
      "weaknesses": ["string"]
    }
  ],
  "overall_score": "number (0-100)",
  "overall_band": "string",
  "primary_strengths": ["string"],
  "primary_weaknesses": ["string"],
  "confidence_level": "string"
}
```

**Quality gate:** Every dimension has a numeric score AND a one-line evidence/justification; no unscored dimension.

### 4. Prioritized Improvement Roadmap
**Shared across:** disaster-preparedness-planner, financial-planner, career-coach, skill-development-advisor

**Reusable component:** Action plan prioritized by effort and impact:
- Categorized recommendations (Quick wins, Major projects, Long-term)
- Effort-impact matrix for each action
- Measurable success criteria
- Resource requirements and dependencies

**Roadmap schema:**
```json
{
  "prioritization_method": "effort-impact",
  "categories": {
    "quick_wins": [
      {
        "action": "string",
        "effort": "string (low/medium/high)",
        "effort_hours_estimate": "number",
        "impact": "string (low/medium/high)",
        "impact_score": "number (0-10)",
        "success_metric": "string",
        "dependencies": ["string"],
        "resources_needed": ["string"],
        "priority": "number"
      }
    ],
    "major_projects": ["same structure"],
    "long_term": ["same structure"]
  },
  "estimated_total_effort": "string",
  "expected_outcomes": ["string"]
}
```

**Quality gate:** Every recommendation has effort, impact, and a measurable success criterion.

## Cross-Skill Integration Points

### 1. Location-Based Risk Sharing
**Direction:** climate-risk-assessor → disaster-preparedness-planner
- Climate projections inform long-term hazard likelihood
- Shared hazard database infrastructure
- Unified environmental profile

### 2. Resource Constraint Integration
**Direction:** financial-planner → disaster-preparedness-planner
- Budget constraints shape realistic recommendations
- Shared resource assessment methodology
- Coordinated emergency fund planning

### 3. Community Coordination Reuse
**Direction:** disaster-preparedness-planner ← community-engagement-advisor
- Community network building patterns
- Mutual aid system design principles
- Shared communication tree templates

### 4. Wellness Integration
**Direction:** wellness-assessor → disaster-preparedness-planner
- Medical and special needs data structure
- Mental health preparedness integration
- Stress management considerations

## Standardized Output Schema

### Unified Assessment Report Format
```json
{
  "skill_id": "string",
  "assessment_date": "ISO date",
  "profile": { /* Profile intake schema */ },
  "risks": { /* Hazard assessment schema */ },
  "scores": { /* Multi-dimensional scoring schema */ },
  "roadmap": { /* Prioritized improvement schema */ },
  "frameworks_cited": ["string"],
  "confidence_level": "string",
  "caveats": ["string"],
  "next_review_date": "ISO date"
}
```

### Cross-Skill Delta Tracking
For benchmark/improvement loops across skills:
```json
{
  "baseline_assessment": { /* Unified report */ },
  "current_assessment": { /* Unified report */ },
  "dimension_deltas": [
    {
      "dimension": "string",
      "baseline_score": "number",
      "current_score": "number",
      "delta": "number",
      "improvement_actions": ["string"]
    }
  ],
  "overall_delta": "number",
  "effective_actions": ["string"],
  "remaining_gaps": ["string"]
}
```

## Integration Quality Gates

### For Reused Components:
- Input schema compatibility verified
- Quality gates preserved from original skill
- Clear attribution to source skill
- Documentation of any schema adaptations

### For Cross-Skill Outputs:
- Unified report format maintained
- Clear indication of contributing skills
- No conflicting recommendations
- Shared components version-tracked

### For Skill Orchestration:
- Handoff protocols documented
- Error handling at integration boundaries
- Graceful degradation if dependent skill unavailable
- User notification of skill interactions

## Reuse Implementation Guidelines

1. **When extracting a shared sub-skill:**
   - Identify the core workflow independent of domain specifics
   - Parameterize domain-specific elements
   - Create schema-agnostic input/output
   - Document quality gate preservation

2. **When importing a shared sub-skill:**
   - Verify schema compatibility
   - Adapt domain-specific references
   - Test with skill-specific scenarios
   - Document any modifications

3. **When composing multi-skill assessments:**
   - Establish clear handoff protocols
   - Coordinate scoring methodologies
   - Merge recommendations without conflict
   - Provide unified user experience

## Future Expansion Pathways

### Potential Cluster Skills:
- **water-security-planner** — Shares hazard assessment, supply calculation, and community coordination patterns
- **energy-resilience-advisor** — Reuse scoring engine, improvement roadmap, and constraint handling
- **food-security-assessor** — Common supply planning, resource constraints, and preservation methods

### Infrastructure Investments:
- Shared hazard database with API access
- Unified constraint satisfaction engine
- Common scoring calibration framework
- Cluster-wide recommendation prioritization algorithm

## Maintenance & Versioning

### Shared Component Versioning:
- Semantic versioning for shared schemas
- Change log for modifications
- Deprecation notice process
- Migration guides for breaking changes

### Integration Testing:
- Cross-skill scenario validation
- Schema compatibility regression tests
- End-to-end integration flows
- User experience consistency checks
