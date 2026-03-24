# GDD — Crop Shooter v2.3
**Design Overview**

> 1 ngày = 24 phút thực · Day 12' / Night 8' / Sleep 4' · WIP sections được đánh dấu

---

## Mục lục
1. [Vòng Thời Gian](#1-vòng-thời-gian)
2. [Core Loop](#2-core-loop)
3. [Progression — Unlock Timeline](#3-progression--unlock-timeline)
4. [Cây Trồng (Crops)](#4-cây-trồng-crops)
5. [Recipes — Crafting Station](#5-recipes--crafting-station)
6. [Bottle System](#6-bottle-system)
7. [Special Craft](#7-special-craft)
8. [Coop — Hen & Rooster](#8-coop--hen--rooster)
9. [Tổng quan công trình](#9-tổng-quan-công-trình)
10. [Farming Buildings](#10-farming-buildings)
11. [Science Lab](#11-science-lab)
12. [Base Construction](#12-base-construction)
13. [Achievement System](#13-achievement-system)

---

## 1. Vòng Thời Gian

### ☀️ Ban Ngày — 12'
- ⛏️ Thu khoáng sản, mở Treasure Pod
- 🌱 Trồng & thu hoạch trái cây tại Garden
- ⚗️ Craft tại Crafting Station
- 🐔 Cho gà ăn, thu trứng / thịt tại Coop
- 🏗️ Nâng cấp công trình tại Builder's Shop
- 🔧 Xây Gadget qua Fabricate Gadget
- 🔫 Nạp đạn Crop Turret

### 🌙 Ban Đêm — 8'
- 👾 Quái xuất hiện theo wave
- 🍅 Bắn quái bằng súng trái cây
- 🧪 Kích hoạt Bottle hỗ trợ
- 🤖 Crop Turret tự động bắn
- ⚠️ Quái có thể tấn công Coop — ăn gà
- 💎 Drop: Granumz, trái cây, blueprint
- 💀 Drop: Monster Meat → nguyên liệu craft

### 💤 Sleep Phase — 4'
- 😴 Ngủ sau khi đánh xong hoặc từ 3h sáng
- ⚙️ Máy móc tiếp tục chạy tự động
- ⏳ Ngủ sớm = mất phút farm ban đêm
- 💧 Water Purifier, Crafting Station chạy nền

> **Sleep Buff:** Hồi đầy HP & Energy khi thức dậy.

---

## 2. Core Loop

```
🌾 Farm → ⚗️ Process → 🎒 Prepare → ⚔️ Fight → 🏗️ Upgrade → (lặp lại)
```

- **Farm:** Thu hoạch trái cây, khai thác khoáng sản
- **Process:** Craft Bottle & Food, lọc nước, chế nguyên liệu
- **Prepare:** Chọn đạn, chuẩn bị Bottle, nạp Crop Turret
- **Fight:** Tiêu diệt wave quái, nhận Granumz & drop
- **Upgrade:** Mở blueprint, xây & nâng cấp công trình

### Nguyên lý: Đạn = Vật Phẩm

1 lần thu hoạch = 1 đạn = 1 nguyên liệu craft. Trái cây dạng bó (Wheat): 1 lần thu hoạch = 1 bó = n items.

Người chơi tự phân chia mục đích sử dụng: 🔫 Đạn · 🧪 Craft Bottle · 🍞 Food · 💰 Bán Granumz · 🐔 Thức ăn gà · ⚗️ Ingredient

---

## 3. Progression — Unlock Timeline

### Day 1 — Starting gear
🫐 Berry (AR) · 🌾 Wheat (SMG) · ⚡ Power Shard · 🔩 Iron / Copper · 🪵 Wood / Stone / Sand · 💀 Monster Meat (đêm drop) · 🌱 Garden · 💧 Water Purifier · ⚗️ Crafting Station · 🏚 Silo · 🏞 Pond

### Day 2 — First discoveries
🪨 Coal vein (shallow caves) · 🧱 Metal Scrap (ruins) · 💎 Treasure Pod #1

### Day 3 — New crops & ingredients
🌱 Bean (SMG ammo) · 🥕 Carrot · 🥬 Cabbage · 🥥 Coconut · 🛢️ Bean Oil (craft) · 🧴 Coconut Oil (craft) · 🧈 Margarine = Bean Oil×3 + Coconut Oil×1

### Day 5 — First expansion
🫚 Beetroot → Sugar · 🧪 Glass Vial Lv1 (9 Sand) · 🥐 Flour / Sugar available · 🍞 Bread +5HP · 🍳 Omelet +25HP · 🥖 Soggy Bread +30HP `STEALTH` · 🎂 Berry Cake +20HP · 🧊 Frost Bottle · 🐔 Coop available (blueprint từ Pod)

### Day 6 — Tomato unlock + Cabbage Sauce
🍅 Tomato (Shotgun) `[Trigger: 🗡 Kill 300 monsters]` · 🥣 Cabbage Sauce (Cabbage×8 + Sugar) · 🍔 Burger Berry +20HP → Rapidfire Bottle · ⚡ Rapidfire Bottle

### Day 8 — Grape & mid-game food
🍇 Grape `[Trigger: 📦 Open Treasure Pod]` · 🌿 Spring Grass upgrade (Coop) · 🥪 Hot Bunny +15HP (Ap-pleClear ×1/3) · 🧁 Carrot Cake +40HP (Ap-pleClear ×2/3) · 🍡 Sweet Grapeball +20HP → Cluster Bottle

### Day 10 — Mid game
⭐ Carambola (Sniper) `[Trigger: ⚔️ Defeat first Boss]` · 🌶️ Chili (Flamethrower) · 🖤 Coal (caves) · 🍦 Cream ingredient (Coconut Milk×3 + Sugar + Egg×6) · 🍲 Tomato Soup +75HP → Crit Bottle · 🤖 Crop Turret (blueprint)

### Day 11 — Automation begins
⛏️ Drill Gadget Lv1 · 🔗 Refinery Link · 🍯 Honey (Apiary Gadget) `[Trigger: 🤖 Place first Apiary]` · 🎯 Crit Bottle

### Day 13 — Mid-late food & bottles
🌭 Burnwich +35HP → Blaze Bottle · 🔥 Red Alert Salad +50HP → Venom Bottle · 🌟 Carambola Cake +60HP → Arc Bottle · 🔆 Blaze Bottle · 🐍 Venom Bottle

### Day 15 — Late game
🍎 Apple (Grenade) · 🫑 Pepper (Toxic Grenade) · 💎 Ruby (deep caves) · 🔬 Glass Vial Lv2 (Vial Lv1×2 + Ruby×2) · ☠️ Poison Shard / Acid Shard · 💥 Cluster Bottle

### Day 16 — Pre-endgame
🚀 Ap-pleClear Ca-Rotket (Special) · 🥧 Apple Pie +100HP (Ap-pleClear ×3/3) · 🥗 Fresh Salad +150HP → Corrosion Bottle · 🍰 Honey Cake +80HP → Miasma Bottle · 🟢 Corrosion Bottle · 🔗 Turret Link / Market Link · 💊 Vitamizer: tốc độ sinh sản tăng · 🐔 Expand Coop → 20 slot

### Day 20 — End game
🌵 Durian *(WIP)* · 🍈 Noni Fruit *(WIP)* · 💛 Gold Crystal (mountains) · ⚗️ Glass Vial Lv3 (Vial Lv2×2 + Gold Crystal×2) · 🌩️ Arc Bottle

### Day 21 — Final unlock
☁️ Miasma Bottle

---

## 4. Cây Trồng (Crops)

| Icon | Tên | Unlock | Trigger | Súng | Yield | Dùng làm |
|------|-----|--------|---------|------|-------|----------|
| 🫐 | Berry | Day 1 | — | AR | 1 quả | Đạn, Frost Bottle |
| 🌾 | Wheat *(1 bó = 3 đơn vị)* | Day 1 | — | SMG | 3/bó | Đạn, Flour, Thức ăn gà |
| 🌱 | Bean | Day 3 | — | SMG | 1 quả | Đạn, Bean Oil |
| 🥕 | Carrot | Day 3 | — | — | 1 quả | Hot Bunny, Carrot Cake, Red Alert Salad |
| 🥬 | Cabbage | Day 3 | — | — | 1 quả | Cabbage Sauce, Burger Berry |
| 🥥 | Coconut | Day 3 | — | — | 1 quả | Coconut Oil, → Coconut Milk |
| 🫚 | Beetroot | Day 5 | — | — | 1 quả | Sugar (9 beet = 1 sugar) |
| 🍇 | Grape | Day 8 | 📦 Open Treasure Pod | (special) | 1 quả | Đạn, Sweet Grapeball, Cluster Bottle |
| 🍅 | Tomato | Day 6 | 🗡 Kill 300 monsters | Shotgun | 1 quả | Đạn, Tomato Soup, Red Alert Salad, → Crit Bottle |
| ⭐ | Carambola | Day 10 | ⚔️ Defeat first Boss | Sniper | 1 quả | Đạn, Carambola Cake, Fresh Salad, Arc Bottle |
| 🌶️ | Chili | Day 10 | — | Flamethrower | 1 quả | Đạn, Burnwich, Red Alert Salad, Blaze Bottle |
| 🍎 | Apple | Day 15 | — | Grenade | 1 quả | Đạn, Apple Pie, Ap-pleClear |
| 🫑 | Pepper | Day 15 | — | Toxic Grenade | 1 quả | Đạn, Fresh Salad, Venom Bottle |
| 🌵 | Durian *(WIP)* | Day 20 | — | — | 1 quả | Miasma Bottle |
| 🍈 | Noni Fruit *(WIP)* | Day 20 | — | — | 1 quả | Corrosion Bottle (legacy) |

> ⚠ **Wheat dual-use:** 1 bó = 3 đạn SMG HOẶC 1 Flour. Khuyến nghị ~2 bó đạn / 1 bó food / 1 bó gà (4 plot Garden).  
> **Beetroot thay Sugar Cane:** Sugar nay craft từ 9 Beetroot (3×3). Sugar Cane đã bị loại bỏ khỏi game.

---

## 5. Recipes — Crafting Station

### Nguyên liệu khoáng sản / Vials

| Icon | Tên | Recipe | Dùng để | Day |
|------|-----|--------|---------|-----|
| 🔋 | Power Core | ⚡ Power Shard + 🔧 Metal Scrap + 🔩 Iron | Mở công trình cơ bản | Day 0 |
| 💡 | Circuit | ⚡ Power Shard + 🔧 Metal Scrap + 🟤 Copper | Mở công trình điện tử | Day 0 |
| 🧪 | Glass Vial Lv1 | 🟡 Sand ×9 | Craft Bottle Tier 1–2 | Day 5 |
| 🔬 | Glass Vial Lv2 | 🧪 Vial Lv1 ×2 + 💎 Ruby ×2 | Craft Bottle Tier 3 | Day 15 |
| ⚗️ | Glass Vial Lv3 | 🔬 Vial Lv2 ×2 + 💛 Gold Crystal ×2 | Craft Bottle Tier 4 | Day 20 |
| ☠️ | Poison Shard | 🗑️ Trash ×6 + 🟡 Sand ×3 | Miasma Bottle | Day 15 |
| 💧 | Acid Shard | 🗑️ Trash ×6 + 🔧 Metal Scrap ×3 | (legacy Corrosion) | Day 15 |

### Nguyên liệu thực phẩm (Ingredients)

| Icon | Tên | Recipe | Dùng để | Day |
|------|-----|--------|---------|-----|
| 🥐 | Flour | 🌾 Wheat ×9 | Bread, Berry Cake, Apple Pie… | Day 1 |
| 🍬 | Sugar | 🫚 Beetroot ×9 | Nhiều food & bottles | Day 5 |
| 🥛 | Coconut Milk | 🥥 Coconut ×3 | Cream, Carrot Cake… | Day 3 |
| 🛢️ | Bean Oil | 🌱 Bean ×9 | Margarine | Day 3 |
| 🧴 | Coconut Oil | 🥥 Coconut ×9 | Margarine | Day 3 |
| 🧈 | Margarine | 🛢️ Bean Oil ×3 + 🧴 Coconut Oil ×1 | Tomato Soup, Burnwich | Day 3 |
| 🥣 | Cabbage Sauce | 🥬 Cabbage ×8 + 🍬 Sugar ×1 | Burnwich, Carambola Cake | Day 6 |
| 🍦 | Cream | 🥛 Coconut Milk ×3 + 🍬 Sugar ×1 + 🥚 Egg ×6 | Apple Pie (ingredient only) | Day 10 |

### Foods

| Icon | Tên | Recipe | HP | Mechanic | Day |
|------|-----|--------|----|----------|-----|
| 🍞 | Bread | 🥐 Flour + 🍬 Sugar + 🥐 Flour | +5 HP | — | Day 5 |
| 🍳 | Omelet | 🥚 Egg ×18 | +25 HP | **REGEN** | Day 5 |
| 🎂 | Berry Cake | 🥐 Flour + 🫐 Berry ×8 + 🍬 Sugar | +20 HP | **BOTTLE** → Frost Bottle | Day 5 |
| 🥖 | Soggy Bread | 🥐 Flour + 💀 Monster Meat ×4 | +30 HP | **STEALTH** — Quái bỏ qua bạn tạm thời | Day 5 |
| 🍔 | Burger Berry | 🥐 Flour + 🥬 Cabbage ×4 + 🫐 Berry ×8 | +20 HP | **BOTTLE** → Rapidfire Bottle | Day 6 |
| 🥪 | Hot Bunny | 🥕 Carrot ×8 + 🧈 Margarine ×1 | +15 HP | **SPECIAL** — Ap-pleClear 1/3 | Day 8 |
| 🍡 | Sweet Grapeball | 🍇 Grape ×16 + 🍬 Sugar ×1 | +20 HP | **BOTTLE** → Cluster Bottle | Day 8 |
| 🧁 | Carrot Cake | 🥕 Carrot ×5 + 🥛 Coconut Milk ×3 + 🍬 Sugar ×1 | +40 HP | **SPECIAL** — Ap-pleClear 2/3 | Day 8 |
| 🍲 | Tomato Soup | 🍅 Tomato ×8 + 🧈 Margarine ×1 + 🍬 Sugar ×1 | +75 HP (+5/s×10s) | **BOTTLE** → Crit Bottle | Day 10 |
| 🌭 | Burnwich | 🥐 Flour + 🌶️ Chili ×8 + 🥣 Cabbage Sauce ×1 | +35 HP | **BOTTLE** → Blaze Bottle | Day 13 |
| 🔥 | Red Alert Salad | 🌶️ Chili ×8 + 🍅 Tomato ×8 + 🥕 Carrot ×4 | +50 HP | **BOTTLE** → Venom Bottle | Day 13 |
| 🌟 | Carambola Cake | ⭐ Carambola ×10 + 🥛 Coconut Milk ×3 + 🥣 Cabbage Sauce ×1 | +60 HP | **BOTTLE** → Arc Bottle | Day 13 |
| 🥧 | Apple Pie | 🍎 Apple ×10 + 🥐 Flour ×1 + 🍦 Cream ×1 | +100 HP | **SPECIAL** — Ap-pleClear 3/3 | Day 16 |
| 🍰 | Honey Cake | 🍯 Honey ×6 + 🥐 Flour ×1 + 🥛 Coconut Milk ×3 | +80 HP | **BOTTLE** → Miasma Bottle | Day 16 |
| 🥗 | Fresh Salad | 🍅 Tomato ×8 + ⭐ Carambola ×10 + 🫑 Pepper ×10 | +150 HP (+15/s×10s) | **BOTTLE** → Corrosion Bottle | Day 16 |

---

## 6. Bottle System

**Loại effect:** ❄ Slow · 🔥 Fire · ⚡ Crit · 💥 Damage · 🏃 Speed · 💫 Split · ☠ Poison · ⚡ Chain · 🧪 Corrosion · 🕶 Stealth

### Tier 1 — Day 5–6 · Vial Lv1

| Icon | Tên | Effect | Duration | Compatible | Recipe |
|------|-----|--------|----------|------------|--------|
| 🧊 | Frost Bottle | ❄ Slow 30–70% · Freeze 30% · +50% dmg if frozen | 12s | SMG · AR | 🎂 Berry Cake ×8 + Vial Lv1 + 🔩 Iron ×2 |
| ⚡ | Rapidfire Bottle | 🏃 +50% fire rate | 8s | AR · SMG · Shotgun | 🍔 Burger Berry ×8 + Vial Lv1 + 🔩 Iron ×2 |

### Tier 2 — Day 10–13 · Vial Lv1

| Icon | Tên | Effect | Duration | Compatible | Recipe |
|------|-----|--------|----------|------------|--------|
| 🎯 | Crit Bottle | ⚡ 100% Crit × 2 dmg | 10s | AR · Shotgun · Sniper | 🍲 Tomato Soup ×8 + Vial Lv1 + 🔩 Iron ×2 |
| 🔆 | Blaze Bottle | 🔥 +30% dmg · fire trail 3/s × 4s | 10s | Flamethrower · AR | 🌭 Burnwich ×8 + Vial Lv1 + 🖤 Coal ×2 |
| 🐍 | Venom Bottle | ☠ Poison cloud 4–10 dmg/s · Lv2: pierce shields | 12s | Toxic Grenade | 🔥 Red Alert Salad ×8 + Vial Lv1 + 🖤 Coal ×2 |

### Tier 3 — Day 15–16 · Vial Lv2

| Icon | Tên | Effect | Duration | Compatible | Recipe |
|------|-----|--------|----------|------------|--------|
| 💥 | Cluster Bottle | 💫 Split → 3 targets 50% dmg | 8s | Grenade · Shotgun | 🍡 Sweet Grapeball ×8 + Vial Lv2 + 💎 Ruby ×2 |
| 🟢 | Corrosion Bottle | 🧪 Stack +2/4/6/8/10 dmg · Lv2: pierce shields | 10s | Shotgun · Sniper | 🥗 Fresh Salad ×10 + Vial Lv2 + 💎 Ruby ×2 |

### Tier 4 — Day 20–21 · Vial Lv3

| Icon | Tên | Effect | Duration | Compatible | Recipe |
|------|-----|--------|----------|------------|--------|
| 🌩️ | Arc Bottle | ⚡ Chain 3 enemies 60% dmg · Lv2: +20%/chain | 8s | SMG | 🌟 Carambola Cake ×10 + Vial Lv3 + 💛 Gold Crystal ×2 |
| ☁️ | Miasma Bottle | ☠ Cloud 60% density · 10 dmg/s · Lv2: 5m AoE | 12s | Grenade | 🍰 Honey Cake ×8 + Vial Lv3 + ☠️ Poison Shard ×2 |

> **Recipe pattern:** Tất cả Bottle đều dùng food tương ứng ×8–10 + Vial phù hợp + khoáng sản. Food "carrier" quyết định loại Bottle — người chơi cần cân đối farm food để ăn vs craft Bottle.

---

## 7. Special Craft

### 🚀 Ap-pleClear Ca-Rotket
**Day 16** · One-use per night · Long cooldown

**Recipe:** 🥪 Hot Bunny ×1 + 🧁 Carrot Cake ×1 + 🥧 Apple Pie ×1

**Effect:** Triệu hồi một quả tên lửa cà rốt khổng lồ mang theo bom táo. Massive AoE — tiêu diệt toàn bộ quái trong phạm vi. Chỉ dùng được 1 lần mỗi đêm, cooldown rất dài. Cần craft đủ cả 3 thành phần là 3 loại food riêng biệt (Hot Bunny ở Day 8, Carrot Cake ở Day 8, Apple Pie ở Day 16).

**Unlock path:** Hot Bunny (1/3) → Carrot Cake (2/3) → Apple Pie (3/3)

---

## 8. Coop — Hen & Rooster

### Lifecycle Gà

```
🐔 Hen/Rooster (6 lần sinh sản)
  → 🥚 Đẻ Egg (mỗi 12h in-game)
  → 🐣 Nở 24h (50/50 Hen·Rooster)
  → 🍖 Thịt bình thường (hết 6 lần sinh sản)
```

**Penalty khi mất cân bằng:**
- 📉 CL Penalty: -1 sinh sản + CL/đợt
- ⚠️ Overwork: thịt chỉ 50% khi vượt ngưỡng

**Thông số cơ bản:**
- Số trứng/đợt = random(1–3) × số con phía nhiều hơn
- Thức ăn: 🌾 200 Wheat / con / ngày
- Tỉ lệ nở: 50/50, tự điều chỉnh ±5% mỗi lần nở
- Khuyến nghị: giữ chênh lệch ≤ 1 để tránh overwork

### Sản lượng trứng — CL = 0 (Cân bằng)

| H–R | CL | Egg/đợt | Đợt | Min | Max |
|-----|----|---------|-----|-----|-----|
| 1–1 | 0 | 1–3 | 6 | 6 | 18 |
| 2–2 | 0 | 2–6 | 6 | 12 | 36 |
| 3–3 | 0 | 3–9 | 6 | 18 | 54 |
| 4–4 | 0 | 4–12 | 6 | 24 | 72 |
| 5–5 | 0 | 5–15 | 6 | 30 | 90 |
| 6–6 | 0 | 6–18 | 6 | 36 | 108 |

### Sản lượng trứng — CL = 1

| H–R | CL | Egg/đợt | Đợt | Min | Max |
|-----|----|---------|-----|-----|-----|
| 1–2 | 1 | 2–6 | 3 | 6 | 18 |
| 2–3 | 1 | 3–9 | 4 | 12 | 36 |
| 3–4 | 1 | 4–12 | 5 | 20 | 60 |
| 4–5 | 1 | 5–15 | 5 | 25 | 75 |
| 5–6 | 1 | 6–18 | 5 | 30 | 90 |

### Sản lượng trứng — CL = 2

| H–R | CL | Egg/đợt | Đợt | Min | Max |
|-----|----|---------|-----|-----|-----|
| 1–3 | 2 | 3–9 | 2 | 6 | 18 |
| 2–4 | 2 | 4–12 | 3 | 12 | 36 |
| 3–5 | 2 | 5–15 | 4 | 20 | 60 |
| 4–6 | 2 | 6–18 | 4 | 24 | 72 |

### Sản lượng trứng — CL = 3

| H–R | CL | Egg/đợt | Đợt | Min | Max |
|-----|----|---------|-----|-----|-----|
| 1–4 | 3 | 4–12 | 2 | 8 | 24 |
| 2–5 | 3 | 5–15 | 3 | 15 | 45 |
| 3–6 | 3 | 6–18 | 4 | 24 | 72 |

### Sản lượng trứng — CL = 4

| H–R | CL | Egg/đợt | Đợt | Min | Max |
|-----|----|---------|-----|-----|-----|
| 1–5 | 4 | 5–15 | 2 | 10 | 30 |
| 2–6 | 4 | 6–18 | 3 | 18 | 54 |

### Sản lượng trứng — CL = 5

| H–R | CL | Egg/đợt | Đợt | Min | Max |
|-----|----|---------|-----|-----|-----|
| 1–6 | 5 | 6–18 | 1 | 6 | 18 |

### Simulate mẫu — 4 Hen – 6 Rooster (CL ban đầu = 2)

| Đợt | H[0] | H[1] | H[2] | H[3] | R[0..5] | CL | Trứng/đợt |
|-----|------|------|------|------|---------|----|-----------|
| Đợt 1 | 6-1-2=3 | 6→5 | 6→5 | 6→5 | 6→5 | CL=2 | 6–18 |
| Đợt 2 | 3-1-2=0 ☠ | 5→4 | 5→4 | 5→4 | 5→4 | CL=2 | 6–18 |
| Đợt 3 | ☠ | 4-1-3=0 ☠ | 4→3 | 4→3 | 4→3 | H=3,R=6 → CL=3 | 6–18 |
| Đợt 4 | ☠ | ☠ | 3-1-4=-2 ☠ tràn+2 | 3-1-2=0 ☠ | 3→2 | H=2,R=6 → CL=4 | 6–18 |
| Đợt 5 | ☠ | ☠ | ☠ | ☠ | — | Không còn H → dừng | — |

**Kết quả:** 4 đợt × 6R = **24–72 trứng**

### Simulate mẫu — 5 Hen – 6 Rooster (CL ban đầu = 1)

| Đợt | H[0] | H[1] | H[2] | H[3] | H[4] | R[0..5] | CL | Trứng/đợt |
|-----|------|------|------|------|------|---------|----|-----------|
| Đợt 1 | 6-1-1=4 | 6→5 | 6→5 | 6→5 | 6→5 | 6→5 | CL=1 | 6–18 |
| Đợt 2 | 4-1-1=2 | 5→4 | 5→4 | 5→4 | 5→4 | 5→4 | CL=1 | 6–18 |
| Đợt 3 | 2-1-1=0 ☠ | 4→3 | 4→3 | 4→3 | 4→3 | 4→3 | CL=1 | 6–18 |
| Đợt 4 | ☠ | 3-1-2=0 ☠ | 3→2 | 3→2 | 3→2 | 3→2 | H=4,R=6 → CL=2 | 6–18 |
| Đợt 5 | ☠ | ☠ | 2-1-3=-2 ☠ tràn+2 | 2-1-2=-1 ☠ tràn+1 | 2-1-1=0 ☠ | 2→1 | H=3,R=6 → CL=3 | 6–18 |
| Đợt 6 | ☠ | ☠ | ☠ | ☠ | ☠ | — | Không còn H → dừng | — |

**Kết quả:** 5 đợt × 6R = **30–90 trứng**

### Coop Upgrades

| Upgrade | Effect |
|---------|--------|
| 🛡 High Wall | Ngăn Monster tấn công gà ban đêm |
| 🌿 Spring Grass | Thức ăn tự nhiên — tăng % sản lượng trứng |
| 💊 Vitamizer | Giảm TG sinh sản, tăng tốc nở trứng |
| 🏠 Expand Coop | Tăng giới hạn 12 → 20 con |

---

## 9. Tổng quan công trình

> ⚠ BASE_UPGRADE_VALUE chưa xác định — sẽ cập nhật sau khi balance. Mọi công trình được xây dựng đều có thể Demolish.

| Icon | Công trình | Khu vực | Chức năng chính | Upgrade nổi bật | Ghi chú |
|------|-----------|---------|-----------------|-----------------|---------|
| 🌱 | Garden | Farming | Trồng & thu hoạch trái cây (tối đa 4 plot) | Auto Harvest, Miracle Mix* | Bắt đầu 1 plot |
| 🏚 | Silo | Farming | Kho chứa vật phẩm (150/port, tối đa 4 port) | Additional Storage ×3 | Auto nhận từ Garden |
| 🏞 | Pond | Farming | Chứa nước tự nhiên, refill + cooldown | More Water Contain, Decrease Cooldown | Cap I→II→III |
| 💧 | Water Purifier | Farming | Salt Water → Fresh Water để tưới Garden | More Contain, Decrease Purifier Time | Chạy khi Sleep |
| ⚗️ | Crafting Station | Farming | Craft toàn bộ: Material, Bottle, Food, Ingredient | Queue +slot, Speed upgrade | Bỏ vào không lấy ra |
| 🐔 | Coop | Farming | Nuôi Hen/Rooster → Egg & Meat | High Wall, Expand Coop (→20) | Max 12 → 20 con |
| 🔬 | Refinery | Science Lab | Kho lưu trữ trung tâm — chỉ bỏ vào | Base Max Value | Không lấy ra được |
| 🏪 | Builder's Shop | Science Lab | Mở blueprint bằng Granumz | — | Một số blueprint từ Treasure Pod |
| 🔧 | Fabricate Gadget | Science Lab | Chế tạo & đặt Gadget ra map | — | Lưu 1 Gadget tại 1 thời điểm |
| 💰 | Farm Market | Science Lab | Bán vật phẩm lấy Granumz | +5% Sell Value ×2 | Giá biến động Perlin Noise |
| 🏠 | Ranch House | Base | Sleep to skip — hồi HP & Energy | — | Ngủ sớm mất phút farm đêm |
| 🎒 | Gear Upgrades | Base | Nâng chỉ số người chơi | Heart / Water / Boost / Backpack Module | Gắn với nhân vật |
| 📦 | Treasure Pod | Map | Granumz + trái cây + blueprint | — | Vị trí cố định, cần kỹ năng |
| ⛏️ | Drill / Pump / Apiary | Gadget | Khai thác tự động (khoáng, nước, tài nguyên) | 3 level / tốc độ khai thác | Đặt ra map qua Fabricate |
| 🔫 | Crop Turret | Gadget | Tự bắn quái ban đêm | Tier đạn, capacity | Nạp thủ công hoặc Turret Link |
| 💊 | Med Station | Gadget | Khu vực hồi máu | Giảm cooldown, tăng HP hồi | Cooldown giữa mỗi lần dùng |
| 🔗 | Warp Tech Links | Gadget | Refinery / Turret / Market từ xa | Turret Link: tier & cap nạp | 3 loại Link riêng biệt |

---

## 10. Farming Buildings

### 🌱 Garden
Công trình chính trong game. Tối đa 4 plot. Flow: Trồng → Tưới Fresh Water → Thu hoạch → Silo. Demolish required.

| # | Upgrade |
|---|---------|
| 1 | Additional Plot II |
| 2 | Nutrient Soil — Tăng % sản lượng tối đa |
| 3 | Additional Plot III |
| 4 | Sprinkler — Auto Watering |
| 5 | Additional Plot IV (max) |
| 6 | Alluvium Soil — Giảm thời gian phát triển |
| 7 | Auto Harvest — Tự động thu → Silo |
| ★ | Miracle Mix — Tăng Rotten timer + harvest count *(Unlock: Achievement Boss Slayer)* |

### 🏚 Silo
Kho chứa items. Mỗi Port chứa tối đa 150 vật phẩm cùng loại. Bắt đầu 1 Port, tối đa 4 Port. Demolish required.

| # | Upgrade |
|---|---------|
| 1 | Additional Storage II — +1 Port |
| 2 | Additional Storage III — +1 Port |
| 3 | Additional Storage IV — +1 Port (max) |

### ⚗️ Crafting Station
Craft toàn bộ: Materials, Bottles, Food Ingredients, Foods. Queue tối đa 3/5/7 recipe × 10 mỗi. Chạy nền khi Sleep. ⚠ Vật phẩm đã bỏ vào không lấy ra.

| # | Upgrade |
|---|---------|
| 1 | Queue Expand I — +2 recipe slots |
| 2 | Craft Speed I — giảm thời gian craft |
| 3 | Queue Expand II — +2 recipe slots |
| 4 | Craft Speed II |

### 🏞 Pond
Nguồn Salt Water tự nhiên. Có khả năng refill tự động + cooldown. Cung cấp nước cho Water Purifier. Demolish required.

| # | Upgrade |
|---|---------|
| 1 | More Water Contain I |
| 2 | Decrease Cooldown I |
| 3 | More Water Contain II |
| 4 | Decrease Cooldown II |
| 5 | More Water Contain III |
| 6 | Decrease Cooldown III |

### 💧 Water Purifier
Lọc Salt Water → Fresh Water để tưới Garden. Chạy tự động khi Sleep phase. Demolish required.

| # | Upgrade |
|---|---------|
| 1 | More Water Contain I |
| 2 | Decrease Purifier Time I |
| 3 | More Water Contain II |
| 4 | Decrease Purifier Time II |
| 5 | More Water Contain III |
| 6 | Decrease Purifier Time III |

### 🐔 Coop
Nuôi Hen/Rooster → Egg & Meat. Max 12 gà (base) → 20. Cặp Hen+Rooster sinh sản mỗi 12h. Demolish required.

| # | Upgrade |
|---|---------|
| 1 | High Wall — Ngăn quái tấn công gà đêm |
| 2 | Spring Grass — Thức ăn tự nhiên, tăng trứng |
| 3 | Vitamizer — Giảm breeding time, tăng tốc nở |
| 4 | Expand Coop — 12 → 20 slot |

---

## 11. Science Lab

The Lab là hub công nghệ trung tâm — chứa Refinery, Fabricate Gadget và Builder's Shop. Nơi unlock, chế tạo và triển khai Gadget ra map.

### 🔬 Refinery
Kho lưu trữ vật phẩm trung tâm. ⚠ Chỉ bỏ vào — không lấy ra được. Kết nối với Refinery Link để nạp từ xa. Upgrade: Base Max Value.

### 🏪 Builder's Shop
Mở khoá blueprint bằng Granumz. Một số blueprint đặc biệt chỉ có từ Treasure Pod (level 3 Gadgets). Blueprint mở rồi dùng trong Fabricate Gadget.

### 🔧 Fabricate Gadget
Chế tạo Gadget từ blueprint đã mở. Lưu 1 Gadget tại một thời điểm. Flow: Press Fabricate → di chuyển ra map → chọn vị trí chỉ định → đặt.

### 💰 Farm Market
Bán trái cây và vật phẩm lấy Granumz — tiền tệ chính. Hệ thống biến động giá: Perlin Noise + chênh lệch số lượng bán. Bán nhiều 1 loại → sụt giá. Đa dạng hoá để giữ giá tốt. Kết nối Market Link để bán từ xa.

| # | Upgrade | Effect |
|---|---------|--------|
| 1 | Sell Value +5% (lần 1) | Blueprint mua tại Builder's Shop |
| 2 | Sell Value +5% (lần 2) | Tổng tối đa +10% sell value |

### Gadgets (chế tạo qua Fabricate Gadget)

**⛏ EXTRACTORS** — Tự động khai thác tài nguyên. 3 level mỗi gadget.
- ⛏️ **Drill** — Khai thác khoáng sản
- 💧 **Pump** — Hút nước vào Pond/Refinery
- 🐝 **Apiary** — Thu mật ong tự động `[Trigger: Place first Apiary]`

**🔧 UTILITIES**
- 🔫 **Crop Turret** — Nạp trái cây → tự bắn quái ban đêm. Upgrade nâng tier trái cây được phép nạp và số lượng tối đa.
- 💊 **Med Station** — Khu vực hồi máu khi đứng gần. Upgrade giảm cooldown và tăng HP hồi mỗi lần.

**🔗 WARP TECH**
- 🔗 **Refinery Link** — Bỏ vật phẩm vào Refinery từ xa. Giảm áp lực Backpack khi farm xa base.
- 🔗 **Turret Link** — Tự nạp trái cây rơi trên ô đất chỉ định vào Crop Turret gần nhất. Upgrade nâng tier & số lượng.
- 🔗 **Market Link** — Bán vật phẩm từ xa — không cần về Farm Market. Tiện khi farm ban ngày.

---

## 12. Base Construction

### 🎒 Gear Upgrades

| Module | Effect | Levels |
|--------|--------|--------|
| ❤️ Heart | Tăng số lượng máu tối đa | 4 level |
| 💧 Water | Tăng sức chứa nước mặn & ngọt | 3 level |
| ⚡ Boost | Tăng tốc độ di chuyển | 2 level |
| 🎒 Backpack | Tăng sức chứa tối đa 1 slot | 4 level |

### 🏠 Ranch House
Sleep to skip — bỏ qua phần còn lại của đêm. Khi thức dậy: hồi đầy HP & Energy. Có thể ngủ sau khi đánh xong hoặc từ 3h sáng.

> ⚠ Ngủ sớm = mất phút farm ban đêm (drop Granumz, trái cây, blueprint). Cần cân bằng tốc độ farm để Sleep không bị spam.

### 📦 Treasure Pod
Rải rác tại vị trí cố định trên map. Mở để nhận: 💰 Granumz · 🍎 Trái cây · 🧪 Bottle · 📋 Blueprint cấp Lv3.

> Blueprint từ Pod: cần kỹ năng điều khiển và HandGun. Achievement Pod Hunter: mở tất cả → Granumz bonus + Vial Lv3 blueprint.

---

## 13. Achievement System

Ghi nhận thụ động — tự động unlock reward khi đạt điều kiện. Không cần claim.

| Icon | Tên | Điều kiện | Reward |
|------|-----|-----------|--------|
| 🌿 | Green Thumb | Thu hoạch 100 Berry lần đầu | +1 Garden Plot (early access) |
| 💀 | Night Cleaner | Giết 50 quái trong 1 đêm | Exclusive blueprint |
| 🗡 | Monster Slayer | Giết 300 quái tổng cộng | Tomato (Shotgun) unlock |
| 🐔 | Balanced Ranch | Nuôi đủ 3 cặp Hen-Rooster cân bằng | Vitamizer unlock sớm |
| 📦 | Pod Hunter | Mở tất cả Treasure Pod trên map | Granumz bonus + Vial Lv3 blueprint |
| 🌙 | Survivor | Sống sót qua 20 ngày | Miracle Mix unlock (Garden) |
| 👑 | Boss Slayer | Giết 3 Boss (Day 5 / 10 / 15) | Miracle Mix — tăng harvest, giảm Rotten timer |
| ⚗️ | Master Brewer | Craft 10 Bottle trong 1 ngày | Crafting Station queue +2 slot |
| 🤖 | Automation King | Đặt đủ Drill + Pump + Apiary | Turret Link Lv2 blueprint |
| 🍇 | Pod Opener | Mở Treasure Pod đầu tiên | Grape crop unlock |
| 🐝 | Beekeeper | Đặt Apiary Gadget lần đầu | Honey resource + Honey Cake recipe |

---

*GDD v2.3 — Crop Shooter · Weapons · Enemies · Map · Balance → TBD*
