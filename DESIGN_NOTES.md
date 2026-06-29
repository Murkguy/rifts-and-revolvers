# Rifts & Revolvers — Design Notes
## For Handoff to Claude Code

This document captures the design reasoning, math validation, and decision history
behind the core rulebook. The HTML file (rifts-and-revolvers.html) is the deliverable.
These notes explain *why* things are the way they are.

---

## System Overview

Three interlocking layers, each doing a distinct job:

| Layer | Physical Object | Job |
|-------|----------------|-----|
| Dice | 5 poker dice (faces: 9, 10, J, Q, K, A) | Action resolution — what happens |
| Cards | Double deck (104 cards + 4 Jokers) | Edge and economy — how it bends |
| Chips | Standard poker set (5 colors) | Status tracking — what you have |

**Core design principle:** Only roll dice when failure has a real consequence.
If you can't describe what losing looks like before the roll, don't roll.

---

## The Eight Classes

Two classes per suit. One honorable, one notorious. They compete for the same cards.

| Class | Suit | Honor/Notorious | Scale Position |
|-------|------|----------------|----------------|
| Doctor | ♥ Hearts | Honor | +2 |
| Charlatan | ♥ Hearts | Notorious | −2 |
| Gunslinger | ♠ Spades | Honor | +2 |
| Bandit | ♠ Spades | Notorious | −2 |
| Cogwright | ♣ Clubs | Honor | +2 |
| Brawler | ♣ Clubs | Notorious | −2 |
| Seer | ♦ Diamonds | Honor | +2 |
| Drifter | ♦ Diamonds | Notorious | −2 |

### Why "Cogwright" not "Engineer"
Engineer felt generic. Cogwright implies steam-punk, the smell of oil and ozone,
brass fittings — it's a person you'd actually meet in this world.

### Why "Charlatan" not "Damsel" or "Grifter"
Damsel is gendered and limiting. Grifter sounds like an insult at the table.
Charlatan has swagger — it's what you'd call yourself if you were proud of it.
It covers snake oil salesman, southern belle working a room, traveling preacher
fleecing a congregation. Same skill set, broader identity.

### Why "Seer" not "Mystic" or "Gypsy"
The original concept was the wandering fortune-teller archetype from classic westerns.
Seer strips the cultural costume while keeping the mechanical identity: someone who
reads the Rift as a living text, interprets dimensional bleeds, sees what's coming.
Their connection to Diamonds/Rift is baked into class identity, not costume.

---

## Chip Economy — Math Validation

### Starting Stacks (validated against session drain)

Estimated average session: 3 combat scenes + 2 social scenes.
White drain: ~3 hits per combat scene = ~9 White total.
Red drain: ~1 nerve test per scene = ~5 Red total.
Black gain: ~2 from Rift interactions per session.

| Class | White | Red | Blue | Green | Black |
|-------|-------|-----|------|-------|-------|
| Doctor | 10 | 8 | 3 | 4 | 0 |
| Charlatan | 10 | 7 | 4 | 6 | 1 |
| Gunslinger | 12 | 7 | 3 | 4 | 0 |
| Bandit | 11 | 7 | 3 | 5 | 1 |
| Cogwright | 12 | 7 | 3 | 5 | 0 |
| Brawler | 15 | 7 | 2 | 3 | 1 |
| Seer | 10 | 7 | 5 | 3 | 2 |
| Drifter | 11 | 8 | 4 | 5 | 1 |

**Why Brawler gets 15 White:** Their primary recovery mechanic requires winning
physical exchanges. They need the buffer to stay in fights long enough to recover.

**Why Seer starts with 2 Black:** They are already entangled with dimensional forces
before the session begins. Their Wild Card ability adds more. Starting at 0 felt false.

**Why only 5 chip colors:** A standard poker set has exactly white, red, blue, green,
and black. No sixth color. Honor/Notoriety is tracked on a character sheet slider,
not with chips — it's a scale, not a stackable resource.

