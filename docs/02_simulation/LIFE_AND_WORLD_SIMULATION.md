# CaDS — Life & World Simulation

- **Document ID:** DOC-SIM-001
- **Version:** 0.1
- **Status:** Design foundation; detailed mechanics remain in progress
- **Last updated:** 2026-11-13

This document consolidates the agreed direction for persistent cats, life simulation, households, residences, territory, neighbourhood evolution, population and human NPCs. It is a design reference, not an implementation specification.

## 1. Simulation priorities

CaDS is a feline-first cozy sandbox. Simulation exists to create understandable choices, relationships and emergent stories. It must not become a constant survival-management chore or a full human-life simulator.

Design priorities:
1. Preserve each cat as a persistent individual.
2. Make households and neighbourhoods capable of changing without player supervision.
3. Preserve continuity across birth, ageing, relocation, household changes and player-control changes.
4. Let places acquire meaning through experience.
5. Scale simulation detail to relevance and available hardware.
6. Keep the base game focused; defer large institutional systems to a possible expansion.

## 2. Cat entity, playable cat and active cat

These are separate concepts:

- **Cat entity:** Any individual cat that exists in the world and has a persistent identity.
- **Playable cat:** A cat the player is allowed to control within the current save.
- **Active cat:** The one playable cat currently under direct control.

Only one cat is actively controlled at a time. Multiple playable cats may exist in a save. NPC cats remain full world entities even when they are not playable.

Changing the active cat must not create or erase identity, lineage, relationships or life history.

## 3. Cat identity and life history

A cat's identity should persist independently of its current household, residence, district or player-control status.

### Stable identity
- Permanent unique Cat ID.
- Name and sex.
- Breed or mixed-breed classification.
- Appearance description/data: coat, colour, pattern, fur length, eye colour, body shape and markings.
- Birth time in the authoritative world-time domain.
- Origin, such as world-born, introduced, adopted or relocated.
- Biological parent references where known.

Breed and visible appearance are separate concepts. A mixed-breed cat can have a particular coat pattern, eye colour, fur length and body shape without those features being inferred from a single breed label.

### Durable life history
Record significant milestones and experiences rather than every trivial action. Examples include birth, adoption, household changes, major relationships, relocation, significant injuries, reproduction, death/revival and other consequential events.

### Current state is separate
Needs, moodlets, mood, current activity, temporary injuries, reproductive status and current location are changing state. They should not be embedded in an immutable identity record.

NPC cats and player cats should use the same core identity model.

## 4. Ageing and life stages

Ageing is automatic and based on one authoritative world clock.

**Derived age = current world time − birth time.**

Do not independently increment each cat's age counter. A shared clock supports save/load, births, multiple households, cat switching, NPC schedules and background simulation.

Five life stages are currently proposed:
1. **Newborn:** Dependent, limited mobility and care needs.
2. **Kitten:** Playful, learning and dependent.
3. **Adolescent:** Increasing independence and developing behavioural tendencies.
4. **Adult:** Full capabilities and reproductive eligibility, subject to final rules.
5. **Senior:** Age-related changes and potentially different activity preferences; not automatically helpless.

The stage list is a working model. Exact durations, lifespan, capabilities and natural mortality remain unresolved.

Ageing and Nine Lives are distinct concepts. A cat does not lose a life merely because it enters a new age stage. Whether natural death from old age consumes a remaining life is unresolved and must be decided before implementation.

## 5. Personality, motivation and emotion

### Personality
The accepted direction is hybrid:
- The player selects a small number of defining traits during character creation.
- Other tendencies can emerge through repeated experiences and meaningful events.
- Personality influences likelihoods, preferences and autonomous decisions; it does not dictate behaviour or remove player agency.

A proposed discrete trait catalogue includes Curious, Shy, Bold, Affectionate, Independent, Playful, Mischievous, Cautious, Territorial and Sociable. Proposed continuous dimensions include sociability, boldness, playfulness, curiosity, affection and territoriality. The final representation is unresolved.

### Distinct motivational layers
- **Core traits:** Relatively stable characteristics.
- **Developed tendencies:** Preferences and behavioural patterns emerging over repeated experience.
- **Wants:** Dynamic short-term desires.
- **Fears:** Dynamic anxieties or aversions.
- **Aspirations:** Flexible, player-directed long-term life directions.
- **Memories:** Experiences that can influence later emotion, motivation and behaviour.

Wants and Fears should respond to needs, mood, personality, relationships, memories, location and available opportunities. Aspirations are not permanent character classes; a cat may change direction without being treated as having failed.

### Needs, moodlets and mood
Needs, moodlets and overall mood are separate layers:
- Needs represent internal conditions.
- Moodlets represent contextual positive or negative influences.
- Overall mood summarises the cat's current emotional state.
- Behaviour and interaction selection can respond to these layers.

