# CaDS — Design Pillars

- **Document ID:** DOC-FOUND-002
- **Version:** 0.1
- **Status:** Draft foundation

Design pillars are decision filters. A feature that conflicts with a pillar must be redesigned, justified as a deliberate exception, or removed.

## P1 — A Cat, Not a Human in a Cat Costume

The player experiences the world through feline embodiment.

**Implications:** Movement, posture, senses, scale and access should feel cat-specific. The environment should contain opportunities designed around climbing, squeezing, hiding, perching, scent investigation and object play. Communication should rely heavily on posture, proximity, vocalisation and readable animal signals.

**Anti-patterns:** Human locomotion with a cat mesh; generic humanoid interactions; every interaction reduced to a context-free button prompt.

**Test:** Would this mechanic still work unchanged if the protagonist were human? If yes, what makes it meaningfully feline?

## P2 — A Living Sandbox

The neighbourhood should create situations through interacting systems, not only scripted events.

**Implications:** NPCs have routines, needs, goals and reactions appropriate to their importance. Objects and locations have consistent affordances and state. Player actions can affect future opportunities. Small systems combine to create unscripted stories.

**Anti-patterns:** A world that only reacts during missions; NPCs that reset without explanation; decorative objects that appear interactive but have no meaningful response.

**Test:** Can this feature combine with existing systems to produce more than one plausible outcome?

## P3 — Relationships Make the World Personal

The world should remember meaningful encounters and distinguish individuals.

**Implications:** Humans and animals recognise the player based on prior interactions. Trust, familiarity, fear, attachment and conflict are expressed through behaviour. Relationships are contextual and individual; one global affection score is insufficient.

**Anti-patterns:** One universal friendship meter; relationship changes without observable feedback; treating every human as an adoption dispenser.

**Test:** Does the player have a reason to care about this particular character?

## P4 — Freedom with Meaningful Consequences

The player should be free to improvise, but the world should respond consistently.

**Implications:** Multiple approaches should be viable where appropriate. Actions have understandable immediate and delayed consequences. Consequences create new situations, not simply punish experimentation. Avoid arbitrary failure states and invisible reputation changes.

**Anti-patterns:** One correct solution to every activity; random punishment disconnected from readable causes; consequence-free interaction spam.

**Test:** Can the player understand why the world responded this way, and can they adapt?

## P5 — A Neighbourhood Worth Exploring

Exploration should reward observation, curiosity and learning the environment.

**Implications:** Routes, vertical spaces, shelters and resources invite investigation. Districts have distinct routines, populations and affordances. Discoveries remain useful through knowledge, shortcuts, safety or relationships. The world feels welcoming and textured, even when it contains tension.

**Anti-patterns:** Large empty spaces; meaningless collectibles; districts differentiated only by palette or architecture.

**Test:** What can the player learn or discover here that changes how they experience the world?

## Cross-pillar quality gate

Before approving a major feature, document its pillar contribution, player value, system owner, dependencies, consequences, feedback and scope cost.

A feature should not be included merely because it is realistic or technically interesting. It must improve the player's experience of being a cat in this particular world.