### Black Chip Design Intent
Black chips are a liability, not a resource. The design goal is a "creeping dread"
mechanic — using dimensional power is always free in the moment and always costs
you later. At 5 Black the GM introduces a Rift Collector. The only exits are
story moments (shed 1) or defeating the Collector in a Duel (shed 3).

---

## Dice Math

### Hand probability with 5 dice (faces: 9, 10, J, Q, K, A)

Single roll (no locking):
- Five of a Kind: 0.08%
- Four of a Kind: 1.93%
- Full House: 3.86%
- Straight: 3.09%
- Three of a Kind: 15.43%
- Two Pair: 23.15%
- One Pair: 46.30%
- High Card: 6.17%

With 3 rolls and optimal locking strategy (greedy — lock most frequent value):
- Five of a Kind: ~4%
- Four of a Kind: ~25%
- Full House: ~42%
- Straight: ~0% (see below)
- Three of a Kind: ~69%
- Two Pair: ~95%
- One Pair: ~100%
- High Card: <1%

### The Straight Problem (important)
With only 6 faces, only TWO straights exist: 9-10-J-Q-K and 10-J-Q-K-A.
With optimal locking strategy, Straight probability drops to near zero after 3 rolls
because locking strategy prioritizes pairs over runs.

**Design decision:** Made Straights the "gambler's hand" — explicitly rare,
rewarded with 1 Blue chip on success. Players who deliberately chase a Straight
are taking a real risk for a real reward. The rulebook calls this out explicitly.

### Difficulty Curve (cumulative probability at 3 rolls)
- Easy (Two Pair): ~95%
- Moderate (Three of a Kind): ~69%
- Hard (Full House): ~42%
- Very Hard (Four of a Kind): ~25%
- Legendary (Five of a Kind): ~4%

These map to GM Fate Chip costs (1–5 chips) in the rulebook.
Players always have mitigation tools (card discards, class abilities, chip spends)
that improve these odds — so the raw numbers are the floor, not the ceiling.

---

## Card System Design

### Double Deck Rationale
104 cards creates:
- Scarcity: you may never see certain cards in a session
- Duplicates: same card can exist in two hands (Resonance mechanic)
- Pass economy: 4–5 players passing left creates genuine information asymmetry

### Opening Hand Probabilities
- Chance of ≥1 face card of your class suit: ~33.5%
- Chance of 3+ cards of your suit (class trigger): ~9.8%
- Chance of all 5 in your suit (max power): ~0.1%

**Design intent:** Players rarely open with what they need. The Pass mechanic
is essential, not optional. Building toward a class trigger is the meta-game.

### The Pass — Silent Table Diplomacy
One card per scene, left only. Face-down. No verbal description of what's passing.
Players CAN express needs ("pass something to the Doctor") but cannot describe
their hand mechanically. This creates genuine silent negotiation at the table.

### Reroll Economy — Kept Deliberately Simple
Any number card (2–10) of matching suit = 1 reroll.
No value-based scaling for number cards (originally considered, abandoned).
Reason: Granularity at the table breaks flow. Players shouldn't be doing math
about whether a 7 gives more than a 4. The card is the cost. The reroll is the reward.

Face cards out of class = must pass left. Cannot discard for rerolls.
This creates a specific pressure: face cards you can't use are not dead weight —
they're someone else's treasure you're responsible for delivering.

### Wild Cards — Seer/GM Exclusive
Wild Cards (one die value = Ace for the scene) are game-breaking in a deliberate way.
Kept exclusive to Seer and GM to preserve rarity. Costs a Diamond face card for Seer,
2 Fate Chips for GM. Always raises Chaos Track by 1.

Effect is table-wide: the GM's hand is affected too. No one is safe from a Wild Card.

---

## GM as House — Design Rationale

The GM does not roll dice against players. This was a deliberate decision that:
1. Keeps the drama on the player side of the table
2. Makes the GM's role feel different from playing a class
3. Allows the GM to set difficulty narratively rather than mechanically

