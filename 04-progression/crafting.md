---
label: Item Crafting
icon: shield
order: 1
---

# Item Quality, Rarity & Modifiers Guide

[!badge variant="info" text="Path of Exile Style"] [!badge variant="success" text="Advanced System"]

This server adds a Path-of-Exile–style item layer on top of normal Tibia/TFS items.

Every eligible equipment item can have:

* **Quality** (0–20): scales the item's *base* stats
* **Rarity** (Normal → Legendary): controls **modifier capacity**
* **Modifiers**: extra stats that change how your **attacks** and **spells** behave

This guide explains what these mean, how they work, and how crafting currencies interact with them.

## 1) Eligibility

Not every item can roll these properties.

**Eligible (typical examples):**

* Weapons (swords/axes/clubs/wands, etc.)
* Armor pieces
* Helmets/boots/legs/shields
* Rings/amulets (when supported)

**Not eligible (typical examples):**

* Stackable items (e.g., runes, many consumables)
* "Charged" or special-use items
* Containers
* Ammo (excluded from quality scaling and usually excluded from properties)

!!! info "Eligibility Note"
If an item is not eligible, it simply won't gain these properties.
!!!

## 2) Quality (0–20)

**Quality increases an item's base stats by a percentage.**
It does **not** change the item's modifiers. Quality only scales what the item already "is" underneath.

### What "base stats" includes

Depending on the item type, Quality can scale things like:

* Weapon **Attack** (physical and the native elemental portion)
* **Defense** and **extra defense**
* **Armor**
* Protection values (absorb/reflect)
* Hit chance
* Speed bonuses
* Stat/skill bonuses
* Regen gain amounts

### Example (weapon)

A Serpent Sword normally shows:

```
You see a serpent sword (Atk:18 physical + 8 earth, Def:15 +1).
Quality: 0
```

At **Quality 20** (20%):

* Physical: 18 → 22
* Earth: 8 → 10
* Def: 15 → 18
* ExtraDef: +1 stays +1 (scaled independently, rounding applies)

So you'd see:

```
You see a serpent sword (Atk:22 physical + 10 earth, Def:18 +1).
Quality: 20
```

### Rounding rule (important)

!!! warning "Important Rounding Rule"
Quality scaling always moves values in the "stronger" direction:

* **Positive values** increase using half-up rounding.
* **Negative values** move **toward 0** (less negative), never further away.
!!!

**Example:**

* Base `-5` with Quality 20% → `-4` (not `-6`)

## 3) Rarity and Modifier Capacity

Rarity is primarily a **modifier capacity tier**.

| Rarity        | Modifier Capacity |
| ------------- | ----------------: |
| **Normal**    |                 0 |
| **Uncommon**  |                 1 |
| **Magic**     |                 2 |
| **Rare**      |                 3 |
| **Epic**      |                 4 |
| **Legendary** |                 5 |

!!! tip "Key Rule"
You can't have more modifiers than your rarity allows.
!!!

## 4) Modifiers

Modifiers are extra properties on top of the base item. They come in two main shapes:

### A) Flat modifiers

These add a fixed amount.

**Examples:**

* `+10 fire attack damage`
* `+10 fire spell damage`
* `+25 max health`

### B) Percent modifiers

These scale an existing base.

**Examples:**

* `+10% fire damage`
* `+12% physical damage`

!!! note "Percent Modifier Behavior"
Percent modifiers scale a base that includes the item's *native/base contribution* (not only "other modifiers").
!!!

## 5) Damage Sources: Attacks vs Spells

Modifiers can apply differently depending on whether the damage comes from an **Attack** or a **Spell**.

### What counts as an Attack?

An **Attack** is a weapon-driven hit:

* sword/axe/club melee swings
* wand hits (their on-hit element is still an "attack source")
* distance attacks (when supported)

### What counts as a Spell?

A **Spell** is something you cast, like:

* `exori`
* `exori hur`
* rune-like spell effects (if treated as spells)

