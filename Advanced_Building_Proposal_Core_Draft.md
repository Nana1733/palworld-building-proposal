# Advanced Building Proposal - Functional and Cosmetic Construction

**Core Draft v1.3**

## Overview

Palworld's building system already allows a significant degree of creativity. However, there is an important distinction between the flexibility of the underlying construction system and the restrictions introduced by the player-facing Helper layer.

This proposal explores ways to provide experienced players with greater building freedom without changing or disrupting the existing building experience.

The core principle is:

> “Separate what makes a base work from what makes a base look the way it does.”

The proposal contains two independent feature directions:

- Direction A - a simpler expansion of placement freedom.
- Direction B - a broader concept that separates Functional and Cosmetic construction.

A separate supporting feature, Connection Point Snapping, is also proposed. This could be useful independently of either direction.

The exact implementation, progression requirements, technical approach, terminology, lore, economy, and roadmap priorities would naturally be left to Pocketpair.

## Reading This Proposal

This document intentionally presents the complete set of ideas developed around the proposal.

The intention is not to decide in advance which parts of the argument are worth a reader's attention. Instead, the ideas are presented as clearly and honestly as possible, with the reader free to decide:

- how much of the document to read
- which ideas are relevant
- which ideas are practical
- which ideas to reject
- whether any of the proposed directions are worth exploring

The document therefore uses chapters to provide a gradual increase in depth and engagement. The feature proposals can be understood without reading every later chapter, while readers who wish to explore the design, player, technical, and strategic reasoning can continue further.

The proposal does not claim to know the correct implementation for Palworld. Its purpose is to present observations, possible directions, opportunities, risks, and hypotheses for Pocketpair to consider at their own discretion.

# 1. Background

## 1.1 The underlying construction system

Palworld's underlying building system appears to be more flexible than the standard player-facing building experience suggests.

Advanced construction techniques can demonstrate that building pieces may still form valid connections when their connection points are manually aligned, even when the pieces are no longer following a single shared grid.

This allows experienced players to create more complex shapes by:

- avoiding standard snapping behaviour
- manually aligning connection points
- rotating separate groups of building pieces
- combining structures built on different orientations

This suggests that the underlying system may be capable of supporting more flexibility than the standard building interface normally exposes.

## 1.2 The Helper layer

The standard building experience benefits from a Helper layer that guides players into predictable placement.

This system:

- assists players with snapping
- keeps building pieces aligned to familiar grids
- reduces placement ambiguity
- prevents many problematic overlap situations
- makes the building system easier to learn and use

These restrictions are valuable for the standard building experience.

The Helper layer also simplifies the problem space for the game itself. When building pieces are guided into predictable relationships and overlap cases are reduced, there are fewer unusual geometric and structural situations that the game needs to manage.

This creates an important distinction:

> “The limitations experienced by advanced builders may not necessarily come entirely from the underlying construction system, but from the Helper layer that makes construction simple and reliable for most players.”

The proposal does not argue that the Helper is bad or should be removed. It is valuable precisely because it reduces complexity for both players and developers.

## 1.3 The risk of an invisible boundary

The effectiveness of a Helper can also create an unintended long-term limitation.

When a Helper provides most of the visible construction logic, players may gradually begin to perceive its boundaries as the boundaries of the building system itself.

In other words:

> “What begins as a guide can eventually be mistaken for the complete definition of what is possible.”

This may create a self-limiting cycle:

1. Players learn the possibilities presented by the Helper.
2. The Helper becomes the mental model of the building system.
3. Possibilities outside its guidance remain largely undiscovered.
4. Limitations imposed by the Helper are attributed to the building system itself.
5. The underlying system is perceived as more limited than it may actually be.

The training-wheel analogy is useful here.

Training wheels are not a limitation of the bicycle. They are a tool that helps a beginner learn to ride it. But if a rider is never given the opportunity to move beyond them, the limitations of the training wheels may eventually be perceived as limitations of the bicycle itself.

The proposed advanced building features could provide a deliberate transition beyond the standard Helper layer - not by removing it, but by making it clear to experienced players that there may be possibilities beyond it.

## 1.4 The cost of aesthetic complexity

When advanced players manually combine independently oriented structures, several problems can appear.

### Visual gaps

Building pieces arranged outside a shared grid can leave visible gaps between:

- walls
- floors
- ceilings
- roofs
- pillars

This can limit how cleanly complex geometry can be finished.

### Gameplay interference

