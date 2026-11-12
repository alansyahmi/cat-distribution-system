# CaDS — Gameplay Systems Map

- **Document ID:** DOC-ARCH-001
- **Version:** 0.2
- **Status:** Draft architecture
- **Last updated:** 2026-11-13

## 1. Architecture principles

1. **Clear ownership:** Every persistent gameplay fact has one authoritative owner.
2. **Composable behaviour:** Systems communicate through explicit events, queries or documented interfaces rather than hidden cross-dependencies.
3. **Simulation tiers:** Important nearby actors can simulate in detail; distant actors use cheaper abstract updates.
4. **Readable causality:** The player should infer important causes from world feedback.
5. **Data-driven content:** Characters, objects, activities, households and district definitions should be authored as data where practical.
6. **Honest prototyping:** The first slice proves core interactions, not the entire neighbourhood simulation.
7. **Identity/state separation:** Stable identity and history are distinct from frequently changing runtime state.
8. **World-time authority:** Age, schedules, pregnancy and long-term simulation derive from one authoritative world clock.

## 2. System registry

| ID | System | Responsibility | Owns authoritative state for |
|---|---|---|---|
| SYS-CAT-001 | Cat Controller & Embodiment | Input, locomotion, posture, animation and feline traversal | Player movement and embodiment |
| SYS-ID-001 | Character Identity & Life History | Stable cat/human identity, origin, lineage references and durable milestones | Identity and durable life-history records |
| SYS-LIFE-001 | Cat Life Simulation | Age stages, needs, moodlets, mood, Wants, Fears, Aspirations and reproductive state | Cat life-stage and life-simulation state |
| SYS-NEED-001 | Needs & Wellbeing | Need values, thresholds and recovery | Need values and wellbeing |
| SYS-SENSE-001 | Perception & Awareness | Detect and prioritise stimuli; communicate awareness | Temporary perception results, not world truth |
| SYS-WORLD-001 | World & District Simulation | World clock, district topology, location hierarchy, access, streaming and simulation tiers | World time, district/location topology and access state |
| SYS-ENV-001 | Environment & Object Interaction | Object state, affordances, interaction conditions and outcomes | Object state and interaction availability |
| SYS-PLACE-001 | Households, Residences & Territory | Household membership, residence assignment, place familiarity and territorial relationships | Household, residence and territory records |
| SYS-POP-001 | Population & Neighbourhood Evolution | Population pressure, arrivals, migration and persistent neighbourhood changes | Population/ecology aggregates and world-development records |
| SYS-NPC-001 | NPC Behaviour & Schedules | Human/animal routines, goals, movement and decisions | NPC internal state and current behaviour |
| SYS-HUMAN-001 | Human Society | Human identity, personality, household roles, occupation and human-cat caregiving decisions | Human-specific profile and routine state |
| SYS-SOC-001 | Social Relationships & Reputation | Individual relationship dimensions and group reputation | Relationship and reputation records |
| SYS-ACT-001 | Activities & Narrative | Authored story beats, activities and conditional opportunities | Activity and narrative progression |
| SYS-PROG-001 | Progression & Knowledge | Skills, discoveries, access unlocks and long-term development | Player progression and knowledge |
| SYS-INV-001 | Inventory & Resources | Carried items, resource quantities and item use | Player-held inventory |
| SYS-UI-001 | Player Feedback & Interface | HUD, prompts, journal, maps and accessibility feedback | UI presentation state only |
| SYS-DATA-001 | Persistence & Save Data | Save schema, serialization, migrations and load validation | Serialized snapshots and version metadata |

These are logical domains, not a mandatory one-script-per-system Godot architecture. A system may be implemented across multiple resources or services, provided state ownership and interfaces remain clear.

## 3. System boundaries

### SYS-CAT-001 — Cat Controller & Embodiment
Converts player intent into cat movement and actions. It owns movement execution, not the rules for whether a target is socially receptive or food restores hunger.

### SYS-ID-001 — Character Identity & Life History
Owns stable identifiers, names, origin, biological identity, appearance references, parent references and durable milestones. It should not own transient needs, current mood or current activity. Cat identity persists through household changes, relocation and player-control changes.

