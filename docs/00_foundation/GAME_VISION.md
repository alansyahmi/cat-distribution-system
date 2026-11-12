# CaDS — Game Vision

- **Document ID:** DOC-FOUND-001
- **Version:** 0.2
- **Status:** Design foundation
- **Last updated:** 2026-11-13

## 1. Game identity

**Title:** Cat Distribution System  
**Short form:** CaDS  
**Tagline:** We deliver. You belong.  
**In-universe motto:** No cat left unassigned.

**Genre:** Feline-life simulation, narrative sandbox, exploration adventure  
**Player structure:** One actively controlled cat at a time; multiple playable cats may exist within a save  
**Structure:** Hybrid narrative and sandbox, with emergent play dominant  
**World:** Multiple seamlessly connected neighbourhood districts  
**Engine:** Godot 4  
**Initial target platforms:** PC and mobile  
**Visual direction:** Vibrant, hand-painted 3D storybook  
**Camera:** Flexible elevated/isometric-leaning camera, able to move closer for interactions and indoor spaces

## 2. High-concept promise

Play as a cat making a life in a living neighbourhood. Explore, observe, hunt for opportunities, interact with humans and animals, establish relationships, discover safe places, and decide what kind of life feels right.

CaDS should make the player feel feline—not like a human avatar wearing a cat model. The cat's body, senses, movement, instincts, vulnerabilities and social signals should shape how the world is navigated.

## 3. Central theme: belonging

The Cat Distribution System is the cultural premise: cats and people seem to find one another through coincidence, persistence and circumstance.

The game expands that premise. Being cared for can be wonderful, but independence, familiar territory, animal companionship and community can also be meaningful. The player's journey—provisionally called **The Choosing**—asks what home means to this particular cat.

Adoption may be an outcome, but it is not the universal win state. The game should avoid framing every independent cat as failed, or every human relationship as automatically benevolent.

## 4. Intended player experience

- **Curiosity:** What is beyond that fence, door or alley?
- **Mischief:** What happens if I knock this object over?
- **Attachment:** Does this person or animal recognise me?
- **Freedom:** Can I choose where and how I spend my time?
- **Discovery:** What routines, places and stories are hidden here?
- **Comfort:** Have I found somewhere that feels safe?
- **Consequence:** How did my behaviour change this neighbourhood's response to me?

## 5. World structure

The full game contains multiple interconnected districts that feel like one continuous neighbourhood. District streaming and background simulation may occur behind the scenes; seamless presentation does not require every district to remain fully loaded.

The conceptual spatial hierarchy is:

1. **District:** A broad neighbourhood area with its own population, routines, resources and character.
2. **Location:** A particular property, business, public space, outdoor area or other identifiable place.
3. **Space:** A traversable or occupiable sub-area, such as a room, garden, rooftop, counter or hiding spot.

Candidate district types include residential streets, commercial areas, back alleys, public parks and apartment complexes. These are candidates, not a locked content list.

Districts should differ through movement routes, traversal affordances, resources, human and animal populations, daily schedules, social norms, access conditions and narrative opportunities.

The first playable slice will use one compact, representative neighbourhood area.

## 6. Cats, households and place

Cats are persistent individuals with identities, personalities, life histories, relationships and lineage. NPC cats are not static decorations: they can form and leave households, establish residences, relocate, develop social relationships and reproduce autonomously.

A household is a social/living arrangement, not a synonym for biological family. Biological relationships persist when cats live separately. The player controls one cat at a time, while multiple playable cats may exist in a save.

A cat can have one primary residence and multiple secondary residences. A resting spot or shelter is not automatically a recognised home. Territory is fluid and experiential: familiarity, attachment and territoriality are distinct, and ordinary neighbourhood spaces can be shared.

## 7. Life simulation

CaDS uses a cozy-sandbox direction. Needs should shape mood and behaviour without making constant survival maintenance the dominant activity. Needs, environmental moodlets and overall mood are separate concepts; comfort is expressed through environmental moodlets rather than a standalone need.

Cats age automatically according to the world clock. Personality combines player-selected defining traits with tendencies that can emerge through repeated experience. Wants and Fears are dynamic short-term motivations; Aspirations express flexible, player-directed long-term life directions.