Large amounts of complex geometry created primarily for aesthetic purposes can also interfere with:

- Pal pathing
- AI navigation
- collision
- physics

### Dynamic object complexity

Normal building pieces may need to remain part of the active gameplay environment because they can:

- take damage
- be destroyed
- collapse
- interact with players and Pals
- affect navigation

This means that large amounts of aesthetic geometry may still need to be treated as dynamic gameplay structures.

The result is a broader problem:

> “The game currently has to treat aesthetic complexity as gameplay complexity.”

## 1.5 The design trade-off

The Helper therefore provides a genuine trade-off.

It protects players and developers from a large amount of placement and overlap complexity. Stepping beyond it may mean that Pocketpair would need to revisit parts of that problem space and decide how much of the resulting complexity is worth supporting.

The proposal does not assume that every restriction can or should be removed.

The relevant questions are instead:

- Which additional freedoms are technically feasible?
- Which problems are worth solving?
- Which solutions fit the game's roadmap?
- When would the benefits justify the development cost?
- Could greater creative depth create enough player or product value to make such work worthwhile?

Those decisions can only be made by Pocketpair.

# 2. Design Direction

## 2.1 Preserve the existing building system

The existing building system should remain unchanged.

This proposal is not intended to make ordinary building more complicated or require players to learn advanced construction mechanics.

The current system should remain:

- accessible
- reliable
- familiar
- easy to understand

## 2.2 Optional advanced access

Advanced construction features could be introduced as optional late-game content.

For example, Pocketpair could make them available through the Technology Tree at a level considered appropriate for the game's progression.

The intention is that players should first have the opportunity to understand:

- the normal building system
- the existing Helper layer
- the strengths and limitations of standard construction

Only then would they gain access to additional construction freedom.

The exact:

- level requirement
- Technology Point cost
- material cost
- progression method

would be up to Pocketpair.

## 2.3 Functional and Cosmetic construction

The main conceptual direction is to separate two different purposes of construction.

### Functional construction

This represents the current building system.

It determines the physical and gameplay properties of a base, including:

- collision
- pathing
- physics
- damage
- destruction
- structural behaviour
- interactive gameplay functions

### Cosmetic construction

This represents advanced visual construction.

Its purpose is to determine:

- appearance
- visual shape
- decorative complexity
- aesthetic continuity

The player is encouraged to think separately about:

> “What makes a base work”

and:

> “What makes a base look the way it does”

This does not remove the importance of functional construction.

Instead, it gives experienced players the ability to add visual complexity without necessarily requiring every aesthetic piece to behave like a gameplay object.

# 3. Supporting Feature - Connection Point Snapping

## The current challenge

Advanced builders can manually align building pieces by lining up their connection points. However, this currently requires a high degree of manual precision.

Two parts of the process are particularly troublesome:

- **Vertical alignment.** When connecting a new building piece to an existing one, the player must manually control the vertical relationship between the connection points - either keeping both pieces level or deliberately maintaining a small vertical offset. This can be difficult to judge by eye.
- **Directional alignment for curves.** When drawing an arc or circle, the player must also manually maintain the relationship between the new piece and the intended centre while managing the connection and its offset. The combination of these tasks makes complex curves difficult to construct consistently.

As a result, advanced construction techniques may remain inaccessible to many players even when the underlying system is capable of supporting the connection.

## Proposed concept

The feature could provide visual connection feedback together with more precise manipulation controls.

The central design principle is to give the player a clear understanding of what they are about to do, what is currently active, and where the active relationship is located.

### Connection point visibility

When the player grabs a connectable building piece, such as a foundation, and moves it near an existing compatible building structure, available connection points could become visible.

- Available connection points could be shown as small, unobtrusive white dots.
- The indicators should be easy to see without becoming visually distracting.
- White means the connection point is available and within the visible detection range, but is not currently engaged.

### Connection engagement

As the held building piece is moved closer, the system could check whether one of its connection points has entered the valid connection range of a compatible target.

- When a valid connection is detected, the active target could change from white to green.
- The green indicator shows that the connection is currently valid.
- When multiple candidates are available, the system could select the closest valid connection point. If the player wants a different target, they can reposition themselves so that the desired connection becomes the valid candidate.
- Once a connection has become active, it remains the current connection until that connection is lost, rather than changing simply because another candidate later becomes closer.
- If the player moves the held piece too far away, the connection is lost and the indicator returns from green to white.

This gives the player continuous feedback:

- White = available, but not currently connected.
- Green = currently within the valid connection range.

