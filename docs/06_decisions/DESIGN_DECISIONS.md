# CaDS — Design Decisions

- **Document ID:** DOC-DEC-001
- **Version:** 0.2
- **Status:** Active decision log
- **Last updated:** 2026-11-13

This log distinguishes confirmed direction from proposals and unresolved questions. An idea is not a commitment until recorded as accepted. Dates indicate when the decision was recorded in the design process.

## 1. Confirmed foundations

| ID | Decision | Status | Rationale |
|---|---|---|---|
| DEC-001 | Official title is Cat Distribution System; shorthand CaDS | Accepted | Establishes project identity |
| DEC-002 | One cat is actively controlled at a time; multiple playable cats may exist in one save | Accepted | Focused moment-to-moment control while allowing family/legacy continuity |
| DEC-003 | Hybrid narrative and sandbox structure | Accepted | Direction without sacrificing emergent play |
| DEC-004 | Sandbox/emergent interactions dominate | Accepted | The world should generate player-driven stories |
| DEC-005 | Full game uses multiple interconnected districts | Accepted | Supports varied neighbourhood contexts |
| DEC-006 | Districts should feel seamlessly connected; streaming may occur behind the scenes | Accepted | Continuous world feel with scalable loading |
| DEC-007 | Initial target platforms are PC and mobile | Accepted target | Requires scalable simulation and adaptable input/UI |
| DEC-008 | Engine is Godot 4 | Accepted | Project technology choice |
| DEC-009 | Visual direction is vibrant hand-painted 3D storybook | Accepted direction | Establishes visual identity |
| DEC-010 | Flexible elevated/isometric-leaning camera with closer interaction and indoor views | Accepted direction | Balances readability and embodiment |
| DEC-011 | Adoption is a possible outcome, not a mandatory ending | Accepted | Belonging is not reduced to ownership |
| DEC-012 | Cat ageing is automatic and derived from the authoritative in-game world clock | Accepted | Supports consistent ageing, schedules and long-term simulation |
| DEC-013 | Personality uses a hybrid approach: player selects a few defining traits; other tendencies can emerge through repeated experience | Accepted | Combines player authorship with emergent character development |
| DEC-014 | Natural reproduction is supported, including mating, pregnancy, birth, kittens and family formation | Accepted | Enables family and generational simulation |
| DEC-015 | Player has full reproductive control for the controlled cat: can choose a partner and initiate reproduction; NPC cats may reproduce autonomously | Accepted | Explicit player agency alongside autonomous world simulation |
| DEC-016 | NPC cats can autonomously establish, join, split from and relocate between households | Accepted | Households are living social units, not static assignments |
| DEC-017 | Player influences NPC household decisions through relationships and interactions but does not directly manage NPC households | Accepted | Preserves NPC autonomy and player influence |
| DEC-018 | Household membership is distinct from biological family and lineage | Accepted | Family relationships persist across separate households |
| DEC-019 | Each settled cat has one primary residence and may have multiple secondary residences | Accepted | Distinguishes home from other recognised places |
| DEC-020 | Player can establish a flexible residence at almost any suitable location that meets basic requirements | Accepted | Supports domestic, independent and unconventional lifestyles |
| DEC-021 | Resting spots, shelters and residences are functionally distinct; a regular sleeping spot is not automatically a home | Accepted direction | Prevents home/residence concepts from collapsing |
| DEC-022 | Territorial boundaries are fluid, overlapping and experiential rather than strict invisible borders | Accepted | Supports coexistence and contextual territorial behaviour |
| DEC-023 | Familiarity, attachment and territoriality are separate concepts | Accepted direction | A cat can know a place without liking or defending it |
| DEC-024 | The world uses a district → location → space hierarchy | Accepted direction | Separates broad simulation from occupiable spaces |
| DEC-025 | Neighbourhood evolution is gradual, using scheduled, autonomous and player-influenced developments | Accepted | Gives the world continuity without turning it into a city simulator |
| DEC-026 | Population management uses soft ecological limits, not abrupt gameplay caps | Accepted | Population pressure should influence circumstances, not arbitrarily prohibit growth |
| DEC-027 | New cat arrivals follow natural turnover rather than frequent random spawning | Accepted | Preserves community continuity while allowing change |
| DEC-028 | Human NPCs have autonomous identities, personalities, routines, relationships and decisions, but less simulation depth than cats | Accepted | Supports a living human society while keeping CaDS feline-first |
| DEC-029 | Dedicated animal-welfare organisations and their operational management are deferred to a possible future expansion/DLC | Accepted scope decision | Protects base-game focus and production scope |
| DEC-030 | The base game retains the veterinary clinic role required by the Nine Lives recovery concept; institutional rescue/shelter/adoption management is not a base-game requirement | Accepted scope boundary | Preserves core recovery logic without importing the larger institutional ecosystem |
| DEC-031 | Repository begins public and may be made private later by the owner | Accepted current setup | Records the initial repository decision |

## 2. Confirmed direction requiring detailed design

These are accepted at the level stated, but their detailed mechanics remain open.

