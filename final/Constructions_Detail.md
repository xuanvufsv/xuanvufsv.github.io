# Construction & Upgrades

> 🎮 Crop Shooter · 📅 Version 300326 · ✍️ For Designer Reference & Editing

---

## System Overview

The construction system is divided into 3 main groups. Each construction can be purchased as a Blueprint at the **Builder's Shop**, placed on the map, and upgraded gradually over in-game days.

| Info | Value |
| --- | --- |
| Total constructions | 12 constructions |
| Main currency | Granumz (G) |
| Craftable Gadgets | 8 gadgets (3 groups) |
| Demolish option | Excludes pre-existing constructions |

### Fabricate Gadget Flow

> **1.** Purchase Blueprint at **Builder's Shop** → **2.** Go to **Fabricate Gadget** and press Fabricate → **3.** Gadget is saved (only 1 at a time) → **4.** Move to designated location → **5.** Select placement point on map.

### Garden Flow

> **Pond / Natural Water Sources** (salt water) → **Water Purifier** (filters into fresh water) → **Garden** (waters crops) → Harvest crops.

### All Constructions Table *(sorted by unlock day)*

| # | Name | Group | Blueprint | Unlock Day | Upgrades | Main Function |
| --- | --- | --- | --- | --- | --- | --- |
| 1 | Gear Upgrades | Base | — | Day 1 | 16 | Upgrade player stats (HP, Water, Speed, Backpack) |
| 2 | Farm House | Base | — | Day 1 | — | Sleep to skip the rest of the night |
| 3 | Farm Market | Base | — | Day 1 | 1 | Sell crops / items, dynamic pricing |
| 4 | Garden | Farming | — | Day 1 | 8 | Main farming construction, max 4 plots |
| 5 | Water Purifier | Farming | — | Day 1 | 4 | Filter salt water → fresh water |
| 6 | Refinery | Science Lab | — | Day 1 | — | Item storage (deposit only, no withdrawal) |
| 7 | Treasure Pod | Base | Free | Day 2 | 3 tiers | Scattered across map, reward Granumz + Crops + Blueprints |
| 8 | Builder's Shop | Base | — | Day 4 | — | Purchase Blueprints to unlock constructions |
| 9 | Silo | Storing | — | Day 4 | 3 | Item storage, max 4 ports |
| 10 | Fabricate Gadget | Science Lab | — | Day 4 | — | Craft and place Gadgets on map |
| 11 | Pond | Farming | — | Day 7 | 6 | Natural salt water source |
| 12 | Coop | Farming | — | Day 7 | 4 | Raise chickens for eggs and meat, max 6–12 chickens |

---

## 🏠 Base Construction

Constructions always present in the main farm area. No Demolish option. Unlocked from Day 1 to Day 4.

---

### ⚙️ Gear Upgrades

**Group:** Base · **Unlocks:** Day 1 · **Blueprint:** Not required.

Upgrade personal player stats. Purchase directly through UI, no blueprint needed, available from Day 1.

> 🎨 **Design Note:** These stats directly impact the farming and combat loop. Needs to be balanced so players have a reason to upgrade all modules evenly rather than focusing on just one type.

---

#### Heart Module — Increases max HP · Base: 50

| # | Name | Effect | Cost | Day |
| --- | --- | --- | --- | --- |
| 1 | Heart Module Lv1 | +25 max HP | 350G | Day 4 |
| 2 | Heart Module Lv2 | +50 max HP | 500G | Day 7 |
| 3 | Heart Module Lv3 | +75 max HP | 750G | Day 12 |
| 4 | Heart Module Lv4 | +100 max HP (max) | 900G | Day 17 |

#### Water Module — Increases water capacity · Base: 100

| # | Name | Effect | Cost | Day |
| --- | --- | --- | --- | --- |
| 1 | Water Module Lv1 | +50 water capacity | 350G | Day 2 |
| 2 | Water Module Lv2 | +100 water capacity | 500G | Day 7 |
| 3 | Water Module Lv3 | +150 water capacity (max) | 750G | Day 12 |