The visual system exposes the existing connection state without requiring the player to guess where the invisible threshold is.

### Optional hinge mode

When a valid green connection exists, the player can optionally engage Hinge Mode.

The hinge is a temporary manipulation constraint, not a force that automatically changes the underlying building rules.

When Hinge Mode is active, the held piece moves like a door swinging around a vertical hinge. The current connection relationship and offsets are preserved while the player rotates the piece around the world up/down axis.

The player can toggle Hinge Mode on and off as needed. A typical advanced workflow may therefore be: connect, hinge, rotate, disengage, make a further offset adjustment, then hinge again.

When Hinge Mode is engaged, a dotted vertical line appears at the active hinge position. This gives the player a direct visual indication of where the pivot is and what axis the piece will rotate around.

Two potential hinge positions are available:

- **Existing structure connection point** - the held piece rotates around the connection point on the existing structure.
- **Held structure connection point** - the held piece rotates around its own connection point.

The player could switch between these two hinge positions, for example using the Tab key. The exact control assignment would be up to Pocketpair.

### Axis locking and precision movement

Before placing the held piece, the player could also constrain manual movement to a selected axis.

The exact key assignments would be up to Pocketpair, but the concept could cycle through:

- None
- Player Look Direction
- Player Left/Right Direction
- World Up/Down Direction

The active axis could be shown visually near the active connection point. For example, a directional arrow could indicate the selected movement direction. The player could cycle through the available axes rather than needing to remember several independent controls.

A Precision Mode could also reduce movement sensitivity, for example to approximately 0.1 times normal movement speed, allowing smaller adjustments.

When Hinge Mode is active, its movement constraint takes precedence. Some axis-lock combinations may therefore produce little or no useful movement. The player can disengage the hinge, make the desired linear adjustment, and re-engage it when needed.

### Combined result

The combined system gives the player direct feedback about several otherwise invisible or difficult-to-control states:

- Where can I connect?
- Am I currently within the valid connection range?
- Which connection is currently active?
- Where is the current hinge?
- Which axis is currently constrained?
- How precisely am I moving?

Together, these tools could allow players to manually construct circles, arcs, curves, radial structures, and other complex shapes without requiring every piece to follow a single shared grid.

The goal is not to automate creativity or make advanced construction effortless. The goal is to remove unnecessary control friction so that techniques which are currently barely manageable become more accessible to players willing to learn them.

This feature is proposed as a standalone supporting feature. It could be useful with Direction A, Direction B, or even without either of them. It does not require the existing Helper to be removed. Instead, it extends the idea of assistance into a form that can support advanced construction.

# 4. Direction A - Expanded Placement Freedom

## The problem

When independently oriented building structures are connected, visible gaps can appear between building pieces.

The simplest solution may be to allow selected building pieces to overlap more freely.

## Possible approach

Building pieces such as:

- floors
- ceilings
- walls
- roofs
- pillars

could be given greater freedom to overlap each other.

This could potentially be implemented by:

- relaxing overlap restrictions on existing pieces
- introducing special versions of selected pieces with relaxed placement rules
- allowing players to use the existing Replace function to swap pieces where needed

This would allow players to patch gaps and create cleaner transitions between complex structures.

## Benefits

Direction A could:

- reduce visible gaps
- improve visual continuity
- enable more complex geometry
- build directly upon existing construction mechanics
- provide advanced builders with greater freedom

## Limitation

Direction A primarily solves the placement and visual problem.

It does not necessarily separate aesthetic geometry from gameplay systems.

Complex decorative structures may therefore still:

- interfere with Pal pathing
- contribute to collision complexity
- participate in physics
- remain subject to damage and destruction
- contribute to the overall complexity of the active environment

Direction A is therefore a more contained solution that improves building freedom without fundamentally changing how building objects behave.

# 5. Direction B - Mirage Construction Set

Direction B is a broader and more ambitious concept.

It proposes a separate construction layer that allows players to distinguish between:

- Real / Functional construction
- Mirage / Cosmetic construction

The term Mirage is used here as a working concept. The final name, lore, and in-world explanation could be adapted to whatever best fits Palworld.

## 5.1 Unlocking the Mirage Construction Set

The Mirage Construction Set could be introduced as an optional Technology Tree entry.

A possible progression would be:

1. The player reaches the required late-game level.
2. The player unlocks the Mirage Construction Set through the Technology Tree.
3. The player spends the required Technology Points.
4. The player gathers the required materials or components.
5. The player constructs the Mirage Construction Set.
6. The player gains access to Mirage construction.

