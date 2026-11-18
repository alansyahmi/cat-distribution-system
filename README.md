# Cat Distribution System (CaDS)

> We deliver. You belong.

A feline-first 3D narrative sandbox about curiosity, mischief, relationships and the meaning of belonging. You play as one cat navigating a living neighbourhood, building a life through the choices you make and the connections you form.

**Engine:** Godot 4.7.2 Stable  
**Language:** GDScript  
**Initial target:** PC  
**Later target:** Mobile  
**Renderer:** Forward+ (initial desktop prototype)  
**Visual direction:** Vibrant, hand-painted 3D storybook  
**Status:** Project bootstrap / M0

## What is CaDS?

The Cat Distribution System is a familiar idea turned into a playable world: sometimes a cat finds a human; sometimes a human finds a cat. But belonging is not necessarily the same as ownership, and a home is not the only meaningful life a cat can build.

CaDS combines a directed narrative about **The Choosing** with a systemic sandbox. The player controls one cat at a time in a seamlessly connected neighbourhood made up of distinct districts. Cats and humans have persistent identities, relationships and routines; households can change; residences and territories develop through experience; and the neighbourhood gradually evolves.

The game is feline-first. Human society exists to make the cats' world believable and reactive, not to turn CaDS into a human life simulator. Adoption is one possible outcome—not a mandatory definition of success.

## Getting started

1. Install **Godot 4.7.2 Standard** (not the .NET build).
2. Clone this repository and check out the active development branch.
3. In Godot Project Manager, choose **Import** and select this repository's project.godot.
4. Open the project and run the main scene (F6/F5 or the Run Project button).

The initial main scene is a simple 3D embodiment testbed. It is intentionally a greybox environment; the player cat and controller have not been implemented yet.

**Engine policy:** Use the pinned stable version for project work. Do not open and resave the project in a preview release. Engine upgrades require an explicit decision and a tested migration.

## Development status

The project is being built through playable milestones. The current milestone is **M0 — Project foundation**. See [Development Roadmap](docs/05_production/DEVELOPMENT_ROADMAP.md) for scope and exit criteria.

## Design documentation

The documents in docs/ are the project's design source of truth. Confirmed decisions are distinguished from proposals and unresolved questions.

| Document | Purpose |
|---|---|
| [Game Vision](docs/00_foundation/GAME_VISION.md) | Identity, player promise, scope and foundational assumptions |
| [Design Pillars](docs/00_foundation/DESIGN_PILLARS.md) | Principles used to evaluate every feature |
| [Systems Map](docs/00_foundation/SYSTEMS_MAP.md) | System boundaries, responsibilities and cross-system relationships |
| [Core Gameplay Loop](docs/01_gameplay/CORE_GAMEPLAY_LOOP.md) | Moment-to-moment, session and long-term loops |
| [Feature Dependency Matrix](docs/01_gameplay/FEATURE_DEPENDENCY_MATRIX.md) | Feature prerequisites, outputs and dependencies |
| [Life & World Simulation](docs/02_simulation/LIFE_AND_WORLD_SIMULATION.md) | Cat identity, life cycle, households, residences, territory, population and human society |
| [Development Roadmap](docs/05_production/DEVELOPMENT_ROADMAP.md) | PC-first milestones and acceptance criteria |
| [Project Structure](docs/05_production/PROJECT_STRUCTURE.md) | Godot folder conventions and architecture boundaries |
| [MVP Scope](docs/05_production/MVP_SCOPE.md) | First playable vertical slice and acceptance criteria |
| [Design Decisions](docs/06_decisions/DESIGN_DECISIONS.md) | Confirmed decisions, rationale and unresolved questions |

## Repository conventions

1. Treat stable IDs such as SYS-CAT-001 and FEAT-INT-001 as cross-document references.
2. Update relevant system and dependency documents when a feature changes.
3. Record consequential decisions in the decision log rather than silently changing assumptions.
4. Keep confirmed decisions distinct from proposals and unresolved questions.
5. Do not implement a feature until its player purpose, dependencies, state ownership, feedback and acceptance criteria are understood.
6. Keep the base game focused. Deferred expansion ideas must not silently become MVP requirements.
7. Keep every milestone runnable and use feature branches for implementation work.

## Production direction

The first playable should prove that ordinary sandbox interactions can produce interesting consequences without relying on a long scripted sequence. Start with cat embodiment, then environmental affordances, basic wellbeing, NPC presence, social consequence and persistence.

All design documents are living drafts. They establish a coherent starting point, not a claim that every mechanic has been fully researched, balanced or technically validated.
