# CaDS — Feature Dependency Matrix

- **Document ID:** DOC-GAME-002
- **Version:** 0.2
- **Status:** Draft; dependencies are conceptual until validated.
- **Last updated:** 2026-11-13

This document makes feature relationships explicit. A feature is not implementation-ready merely because it appears in a list.

## 1. Feature registry

| Feature ID | Feature | Primary owner | Requires | Produces / affects |
|---|---|---|---|---|
| FEAT-CAT-001 | Basic feline locomotion | SYS-CAT-001 | Input, collision, navigation geometry | Position and movement state |
| FEAT-CAT-002 | Jump, climb and squeeze affordances | SYS-CAT-001 / SYS-ENV-001 | Traversal geometry, affordance queries | New reachable routes |
| FEAT-ID-001 | Persistent cat identity | SYS-ID-001 | Stable ID generation, identity schema | Durable individual identity |
| FEAT-ID-002 | Lineage and life-history records | SYS-ID-001 | Cat identity, lifecycle events | Parent references and durable milestones |
| FEAT-LIFE-001 | Automatic ageing | SYS-LIFE-001 / SYS-WORLD-001 | Authoritative world clock, birth time | Derived age and life-stage transitions |
| FEAT-LIFE-002 | Personality and emerging tendencies | SYS-LIFE-001 | Character profile, repeated experience | Behavioural preferences and tendencies |
| FEAT-LIFE-003 | Wants, Fears and Aspirations | SYS-LIFE-001 | Needs, mood, personality, memories, opportunities | Dynamic motivation and long-term direction |
| FEAT-LIFE-004 | Natural reproduction | SYS-LIFE-001 | Reproductive maturity, partner choice, lifecycle rules | Pregnancy, births and lineage events |
| FEAT-NEED-001 | Hunger | SYS-NEED-001 | Time/update policy, tuning | Food-seeking motivation |
| FEAT-NEED-002 | Energy and rest | SYS-NEED-001 | Time/update policy, rest affordances | Activity pacing and recovery |
| FEAT-NEED-003 | Moodlets and overall mood | SYS-LIFE-001 | Needs, environment, memories and events | Behavioural/emotional context |
| FEAT-SENSE-001 | Nearby stimulus detection | SYS-SENSE-001 | Sensory sources, range and occlusion rules | Awareness candidates |
| FEAT-ENV-001 | Interactable object framework | SYS-ENV-001 | Stable object IDs, interaction contract | Validated interaction outcomes |
| FEAT-ENV-002 | Food source interactions | SYS-ENV-001 | Object framework, food data, hunger | Food consumed/acquired; source state |
| FEAT-ENV-003 | Resting and hiding places | SYS-ENV-001 | Object framework, cat affordances | Recovery, concealment or safety |
| FEAT-WORLD-001 | District/location/space topology | SYS-WORLD-001 | World data and stable location IDs | Reachability and spatial hierarchy |
| FEAT-WORLD-002 | Seamless district streaming | SYS-WORLD-001 | District topology, streaming and memory budgets | Continuous-feeling traversal |
| FEAT-PLACE-001 | Dynamic household membership | SYS-PLACE-001 | Cat/human identity, social and lifecycle events | Household formation, joining, splitting and departure |
| FEAT-PLACE-002 | Primary and secondary residences | SYS-PLACE-001 | Residence records, access and suitability | Recognised living places |
| FEAT-PLACE-003 | Flexible player residence establishment | SYS-PLACE-001 | Accessibility, shelter, rest, safety and stability | Player-designated primary residence |
| FEAT-PLACE-004 | Fluid territorial familiarity | SYS-PLACE-001 | Location visits, memories and personality | Familiarity, attachment and territorial response |
| FEAT-POP-001 | Soft ecological population pressure | SYS-POP-001 | Resources, shelter, district and household state | Contextual crowding and migration pressure |
| FEAT-POP-002 | Natural population turnover | SYS-POP-001 | Births, relocation, adoption/arrival events | Plausible arrivals and changing population |
| FEAT-POP-003 | Gradual neighbourhood evolution | SYS-POP-001 / SYS-WORLD-001 | Persistent world events and authored data | Long-term district changes |
| FEAT-NPC-001 | NPC schedules | SYS-NPC-001 | World clock, schedule data | NPC location and routine state |
| FEAT-NPC-002 | Basic human reactions | SYS-NPC-001 / SYS-HUMAN-001 | Perception, interaction events, human profile | Human responses |
| FEAT-NPC-003 | Basic animal behaviour | SYS-NPC-001 / SYS-LIFE-001 | Perception, needs/goals, movement | Animal responses and encounters |
| FEAT-HUMAN-001 | Autonomous human profiles and routines | SYS-HUMAN-001 | Human identity, world clock, household | Human schedules and independent decisions |
| FEAT-HUMAN-002 | Individual human-cat relationships | SYS-SOC-001 | Human and cat identities, interaction events | Asymmetric familiarity, trust and attachment |
| FEAT-SOC-001 | Individual relationship dimensions | SYS-SOC-001 | Actor IDs, interaction outcome events | Trust/familiarity/fear or other approved dimensions |
| FEAT-SOC-002 | Recognition and memory | SYS-SOC-001 / SYS-NPC-001 | Relationship records, encounter history | Context-aware reactions |
| FEAT-ACT-001 | Activity opportunity conditions | SYS-ACT-001 | World state and event subscriptions | Available activity opportunities |
| FEAT-PROG-001 | Discovery and route knowledge | SYS-PROG-001 | Exploration/perception events | Persistent knowledge and shortcuts |
| FEAT-UI-001 | Contextual interaction feedback | SYS-UI-001 | Interaction result contract | Clear player feedback |
| FEAT-DATA-001 | Save/load core state | SYS-DATA-001 | Stable IDs, serialization contracts | Persistent session continuity |