The Construction Set could function as a player-bound capability rather than a freely transferable item.

The exact level, Technology Point cost, and material requirements would be left to Pocketpair.

## 5.2 The Mirage layer

The Mirage layer would use the same general library of buildable objects as the existing construction system.

Anything currently buildable could potentially have a Mirage version, including:

- foundations
- floors
- ceilings
- walls
- roofs
- pillars
- stairs
- windows
- doors
- decorative objects
- Palboxes
- other player-buildable objects

Mirage objects would exist primarily for visual purposes.

They could:

- overlap other building pieces
- overlap other Mirage objects
- clip into terrain
- clip into rock faces
- clip into the ground

Because Mirage structures are not intended to participate in the normal physical gameplay environment, they would not experience the same placement resistance as Real structures.

The existing Helper and snapping functions could still remain available for players who want to use them.

Players could therefore choose between:

- familiar snapping
- manual placement
- advanced manual connection using Connection Point Snapping

# 6. Real and Mirage Build Modes

When entering Build Mode, an authorized player could choose which layer they wish to work within.

## Real Build Mode

When focused on the Real layer:

- Real structures behave normally.
- Normal building rules apply.
- Mirage structures are non-physical.
- The player can walk through Mirage structures.
- Mirage objects cannot be interacted with.

The player is effectively working within the existing functional building system.

## Mirage Build Mode

When focused on the Mirage layer:

- Mirage structures become temporarily physical for the builder.
- Real structures become non-physical from the builder's perspective.
- The player can walk through Real structures.
- Existing build functions work normally on Mirage structures.
- Mirage structures can be placed and dismantled.
- Mirage pieces can overlap without the usual placement restrictions.

This allows players to construct within the Mirage layer using the same familiar building experience.

However, when the player exits Mirage Build Mode:

> “The Mirage returns to being non-physical.”

If the player is standing on a Mirage structure when leaving the mode, they would fall through it.

This creates an important balance:

> “Mirage provides construction freedom, but functional structures still matter.”

Players would still need to consider:

- real scaffolding
- real access routes
- functional construction planning

# 7. Mirage Objects and Interaction

A Mirage version of an interactive object is purely an illusion.

It does not participate in its normal gameplay function.

For example:

- a Mirage Palbox is not a functional Palbox
- a Mirage chest cannot be opened
- a Mirage workbench cannot be used
- a Mirage bed cannot be used
- a Mirage door does not provide normal interaction

The simple principle is:

> “Mirage affects perception, not simulation.”

Or perhaps more playfully:

> “Mirage can deceive human perception, but it won't affect a Pal's native instinct.”

A human player may be fooled by a fake Palbox.

A Pal, however, will continue to navigate toward the real Palbox because the Mirage version does not exist within the functional gameplay simulation.

# 8. Real Vision and Guild Permissions

The Mirage system could build upon Palworld's existing guild and building permission systems rather than requiring a completely new access mechanism.

## Non-guild players

A player without Real Vision would see:

> “The Real and Mirage layers together as one apparent structure.”

They could not:

- distinguish between the layers
- hide the Real layer
- hide the Mirage layer
- determine which objects are functional

To them, what they see is simply the apparent world.

## Guild members - Real Vision

Guild members could receive Real Vision.

This allows them to distinguish and control their view of the two layers.

They could choose to display:

- Mirage only
- Real only
- both layers

At least one layer would always remain visible.

When both layers are displayed, the Real layer could use a subtle tint, outline, or other visual treatment to distinguish it from the Mirage layer.

This would allow the Mirage layer to retain its intended appearance while making the functional structure easier to identify.

## Guild members with Build permission

Guild members with the existing permission to build could additionally:

- use Real Vision
- enter Mirage Build Mode
- place Mirage structures
- modify Mirage structures
- dismantle Mirage structures

This reuses existing multiplayer permission concepts rather than introducing a separate access system.

# 9. Player-Controlled Perceived Reality

The Mirage layer is not simply cosmetic geometry.

> “It is a player-controlled layer of perceived reality.”

Players who do not have Real Vision experience the combined appearance of the Real and Mirage layers.

This creates new possibilities for architecture and gameplay.

## PvP possibilities

Players could create:

- false floors
- fake bridges
- hidden routes
- deceptive fortifications
- misleading walls
- fake entrances
- false objectives
- fake Palboxes

