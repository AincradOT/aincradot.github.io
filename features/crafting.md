---
label: Item Crafting
icon: shield
order: 1
---

# Item Quality, Rarity & Modifiers Guide

[!badge variant="info" text="Path of Exile Style"] [!badge variant="success" text="Advanced System"]

This server adds a Path-of-Exile–style item layer on top of normal Tibia items.

Every eligible equipment item can have:

* **Quality** (0–20): scales the item's *base* stats
* **Rarity** (Normal → Legendary): controls **modifier capacity**
* **Modifiers**: extra stats that change how your **attacks** and **spells** behave

This guide explains what these mean, how they work, and how crafting currencies interact with them.

---

## Eligibility

Not every item can roll these properties.

**Eligible items:**

* Weapons (swords/axes/clubs/wands, etc.)
* Rings/amulets
* Armor pieces

**Not eligible:**

* Stackable items (e.g., runes, many consumables)
* "Charged" or special-use items
* Containers
* Ammo (excluded from quality scaling and usually excluded from properties)

!!!info Eligibility
If an item is not eligible, it simply won't gain these properties.
!!!

---

## Quality (0–20)

**Quality increases an item's base stats by a percentage.**

It does **not** change the item's modifiers. Quality only scales what the item already "is" underneath.


### Base Stats

Depending on the item type, Quality can scale:

* Weapon **Attack** (physical and the native elemental portion)
* **Defense** and **extra defense**
* **Armor**
* Protection values (absorb/reflect)
* Hit chance
* Speed bonuses
* Stat/skill bonuses
* Regen gain amounts


### Example: Serpent Sword

**Base stats (Quality 0):**

```
You see a serpent sword (Atk:18 physical + 8 earth, Def:15 +1).
```

**At Quality 20 (20% increase):**

* Physical: 18 → 22
* Earth: 8 → 10
* Def: 15 → 18
* ExtraDef: +1 stays +1 (scaled independently, rounding applies)

**Result:**

```
You see a serpent sword (Atk:22 physical + 10 earth, Def:18 +1).
```


### Rounding Rule

!!!danger Important
Quality scaling always moves values in the "stronger" direction:

* **Positive values** increase using half-up rounding
* **Negative values** move **toward 0** (less negative), never further away
!!!

**Example:** Base `-5` with Quality 20% → `-4` (not `-6`)

---

## Rarity and Modifier Capacity

Rarity determines how many modifiers an item can have.

| Rarity        | Modifier Capacity |
| ------------- | ----------------: |
| **Normal**    |                 0 |
| **Uncommon**  |                 1 |
| **Magic**     |                 2 |
| **Rare**      |                 3 |
| **Epic**      |                 4 |
| **Legendary** |                 5 |

!!!tip Key Rule
You can't have more modifiers than your rarity allows.
!!!

---

## Modifiers

Modifiers are extra properties on top of the base item. They come in two types:


### Flat Modifiers

Add a fixed amount to stats.

**Examples:**

* `+10 fire attack damage`
* `+10 fire spell damage`
* `+25 max health`


### Percent Modifiers

Scale an existing base value.

**Examples:**

* `+10% fire damage`
* `+12% physical damage`

!!!info Behavior
Percent modifiers scale a base that includes the item's *native/base contribution* (not only "other modifiers").
!!!

### Available Modifier Types

Here are some examples of the modifiers available in the system:

| Category | Modifier | Type | Example |
|----------|----------|------|---------|
| **Elemental Damage** | Fire/ice/energy/earth/holy/death/physical | Flat | `+10 fire attack damage` |
| **Damage Increase** | Elemental damage boost | Percentage | `+15% fire damage` |
| **Resistance** | Elemental absorption | Percentage | `+20% fire absorb` |
| **Resistance** | Elemental reduction | Flat | `+15 fire resistance` |
| **Damage Over Time** | Elemental DoT | Flat | `+8 fire damage over time` |
| **Stats** | Health/Mana | Flat | `+50 max health` |
| **Stats** | Health/Mana | Percentage | `+10% max mana` |
| **Critical** | Critical chance | Flat | `+5% critical chance` |
| **Critical** | Critical damage | Percentage | `+25% critical damage` |
| **Recovery** | Health/Mana regen | Flat | `+3 health per second` |
| **Leech** | Life/Mana leech | Percentage | `+5% life leech` |
| **Attributes** | Intelligence/Dexterity/Strength | Flat | `+30 intelligence` |
| **Attributes** | Intelligence/Dexterity/Strength | Percentage | `+10% strength` |

!!!info More Modifiers Available
This table shows a sample of available modifiers. The full system includes modifiers for all seven elements (energy, fire, ice, earth, holy, death, physical) across multiple categories. Modifier values scale with item tier/level.
!!!