Natural reproduction is part of the simulation. The player can choose partners and initiate reproduction for the controlled cat; NPC cats may reproduce autonomously. Pregnancy, birth, kitten development and lineage are represented as actual cat entities and relationships.

The Nine Lives concept uses nine actual lives, with fatal incidents consuming a life and recovery taking place at a veterinary clinic. The interaction between natural old age and remaining lives is unresolved.

## 8. Neighbourhood and human society

The neighbourhood gradually evolves through a combination of scheduled events, autonomous NPC developments and player-influenced changes. New cats arrive through plausible natural turnover rather than constant random spawning.

Population uses soft ecological limits: crowding can increase resource and residential pressure, but the game should not abruptly prohibit births or erase cats to satisfy a target. Technical entity limits are a separate performance concern and must be handled through simulation tiers and graceful degradation.

Human NPCs have identities, personalities, routines, relationships, households and independent decisions, but their simulation is less detailed than the cats'. Humans can form individual relationships with cats and may independently care for, welcome, tolerate or avoid them.

Dedicated animal-welfare organisations, rescue networks, shelter operations, adoption-centre systems and community-programme management are deferred to a possible future expansion/DLC. They are not base-game requirements. A veterinary clinic remains relevant to the Nine Lives recovery mechanic.

## 9. Core gameplay shape

**Observe → Explore → Interact → Respond → Develop → Choose**

The player reads the environment, moves through it, acts on opportunities, experiences reactions, develops capabilities and relationships, and makes choices that influence future possibilities.

The loop is systemic rather than strictly sequential. Needs can prompt exploration; exploration can reveal social opportunities; social outcomes can change access; and access can expose new resources or risks.

## 10. Progression philosophy

Progression should deepen the player's options rather than turn the cat into a superhero.

Potential dimensions include physical capability and movement confidence; knowledge of routes, hiding places and routines; relationships with specific humans and animals; access to places and resources; possessions and personal territory; and shelter quality, comfort and security.

Progression should be legible through changed opportunities and behaviour, not only numerical levels.

## 11. Narrative philosophy

The narrative is hybrid: authored characters and story opportunities exist inside a world that continues to respond to player behaviour.

The main narrative should create direction without dictating every action. Side activities, routines, encounters and systemic consequences should make the world feel alive between major story beats.

The story should allow multiple credible ways of belonging, including a domestic life, an independent life, or a community-centred life. Specific endings and branching structures remain undecided.

## 12. Design and production constraints

Every major feature must state its player-facing purpose, authoritative state owner, prerequisites, affected systems, player feedback and acceptance criteria.

PC and mobile are target platforms, but feature parity and performance budgets must be validated through prototypes. Simulation density, input, camera, UI, memory, thermal load and save behaviour cannot be left until the end.

The world simulation must distinguish:
- **Entity existence:** A cat or human continues to exist even when not actively simulated.
- **Simulation detail:** Nearby actors receive detailed behaviour; distant actors use cheaper scheduled or abstract updates.
- **Presentation:** Rendering, animation and physics are activated only when needed.

## 13. Initial prototype promise

The first playable build should demonstrate one playable cat; one dense neighbourhood area; basic feline movement and interaction; a small set of needs and environmental resources; interactive objects and traversal affordances; a few human and animal NPCs with simple autonomous behaviours; relationships and observable reactions; at least one repeatable activity or small narrative opportunity; and persistence through save/load.

The prototype is successful if players can spend 15–20 minutes exploring and creating their own small stories, with understandable consequences, without requiring a scripted sequence to constantly direct them.

## 14. Explicitly unresolved

- Exact needs list, thresholds and time scale.
- Exact life-stage durations and natural lifespan.
- Whether natural death from old age consumes a Nine Lives life.
- Exact personality trait representation and development rules.
- Reproductive eligibility, pregnancy timing, and population safeguards.
- Detailed household stability and residence suitability calculations.
- Territorial memory decay and the scope of location-based memories.
- Population targets, technical entity budgets and background simulation fidelity.
- Human personality and relationship model detail.
- District count, layout, streaming boundaries and world scale.
- Narrative branches and endings.
- Progression pacing, PC/mobile controls and performance targets.
- Multiplayer or online features.

Resolve these through design analysis and targeted prototypes, not accidental implementation decisions.
