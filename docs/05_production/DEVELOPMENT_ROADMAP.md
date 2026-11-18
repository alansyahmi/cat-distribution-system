# CaDS — Development Roadmap

- **Document ID:** DOC-PROD-002
- **Version:** 0.1
- **Status:** Initial production plan
- **Target strategy:** PC first; mobile later

## 1. Production strategy

CaDS will be developed through playable vertical slices. Each milestone must validate a meaningful part of the player experience before the project expands in content or simulation complexity.

The first production goal is not a miniature version of the whole game. It is a small, representative neighbourhood in which controlling a cat, exploring, interacting with objects and encountering a few inhabitants is enjoyable without requiring a scripted quest chain.

### Platform decision

- **Initial target:** Desktop PC.
- **Later target:** Mobile.
- **Architectural constraint:** Avoid unnecessary platform-specific coupling; keep input, UI scaling, rendering features and simulation budgets adaptable.
- **Do not optimise for mobile prematurely:** Mobile compatibility is a design constraint, not a reason to compromise the first PC prototype before its gameplay is validated.

## 2. Engine baseline

- **Engine:** Godot 4.7.2 Stable.
- **Language:** GDScript.
- **Renderer:** Forward+ for the initial desktop prototype.
- **Physics:** Godot 3D physics, initially using straightforward CharacterBody3D and StaticBody3D patterns where appropriate.
- **Version control:** Git; all meaningful changes occur on feature branches and are reviewed before merging.
- **Project configuration:** Commit project settings and source assets; exclude generated editor/import caches and local build output.

Do not adopt preview engine releases for the production project. Reconsider the engine version only through an explicit upgrade decision, with a backup and a tested migration.

## 3. Milestones

### M0 — Project foundation

**Purpose:** Establish a reproducible, runnable Godot project.

Scope:
- Project configuration and main testbed scene.
- Repository ignore rules.
- Agreed folder conventions.
- Versioned project setup instructions.
- Confirm project opens and runs in the pinned engine version.

Exit criteria:
1. A clean clone can be opened in Godot 4.7.2.
2. The main testbed scene runs without errors.
3. Generated editor/import cache is not committed.
4. The project can be launched from the editor and command line.

### M1 — Cat embodiment

**Purpose:** Make controlling a cat feel responsive and readable.

Scope:
- Player input abstraction.
- Ground movement, acceleration and deceleration.
- Turning and orientation.
- Jumping and landing.
- Camera follow, orbit, zoom and collision handling.
- Placeholder animation states and transitions.
- A greybox test area with walls, obstacles and simple height changes.

Exit criteria:
1. Movement is predictable and responsive.
2. Turning does not snap unnaturally.
3. Jump initiation, airborne movement and landing are readable.
4. Camera behaviour does not routinely obstruct navigation.
5. The controller handles walls, edges and slopes without frequent instability.
6. Movement values can be tuned without rewriting controller logic.

### M2 — Environmental affordances

**Purpose:** Make the world meaningfully interactive.

Scope:
- Interaction query/targeting.
- An explicit interaction contract.
- Object affordances and validation.
- Food, rest, hiding and perching test objects.
- Success, failure and interruption feedback.

Exit criteria:
1. The player can identify valid interactions.
2. Interactions validate range, access and actor capability.
3. Objects update their own authoritative state.
4. Failed interactions provide understandable feedback.

### M3 — Basic wellbeing and activity

**Purpose:** Turn needs into optional gameplay direction rather than chores.

Scope:
- Hunger and energy only.
- Food and rest recovery.
- Generous initial tuning.
- Basic activity opportunities.
- Clear visual/audio feedback.

Exit criteria:
1. Need changes have understandable causes.
2. Recovery is discoverable and reliable.
3. Needs do not dominate a short exploratory session.
4. UI does not own authoritative gameplay values.

### M4 — Living presence

**Purpose:** Make a small number of inhabitants feel independent.

Scope:
- Two NPC cats with limited autonomous behaviour.
- One or two human NPCs with simple routines.
- Basic perception and reaction.
- Small, testable behaviour state machines.

Exit criteria:
1. NPCs can act without direct player commands.
2. Reactions depend on perception and context.
3. NPC behaviour remains legible and recoverable.
4. Simulation does not require every distant actor to run full physics and animation.

### M5 — Social consequence

**Purpose:** Make repeated encounters matter.

Scope:
- Minimal individual relationship records.
- Recognition across encounters.
- A small number of observable relationship dimensions.
- Context-sensitive later reactions.

Exit criteria:
1. Repeated encounters can change later behaviour.
2. Relationship changes have identifiable causes.
3. Relationships are not represented by an unexplained single universal score.

### M6 — First playable vertical slice

**Purpose:** Validate a complete short session.

Scope:
- One compact neighbourhood block.
- Player cat, a few cat NPCs and human NPCs.
- Environmental interactions, hunger and energy.
- Minimal social recognition.
- One repeatable systemic activity.
- One optional adoption-related opportunity.
- Save/load for implemented persistent state.
- Basic accessibility, audio and performance profiling.

Exit criteria:
1. A player can explore for 15–20 minutes without a mandatory quest chain.
2. At least one unscripted sequence emerges from the systems.
3. The player can ignore the optional adoption opportunity.
4. Save/load restores implemented persistent state correctly.
5. A playtest identifies no critical controller, interaction or progression blockers.

## 4. Post-vertical-slice expansion

The following systems are part of the wider game direction, but must not block M0–M6:

- Full needs, moodlets, Wants, Fears and Aspirations.
- Ageing, Nine Lives and veterinary recovery.
- Reproduction, pregnancy, births and lineage.
- Dynamic households and multiple residences.
- Fluid territory and detailed location memory.
- More districts and seamless streaming.
- Population turnover and neighbourhood evolution.
- Advanced human autonomy.
- Large-scale simulation and mobile optimisation.

Dedicated animal-welfare organisations and institutional management remain deferred to a possible future expansion/DLC.

## 5. Engineering rules

1. **Playable increments:** Every milestone should leave the project runnable.
2. **Authoritative ownership:** Each persistent gameplay fact has one owning system.
3. **Data before duplication:** Repeated character, object and tuning definitions should become data-driven where this reduces coupling.
4. **Separate simulation from presentation:** Do not make distant NPC simulation depend on loaded 3D scenes.
5. **Explicit simplification:** Prototype shortcuts must be documented and must not contradict the intended ownership model.
6. **Measure before optimising:** Profile representative scenes before introducing complex optimisation infrastructure.
7. **Avoid speculative frameworks:** Build the smallest architecture that supports the current milestone and its known dependencies.
8. **Protect the playable loop:** New features must justify their cost against the current milestone's acceptance criteria.

## 6. Current status

- [x] PC-first platform strategy selected.
- [x] Godot 4.7.2 Stable selected as the initial engine baseline.
- [ ] Local project opened and validated.
- [ ] M0 accepted.
- [ ] M1 started.