---

## Damage Sources: Attacks vs Spells

Modifiers can apply differently depending on whether the damage comes from an **Attack** or a **Spell**.


### Attacks

An **Attack** is a weapon-driven hit:

* Sword/axe/club melee swings
* Wand hits (their on-hit element is still an "attack source")
* Distance attacks


### Spells

A **Spell** is something you cast:

* `exori`
* `exori hur`
* Rune-like spell effects (if treated as spells)

---

## Elemental Components

A hit can have multiple elemental components (physical, fire, ice, energy, etc.).


### Creating Damage Types

If a modifier adds an element, and the hit does **not** already have that element component:

* The element component is **created**, **as long as the modifier matches the hit's source type** (attack vs spell).

**Example 1:**

* `+10 fire attack damage` on a pure physical sword hit:
  * Creates a **fire component** and adds **+10 fire** to it

**Example 2:**

* A wand that normally deals **energy** (attack source)
* Add `+10 fire attack damage`
  * The hit keeps its **energy** component
  * And gains a new **fire** component (+10)


### Percent Modifiers

* `+10% fire damage` applies to **fire damage from attacks and spells**.

---

## Modifier Examples (Fire)


### `+10 fire attack damage`

* Applies only to **attack hits** (weapon-based hits)
* Adds +10 to the hit's **fire** component
* If the hit has no fire component, it **creates one**

**Example:** Wand of Vortex (base energy hit)
**Result:** **energy base** + **new fire component**


### `+10 fire spell damage`

* Applies only to **spell hits** (casted spells)
* Adds +10 to the spell's **fire** component
* If the spell has no fire component, it **creates one**

**Example:** `exori hur` that normally deals physical
**Result:** **physical base** + **new fire component**


### `+10% fire damage`

* Applies to **all fire damage**, regardless of source:
  * Attack fire components
  * Spell fire components
* Scales the total fire base (native + flat adds)

---

## Crafting Currencies

These currencies mutate **rarity**, **modifiers**, and **quality** (when allowed by item eligibility).

!!!danger Important
You can only change Quality/Rarity/Modifiers while the item is **NOT equipped**.
!!!


### Currency Catalogue

| Currency         | Effect                                    | Restrictions              | Use Case                          |
| ---------------- | ----------------------------------------- | ------------------------- | --------------------------------- |
| **Quality**      | +1 Quality (max 20), scales base stats    | Eligible, Quality < 20   | Improve base stats                |
| **Transmutation** | Normal → Uncommon/Magic, 1-2 mods        | Normal only               | Upgrade white items               |
| **Alteration**   | Rerolls all mods, keeps rarity            | Uncommon/Magic only       | Reroll bad mods                   |
| **Augmentation** | +1 mod to Magic                            | Magic with 1 mod only     | Add second mod to Magic           |
| **Chance**       | Normal → random tier                      | Normal only               | Gamble for high tiers             |
| **Scouring**     | Removes all mods, resets to Normal        | Any item                  | Start fresh                       |
| **Regal**        | Magic → Rare, +1 mod, keeps existing       | Magic only                | Upgrade to Rare                   |
| **Alchemy**      | Normal → Rare, 3 mods                     | Normal only               | Fast path to Rare                 |
| **Chaos**        | Rerolls mods and rarity, can upgrade      | 3+ mods (Rare+)           | Reroll everything                 |
| **Annulment**    | Removes 1 random mod                       | Items with mods           | Remove bad mods                   |
| **Exalted**      | +1 mod if capacity allows                 | Rare/Epic with open slots | Fill remaining slots              |
| **Divination**   | Rerolls mod values, keeps mod types        | Items with mods           | Improve values on good mods       |

!!!info Server Tuning
Exact drop rates and some rule details are server-tuned.
!!!

---

## Rules and Safeguards


### No Mutation While Equipped

Quality, rarity, and modifier changes are blocked if the item is in a real equipment slot.

* If it's equipped: the currency/action **fails**
* Unequip it first, then try again


### Quality and Modifiers Are Independent

* **Quality** scales base stats
* **Modifiers** add or scale extra effects
* Quality does **not** multiply modifier values

---

## Quick Examples


### Example A: Quality Scaling

**Serpent Sword:**
* Base: `Atk:18 physical + 8 earth`
* Quality 20 → `Atk:22 physical + 10 earth`


### Example B: Element Creation

**Physical sword hit with `+10 fire attack damage`:**
* Physical remains
* Fire component is created: `+10 fire`


### Example C: Spell vs Attack

* `+10 fire spell damage` affects `exori` casts, not sword swings
* `+10 fire attack damage` affects sword swings, not `exori`
* `+10% fire damage` affects both (any fire component)
