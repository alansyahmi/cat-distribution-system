# CaDS — Design Decisions

- **Document ID:** DOC-DEC-001
- **Version:** 0.1
- **Status:** Active decision log

This log distinguishes confirmed direction from proposals and unresolved questions. An idea is not a commitment until recorded as accepted.

## 1. Confirmed foundations

| ID | Decision | Status | Rationale |
|---|---|---|---|
| DEC-001 | Official title is Cat Distribution System; shorthand CaDS | Accepted | Establishes project identity |
| DEC-002 | One playable cat | Accepted | Focused player identity and attachment |
| DEC-003 | Hybrid narrative and sandbox structure | Accepted | Direction without sacrificing emergent play |
| DEC-004 | Sandbox/emergent interactions dominate | Accepted | The world should generate player-driven stories |
| DEC-005 | Full game uses multiple interconnected districts | Accepted direction | Supports varied neighbourhood contexts |
| DEC-006 | Initial target platforms are PC and mobile | Accepted target | Requires scalable simulation and adaptable input/UI |
| DEC-007 | Engine is Godot 4 | Accepted | Project technology choice |
| DEC-008 | Visual direction is vibrant hand-painted 3D storybook | Accepted direction | Establishes visual identity |
| DEC-009 | Flexible elevated/isometric-leaning camera with closer interaction and indoor views | Accepted direction | Balances readability and embodiment |
| DEC-010 | Adoption is a possible outcome, not a mandatory ending | Accepted | Belonging is not reduced to ownership |
| DEC-011 | Repository is initially public and may become private later | Accepted | Current repository setup |

## 2. Working proposals (not locked)

| ID | Proposal | Rationale | Validation |
|---|---|---|---|
| PROP-001 | Main narrative concept is called The Choosing | Frames the cat's search for belonging | Narrative outline and prototype arc |
| PROP-002 | Core loop is Observe → Explore → Interact → Respond → Develop → Choose | Connects moment-to-moment and long-term agency | Playtest evidence |
| PROP-003 | Hunger and energy are the first needs | Simple motivation and pacing | Prototype shows they support rather than interrupt play |
| PROP-004 | First slice includes a few humans and two other cats | Tests social and animal interactions | Performance and interaction tests |
| PROP-005 | Relationship dimensions may include trust, familiarity, fear and attachment | Distinguishes social states | Behaviour design and player comprehension |
| PROP-006 | First slice contains one adoption opportunity | Tests the premise without requiring a full narrative system | Coherent interaction chain |

## 3. Open questions

| ID | Question | Why it matters | Recommended next step |
|---|---|---|---|
| OPEN-001 | Which needs exist beyond hunger and energy? | Realism can become chores/UI complexity | Prototype the minimum model |
| OPEN-002 | How severe are injury, illness, exhaustion and capture? | Determines tone and failure states | Define emotional intensity and recovery |
| OPEN-003 | Is conflict avoidance, intimidation, chase or physical combat? | Affects rating, animation, AI and tone | Prefer readable non-lethal conflict unless justified |
| OPEN-004 | How are food and resources acquired? | Shapes economy and NPC reactions | Map resource sources and ownership |
| OPEN-005 | How autonomous are off-screen NPCs? | Major simulation and mobile cost | Define simulation tiers |
| OPEN-006 | How are districts unlocked and connected? | Shapes progression and topology | Define first district boundary |
| OPEN-007 | What are narrative branches and endings? | Prevents systemic/narrative contradictions | Draft arcs after core systems validation |
| OPEN-008 | Is progression numerical, capability-based, knowledge-based or mixed? | Affects motivation and balancing | Start with visible capability/knowledge changes |
| OPEN-009 | What are PC/mobile controls and performance targets? | Affects input, camera, UI and simulation | Build early control/performance test |
| OPEN-010 | Is multiplayer or online functionality in scope? | Could radically alter architecture and scope | Assume single-player for prototype; decide before networking |
| OPEN-011 | How persistent is simulation between sessions? | Affects schedules and mobile background behaviour | Define offline-time policy |
| OPEN-012 | What does a successful non-adoption ending look like? | Central to belonging theme | Write outcome principles before endings |

## 4. Change control

When a decision changes:
1. Update this log with its ID and date.
2. State whether it supersedes an accepted decision or resolves an open question.
3. Update affected system and feature documents.
4. Check the dependency matrix and MVP scope for contradictions.
5. Record migration implications if implementation or save data already exists.

Do not silently turn a working proposal into a confirmed decision.
