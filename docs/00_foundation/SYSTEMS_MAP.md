# CaDS — Gameplay Systems Map

- **Document ID:** DOC-ARCH-001
- **Version:** 0.1
- **Status:** Draft architecture

## 1. Architecture principles

1. **Clear ownership:** Every persistent gameplay fact has one authoritative owner.
2. **Composable behaviour:** Systems communicate through explicit events, queries or documented interfaces rather than hidden cross-dependencies.
3. **Simulation tiers:** Important nearby actors can simulate in detail; distant actors use cheaper abstract updates.
4. **Readable causality:** The player should infer important causes from world feedback.
5. **Data-driven content:** Characters, objects, activities and district definitions should be authored as data where practical.
6. **Honest prototyping:** The first slice proves core interactions, not the entire neighbourhood simulation.

## 2. System registry

| ID | System | Responsibility | Owns authoritative state for |
|---|---|---|---|
| SYS-CAT-001 | Cat Controller & Embodiment | Input, locomotion, posture, animation and feline traversal | Player movement and embodiment |
| SYS-NEED-001 | Needs & Wellbeing | Hunger, energy and approved needs; thresholds and recovery | Player need values and wellbeing |
| SYS-SENSE-001 | Perception & Awareness | Detect and prioritise stimuli; communicate awareness | Temporary perception results, not world truth |
| SYS-WORLD-001 | World & District Simulation | District topology, time, access and simulation tiers | World clock, district and access state |
| SYS-ENV-001 | Environment & Object Interaction | Object state, affordances, interaction conditions and outcomes | Object state and interaction availability |
| SYS-NPC-001 | NPC Behaviour & Schedules | Human/animal routines, goals, movement and decisions | NPC internal state and current behaviour |
| SYS-SOC-001 | Social Relationships & Reputation | Individual relationship dimensions and group reputation | Relationship and reputation records |
| SYS-ACT-001 | Activities & Narrative | Authored story beats, activities and conditional opportunities | Activity and narrative progression |
| SYS-PROG-001 | Progression & Knowledge | Skills, discoveries, access unlocks and long-term development | Player progression and knowledge |
| SYS-INV-001 | Inventory & Resources | Carried items, resource quantities and item use | Player-held inventory |
| SYS-UI-001 | Player Feedback & Interface | HUD, prompts, journal, maps and accessibility feedback | UI presentation state only |
| SYS-DATA-001 | Persistence & Save Data | Save schema, serialization, migrations and load validation | Serialized snapshots and version metadata |

## 3. System boundaries

### SYS-CAT-001 — Cat Controller & Embodiment
Converts player intent into cat movement and actions. It owns movement execution, not the rules for whether a target is socially receptive or food restores hunger.

### SYS-NEED-001 — Needs & Wellbeing
Owns need values and thresholds. It publishes events such as need threshold crossed or need recovered. It does not choose the route to food.

### SYS-SENSE-001 — Perception & Awareness
Produces context about detectable stimuli. Detection must be distinguished from knowledge: an NPC cannot react to information it has not perceived unless explicitly designed to do so.

### SYS-WORLD-001 — World & District Simulation
Owns world time, district membership, access and simulation update tiers. It coordinates what is active without owning detailed NPC behaviour or object interaction logic.

### SYS-ENV-001 — Environment & Object Interaction
Defines object affordances, state, interaction conditions and outcomes. A bowl may expose food; a box may provide hiding or resting; a bin may contain discoverable resources.

### SYS-NPC-001 — NPC Behaviour & Schedules
Owns individual NPC state and chooses behaviour from needs, schedules, goals, perception and social context. It requests interactions; it does not directly rewrite player relationship values.

### SYS-SOC-001 — Social Relationships & Reputation
Owns individual relationship dimensions and group reputation. Social changes should be caused by explicit events with context and source recorded where useful.

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
1. SYS-NPC-001 runs a human schedule and behaviour.
2. SYS-SENSE-001 determines whether the human notices the cat.
3. An interaction handler resolves the attempted approach.
4. SYS-NPC-001 selects a response based on personality and context.
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
- reputation_changed
- activity_unlocked
- discovery_recorded
- district_access_changed
- save_requested

Events should include stable actor/target IDs, world-time context, source system and outcome data where relevant. Avoid vague events such as something happened.

## 6. State and dependency rules

- A system may read another system's public state or query its interface; it should not silently mutate another system's authoritative data.
- Consequential cross-system changes pass through an owning system's API or event handler.
- Derived values require explicit recomputation or cache invalidation rules.
- Save data is versioned independently from runtime node layout.
- NPC simulation detail scales with relevance and distance, but important causal outcomes remain consistent across tiers.
- Do not create one monolithic GameManager that owns all gameplay state. A small coordinator may route events or manage lifecycle, while systems retain domain ownership.

## 7. Questions before full implementation

Resolve needs scope; perception versus interaction targeting; time behaviour during pause/backgrounding; off-screen simulation fidelity; relationship dimensions; Godot affordance representation; deterministic test fixtures; and minimum save boundaries/migrations.

The vertical slice may simplify these systems, provided simplifications are explicit and do not establish contradictory ownership.