#### Boost Module — Increases movement speed · Base: Walk 5 / Run 7

| # | Name | Effect | Cost | Day |
| --- | --- | --- | --- | --- |
| 1 | Boost Module Lv1 | +1 movement speed | 500G | Day 4 |
| 2 | Boost Module Lv2 | +2 movement speed (max) | 950G | Day 12 |

#### Backpack Module — Increases carry capacity · Base: 50

| # | Name | Effect | Cost | Day |
| --- | --- | --- | --- | --- |
| 1 | Backpack Lv1 | +15 capacity | 500G | Day 5 |
| 2 | Backpack Lv2 | +35 capacity | 950G | Day 9 |
| 3 | Backpack Lv3 | +65 capacity | 4,500G | Day 17 |
| 4 | Backpack Lv4 | +85 capacity (max) | 9,000G | Day 21 |

#### Energy Module — Increases stamina regen rate · Base: 100, 10/s

| # | Name | Effect | Cost | Day |
| --- | --- | --- | --- | --- |
| 1 | Energy Module Lv1 | +1 stamina regen | 300G | Day 5 |
| 2 | Energy Module Lv2 | +3 stamina regen | 600G | Day 10 |
| 3 | Energy Module Lv3 | +6 stamina regen (max) | 1,100G | Day 20 |

> - [ ] **TODO:** Define `BASE_UPGRADE_VALUE` — HP value per slot, specific stamina regen per module level.

---

### 🏡 Farm House

**Group:** Base · **Unlocks:** Day 1 · **Blueprint:** Not required.

**Sleep to skip** — skips the rest of the night, jumping straight to 7 AM. Can sleep after clearing all monsters or from 3 AM onward. On wake: fully restores HP and Energy. Increases movement speed for 3 hours by 25%.

> ⚠️ Sleeping early = lost farming minutes (Granumz drops, crops, blueprints). Farm rate needs to be balanced so Sleep is not spammed.

---

### 🏪 Farm Market

**Group:** Base · **Unlocks:** Day 1 · **Blueprint:** Not required.

Sell crops and items for Granumz. Dynamic pricing system uses **Perlin Noise + supply/demand differential**. Selling more of one type → price drops. Encourages players to diversify their crops.

> 💡 **Dynamic Pricing:** Uses Perlin Noise combined with the sales volume difference between item types. Selling too much of one type → price drops. Diversify the selling catalog to maintain good prices.

| # | Name | Effect | Cost | Day | Type |
| --- | --- | --- | --- | --- | --- |
| 1 | Selling Boost | +5% sell value on all items (×2 times) | Free | — | Unlock Event |

---

### 📦 Treasure Pod

**Group:** Base · **Unlocks:** Day 2 · **Blueprint:** Free — fixed spawn across map.

Scattered at fixed positions across the map, from simple terrain to challenging locations (cliff gaps, tall trees…). Access difficulty varies — requires platforming skill and HandGun. Rewards: **Granumz + Crops + Potion + Lv3 Fabricate Gadget Blueprint**.

> 🎨 **Level Design:** Treasure Pod locations need a clear difficulty gradient. Lv3 Pods must require a high skill ceiling — rewards are intended exclusively for hardcore players, providing high-tier gadget blueprints.

| # | Tier | Reward | Appears On | Type |
| --- | --- | --- | --- | --- |
| 1 | Treasure Pod Lv1 | Standard pod — common rewards | Day 2 | — |
| 2 | Treasure Pod Lv2 | Medium difficulty — better rewards | Day 8 | Milestone |
| 3 | Treasure Pod Lv3 | Hard reach — blueprint + rare item drop | Day 15 | Milestone |

---

### 🔨 Builder's Shop

**Group:** Base · **Unlocks:** Day 4 · **Blueprint:** Not required.

Purchase Blueprints with Granumz to unlock new constructions and Fabricate Gadgets.