| ID | Direction | Still to specify |
|---|---|---|
| DIR-001 | Cozy sandbox; needs influence mood and behaviour without constant survival pressure | Final needs, thresholds, decay and tuning |
| DIR-002 | Needs, moodlets and overall mood are distinct; comfort is an environmental moodlet, not a standalone need | Full moodlet catalogue and calculation |
| DIR-003 | Wants and Fears follow a dynamic, Sims 2-like model; Aspirations are flexible long-term directions | Generation, fulfilment, rewards and UI |
| DIR-004 | Nine Lives are nine actual lives; fatal incidents consume a life and recovery takes place at a veterinary clinic | Fatality rules, costs, recovery presentation and natural old-age interaction |
| DIR-005 | At the ninth death, the player receives continuation choices including eligible biological heir, restart, save/exit/new cat, or another playable cat in the same save | Exact UI and save-state handling |
| DIR-006 | A legacy heir must be biologically related; an unrelated companion is not an heir | Eligible kinship range and selection rules |
| DIR-007 | Restart can offer a fresh personal life or a fresh start in the same neighbourhood | Exact reset/preservation matrix |
| DIR-008 | NPC simulation uses relevance-based tiers instead of full-detail simulation for every entity | Tier thresholds, update cadence and budgets |
| DIR-009 | Lightweight appearance inheritance is desirable; a full genetics simulator is not required for the initial design | Inheritance rules and controlled variation |

## 3. Working proposals (not locked)

| ID | Proposal | Rationale | Validation |
|---|---|---|---|
| PROP-001 | Main narrative concept is called The Choosing | Frames the cat's search for belonging | Narrative outline and prototype arc |
| PROP-002 | Core loop is Observe → Explore → Interact → Respond → Develop → Choose | Connects moment-to-moment and long-term agency | Playtest evidence |
| PROP-003 | Hunger and energy are the first needs | Simple motivation and pacing | Prototype shows they support rather than interrupt play |
| PROP-004 | First slice includes a few humans and two other cats | Tests social and animal interactions | Performance and interaction tests |
| PROP-005 | Relationship dimensions may include trust, familiarity, fear and attachment | Distinguishes social states | Behaviour design and player comprehension |
| PROP-006 | First slice contains one adoption opportunity | Tests the premise without requiring a full narrative system | Coherent interaction chain |
| PROP-007 | Five proposed life stages: newborn, kitten, adolescent, adult and senior | Gives age transitions behavioural significance | Validate durations and capabilities |
| PROP-008 | Six proposed continuous personality dimensions plus a discrete trait catalogue | Allows nuanced behavioural tendencies | Decide final representation and authoring model |
| PROP-009 | Residence suitability uses accessibility, shelter, resting space, safety and stability | Makes flexible homes legible without requiring food/water as mandatory residence gates | Prototype and tuning |
| PROP-010 | District carrying capacity is a dynamic ecological estimate influenced by resources and suitable habitat | Provides soft population pressure | Simulation tests and performance profiling |

## 4. Open questions

| ID | Question | Why it matters | Recommended next step |
|---|---|---|---|
| OPEN-001 | Which needs exist beyond hunger and energy? | Realism can become chores/UI complexity | Prototype the minimum model |
| OPEN-002 | Does natural death from old age consume a Nine Lives life? | Separates ageing from fatal-incident recovery | Decide mortality policy before implementing life loss |
| OPEN-003 | What are exact age-stage durations, lifespan and natural mortality rules? | Affects generations and long-term population | Define time scale and test a simulated lifespan |
| OPEN-004 | What is the final personality representation? | Affects authoring, behaviour and data model | Compare trait-only, dimensions-only and hybrid |
| OPEN-005 | How severe are injury, illness, exhaustion and capture? | Determines tone and failure states | Define emotional intensity and recovery |
| OPEN-006 | Is conflict avoidance, intimidation, chase or physical combat? | Affects rating, animation, AI and tone | Prefer readable non-lethal conflict unless justified |
| OPEN-007 | How are food and resources acquired? | Shapes economy and NPC reactions | Map resource sources and ownership |
| OPEN-008 | What are reproductive maturity, pregnancy duration and care rules? | Affects lifecycle plausibility and population | Define age gates and care arrangements |
| OPEN-009 | How autonomous are off-screen NPCs and households? | Major simulation and mobile cost | Define tier update rules and causal guarantees |
| OPEN-010 | What are residence suitability, capacity and relocation rules? | Affects households and population | Define minimum viable rules before implementation |
| OPEN-011 | How does territorial familiarity and location memory change over time? | Affects NPC behaviour and persistence | Define memory creation, decay and retrieval |
| OPEN-012 | How many districts exist and what are their topology/streaming boundaries? | Shapes world scale and performance | Prototype one connected district pair |
| OPEN-013 | What are narrative branches and endings? | Prevents systemic/narrative contradictions | Draft arcs after core systems validation |
| OPEN-014 | What are PC/mobile controls and performance targets? | Affects input, camera, UI and simulation | Build early control/performance test |
| OPEN-015 | Is multiplayer or online functionality in scope? | Could radically alter architecture and scope | Assume single-player for prototype; decide before networking |
| OPEN-016 | How persistent is simulation between sessions? | Affects schedules and mobile background behaviour | Define offline-time policy |
| OPEN-017 | What does a successful non-adoption ending look like? | Central to belonging theme | Write outcome principles before endings |
| OPEN-018 | What are the technical entity budgets and graceful-degradation rules? | Prevents soft ecological limits from becoming performance failures | Profile representative PC and mobile scenes |

## 5. Deferred expansion scope

The following are deliberately deferred and must not be treated as base-game requirements:
- Dedicated animal rescue organisations and rescue networks.
- Full animal shelter operations and staffing.
- Adoption-centre operations and management.
- Volunteer coordination and institutional funding.
- Community animal-welfare programme management.

This does not prohibit ordinary human NPCs from caring for, feeding, sheltering or adopting cats where those behaviours fit the base-game simulation. The institutional ecosystem is a future expansion direction.

## 6. Change control

When a decision changes:
1. Update this log with its ID and date.
2. State whether it supersedes an accepted decision or resolves an open question.
3. Update affected system and feature documents.
4. Check the dependency matrix and MVP scope for contradictions.
5. Record migration implications if implementation or save data already exists.

Do not silently turn a working proposal into a confirmed decision.