Comfort is not a standalone need. Environmental comfort or discomfort should be expressed through moodlets such as Warm Sunbeam, Soft Bedding, Wet Fur, Loud Construction or Disturbed Rest.

The confirmed design direction is cozy sandbox: needs influence mood and behaviour without constant punishment or overwhelming survival management. The final needs list is unresolved.

## 6. Nine Lives

Nine Lives represents nine actual lives, not nine symbolic chapters.

Current agreed direction:
- A cat begins with nine lives.
- Fatal incidents consume a life.
- A failed jump or ordinary mistake should not automatically consume a life; lesser consequences such as a fall, fright or temporary setback should be possible.
- Recovery after a life is lost takes place at a veterinary clinic.
- The clinic is the expected recovery location, not a context-sensitive nearby safe spot.
- At the ninth death, the player receives continuation choices rather than a conventional irreversible Game Over.

The continuation concepts include:
- Continue as an eligible biological heir.
- Restart the cat's life.
- Save/exit or create a new cat/save.
- Continue as another playable cat in the same save.

An heir must be biologically related to the deceased cat; an unrelated companion is not an heir. Eligible kinship range and exact restart/reset preservation rules remain to be specified.

The interaction between natural old-age mortality and remaining lives is unresolved.

## 7. Reproduction and lineage

Natural reproduction is supported, including mating, pregnancy, birth, kittens and family formation.

Player control is explicit:
- The player can choose a reproductive partner for the controlled cat.
- The player can initiate reproduction.
- NPC cats can reproduce autonomously.

The simulation should enforce reproductive maturity and other eligibility rules, which remain to be detailed. Pregnancy is a temporary lifecycle state with an expected birth event. Birth creates individual cat entities, each with a persistent Cat ID, birth information and parent references.

Lineage is permanent even when family members live in different households or districts. Household membership is not a substitute for biological family. Lightweight appearance inheritance is a future design direction; a full genetics simulator is not required.

Kitten care arrangements may differ across domestic households, independent/stray families and multi-cat households. Detailed care, vulnerability and population safeguards remain unresolved.

## 8. Households

A household is a social and living arrangement, not a biological family.

NPC cats can autonomously:
- Establish new households.
- Join existing households.
- Split from current households.
- Relocate between residences and districts.

The player influences NPC household decisions through relationships and interactions, but does not directly manage NPC households.

Possible household arrangements include:
- Human household with one or more cats.
- Cat family.
- Unrelated cats sharing a shelter or residence.
- Independent cat without a formal household.
- Mixed household with biological relatives living alongside unrelated cats.

Biological relationships persist when cats live separately. Household membership and lineage must be stored as distinct relationships.

Household resources, stability, care arrangements and soft capacity are relevant design dimensions, but their exact calculations remain unresolved.

## 9. Residences and place

### Place hierarchy
The world uses three conceptual spatial levels:
1. **District:** Broad neighbourhood area.
2. **Location:** A house, shop, park, alley, property or other identifiable place.
3. **Space:** A room, garden, rooftop, counter, hiding place or other occupiable sub-area.

### Resting spot, shelter and residence
These are functional classifications:
- **Resting spot:** A place where a cat can sleep or rest.
- **Shelter:** A place offering some protection from weather, danger or disturbance.
- **Residence:** An established home with regular occupation, recognised access and suitable living conditions.

One physical place may serve more than one function. A shelter can become a residence through sustained occupation and suitable circumstances.

### Residence arrangement
A settled cat has:
- One primary residence.
- Zero or more secondary residences where it is welcome to stay.
- Other familiar locations that are not residences.

A sleeping spot is not automatically a residence. A residence should represent a more established living arrangement.

### Flexible player residence
The player can establish almost any suitable location as a home, subject to basic requirements. Proposed requirements:
- Accessibility.
- Some shelter/protection.
- Suitable resting space.
- Sufficient perceived safety.
- Reasonable stability/continuity.

Food and water are desirable but should not be mandatory gates, otherwise independent cats would be forced into a narrow definition of home.

### Access and capacity
Access can be Welcomed, Tolerated, Restricted or Inaccessible. Physical accessibility and social permission are distinct. Residence capacity should be soft and contextual, based on space, resources, environmental conditions and compatibility rather than a universal hard occupancy number.

## 10. Territory and location memory

Territorial boundaries are fluid, overlapping and experiential—not strict invisible property lines.

Keep three concepts separate:
- **Familiarity:** How well the cat knows a location.
- **Attachment:** How much the cat likes or values a location.
- **Territoriality:** How strongly the cat tends to claim or defend a location.

A cat may know a veterinary clinic well but dislike it. Another may love a garden without defending it from other cats.