> 💡 **Note:** Some WarpTech Lv3 Gadgets can only be unlocked via **Treasure Pod Lv3**, not purchasable here.

---

## 🌿 Farming Construction

> ⚠️ **Demolish required** — All Farming constructions can be Demolished so players can destroy and replace them with other constructions.

---

### 🌱 Garden

**Group:** Farming · **Unlocks:** Day 1 · **Blueprint:** Not required · 🔴 Demolish required.

Main farming construction. Starts with 1 plot — each plot grows 1 crop type. Crops = ammo = crafting materials. Max 4 plots after upgrades.

| # | Name | Effect | Cost | Day | Type |
| --- | --- | --- | --- | --- | --- |
| 1 | Additional Plot II | Unlocks 2nd plot | 350G | Day 1 | — |
| 2 | Additional Plot III | Unlocks 3rd plot | 350G | Day 1 | — |
| 3 | Additional Plot IV | Unlocks 4th plot (max) | 350G | Day 1 | — |
| 4 | Nutrient Soil | +25% max harvest yield for all crops | 500G | Day 5 | — |
| 5 | Alluvium Soil | -20% grow time permanently for all crops | 900G | Day 8 | — |
| 6 | Sprinkler | Auto-waters all plots — no manual watering required | 1,500G | Day 10 | — |
| 7 | Auto Harvest | Automatically harvests into Silo when crops are ripe | 1,800G | Day 15 | — |
| 8 | Miracle Mix | +Rotten timer · +Harvest count | Free | — | Achievement |

> 🏆 **Miracle Mix:** Unlocked after defeating 4 bosses (Day 5 / 10 / 15 / 20). Important mid-game reward — boss milestones need clear design.

> - [ ] **TODO:** Define `BASE_UPGRADE_VALUE` — % yield increase from Nutrient Soil, grow time reduction value from Alluvium Soil.

---

### 🏚️ Silo

**Group:** Storing · **Unlocks:** Day 4 · **Blueprint:** Not required · 🔴 Demolish required.

Item storage. Each port holds up to **150 items of the same type**. Starts with 1 port (Port I), max 4 ports.

| # | Name | Effect | Cost | Day |
| --- | --- | --- | --- | --- |
| 1 | Additional Storage II | Unlocks 2nd port | 500G | Day 4 |
| 2 | Additional Storage III | Unlocks 3rd port | 500G | Day 4 |
| 3 | Additional Storage IV | Unlocks 4th port (max) | 1,100G | Day 4 |

> - [ ] **TODO:** Define optimal max capacity (currently 150 — *modify later*).

---

### 💧 Pond

**Group:** Farming · **Unlocks:** Day 7 · **Blueprint:** Not required · 🔴 Demolish required.

Holds water generated from natural sources. Capable of auto-refill with cooldown. Provides **salt water** — must pass through Water Purifier before use in Garden.

| # | Name | Effect | Cost | Day |
| --- | --- | --- | --- | --- |
| 1 | More Water I | +20 max water capacity | 350G | Day 7 |
| 2 | Decrease Cooldown I | -20% refill cooldown | 350G | Day 7 |
| 3 | More Water II | +30 max water capacity | 500G | Day 7 |
| 4 | Decrease Cooldown II | -20% refill cooldown | 500G | Day 7 |
| 5 | More Water III | +50 max water capacity | 1,300G | Day 7 |
| 6 | More Water IV | +100 max water capacity (max) | 1,300G | Day 7 |

---

### 🔬 Water Purifier

**Group:** Farming · **Unlocks:** Day 1 · **Blueprint:** Not required · 🔴 Demolish required.

Filters water from Pond or Natural Water Sources. Converts **Salt Water → Fresh Water** for watering crops in the Garden. Runs automatically during Sleep phase.