An enemy could attack what appears to be a vulnerable Palbox, while the actual functional Palbox is located elsewhere.

An enemy could storm toward a seemingly defenseless village sitting on a cliff - only to discover that the floor beneath them was never physically there.

This introduces a new form of strategy based on:

- perception
- information
- deception
- architecture

The Mirage layer can deceive human perception while the underlying game simulation continues to function normally.

## Social possibilities

The system could also create entertaining multiplayer interactions.

A player might appear to have a perfectly normal guest room while quietly knowing that the floor is a Mirage.

An unwanted visitor may confidently walk toward the restroom...

...and suddenly discover there was a cliff behind the floor.

Repeatedly. :D

# 10. A More Controlled Visual State

One of the most interesting potential advantages of Direction B is the opportunity created by separating cosmetic structures from dynamic gameplay behaviour.

Normal functional structures may need to respond to many unexpected changes, including:

- damage
- destruction
- structural collapse
- collision
- physics
- AI and pathing

Mirage structures would have a more controlled and predictable state.

They would primarily remain visually unchanged unless they are intentionally:

- placed
- modified
- dismantled

by an authorized player.

Because Mirage structures are not required to participate in the same dynamic gameplay systems, this separation may create opportunities for the development team to handle and optimize them differently from normal functional structures.

The exact technical approach would naturally depend on Palworld's existing architecture and would be entirely up to Pocketpair.

The important opportunity is:

> “Separating cosmetic structures from unpredictable gameplay changes creates a more controlled category of visual objects.”

This may allow Pocketpair to explore technical approaches that are not practical when every building piece must remain fully dynamic and gameplay-reactive.

# 11. The Value of Creative Depth

## 11.1 Finite content and open-ended creative space

Story, quests, progression, and collectible content can provide a great deal of value, but they are ultimately finite.

A player may eventually:

- complete every quest
- capture every Pal
- obtain every item

Creative systems behave differently.

A sufficiently deep creative space does not have a fixed set of outcomes. The number of possible combinations can continue to grow through the player's own imagination and goals.

Building is one of the clearest examples.

> “A player may be able to obtain every building piece, but they cannot build every possible building.”

This creates a different kind of long-term motivation. Players can form goals that are not directly prescribed by the game.

## 11.2 Depth, personal vision, and satisfaction

The value of creative depth is not only the amount of time it can occupy.

Greater depth can allow players to approach their own ideas and personal visions more faithfully.

The underlying chain is:

**Creative depth**  
→ more possible combinations  
→ greater ability to approach a personal vision  
→ greater satisfaction when that vision is successfully realised

The closer a finished creation is to what the player intended to express, the greater the potential satisfaction of:

- creating it
- completing it
- sharing it
- having it successfully perceived and experienced by others

## 11.3 The social multiplier

When player creations can be visited, interacted with, or experienced by other players, their value can extend beyond the original builder.

A build can become:

- a personal goal
- an expression
- a challenge
- a place to visit
- an experience to share
- something that inspires others
- a source of new community activity

This can create a continuing cycle:

> “Creation → Sharing → Inspiration → Further Creation”

Direction B may extend this even further by allowing builders to create not only structures, but experiences based on perception, deception, discovery, and interaction.

A player may no longer simply say:

> “Look at my house.”

They may instead create an experience that another player can explore, misunderstand, discover, or be surprised by.

# 12. Potential Strategic Value

## 12.1 A more self-sustaining creative ecosystem

The potential strategic value of deeper creative systems is not that they remove the need for developers to create content.

Rather, they may change the relationship between developer-created tools and player-created activity.

A finite content cycle may look like:

**Developer creates content**  
→ players consume it  
→ the content is largely exhausted  
→ the developer creates more content

A productive creative ecosystem may instead look like:

**Developer provides a deep creative space**  
→ players create  
→ creations attract attention and inspire others  
→ new and existing players enter or return  
→ the community creates more  
→ the developer observes how the ecosystem evolves  
→ new tools and features expand the creative space again

The ideal opportunity is not simply that players spend more time.

It is that players may increasingly create reasons for one another to return.

## 12.2 The multiplying value of new creative tools

In a sufficiently deep creative system, new building content may have multiplying rather than purely additive value.

A new building piece, furniture set, material, or construction tool is not experienced in isolation.

It can combine with:

- existing building pieces
- existing materials
- existing techniques
- different architectural styles
- player imagination
- future tools and techniques

This means a relatively small addition can potentially generate a large amount of player-created output.