Familiarity can develop through repeated visits, resting, eating, drinking, social encounters, exploration and significant events. Location attachment can reflect positive or negative experiences.

Territorial behaviour should be contextual. Reactions depend on personality, relationships, location familiarity, resources, mood, fears and prior encounters. Entering a familiar place should not automatically trigger aggression.

Location-based memories are a design direction: a cat may remember where it met a companion, experienced danger, grew up or regularly watched birds. Memory scope, decay and retrieval rules remain unresolved.

## 11. Neighbourhood structure and evolution

Districts should feel like one continuous neighbourhood. Streaming or loading can occur behind the scenes to support PC and mobile performance.

Neighbourhood evolution is gradual, not a city-building simulation. Changes may include:
- Commercial: businesses open, close, renovate or change ownership.
- Residential: households arrive, leave, split, merge or relocate.
- Community: public spaces and shared resources improve or deteriorate.
- Infrastructure: construction and maintenance change routes and access.

Development can come from scheduled events, autonomous developments and player-influenced developments. Important changes should have understandable causes and be retained as world history. Do not persist every trivial animation or temporary visual effect.

## 12. Population and natural turnover

Population management uses **soft ecological limits**.

A district's comfortable carrying capacity is an approximate, dynamic estimate influenced by suitable shelter, food, water, habitat, household resources and human activity. Exceeding it creates gradual contextual pressure rather than abruptly prohibiting births or deleting cats.

Possible effects include resource competition, reduced suitable shelter, social pressure, household changes and migration. These are not automatic punishments; context matters. A dense district with reliable resources and tolerant social relationships may remain viable.

New cat arrivals follow natural turnover rather than frequent random spawning. Plausible origins include:
- Born locally.
- Relocated from another district or neighbourhood.
- Introduced through human activity, such as adoption, abandonment or a new resident moving in.

New arrivals should have identities and plausible histories. They should integrate through exposure, familiarity, compatibility, interactions and social context rather than being automatically accepted or rejected.

Technical entity limits are separate from ecological limits. Use simulation tiers, scheduled updates and graceful degradation; do not silently erase persistent cat entities to meet a performance target.

## 13. Human NPC society

Human NPCs have persistent identities, personalities, routines, relationships, households and independent decisions. Their simulation is less detailed than feline simulation.

Human profiles may include identity, age, appearance, personality, relationships, household, occupation, routine, attitude towards cats and significant life history.

Human-cat relationships are individual and asymmetric. A cat may trust one household member, tolerate another and avoid a third. A human may adore a cat that barely tolerates them. Familiarity, trust, affection and reliability are candidate dimensions, not a final locked schema.

Humans can make context-sensitive decisions to feed, shelter, welcome, tolerate, avoid, care for or adopt cats. Human behaviour should depend on personality, familiarity, resources, time, prior experiences and household circumstances.

### Deferred institutional ecosystem

Dedicated animal-welfare organisations, rescue networks, full shelter operations, adoption-centre operations, volunteer coordination and community-programme management are deferred to a possible future expansion/DLC. They are not base-game requirements.

The base game may still contain ordinary human-cat care behaviours where appropriate. The veterinary clinic remains part of the core world concept because it supports Nine Lives recovery.

## 14. Simulation tiers

Entity existence is independent of active simulation. Recommended conceptual tiers:

- **Active:** Full movement, perception, animation, interactions and behaviour for the player and relevant nearby actors.
- **Nearby:** Simplified behaviour and interactions for actors in the surrounding area.
- **Background:** Scheduled activities, household decisions and important state changes without continuous physics or navigation.
- **Dormant:** Minimal processing; preserve identity and important state, then resume when relevant.

The exact tier thresholds, update cadence and population budgets must be measured on representative PC and mobile hardware.

## 15. Technical design guardrails

- Use stable IDs for cats, humans, households, residences, districts and important world events.
- Separate stable identity, durable history, relationships and mutable current state.
- Derive age from birth time and world time.
- Keep lineage separate from household membership.
- Keep household membership separate from residence assignment and human care/ownership.
- Treat familiarity, attachment and territoriality as distinct data.
- Avoid simulating distant actors with continuous physics, animation or pathfinding.
- Persist consequential changes; avoid saving every ephemeral visual detail.
- Use versioned save data and explicit migration rules.
- Treat all numeric thresholds, lifespans, capacities and simulation budgets as unvalidated until tested.

## 16. Outstanding design work

This document does not settle exact needs, mood calculation, life-stage durations, old-age mortality, personality representation, reproductive timing, household suitability, territory memory decay, district topology, population budgets, human relationship dimensions or offline-time behaviour. These remain open design tasks and should be resolved before the affected systems are implemented.
