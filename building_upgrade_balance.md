# BUILDINGS & UPGRADES — FORMULAS + BALANCE NOTES

## 1. Upgrade Scaling Philosophy
- Early: Strong impact, clear progression
- Mid: Diminishing returns
- Late: Expensive + specialized

---

## 2. Cost Formula

Cost_n = BaseCost × Growth^(n-1)

Recommended:
- Growth = 1.5 → 2.2

Example:
Level 1: 100
Level 2: 180
Level 3: 324
Level 4: 583
Level 5: 1049

---

## 3. Effect Formulas

### Additive (slots, ports)
Value_n = Base + n × Step

### Multiplicative (yield, damage)
Value_n = Base × (1 + k × n)
k = 0.1 → 0.25

### Time Reduction
Time_n = BaseTime × (1 - r)^n
r = 0.15 → 0.25
Clamp: ≥ 30–40% BaseTime

### Capacity Scaling
Capacity_n = Base × (1 + n^1.2)

### Automation Value
EffectiveGain = (ManualTime - AutoTime) × Efficiency

---

## 4. Applied to Systems

### Garden
- Plot: +1 each upgrade
- Yield: +15%/level
- Grow Time: -12%/level (min 40%)
- Auto Harvest: unlock

### Pond
- Capacity: n^1.2
- Cooldown: -10%

### Water Purifier
- Speed: -15%
- Capacity: +25%

### Coop
- Breeding Time: -10%
- Yield: +10%
- Capacity: +fixed

### Silo
- Port: +1
- Capacity: +50%

### Turret
- Fire Rate: +12%
- Capacity: +30%
- Tier unlock: discrete

---

## 5. Critical Balance Risks & Fixes

### 5.1 Infinite Farming Loop
Garden → Crop → Sell → Upgrade → Repeat

Fix:
- Dynamic pricing
- Rot time
- Storage limit

---

### 5.2 Water System Collapse
Purifier too fast → infinite water

Fix:
- Add energy cost
- Maintenance
- Efficiency cap

---

### 5.3 Coop Exploit

Current:
Egg = random(1–3) × max(H, R)

Fix:
Egg = random(1–3) × min(H, R)
OR
Egg = random × (H × R)

---

### 5.4 Idle Automation Abuse
Auto Harvest + Large Silo → AFK gameplay

Fix:
- Resource decay
- Maintenance cost
- Energy system

---

### 5.5 Turret Replacing Player

Fix:
- Limit to 40–60% player DPS
- Reduce range
- Target limitations

---

### 5.6 Bottle System Overpower

Fix:
- Global cooldown
- Limit stack
- Diminishing effects

---

### 5.7 Sleep Exploit

Fix:
- Growth tied to real-time
- Sleep reduces efficiency

---

### 5.8 Refinery Friction

Fix:
- Show output preview
- Allow limited retrieval

---

## 6. Final Notes

- Every upgrade must:
  - Provide clear value
  - Avoid breaking the game
  - Create meaningful decisions

- Core Risk Areas:
  - Coop system
  - Water system
  - Automation layer