Future additions could potentially be delivered in whatever form Pocketpair considers appropriate, including free updates, optional paid content, or other approaches.

The proposal does not prescribe a business model. The point is simply that deeper creative systems can increase the number of ways future additions may be used.

## 12.3 A living source of player insight

A healthy creative community can also reveal what players naturally value.

By observing what players build and share, a developer may gain insight into:

- emerging themes and trends
- common limitations
- desired tools
- social behaviours
- preferred forms of interaction
- the kinds of spaces players want to experience together

This may help future additions respond to genuine player interests rather than relying only on assumptions.

Investment in deep, self-sustaining player creativity can therefore potentially create value that extends beyond a single update cycle.

The behaviours, communities, and creative patterns that emerge may also provide useful insight for the continued evolution of the wider Palworld ecosystem.

This is particularly relevant to any future products or multiplayer experiences, although the exact strategic relevance and implementation would naturally be for Pocketpair to determine.

# 13. Technical and Design Considerations

Direction B is substantially more ambitious than Direction A.

The proposal does not assume that it would be easy, inexpensive, or immediately suitable for Palworld.

Stepping beyond the Helper may reintroduce complexity that the current system intentionally avoids.

For that reason, the following remain unknown from outside the development team:

- technical feasibility
- implementation cost
- networking implications
- optimisation requirements
- save and persistence considerations
- roadmap suitability
- progression and balance requirements

Direction B should therefore be understood as a conceptual direction rather than a claim about how Palworld must be implemented.

The more controlled state of Mirage structures may create new opportunities for different technical handling, but this is an opportunity rather than a guaranteed performance benefit.

Pocketpair would be best placed to determine:

- whether such a separation is technically worthwhile
- how it could be represented internally
- what optimisation approaches become possible
- which parts of the concept are useful
- whether the feature should be explored incrementally
- when the potential benefits justify the cost

# 14. Lore and World Integration

“Mirage” does not need to be the literal explanation for the system.

Pocketpair could choose whatever terminology and lore fits Palworld best.

One possible interpretation is phasing.

The Real and Mirage layers could exist as different phases of the same world.

A player entering the appropriate phase would be able to:

- interact with structures in that phase
- walk on structures in that phase
- modify structures in that phase

This would create a symmetrical logic:

### Real phase

Real structures are physical.

Mirage structures can be passed through.

### Mirage phase

Mirage structures are physical.

Real structures can be passed through.

Other possible explanations could include:

- ancient technology
- dimensional overlap
- projection technology
- illusion technology
- a Pal-related phenomenon

The exact lore explanation is less important than the underlying design principle.

# 15. Summary

## Supporting Feature - Connection Point Snapping

A standalone feature that could make advanced manual construction easier and more accessible by allowing compatible connection points to temporarily hinge together within their valid connection range.

## Direction A - Expanded Placement Freedom

A simpler and more contained direction.

This could allow selected building pieces to overlap more freely, helping advanced builders:

- patch gaps
- improve visual continuity
- create more complex geometry

## Direction B - Mirage Construction Set

A broader direction that separates:

> “What makes a base work”

from:

> “What makes a base look the way it does.”

The Mirage Construction Set could provide:

- advanced visual construction freedom
- unrestricted overlap for cosmetic structures
- separation between Functional and Cosmetic construction
- reduced interference between cosmetic geometry and AI/pathing
- a more controlled visual state
- opportunities for different technical handling
- new multiplayer and PvP gameplay
- player-controlled perception of the environment

## The broader opportunity

The purpose of deeper creative systems is not unlimited complexity for its own sake.

The opportunity is to create a space deep enough that players can:

- keep discovering new possibilities
- form new self-directed goals
- move closer to the visions they want to realise
- create experiences for other players
- inspire further creation

A game can continue to create content for players, but a deep creative system can also provide a space in which players increasingly create reasons for one another to remain engaged.

## Final Thought

The intention is not to replace Palworld's existing building system.

The current system should remain exactly what it is for players who simply want to build normally.

Instead, this proposal explores what could become possible if experienced players were given an optional, deliberate path beyond the existing Helper layer.

Direction A and Direction B are deliberately presented as alternatives.

Either could be valuable.

The exact design, technical implementation, economy, progression, lore, terminology, and priorities should ultimately be determined by Pocketpair.

The central question is simply:

> “What if Palworld separated what a base looks like from what it physically is?”

And beyond that:

> “What if the Helper remained the accessible foundation of the building system - while the game also provided a visible path for players who wished to explore further?”