### SYS-LIFE-001 — Cat Life Simulation
Coordinates age-stage transitions, personality tendencies, Wants/Fears, Aspirations, memories and reproductive lifecycle state. It reads world time and emits events; it does not directly mutate household membership or relationship records.

### SYS-NEED-001 — Needs & Wellbeing
Owns need values and thresholds. It publishes events such as need threshold crossed or need recovered. Needs influence mood and behaviour but should not turn the cozy sandbox into constant survival maintenance. Comfort is not a standalone need; environmental comfort/discomfort is represented through moodlets.

### SYS-SENSE-001 — Perception & Awareness
Produces context about detectable stimuli. Detection must be distinguished from knowledge: an NPC cannot react to information it has not perceived unless explicitly designed to do so.

### SYS-WORLD-001 — World & District Simulation
Owns the authoritative world clock, district/location/space topology, access and simulation update tiers. It coordinates what is active without owning detailed NPC behaviour or object interaction logic. Seamless district presentation may use asynchronous streaming and hidden transitions.

### SYS-ENV-001 — Environment & Object Interaction
Defines object affordances, state, interaction conditions and outcomes. A bowl may expose food; a box may provide hiding or resting; a bin may contain discoverable resources.

### SYS-PLACE-001 — Households, Residences & Territory
Owns household membership and residence records, plus place familiarity and territorial data. Household membership is not biological lineage. Each settled cat has one primary residence and may have secondary residences; familiar locations and resting spots are not automatically residences. Territory is fluid, overlapping and individual rather than a rigid ownership boundary.

### SYS-POP-001 — Population & Neighbourhood Evolution
Owns population-level aggregates and persistent development events. It models soft ecological pressure and plausible natural turnover, not arbitrary deletion or hard gameplay birth prohibitions. Technical entity limits are enforced by simulation/performance infrastructure, not by falsifying population state.

### SYS-NPC-001 — NPC Behaviour & Schedules
Owns individual NPC behaviour and autonomous decisions. Cat NPCs can establish, join, split from and relocate between households. NPC cats can reproduce autonomously. Decisions should depend on needs, personality, relationships, memories, place, resources and opportunity.

### SYS-HUMAN-001 — Human Society
Owns human-specific identity, personality, routine, household roles and occupation data. Human simulation is autonomous but deliberately less detailed than feline simulation. Humans can independently make context-sensitive decisions about feeding, sheltering, welcoming, tolerating or avoiding cats. Dedicated institutional animal-welfare operations are deferred from the base game.

### SYS-SOC-001 — Social Relationships & Reputation
Owns individual relationship dimensions and group reputation. Social changes should be caused by explicit events with context and source recorded where useful. Human-cat relationships are asymmetric: each participant can evaluate the other differently.

### SYS-ACT-001 — Activities & Narrative
Owns authored activity and narrative progression. It can listen for systemic events but does not own hunger, object states, NPC schedules or relationship values.

### SYS-PROG-001 — Progression & Knowledge
Owns persistent discoveries, capabilities and access-related progression. It translates experience into new options only where justified.

### SYS-INV-001 — Inventory & Resources
Owns carried items and resource quantities. It is distinct from world object contents: taking food changes the source through SYS-ENV-001 and carried quantity through SYS-INV-001 if portable.

### SYS-UI-001 — Player Feedback & Interface
Reads gameplay state and events. It must not own gameplay rules or values.

### SYS-DATA-001 — Persistence & Save Data
Coordinates save/load and schema versioning. Systems expose serializable state through documented contracts. Transient effects, cached perception and derived UI state should not automatically be persisted.

## 4. Primary interaction flows

### A. Hunger leads to a food opportunity
1. SYS-NEED-001 updates hunger and publishes a threshold event.
2. SYS-SENSE-001 or player observation identifies possible food sources.
3. SYS-CAT-001 moves the cat to an accessible source.
4. SYS-ENV-001 validates and resolves the food interaction.
5. SYS-NEED-001 applies the wellbeing effect; SYS-ENV-001 updates source state.
6. SYS-NPC-001 may react if an NPC perceives the event.
7. SYS-SOC-001 records social consequences if warranted.
8. SYS-UI-001 communicates the result; SYS-DATA-001 persists relevant state.