| # | Name | Effect | Cost | Day |
| --- | --- | --- | --- | --- |
| 1 | More Water Contain I | +25 tank capacity | 350G | Day 1 |
| 2 | Decrease Purifier Time I | -25% purification time | 350G | Day 5 |
| 3 | More Water Contain II | +25 tank capacity | 500G | Day 7 |
| 4 | More Water Contain III | +50 tank capacity (max) | 1,100G | Day 10 |

> - [ ] **TODO:** Define `BASE_UPGRADE_VALUE` — default capacity, initial purification time.

---

### 🐔 Coop

**Group:** Farming · **Unlocks:** Day 7 · **Blueprint:** Not required · 🔴 Demolish required.

Raise chickens to produce eggs and meat. Max **6 chickens (base)**, expandable to 12. A Hen + Rooster pair breeds every 12h in-game. Chickens age out after 6 breeding cycles and automatically convert to meat.

| # | Name | Effect | Cost | Day |
| --- | --- | --- | --- | --- |
| 1 | High Wall | Prevents Monsters from attacking chickens at night | 900G | Day 7 |
| 2 | Bug Free Spring Grass | +% max egg production — chickens eat natural grass | 900G | Day 7 |
| 3 | Vitamizer | -20% breeding time · +10% egg production rate | 1,200G | Day 7 |
| 4 | Expand Coop | Increases max chickens from 6 → 12 | 2,000G | Day 7 |

> - [ ] **TODO:** Define `BASE_UPGRADE_VALUE` — base eggs/day, breeding rate, chick → adult grow time.

---

## 🧪 Science Lab — Fabricate Gadgets

The Science Lab is the central technology hub, consisting of 3 sub-systems: **Refinery**, **Fabricate Gadget**, and **Builder's Shop**.

> **Refinery:** Central item storage — deposit only, no withdrawal. Connects with Refinery Link for remote loading.
> **Builder's Shop:** Purchase Blueprints with Granumz. Some Lv3 Gadget Blueprints are only available from Treasure Pods.
> **Fabricate Gadget:** Craft Gadgets from unlocked Blueprints. Stores 1 Gadget at a time, placed on the map at a designated location.

---

### ⛏️ Extractors

Automatically extract resources. Placed on resource nodes or near constructions. Each gadget has 3 levels — higher levels increase speed and output.

---

#### Drill

**Unlocks:** Day 4 · **Blueprint:** 500G · Extract Time: 18h/cycle · Output: 10–40 items/cycle

| Level | Output | Cost |
| --- | --- | --- |
| Lv1 | 10–20 items | 450G |
| Lv2 | 20–30 items | 800G |
| Lv3 | 30–40 items | 1,300G |

#### Water Pump

**Unlocks:** Day 7 · **Blueprint:** 750G · Pump Time: 6h/cycle · Output: 100–200 water/cycle

| Level | Output | Cost |
| --- | --- | --- |
| Lv1 | 100 water | 450G |
| Lv2 | 150 water | 800G |
| Lv3 | 200 water | 1,300G |

#### Apiary

**Unlocks:** Day 7 · **Blueprint:** 750G · Honey Time: 12h/cycle · Output: Low–High honey/cycle

| Level | Output | Cost |
| --- | --- | --- |
| Lv1 | Low honey/cycle | 500G |
| Lv2 | Medium honey/cycle | 900G |
| Lv3 | High honey/cycle (max) | 1,400G |

> - [ ] **TODO:** Define `BASE_UPGRADE_VALUE` for Extractors — base max yield, upgrade value per level.

---

### 🛡️ Utilities

Support gadgets for combat and quality-of-life. Place near base.

---

#### Crop Turret

**Unlocks:** Day 10 · **Blueprint:** 1,800G · Ammo Cap: 50–350 crops · Fire Rate: 1 shot/2s · Range: 8m

> 🎨 **Design Note:** Load crops as ammo to automatically shoot monsters during night phase. Higher levels unlock higher crop tiers and increase total ammo capacity.