## 2. Critical dependency chains

### Chain A — Needs become meaningful gameplay

Hunger → stimulus detection/player observation → locomotion → interactable framework → food source interaction → hunger recovery and source state change → optional NPC perception/reaction → optional social consequence.

**Key point:** Hunger alone is only a meter. It becomes gameplay when the player can perceive, reach, interact with and experience consequences around food sources.

### Chain B — Social relationships become systemic

NPC schedules → NPC presence in a world context → perception → human reaction → interaction outcome → relationship update → recognition → future reaction or activity opportunity.

**Key point:** A relationship score without repeated recognition and changed behaviour is not a relationship system.

### Chain C — Exploration becomes lasting progress

Traversal and observation → discovery candidate → persistent route knowledge → shortcut, access, safer route or new activity condition → future exploration becomes meaningfully different.

### Chain D — Life events create persistent individuals

World clock + birth time → age/life-stage transition → lifecycle event → identity/history update → household and social consequences → persistence.

### Chain E — Household and residence changes remain coherent

NPC/player decision → household validation → residence/access update → district population update → preserved identity, lineage and relationships → save.

### Chain F — Reproduction creates a new cat

Reproductive maturity + player intent or autonomous NPC decision → partner selection → pregnancy → birth event → new cat identity and parent references → household/care arrangement → population update.

## 3. Dependency and ownership rules

- A feature may depend on multiple systems, but one primary owner must be named.
- Cross-system effects use explicit result objects or events.
- UI consumes gameplay state; it is never the source of truth.
- Save/load depends on stable identifiers and state contracts, not arbitrary scene-tree serialization as the long-term data model.
- NPC schedules depend on world time; reactions depend on perception and context; relationships depend on resolved events, not raw input.
- Age is derived from world time and birth time, not incremented independently for every cat.
- Household, lineage, residence, care/ownership and territory must not be collapsed into one relationship field.
- A feature is not complete until downstream consequences and failure cases are tested.

## 4. MVP implementation order

1. Stable scene/world setup and basic cat movement.
2. Interaction targeting and object affordance contract.
3. Hunger and energy with time/update rules.
4. Food and rest objects with state changes.
5. Minimal NPC perception and reactions.
6. Minimal relationship memory with visible behavioural consequences.
7. One repeatable activity opportunity.
8. Save/load for implemented state.
9. Feedback, accessibility and performance pass.

The broader life and neighbourhood systems in this matrix are not all MVP commitments. Their presence here documents intended architecture and dependencies; MVP inclusion is governed by `docs/05_production/MVP_SCOPE.md`.

## 5. Feature readiness checklist

Before implementation, add player-facing behaviour and non-goals; primary system owner; required state and stable IDs; prerequisites and downstream effects; success/failure/interruption outcomes; player feedback; persistence requirements; acceptance tests; and performance implications for PC and mobile.
