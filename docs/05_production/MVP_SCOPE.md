# CaDS — MVP / First Playable Scope

- **Document ID:** DOC-PROD-001
- **Version:** 0.1
- **Status:** Draft scope proposal

## 1. Purpose

The first playable build is a vertical slice, not a miniature version of the entire game. It should prove that CaDS's central systems can create a satisfying short session.

**Test question:** Can a player spend 15–20 minutes as a cat, freely exploring a compact neighbourhood, interacting with its inhabitants and objects, and experiencing understandable consequences—without depending on a scripted sequence to keep play interesting?

## 2. Included

### Player cat
- One controllable cat.
- Basic movement, turning, jumping and context-sensitive interaction.
- A small set of readable feline animations and postures.
- Camera supporting navigation and close interaction.

### World
- One compact, dense neighbourhood block or connected sub-area.
- Ground-level and limited vertical routes.
- A few interiors or sheltered spaces only if they add meaningful interactions.
- Clear landmarks, hiding places and traversal affordances.

### Needs and resources
- Hunger and energy only, subject to prototype validation.
- At least one food source with state that changes when used.
- At least one resting location with a meaningful recovery effect.
- No elaborate currency or crafting economy.

### Objects and interactions
- A small set of functional objects such as a food bowl, rubbish bin, cardboard box, bench or furniture.
- At least one hiding affordance and one elevated/perch affordance.
- Contextual feedback for success, failure and interruption.

### NPCs
- A few human NPCs with simple schedules or routine states.
- Two other cats with basic autonomous behaviours.
- NPCs can notice the player under defined conditions and respond differently based on context.

### Social system
- Minimal individual relationship state for at least one human and one animal.
- At least two distinguishable relationship dimensions only if they lead to different observable behaviours.
- Recognition across repeated encounters.

### Activity and narrative
- At least one repeatable systemic activity or small narrative opportunity.
- One optional adoption-related opportunity to test the premise.
- The player can ignore the opportunity and continue sandbox play.

### Persistence
- Save/load player location, needs, relevant object states, relationship state and activity progress.
- Versioned save format, even if the first schema is small.

## 3. Explicitly excluded

Multiple fully developed districts; full main story and all endings; large quest chains or branching dialogue trees; full survival simulation or many needs; complex combat; full animal ecology or breeding; large crowds and city-scale simulation; online features or multiplayer; elaborate economy, crafting or housing decoration; full mobile optimisation and platform certification.

Excluded does not mean permanently rejected. It means the feature must not block validation of the first playable loop.

## 4. Prototype sequence

A. **Embodiment:** Prove cat movement, camera, collision, traversal and basic animation in a greybox area.  
B. **Affordances:** Add stable interactable objects, targeting, food/rest outcomes and feedback.  
C. **Motivation:** Add hunger and energy with tuning that encourages choices without becoming a chore.  
D. **Living presence:** Add a small number of NPC routines, perception and reactions.  
E. **Social consequence:** Add minimal relationship memory and demonstrate repeated encounters changing behaviour.  
F. **Persistence and polish:** Add save/load, feedback, basic accessibility and performance profiling.

Each slice should remain playable and testable. Do not add more content to conceal weaknesses in the underlying loop.

## 5. Acceptance criteria

The vertical slice is accepted only when:
1. The player moves around the test area without frequent camera or collision failures.
2. The player identifies and uses at least three distinct environmental affordances.
3. Hunger and energy have understandable effects and recovery paths.
4. Food/rest interactions update the correct owning system and world object state.
5. At least two NPCs perceive and react to the player in context.
6. Repeated interaction with at least one NPC changes a later response visibly.
7. At least one unscripted sequence emerges from needs, objects and NPC behaviour.
8. The player can ignore the optional adoption opportunity without becoming blocked.
9. Save/load restores implemented persistent state without duplication or loss.
10. A 15–20 minute exploratory session remains interesting without a mandatory quest chain.
11. No critical gameplay state is owned only by UI or a monolithic global manager.
12. The slice is profiled on a representative PC and mobile device before platform commitments expand.

## 6. Evidence to collect

Playtest notes on exploration, hesitation and confusion; interaction success/failure and common causes; time spent on needs versus free exploration; NPC recognition comprehension; save/load test results; frame time, memory and thermal observations on target devices.

## 7. Scope-change rule

A proposed feature enters the MVP only if it is required to test a core pillar or is a prerequisite for an included feature. Otherwise, record it as a post-slice candidate. This protects the prototype from becoming a feature-complete but unvalidated mini-game.
