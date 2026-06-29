# Rifts & Revolvers — Claude Code Handoff
## Context Brief for New Session

You are picking up development of **Rifts & Revolvers**, an original tabletop RPG
rulebook. The core system has been fully designed and documented. Your job is to
continue building on it.

---

## Files in This Repo

| File | What It Is |
|------|-----------|
| `rifts-and-revolvers.html` | Complete core rulebook, v2.0. Single self-contained file — all CSS inline. |
| `DESIGN_NOTES.md` | Full design reasoning, math validation, decision history. Read this before touching mechanics. |
| `CLAUDE_CODE_HANDOFF.md` | This file. Start here. |

---

## The Game in One Paragraph

Rifts & Revolvers is a Weird West tabletop RPG where cowboys, robots, and magic
collide across dimensional Rifts. Three physical layers run simultaneously: poker
dice resolve all actions using hand rankings (pair, full house, etc.), a double
deck of playing cards (104 cards) gives players a secret 5-card hand that fuels
class abilities and can be passed left silently, and five colors of poker chips
track health (White), nerve (Red), luck (Blue), money (Green), and dimensional
debt (Black). The GM acts as the house — setting stakes with chips, never rolling
dice against players.

---

## Eight Classes — Quick Reference

| Class | Suit | Role | Honor |
|-------|------|------|-------|
| Doctor | ♥ | Healer, support, recharge enabler | +2 |
| Charlatan | ♥ | Con artist, misdirection, forced rerolls | −2 |
| Gunslinger | ♠ | Precision, die locking, duel specialist | +2 |
| Bandit | ♠ | Disruption, ambush, chip theft | −2 |
| Cogwright | ♣ | Builder, saboteur, prepared locking | +2 |
| Brawler | ♣ | Attrition, wild dice, physical recovery | −2 |
| Seer | ♦ | Fate manipulation, Wild Cards, Rift reading | +2 |
| Drifter | ♦ | Movement, escape, dimensional navigation | −2 |

---

## Card Hand Rules — Critical Summary

Every player holds 5 cards from a double deck (104 cards). Cards are secret.
Cannot be shown or described verbally. Pass 1 card left per scene, face-down.

**Number cards (2–10) of your class suit:** Trigger class ability OR discard for 1 reroll on a matching-suit action.
**Number cards out of class:** Discard for 1 reroll on matching-suit action only.
**Face cards of your class suit:** Named class abilities. Cannot be used for rerolls.
**Face cards out of class:** Pass left only. Cannot be discarded cheaply.
**Diamond face cards (any class):** Rift Reading access. Non-Seers also gain 1 Black chip.

**Recharge is a class ability, not automatic.** Every card drawn during recharge
gives the GM 1 Fate Chip. This is the core economy loop.

---

## GM Rules — Critical Summary

GM does not roll dice. GM sets stakes using Fate Chips placed in the center.
Players match the chips with their own to attempt the action, then roll.

| Fate Chips | Difficulty | Required Hand |
|------------|-----------|---------------|
| 1 | Easy | Two Pair |
| 2 | Moderate | Three of a Kind |
| 3 | Hard | Full House |
| 4 | Very Hard | Four of a Kind |
| 5 | Legendary | Five of a Kind |

GM earns Fate Chips when players recharge cards (1 chip per card drawn).
GM spends 3 Fate Chips to redraw their own 5-card hand.

---

## Honor/Notoriety Scale

Runs −5 (notorious) to +5 (honorable). Zero = stagnation.

- −5 to −3 or +3 to +5: 5 XP per session
- −2 or +2 (class home): 4 XP per session
- −1 to +1: 3 XP per session

Ability costs: 10–15 XP. Class transition: 20 XP + narrative moment.
Transition requires reaching the new class's scale position first.
During transition, character sits in stagnation zone earning only 3 XP/session.

---

## What's Already Built (in the HTML)