### B. A human relationship develops
1. SYS-HUMAN-001 provides human profile and routine context.
2. SYS-NPC-001 runs the human's schedule and behaviour.
3. SYS-SENSE-001 determines whether the human notices the cat.
4. The interaction resolves according to context and individual disposition.
5. SYS-SOC-001 updates relationship dimensions from the resulting event.
6. SYS-ACT-001 may expose an opportunity if conditions are met.
7. SYS-UI-001 communicates the response through animation, audio and optional journal feedback.

### C. Exploration creates lasting knowledge
1. SYS-WORLD-001 exposes reachable topology and access rules.
2. SYS-CAT-001 traverses routes and affordances.
3. SYS-SENSE-001 supports observation and discovery.
4. SYS-PROG-001 records meaningful discoveries or learned routes.
5. SYS-ACT-001 may use discovery as an activity condition.
6. SYS-DATA-001 saves durable knowledge.

### D. A cat changes household or residence
1. SYS-NPC-001 or a player-mediated interaction produces a relocation/join/split decision.
2. SYS-PLACE-001 validates household and residence changes.
3. SYS-ID-001 retains identity and lineage; SYS-SOC-001 retains relationships.
4. SYS-POP-001 updates district population aggregates where required.
5. SYS-WORLD-001 updates district membership and access context.
6. SYS-DATA-001 persists the resulting state.

### E. Reproduction creates a new cat
1. SYS-LIFE-001 validates reproductive maturity and lifecycle conditions.
2. Player intent or autonomous NPC behaviour initiates the process.
3. Pregnancy and birth are represented as lifecycle events.
4. SYS-ID-001 creates a persistent identity for each kitten and records parent references.
5. SYS-PLACE-001 resolves household/care arrangements.
6. SYS-POP-001 updates population aggregates.
7. SYS-DATA-001 persists the new entities and lineage.

## 5. Initial event vocabulary

Names are provisional contracts, not implemented APIs:
- need_threshold_crossed
- need_recovered
- stimulus_detected
- interaction_started
- interaction_resolved
- object_state_changed
- npc_perceived_player
- npc_behaviour_changed
- relationship_changed
- household_membership_changed
- residence_changed
- territory_familiarity_changed
- life_stage_changed
- reproductive_state_changed
- cat_born
- cat_relocated
- neighbourhood_event_recorded
- activity_unlocked
- discovery_recorded
- district_access_changed
- save_requested

Events should include stable actor/target IDs, world-time context, source system and outcome data where relevant. Avoid vague events such as something happened.

## 6. State and dependency rules

- A system may read another system's public state or query its interface; it should not silently mutate another system's authoritative data.
- Consequential cross-system changes pass through an owning system's API or event handler.
- Derived values require explicit recomputation or cache invalidation rules.
- Age is derived from world time and birth time; do not maintain conflicting independently incremented age counters.
- Parent references are authoritative lineage links; offspring lists may be indexed/derived rather than duplicated as a second source of truth.
- Household membership, biological lineage, human ownership/care, residence assignment and territorial familiarity are distinct relationships.
- Save data is versioned independently from runtime node layout.
- NPC simulation detail scales with relevance and distance, but important causal outcomes remain consistent across tiers.
- Do not create one monolithic GameManager that owns all gameplay state. A small coordinator may route events or manage lifecycle, while systems retain domain ownership.

## 7. Questions before full implementation

Resolve exact needs and mood model; perception versus interaction targeting; time behaviour during pause/backgrounding; off-screen simulation fidelity; relationship dimensions; personality data representation; life-stage durations and old-age mortality; reproductive timing and eligibility; household suitability rules; territory memory decay; population and technical entity budgets; Godot affordance representation; deterministic test fixtures; and minimum save boundaries/migrations.

The vertical slice may simplify these systems, provided simplifications are explicit and do not establish contradictory ownership.