## 6) Elemental components and "creating" damage types

A hit can have multiple elemental components (physical, fire, ice, energy, etc.).

### Flat elemental adds can create a component

If a modifier says it adds an element, and the hit does **not** already have that element component:

* The element component is **created**, **as long as the modifier matches the hit's source type** (attack vs spell).

**Example:**

* `+10 fire attack damage` on a pure physical sword hit:
  * creates a **fire component** and adds **+10 fire** to it

**Example:**

* A wand that normally deals **energy** (attack source)
* Add `+10 fire attack damage`
  * the hit keeps its **energy** component
  * and gains a new **fire** component (+10)

### Percent elemental modifiers apply to both sources (unless stated otherwise)

* `+10% fire damage` applies to **fire damage from attacks and spells**.

## 7) Modifier wording examples (fire)

### `+10 fire attack damage`

* Applies only to **attack hits** (weapon-based hits).
* Adds +10 to the hit's **fire** component.
* If the hit has no fire component, it **creates one**.

**Example:** Wand of Vortex (base energy hit)
Result: **energy base** + **new fire component**

### `+10 fire spell damage`

* Applies only to **spell hits** (casted spells).
* Adds +10 to the spell's **fire** component.
* If the spell has no fire component, it **creates one**.

**Example:** `exori hur` that normally deals physical
Result: **physical base** + **new fire component**

### `+10% fire damage`

* Applies to **all fire damage**, regardless of source:
  * attack fire components
  * spell fire components
* Scales the total fire base (native + flat adds).

## 8) Crafting currencies (what they do)

These currencies mutate **rarity**, **modifiers**, and **quality** (when allowed by item eligibility).

!!! danger "Important Restriction"
You can only change Quality/Rarity/Modifiers while the item is **NOT equipped**.
!!!

### Currency catalogue

| Currency                 | Typical outcome                                                   |
| ------------------------ | ----------------------------------------------------------------- |
| **Orb of Transmutation** | Normal → Magic (rolls up to Magic capacity)                       |
| **Orb of Alteration**    | Rerolls modifiers (within current rarity capacity)                |
| **Orb of Augmentation**  | Adds 1 new modifier (if capacity allows)                          |
| **Orb of Regal**         | Magic → Rare (+1 modifier)                                        |
| **Orb of Exalted**       | Adds 1 new modifier and may increase rarity tier (if rules allow) |
| **Orb of Chaos**         | Rerolls a rare item's modifiers                                   |
| **Divine Orb**           | Rerolls modifier values (keeps the same modifier IDs)             |
| **Orb of Annulment**     | Removes 1 modifier                                                |
| **Orb of Scouring**      | Removes all modifiers (and normalizes item state per rules)       |
| **Orb of Chance**        | Random rarity outcome (rule-based)                                |
| **Orb of Alchemy**       | Normal → Rare (rolls up to Rare capacity)                         |
| **Quality currency**     | Increases Quality up to the cap (0–20)                            |

!!! note "Server Tuning"
Exact drop rates and some rule details are server-tuned.
!!!

## 9) Rules and safeguards

### "No mutation while equipped"

Quality, rarity, and modifier changes are blocked if the item is in a real equipment slot.

* If it's equipped: the currency/action **fails**.
* Unequip it first, then try again.

### Quality and Modifiers are independent

* **Quality** scales base stats.
* **Modifiers** add or scale extra effects.
* Quality does **not** multiply modifier values.

## 10) Quick examples

### Example A: Quality scaling (Serpent Sword)

* Base: `Atk:18 physical + 8 earth`
* Quality 20 → `Atk:22 physical + 10 earth`

### Example B: Element creation (attack)

A physical sword hit with `+10 fire attack damage`:

* Physical remains
* Fire component is created: `+10 fire`

### Example C: Spell vs attack

* `+10 fire spell damage` affects `exori` casts, not sword swings
* `+10 fire attack damage` affects sword swings, not `exori`
* `+10% fire damage` affects both (any fire component)