- Full setting introduction
- All 8 class cards with starting chip stacks
- Complete chip economy (5 colors, all costs documented)
- Dice system with hand rankings and probability notes
- All 4 dice modifier mechanics (Lock, Wild Die, Reroll, Wild Card)
- Persistent Hand rules (all 3 Card Laws)
- Class abilities for all 8 classes including face card named abilities
- Rift Reading rules
- Honor/Notoriety scale and XP economy
- Class transition rules
- 5 minigames: Duel, Shootout, Bar Brawl, Confrontation, Workshop
- GM tools (Fate Chips, GM hand, NPC tiers, scene types, Fate Cut)
- Complete quick reference table

---

## What Still Needs Building

These are designed in conversation but not yet documented:

### Priority 1 — Character Sheet
A printable/fillable page tracking:
- Class and suit
- Chip stacks (visual track for each color)
- Persistent Hand card slots (5 slots, face-down visual)
- Wound conditions
- Honor/Notoriety slider (−5 to +5)
- XP tracker
- Active class abilities (checkboxes)
- Black chip debt tracker (5 slots, collector triggered at 5)

### Priority 2 — Progression Trees
Each class needs:
- 2–3 basic abilities (10 XP each)
- 1–2 advanced abilities (15 XP each)
- Clear unlock prerequisites

Basic ability examples already implied in the rulebook:
- Doctor: Treat (core), Field Medicine (recharge), Teammate Recharge (advanced)
- Gunslinger: Called Shot (core), Clean Win recharge, Red chip recovery

### Priority 3 — Starter Scenario
One-session intro adventure that:
- Introduces all 5 minigames
- Has a natural Rift event
- Includes pre-generated characters (one per class pair)
- Shows the GM Fate Chip economy in action

### Priority 4 — Equipment List
Gear that modifies starting chip stacks or dice mechanics:
- Weapons (modify duel dice counts)
- Medical supplies (Doctor ability fuel)
- Cogwright tools (pre-built devices)
- Rift artifacts (Black chip items with powerful effects)

---

## Tech Notes for the HTML File

- Single file, all CSS inline — no external dependencies except Google Fonts
- Google Fonts: Playfair Display (headers), Special Elite (flavor/labels), Lato (body)
- CSS custom properties in :root for the color palette
- Mobile responsive at 600px breakpoint
- No JavaScript — pure HTML/CSS

If splitting into components:
- The color palette variables are in :root at top of <style>
- Chapter sections are clearly labeled with HTML comments
- Class cards use a consistent .class-card + suit modifier pattern
- Chip visuals use radial-gradient on .chip-visual + color modifier classes

---

## Design Constraints — Do Not Change Without Review

These are load-bearing decisions that affect multiple systems simultaneously:

1. **Five cards per hand, always.** Mirrors poker. Non-negotiable.
2. **Pass left only, one per scene.** Direction matters. Right-to-left information flow is intentional.
3. **No automatic recharge.** Recharge must be earned through class abilities.
4. **GM never rolls against players.** GM is the house, not a player.
5. **Black chips cannot be restored through rest.** The debt sleeps but doesn't die.
6. **Wild Cards are Seer/GM exclusive.** Too powerful to distribute widely.
7. **Straight = 1 Blue chip bonus.** Compensates for near-impossibility with locking strategy.
8. **Number card rerolls are flat (no value scaling).** Granularity breaks table flow.
9. **Honor scale is ±2 per class, not ±5.** Keeps transitions achievable without being trivial.
10. **Same-suit classes share the full card range.** Doctor and Charlatan both want high Hearts. That competition is intentional.

---

## Tone and Voice

The rulebook voice is:
- Confident, not academic
- Western grit without parody
- Rules stated plainly, flavor brief
- Flavor quotes are first-person overheard dialogue, not omniscient narration
- Chapter titles use evocative names ("High Noon", "Last Call", "Words Like Weapons")

Match this voice in any new content.

---

*Handoff prepared from claude.ai design session. All math validated. v2.0 complete.*