| Level | Description | Ammo Cap | Tier | Fire Rate | Cost |
| --- | --- | --- | --- | --- | --- |
| Lv1 | Basic auto-fire at nearby enemies | 50 | T1 | 1/2s | 1,500G |
| Lv2 | Faster fire rate, higher capacity | 200 | T1-2 | 1/1.5s | 4,000G |
| Lv3 | Max capacity, all crop tiers (max) | 350 | All | 1/1s | 9,000G |

#### Med Station

**Unlocks:** Day 13 · **Blueprint:** 900G · Heal: 100 HP · Cooldown: 4h · Range: 3m

> 🎨 **Design Note:** Healing zone when standing nearby. Higher levels reduce cooldown and increase HP healed per use. Cooldown between uses needed to prevent abuse.

| Level | Description | Heal | Cooldown | Range | Cost |
| --- | --- | --- | --- | --- | --- |
| Lv1 | Base heal station | 100 HP | 4h | 3m | 500G |
| Lv2 | Improved healing | 125 HP | 3h | 4m | 900G |
| Lv3 | Max healing (max) | 150 HP | 3h | 5m | 1,300G |

> - [ ] **TODO:** Define `BASE_UPGRADE_VALUE` — Turret damage per crop tier, balance heal vs HP pool.

---

### 🌀 WarpTech

Advanced remote-control technology. **All require Blueprint from Treasure Pod Lv3**, not purchasable at Builder's Shop.

> 🗝️ **WarpTech Unlock:** Only unlockable via **Treasure Pod Lv3** (hard reach). This is late-game tech, creating differentiation between casual and dedicated players.

---

#### Refinery Link *(Blueprint only)*

**Unlocks:** Day 15 · **Cost:** 2,000G · **Range:** Entire map · No upgrades.

Remotely loads items into the Refinery. Reduces Backpack pressure when farming far from base.

#### Turret Link *(Blueprint only)*

**Unlocks:** Day 16 · **Cost:** 4,500G · No upgrades.

Automatically loads crops from a designated plot into the nearest Crop Turret. Combined with Garden Auto Harvest, creates a complete automation loop.

#### Market Link *(Blueprint only)*

**Unlocks:** Day 18 · **Cost:** 4,500G · No upgrades.

Sell items remotely — no need to travel back to Farm Market. Convenient during daytime farming.

> - [ ] **TODO:** Define `BASE_UPGRADE_VALUE` for WarpTech — default transfer cooldown of Refinery Link.

---

## 💰 Economy & Granumz

All upgrade costs use **Granumz (G)** — the main in-game currency. Primary income source is the Farm Market.

> ✅ **Full game max cost breakdown:**
>
> **Gear Upgrades (no Blueprint required):**
> Heart ×4: 2,500G · Water ×3: 1,600G · Boost ×2: 1,450G · Backpack ×4: 14,950G · Energy ×3: 2,000G
> **Subtotal Gear Upgrades: 22,500G**
>
> **Farming & Storing (Build + all upgrades):**
> Farm Market: Free · Garden: 250G build + 5,750G upgr · Silo: 450G build + 2,100G upgr · Pond: 450G build + 4,300G upgr · Water Purifier: 2,300G · Coop: 250G build + 5,000G upgr
> *(Build costs: Garden 250G · Silo 450G · Pond 450G · Coop 250G — one-time construction costs, separate from blueprint & upgrade costs.)*
> **Subtotal Farming & Storing: 20,850G**
>
> **Gadgets (Blueprint + all upgrades):**
> Drill: 3,050G · Water Pump: 3,300G · Apiary: 3,550G · Crop Turret: 16,300G · Med Station: 3,600G · Refinery Link: 2,000G · Turret Link: 4,500G · Market Link: 4,500G
> **Subtotal Gadgets: 40,800G**
>
> **🏆 Grand Total (Gear 22,500 + Farming 20,850 + Gadgets 40,800): 84,150G**

> 🎨 **Dynamic Pricing System:** Farm Market uses Perlin Noise + supply/demand tracking. Selling too much of one crop type → price drops (inflation). Encourages players to diversify crops and optimize their daily selling catalog.
