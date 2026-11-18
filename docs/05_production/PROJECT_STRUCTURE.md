# CaDS — Godot Project Structure

- **Document ID:** DOC-TECH-001
- **Version:** 0.1
- **Status:** Initial convention

## 1. Principles

- Organise files by domain and purpose, not by arbitrary technical type alone.
- Keep reusable scenes, scripts and resources close to the domain that owns them.
- Keep testbeds separate from production scenes.
- Avoid a monolithic global manager.
- Do not create folders or abstractions before they have a real use.
- Godot scene nodes are presentation/runtime objects; persistent game identity and simulation data should not depend on fragile scene-tree paths.

## 2. Intended layout

~~~text
cat-distribution-system/
├── project.godot
├── README.md
├── .gitignore
├── assets/
│   ├── audio/
│   ├── fonts/
│   ├── materials/
│   ├── models/
│   └── textures/
├── scenes/
│   ├── testbeds/
│   ├── actors/
│   │   ├── cats/
│   │   └── humans/
│   ├── environment/
│   ├── world/
│   └── ui/
├── scripts/
│   ├── core/
│   ├── actors/
│   │   ├── cats/
│   │   └── humans/
│   ├── systems/
│   ├── world/
│   ├── interactions/
│   └── ui/
├── resources/
│   ├── cats/
│   ├── humans/
│   ├── interactions/
│   └── world/
├── tests/
│   ├── unit/
│   └── integration/
└── docs/
    ├── 00_foundation/
    ├── 01_gameplay/
    ├── 02_simulation/
    ├── 05_production/
    └── 06_decisions/
~~~

This is the intended destination, not a requirement to create every directory immediately. Add a directory when the first real file needs it.

## 3. File conventions

- Use snake_case for file and directory names.
- Use PascalCase for named Godot classes and scene root nodes.
- Prefer one primary class_name per script, and only expose a global class when other domains genuinely need it.
- Use typed GDScript for public interfaces and state contracts.
- Keep tuning values in resources/configuration when designers need to adjust them.
- Keep temporary test content in scenes/testbeds/ and remove or promote it deliberately.
- Avoid deeply nested folders for one-file categories.

## 4. Runtime and data boundaries

- **Scenes:** compose nodes and presentation.
- **Scripts:** implement behaviour and domain logic.
- **Resources:** hold reusable authored definitions and tuning.
- **Assets:** hold source art, audio and imported media.
- **Tests:** verify logic and cross-system contracts.
- **Docs:** explain design intent, ownership and acceptance criteria.

Do not store persistent cat identity solely in a Node's name, node path or transient scene instance. Stable IDs and serializable records will be introduced when the relevant gameplay systems are implemented.

## 5. Autoload policy

Do not add a global singleton merely because a system is important. An autoload is justified only when a service has genuinely application-wide lifetime and a clear, narrow responsibility (for example, later save orchestration or world-time coordination).

Any proposed autoload must document:
- Its authoritative state, if any.
- Its public API.
- Which systems depend on it.
- Why scene-local or explicitly injected ownership is insufficient.

The first project bootstrap intentionally has no custom autoloads.