**Fate Chips as difficulty currency:** GM places chips, players match or walk away.
The type of chip demanded signals the cost: White = physical, Red = nerve,
Black = only the willing to acquire Rift Debt may attempt this.

**The closed loop:**
- Players spend cards for class abilities
- Players recharge cards (GM gains 1 Fate Chip per card drawn)
- GM uses Fate Chips to raise stakes or redraw their own hand
- Higher stakes push players to use more cards
- Repeat

This creates a session arc where GM pressure builds naturally through player activity,
peaking in the final scenes when the GM has accumulated the most Fate Chips.

**GM recharge cost:** 3 Fate Chips to redraw full hand. At ~2 player redraws per
player per session (4 players = ~8 Fate Chips total), the GM can redraw twice
per session. Feels right — the GM gets one mid-session adjustment and one late push.

---

## Honor/Notoriety Scale

Scale runs −5 to +5. Zero is stagnation. Every class starts at ±2.

**XP per session:**
- Deeply committed (±3 to ±5): 5 XP
- At class home (±2): 4 XP
- Stagnation zone (−1 to +1): 3 XP

**Ability costs:**
- Basic class ability: 10 XP
- Advanced class ability: 15 XP
- Class transition: 20 XP + narrative moment

**Why stagnation at zero, not negative:**
Players who hedge aren't being punished — they're being accurately represented.
A character with no clear identity is harder to play well and progresses slower.
The mechanic describes reality: unclear people don't grow as fast as committed ones.

### Class Transition Math

Transition distance = absolute difference in scale positions.
Bandit (−2) → Doctor (+2) = 4 points = ~4 stagnation sessions at 3 XP.
During those 4 sessions: 12 XP earned, then ~2 more sessions at 4 XP to reach 20.
Total: ~6 sessions for the longest transition. Feels right for a redemption arc.

Same-position transitions (Bandit → Brawler = 0 points) cost only the 20 XP,
no stagnation. This is a career change, not a moral arc.

### Old abilities are kept on transition
The retired Bandit who became a Doctor still knows how to disrupt a roll.
Abilities are permanent. The history is mechanical, not just narrative.

---

## Minigame Structure

Five minigames, all accessible to all classes at base level.
Classes provide advantages within minigames, not access gates.

| Minigame | Primary Classes | Core Mechanic |
|----------|----------------|---------------|
| The Duel | Gunslinger, Bandit | Hidden dice, Wound Track |
| The Shootout | All | Cover Cards, Chaos Track, Initiative |
| The Bar Brawl | Brawler | Simultaneous card play |
| The Confrontation | Charlatan, Seer | Social stakes, Romance rules |
| The Workshop | Cogwright, Drifter | Build/sabotage/navigation |

**Bar Brawl key rule:** Card value wins exchanges, not hand rank.
Simultaneous reveal — everyone plays one card face-down, flips together.
Brawler's low Clubs cards get a free Wild Die in this context.
Chaos Track starts at 2 in Bar Brawls (already chaotic).

**Rift exception:** Reading the Rift requires a Diamond face card for non-Seers.
Seer can use any Diamond. This is the only hard class gate in the game.

---

## What's Not Yet Built

The rulebook covers core mechanics. The following are designed in conversation
but not yet documented:

1. **Full progression trees** — specific abilities per class at 10 XP and 15 XP tiers
2. **Character sheet** — tracking chips, hand slots, wound track, honor scale
3. **Starter scenario** — a one-session intro adventure
4. **Equipment list** — gear that modifies chip stacks or dice pools
5. **Extended NPC rosters** — named Legends with full card hands and class identities

---

## Conversation History

This system was designed iteratively in a Claude claude.ai conversation.
The design notes above capture the key decisions. If you need the full reasoning
trail for any specific mechanic, the conversation is the source of truth.

The HTML rulebook (rifts-and-revolvers.html) is v2.0 — a full refactor from
an earlier version that used different archetype names and chip values.
All math in v2.0 has been validated against the probability calculations above.
