# Cat Distribution System (CaDS)

> We deliver. You belong.

A feline-first 3D narrative sandbox about curiosity, mischief, relationships and the meaning of belonging. You play as one cat navigating a living neighbourhood, building a life through the choices you make and the connections you form.

**Engine:** Godot 4  
**Initial platforms:** PC and mobile  
**Visual direction:** Vibrant, hand-painted 3D storybook  
**Status:** Pre-production / design foundation

## What is CaDS?

The Cat Distribution System is a familiar idea turned into a playable world: sometimes a cat finds a human; sometimes a human finds a cat. But belonging is not necessarily the same as ownership, and a home is not the only meaningful life a cat can build.

CaDS combines a directed narrative about The Choosing with a systemic sandbox. The player controls one cat and explores interconnected neighbourhood districts. Needs, curiosity, territory, social bonds, human routines, animal behaviour and environmental opportunities create situations that can be approached in different ways.

Adoption is one possible outcome—not a mandatory definition of success.

## Design documentation

The documents in docs/ are the project's design source of truth.

| Document | Purpose |
|---|---|
| [Game Vision](docs/00_foundation/GAME_VISION.md) | Identity, player promise, scope and foundational assumptions |
| [Design Pillars](docs/00_foundation/DESIGN_PILLARS.md) | Principles used to evaluate every feature |
| [Systems Map](docs/00_foundation/SYSTEMS_MAP.md) | System boundaries, responsibilities and cross-system relationships |
| [Core Gameplay Loop](docs/01_gameplay/CORE_GAMEPLAY_LOOP.md) | Moment-to-moment, session and long-term loops |
| [Feature Dependency Matrix](docs/01_gameplay/FEATURE_DEPENDENCY_MATRIX.md) | Feature prerequisites, outputs and dependencies |
| [Design Decisions](docs/06_decisions/DESIGN_DECISIONS.md) | Confirmed decisions, rationale and unresolved questions |
| [MVP Scope](docs/05_production/MVP_SCOPE.md) | First playable vertical slice and acceptance criteria |

## How to use this repository

1. Treat stable IDs such as SYS-CAT-001 and FEAT-INT-001 as cross-document references.
2. Update relevant system and dependency documents when a feature changes.
3. Record consequential decisions in the decision log rather than silently changing assumptions.
4. Keep proposals distinct from confirmed decisions.
5. Do not implement a feature until its player purpose, dependencies, state ownership, feedback and acceptance criteria are understood.

## Production direction

Design the gameplay architecture at a conceptual level, then implement a deliberately small vertical slice. The first prototype should prove that ordinary sandbox interactions can produce interesting consequences without relying on a long scripted sequence.

All design documents are living drafts. They establish a coherent starting point, not a claim that every mechanic has been fully researched, balanced or technically validated.
