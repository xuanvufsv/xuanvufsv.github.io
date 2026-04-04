# 📋 Crop Shooter — Addressables Asset TODO List
> **Strategy:** Group theo Day · Label theo Type
> **SO Architecture:** Component-based — `CollectableObjectStat` + components
> **Trạng thái:** `[ ]` Chưa làm · `[x]` Hoàn thành · `[~]` Đang làm · `[!]` Cần review

---

## 0. FOLDER STRUCTURE — Hiện trạng & Đề xuất bổ sung

> Dựa trên project structure thực tế. Các folder đã có giữ nguyên, chỉ bổ sung những gì còn thiếu.
> SmartAddresser rule sẽ map theo path thực tế này.

### 0.1 Folder đã có — Giữ nguyên, bổ sung subfolder

```
Assets/
│
├── Art/                            ← ĐÃ CÓ — thành phần thô, hầu hết KHÔNG mark Addressable
│   ├── Accessories/                ← ĐÃ CÓ
│   ├── Animals/                    ← ĐÃ CÓ
│   ├── Characters/                 ← ĐÃ CÓ
│   ├── Constructions/              ← ĐÃ CÓ — mesh/texture của building
│   ├── Consumables/                ← ĐÃ CÓ — mesh/texture của food, bottle
│   ├── Effects/                    ← ĐÃ CÓ — raw particle/effect component
│   ├── Fonts/                      ← ĐÃ CÓ
│   ├── Materials/                  ← ĐÃ CÓ
│   │   ├── Materials/
│   │   └── Textures/
│   ├── Monster/                    ← ĐÃ CÓ
│   ├── Nature/                     ← ĐÃ CÓ
│   ├── Plants/                     ← ĐÃ CÓ — mesh/texture của crop
│   ├── Props/                      ← ĐÃ CÓ
│   ├── Resources/                  ← ĐÃ CÓ — raw natural resource mesh
│   ├── Skybox/                     ← ĐÃ CÓ
│   ├── Sprites/                    ← ĐÃ CÓ
│   │   ├── Icons/                  ← ĐÃ CÓ — icons hiện có (Construction, Potions, Skills, UI)
│   │   │   ├── Construction/       ← ĐÃ CÓ
│   │   │   ├── Potions/            ← ĐÃ CÓ — đổi tên thành Bottles/ cho nhất quán
│   │   │   ├── Skills/             ← ĐÃ CÓ
│   │   │   └── UI/                 ← ĐÃ CÓ
│   │   │   ── [THÊM] Crops/        ← CẦN TẠO — icon cho 15 crop
│   │   │   ── [THÊM] NaturalResources/ ← CẦN TẠO — icon cho 16 natural
│   │   │   ── [THÊM] Food/         ← CẦN TẠO — icon cho 15 food
│   │   │   ── [THÊM] Gadgets/      ← CẦN TẠO — icon cho 8 gadget
│   │   ├── Background/             ← ĐÃ CÓ
│   │   └── Weapon/                 ← ĐÃ CÓ
│   ├── Textures/                   ← ĐÃ CÓ
│   ├── UI/                         ← ĐÃ CÓ
│   └── Weapons/                    ← ĐÃ CÓ
│
├── Game Data/                      ← ĐÃ CÓ — ScriptableObject data
│   ├── Ammo/                       ← ĐÃ CÓ — CollectableObjectStat (AttackingCropStat)
│   │   └── Normal/
│   ├── Construction/               ← ĐÃ CÓ — BuildingSO
│   │   └── Garden/
│   │   ── [THÊM] Pond/
│   │   ── [THÊM] Coop/
│   │   ── [THÊM] Silo/
│   │   ── [THÊM] WaterPurifier/
│   │   ── [THÊM] FarmHouse/
│   │   ── [THÊM] FarmMarket/
│   │   ── [THÊM] Refinery/
│   │   ── [THÊM] BuildersShop/
│   │   ── [THÊM] FabricateGadget/
│   │   ── [THÊM] TreasurePod/
│   ├── Enemy/                      ← ĐÃ CÓ — EnemySO (TBD)
│   ├── Recipe/                     ← ĐÃ CÓ — RecipeData SO
│   ├── Resource/                   ← ĐÃ CÓ — CollectableObjectStat các loại
│   │   ├── Crafting Product/       ← ĐÃ CÓ — Ingredient + Food SO
│   │   ├── Farming Product/        ← ĐÃ CÓ — Crop SO (FarmingCropStat)
│   │   └── Natural/                ← ĐÃ CÓ — Natural Resource SO
│   ├── Weapon/                     ← ĐÃ CÓ — WeaponSO
│   ── [THÊM] Gadget/               ← CẦN TẠO — GadgetSO (Drill, Pump, Apiary...)
│   ── [THÊM] Upgrade/              ← CẦN TẠO — UpgradeInfo + UpgradeOptionInfo SO
│   │   ├── Gear/                   ← GearUpgradeInfo
│   │   └── Options/                ← UpgradeOptionInfo concrete per building
│   └── [THÊM] Registry/            ← CẦN TẠO — SharedUIData Registry SO
│
├── Prefabs/                        ← ĐÃ CÓ — asset cuối, mark Addressable
│   ├── Ammo/                       ← ĐÃ CÓ — Prefab của ammo/crop (Beetroot đã có)
│   │   ├── Normal/
│   │   │   └── Beetroot/           ← ĐÃ CÓ — mẫu tham khảo cấu trúc
│   │   └── Pack/
│   ├── Animals/                    ← ĐÃ CÓ
│   ├── Construction/               ← ĐÃ CÓ — prefab building
│   │   ├── Fabricate Gadgets/      ← ĐÃ CÓ
│   │   ├── Gear Upgrades/          ← ĐÃ CÓ
│   │   ├── Shared/                 ← ĐÃ CÓ — shared parts (Fence, WoodPanel...)
│   │   └── Silo/                   ← ĐÃ CÓ
│   │   ── [THÊM] Garden/
│   │   ── [THÊM] Pond/
│   │   ── [THÊM] Coop/
│   │   ── [THÊM] WaterPurifier/
│   │   ── [THÊM] FarmHouse/
│   │   ── [THÊM] FarmMarket/
│   ├── Environment/                ← ĐÃ CÓ
│   ├── Natural Resources/          ← ĐÃ CÓ — prefab node khai thác
│   ├── Product/                    ← ĐÃ CÓ — prefab item drop (pickup)
│   ├── Products/                   ← ĐÃ CÓ (trùng với Product? → xem xét gộp)
│   │   ├── Normal/
│   │   └── Pack/
│   ├── UI/                         ← ĐÃ CÓ — UI prefab
│   ── [THÊM] Crops/                ← CẦN TẠO — crop model prefab (plant in garden)
│   │   ├── Day1_3/                 ← Berry, Wheat, Bean, Carrot, Cabbage, Coconut
│   │   ├── Day5_6/                 ← Beetroot, Tomato
│   │   ├── Day7_9/                 ← Grape
│   │   ├── Day10_12/               ← Carambola, Chili
│   │   ├── Day13_16/               ← Apple, Pepper
│   │   └── Day17_Plus/             ← Durian, NoniFruit (WIP)
│   ── [THÊM] Gadgets/              ← CẦN TẠO — gadget prefab đặt trên map
│   └── [THÊM] VFX/                 ← CẦN TẠO — assembled VFX prefab (trail, hit, grow)
│
├── VFX/                            ← ĐÃ CÓ — raw VFX components
│   ├── Materials/
│   ├── Prefabs/                    ← ĐÃ CÓ — có thể dùng thay cho Prefabs/VFX/
│   └── Textures/
│
├── Scripts/                        ← ĐÃ CÓ — không liên quan Addressables
│
├── [THÊM] Audio/                   ← CẦN TẠO — hoàn thiện sau
│   ├── SoundEffects/               ← AudioClip SFX
│   └── Soundtrack/                 ← AudioClip nhạc nền
│
└── [THÊM] Shaders/                 ← CẦN TẠO
    ├── Shaders/                    ← .shader / .shadergraph file
    └── ShaderGraphs/
```

### 0.2 Vấn đề cần làm sạch trước khi setup Addressables

- [ ] **Thống nhất `Product/` vs `Products/`** — hai folder trùng chức năng, gộp lại thành `Prefabs/Products/`
- [ ] **`Art/Resources/`** — Unity treat folder tên `Resources/` đặc biệt (load bằng Resources.Load). Đổi tên thành `Art/NaturalResourcesArt/` để tránh conflict với Addressables
- [ ] **`Art/Sprites/Icons/Potions/`** — đổi tên thành `Bottles/` để nhất quán với DataSpec v3
- [ ] Verify `Prefabs/Ammo/Normal/Beetroot/` — đây là mẫu tốt, dùng làm template cấu trúc cho các crop còn lại

---

## 1. ADDRESSABLES GROUPS — Tạo và cấu hình

- [ ] Tạo **LocalCore** group
  - Type: Local · Bundle Mode: Pack Together · Prevent Updates: ON
- [ ] Tạo **SharedAssets** group *(tạo sau khi chạy Analyze phát hiện duplicate)*
  - Type: Local · Bundle Mode: Pack Together · Prevent Updates: ON
  - Chứa: Prefab/texture/material dùng chung nhiều group (Fence, shared wood panel, shared stone mat...)
- [ ] Tạo **Remote_Day5_6** group — Pack Together · Prevent Updates: OFF
- [ ] Tạo **Remote_Day7_9** group — Pack Together · Prevent Updates: OFF
- [ ] Tạo **Remote_Day10_12** group — Pack Together · Prevent Updates: OFF
- [ ] Tạo **Remote_Day13_16** group — Pack Together · Prevent Updates: OFF
- [ ] Tạo **Remote_Day17_Plus** group — Pack Together · Prevent Updates: OFF
- [ ] Tạo **OTA_Events** group — Pack Separately · Prevent Updates: OFF
- [ ] Tạo **OTA_LiveConfig** group — Pack Separately · Prevent Updates: OFF
- [ ] Configure Remote Load Path: `https://cdn.cropshooter.com/[BuildTarget]/[hash]`

---

## 2. SMARTADDRESSER — Layout Rules

> Folder không theo Addressables structure → SmartAddresser cần rule phức tạp hơn.
> Rule match theo **path subfolder + asset type + SO field value**.

- [ ] Cài SmartAddresser:
  ```
  https://github.com/CyberAgentGameEntertainment/SmartAddresser.git?path=/Assets/SmartAddresser
  ```

### 2.1 Group Rules

**LocalCore:**
- [ ] Path `Assets/Prefabs/Construction/Shared/**` → LocalCore *(shared parts dùng chung)*
- [ ] Path `Assets/Game Data/Resource/Farming Product/**` + SO.unlockDay <= 4 → LocalCore
- [ ] Path `Assets/Game Data/Resource/Natural/**` + SO.unlockDay <= 4 → LocalCore
- [ ] Path `Assets/Game Data/Resource/Crafting Product/**` + SO.unlockDay <= 4 → LocalCore
- [ ] Path `Assets/Game Data/Construction/**` + SO.unlockDay <= 4 → LocalCore
- [ ] Path `Assets/Prefabs/Crops/Day1_3/**` → LocalCore
- [ ] Path `Assets/Game Data/Registry/**` → LocalCore
- [ ] Path `Assets/Prefabs/UI/**` → LocalCore
- [ ] Scene files → LocalCore

**Remote theo Day:**
- [ ] Path `Assets/Prefabs/Crops/Day5_6/**` → Remote_Day5_6
- [ ] Path `Assets/Prefabs/Crops/Day7_9/**` → Remote_Day7_9
- [ ] Path `Assets/Prefabs/Crops/Day10_12/**` → Remote_Day10_12
- [ ] Path `Assets/Prefabs/Crops/Day13_16/**` → Remote_Day13_16
- [ ] Path `Assets/Prefabs/Crops/Day17_Plus/**` → Remote_Day17_Plus
- [ ] `Game Data` SO: unlockDay 5–6 → Remote_Day5_6
- [ ] `Game Data` SO: unlockDay 7–9 → Remote_Day7_9
- [ ] `Game Data` SO: unlockDay 10–12 → Remote_Day10_12
- [ ] `Game Data` SO: unlockDay 13–16 → Remote_Day13_16
- [ ] `Game Data` SO: unlockDay >= 17 → Remote_Day17_Plus
- [ ] Path `Assets/Prefabs/Construction/Pond/**` OR `Coop/**` → Remote_Day7_9
- [ ] Path `Assets/Prefabs/Gadgets/**` + SO.unlockDay range → Remote tương ứng

**OTA:**
- [ ] Path `Assets/Game Data/OTA/LiveConfig/**` → OTA_LiveConfig · label: `live_config`
- [ ] Path `Assets/**/OTA/Events/{eventName}/**` → OTA_Events · label: `seasonal_{eventName}`

### 2.2 Label Rules

- [ ] Path `Assets/Game Data/Resource/Farming Product/**` → label: `crop`
- [ ] Path `Assets/Game Data/Ammo/**` → label: `crop` *(ammo là crop với AttackingCropStat)*
- [ ] Path `Assets/Game Data/Resource/Crafting Product/` + subfolder `Ingredients/` → label: `ingredient`
- [ ] Path `Assets/Game Data/Resource/Crafting Product/` + subfolder `Food/` → label: `food`
- [ ] Path `Assets/Game Data/Resource/Crafting Product/` + subfolder `Bottles/` → label: `bottle`
- [ ] Path `Assets/Game Data/Resource/Natural/**` → label: `natural`
- [ ] Path `Assets/Game Data/Construction/**` → label: `building`
- [ ] Path `Assets/Game Data/Gadget/**` → label: `gadget`
- [ ] Path `Assets/Game Data/Registry/**` → label: `ui_registry`

### 2.3 Address Rules

- [ ] Address = filename (không extension): asset `Berry.asset` → address `"Berry"`
- [ ] Validate toàn bộ rule: SmartAddresser → Validate
- [ ] Test với `Beetroot` (đã có prefab) → verify group + label + address đúng

---

## 3. PREFAB TODO — Ưu tiên theo Day

> Đây là phần chính cần làm. Mỗi crop/item cần có **Prefab** hoàn chỉnh trước khi assign SO reference.
> Tham khảo `Prefabs/Ammo/Normal/Beetroot/` làm template.
>
> **Quy tắc:** Prefab = asset cuối, mark Addressable. Art/ = thành phần thô, KHÔNG mark Addressable.

### 3.1 Crop Prefabs — Plant model trong Garden

> Path đề xuất: `Assets/Prefabs/Crops/{DayFolder}/`
> Mỗi crop cần: model growing state + model ready state (hoặc dùng animator)
> Art raw: `Art/Plants/` hoặc `Art/Consumables/`

**Day 1–3 (LocalCore):** — `Assets/Prefabs/Crops/Day1_3/`

- [ ] `Berry.prefab` — BodyType: Vegetable · check `Art/Plants/` có mesh chưa
- [ ] `Wheat.prefab` — BodyType: Vegetable
- [ ] `Bean.prefab` — BodyType: Climbing
- [ ] `Carrot.prefab` — BodyType: Vegetable
- [ ] `Cabbage.prefab` — BodyType: Vegetable
- [ ] `Coconut.prefab` — BodyType: Tree
- [ ] Sau khi tạo xong → assign vào `FarmingCropStat.growingBody` và `defaultModelPlant`

**Day 5–6 (Remote_Day5_6):** — `Assets/Prefabs/Crops/Day5_6/`

- [ ] `Beetroot.prefab` — BodyType: Vegetable *(đã có ở Prefabs/Ammo/Normal/Beetroot/ → kiểm tra có dùng được không)*
- [ ] `Tomato.prefab` — BodyType: Vegetable

**Day 7–9 (Remote_Day7_9):** — `Assets/Prefabs/Crops/Day7_9/`

- [ ] `Grape.prefab` — BodyType: Climbing

**Day 10–12 (Remote_Day10_12):** — `Assets/Prefabs/Crops/Day10_12/`

- [ ] `Carambola.prefab` — BodyType: Tree
- [ ] `Chili.prefab` — BodyType: Vegetable

**Day 13–16 (Remote_Day13_16):** — `Assets/Prefabs/Crops/Day13_16/`

- [ ] `Apple.prefab` — BodyType: Tree
- [ ] `Pepper.prefab` — BodyType: Vegetable

**Day 17+ (Remote_Day17_Plus):** — `Assets/Prefabs/Crops/Day17_Plus/`

- [ ] `Durian.prefab` — WIP
- [ ] `NoniFruit.prefab` — WIP

### 3.2 Ammo Prefabs — Projectile bay trong không khí

> Path: `Assets/Prefabs/Ammo/Normal/{CropName}/`
> Đây là bullet prefab khi bắn, khác với crop model trong garden.
> Beetroot đã có — dùng làm template.

- [ ] Verify `Prefabs/Ammo/Normal/Beetroot/` — xem cấu trúc bên trong làm template
- [ ] `Berry/` — bullet AR, raycast
- [ ] `Wheat/` — bullet SMG, multiplier=3
- [ ] `Bean/` — bullet SMG
- [ ] `Tomato/` — bullet Shotgun, bulletCount=5
- [ ] `Grape/` — bullet special
- [ ] `Carambola/` — bullet Sniper, HasScope
- [ ] `Chili/` — bullet Flamethrower
- [ ] `Apple/` — bullet Grenade
- [ ] `Pepper/` — bullet ToxicGrenade
- [ ] Carrot, Cabbage, Coconut — không có AttackingCropStat, không cần ammo prefab

### 3.3 VFX Prefabs — Assembled, đã config xong

> Path: `Assets/Prefabs/VFX/` HOẶC `Assets/VFX/Prefabs/` *(đã có)*
> Chọn 1 trong 2, không để ở cả hai. Đề xuất: dùng `VFX/Prefabs/` vì đã có sẵn.

- [ ] **Quyết định:** dùng `VFX/Prefabs/` hay `Prefabs/VFX/` → thống nhất 1 nơi
- [ ] `SeedEffect.prefab` — VFX giai đoạn hạt giống (dùng chung các crop)
- [ ] `GrowEffect.prefab` — VFX khi cây trưởng thành
- [ ] `HarvestEffect.prefab` — VFX khi thu hoạch
- [ ] Trail prefab per gun:
  - [ ] `Trail_AR.prefab`
  - [ ] `Trail_SMG.prefab`
  - [ ] `Trail_Shotgun.prefab`
  - [ ] `Trail_Sniper.prefab`
  - [ ] `Trail_Grenade.prefab`
  - [ ] `Trail_Flamethrower.prefab`
  - [ ] `Trail_ToxicGrenade.prefab`
- [ ] Hit effect per gun:
  - [ ] `HitEffect_AR.prefab`
  - [ ] `HitEffect_Shotgun.prefab`
  - [ ] `HitEffect_Grenade.prefab`
  - [ ] `HitEffect_Flamethrower.prefab`
- [ ] Assign vào `AttackingCropStat.trailTracer`, `hitEffectPrefab`

### 3.4 Building Prefabs — Construction đặt trên map

> Path: `Assets/Prefabs/Construction/{BuildingName}/`
> Shared parts (Fence, WoodPanel, Stone...) → `Prefabs/Construction/Shared/` *(đã có)*
> Shared parts mark Addressable → assign **SharedAssets** group để tránh duplicate

**LocalCore (Day 1–4):**

- [ ] `Garden.prefab` — kiểm tra `Art/Constructions/` có mesh chưa
- [ ] `WaterPurifier.prefab`
- [ ] `FarmHouse.prefab`
- [ ] `FarmMarket.prefab`
- [ ] `Refinery.prefab`
- [ ] `BuildersShop.prefab`
- [ ] `FabricateGadget.prefab`
- [ ] `Silo.prefab` *(đã có folder Prefabs/Construction/Silo/ → check xem prefab đã có chưa)*
- [ ] `TreasurePod.prefab`

**Remote_Day7_9:**

- [ ] `Pond.prefab`
- [ ] `Coop.prefab`

### 3.5 Gadget Prefabs — Đặt trên map

> Path: `Assets/Prefabs/Gadgets/` *(cần tạo)*

- [ ] `Drill.prefab` — LocalCore (Day 4)
- [ ] `WaterPump.prefab` — Remote_Day7_9
- [ ] `Apiary.prefab` — Remote_Day7_9
- [ ] `CropTurret.prefab` — Remote_Day10_12
- [ ] `MedStation.prefab` — Remote_Day13_16
- [ ] `RefinaryLink.prefab` — Remote_Day13_16
- [ ] `TurretLink.prefab` — Remote_Day13_16
- [ ] `MarketLink.prefab` — Remote_Day17_Plus

### 3.6 Natural Resource Node Prefabs — Node khai thác trên map

> Path: `Assets/Prefabs/Natural Resources/` *(đã có)*

- [ ] Verify các prefab đã có trong `Prefabs/Natural Resources/`
- [ ] `IronOre_Node.prefab`, `CopperOre_Node.prefab`, `SandDeposit_Node.prefab`
- [ ] `CoalVein_Node.prefab` (Day 10)
- [ ] `RubyDeposit_Node.prefab` (Day 15)
- [ ] `GoldCrystal_Node.prefab` (Day 20)
- [ ] Assign vào `NaturalResourceStat` tương ứng

### 3.7 Product/Pickup Prefabs — Item drop khi thu hoạch/kill

> Path: `Assets/Prefabs/Products/` *(đã có Normal/ và Pack/)*
> Đây là item 3D bay ra khi harvest hoặc enemy drop.

- [ ] Verify cấu trúc `Prefabs/Products/Normal/` — đã có gì chưa
- [ ] Tạo pickup prefab cho các item chưa có
- [ ] `Products/Normal/` — 1 item pickup
- [ ] `Products/Pack/` — bundle nhiều item (Wheat×3 bundle)

---

## 4. GAME DATA SO — Data Asset

> Path gốc: `Assets/Game Data/`
> SmartAddresser assign group theo `unlockDay` field trong SO.

### 4.1 Cấu trúc Game Data cần bổ sung

- [ ] Tạo `Game Data/Resource/Crafting Product/Ingredients/` ← tách rõ khỏi Food
- [ ] Tạo `Game Data/Resource/Crafting Product/Food/`
- [ ] Tạo `Game Data/Resource/Crafting Product/Bottles/`
- [ ] Tạo `Game Data/Gadget/` ← GadgetSO
- [ ] Tạo `Game Data/Upgrade/Gear/` ← GearUpgradeInfo
- [ ] Tạo `Game Data/Upgrade/Options/` ← UpgradeOptionInfo concrete
- [ ] Tạo `Game Data/Registry/` ← SharedUIData Registry SO

### 4.2 Kiểm tra SO đã có

- [ ] Mở `Game Data/Resource/Farming Product/` → list SO đã có, đánh dấu còn thiếu
- [ ] Mở `Game Data/Resource/Natural/` → list SO đã có
- [ ] Mở `Game Data/Resource/Crafting Product/` → list SO đã có
- [ ] Mở `Game Data/Construction/Garden/` → verify Garden SO fields theo DataSpec v3
- [ ] Mở `Game Data/Ammo/Normal/` → list ammo SO đã có

*(Phần SO data chi tiết xem TODO List v2 — Phần 4 đến Phần 9)*

---

## 5. ICONS — Sprites cho UI

> Path: `Assets/Art/Sprites/Icons/`
> Icons mark Addressable (reference từ Registry SO → ship LocalCore).
> Import settings: Sprite · Max Size 128px · Crunch Compression

### 5.1 Đã có

- [ ] Verify `Icons/Construction/` — đủ 12 building chưa (Coop, FarmHouse, FarmMarket, Garden, GearUpgrades, Pond, ScienceLab, Silo, TreasurePod, WaterPurifier)
- [ ] Verify `Icons/Potions/` → đổi tên thành `Icons/Bottles/` → đủ 9 bottle chưa
- [ ] Verify `Icons/Skills/` và `Icons/UI/`

### 5.2 Cần tạo thêm

- [ ] Tạo `Icons/Crops/` — 15 icon crop
  - Berry, Wheat, Bean, Carrot, Cabbage, Coconut, Beetroot, Tomato, Grape, Carambola, Chili, Apple, Pepper, Durian(WIP), NoniFruit(WIP)
- [ ] Tạo `Icons/NaturalResources/` — 16 icon
  - MonsterMeat, MetalScrap, Sand, Trash, Iron, PowerShard, Copper, Wood, Stone, Coal, Egg, CoconutMilk, Honey, Ruby, GoldCrystal, CoalShallow
- [ ] Tạo `Icons/Food/` — 15 icon
  - Bread, SoggyBread, BerryCake, BurgerBerry, Omelet, HotBunny, CarrotCake, SweetGrapeball, TomatoSoup, Burnwich, RedAlertSalad, CarambolaCake, ApplePie, FreshSalad, HoneyCake
- [ ] Tạo `Icons/Gadgets/` — 8 icon
  - Drill, WaterPump, Apiary, CropTurret, MedStation, RefinaryLink, TurretLink, MarketLink
- [ ] Tạo `Icons/Ingredients/` — 14 icon
  - Flour, PowerCore, Circuit, BeanOil, CoconutOil, Margarine, Sugar, GlassVialLv1, CabbageSauce, Cream, GlassVialLv2, PoisonShard, AcidShard, GlassVialLv3

---

## 6. AUDIO & SHADERS — Hoàn thiện sau

> Tạo folder ngay bây giờ để SmartAddresser rule đã sẵn sàng khi asset có.

### 6.1 Audio

- [ ] Tạo `Assets/Audio/` folder
  - [ ] `Audio/SoundEffects/` — SFX (harvest, shoot, build, UI click...)
  - [ ] `Audio/Soundtrack/` — nhạc nền (Day theme, Night battle theme...)
- [ ] Audio LocalCore (core SFX + Day/Night theme) → assign LocalCore
- [ ] Audio Remote (event music, seasonal SFX) → assign OTA_Events
- [ ] SmartAddresser rule: `Audio/SoundEffects/**` → LocalCore · label: `sfx`
- [ ] SmartAddresser rule: `Audio/Soundtrack/**` → LocalCore · label: `music`

### 6.2 Shaders

- [ ] Tạo `Assets/Shaders/` folder
  - [ ] `Shaders/Shaders/` — .shader file
  - [ ] `Shaders/ShaderGraphs/` — .shadergraph file
- [ ] Custom shader → LocalCore (ship cùng game)
- [ ] Note: Addressables tự tạo Shader Bundle riêng → không cần mark Addressable thủ công cho shader
- [ ] Verify `Shader Bundle Naming Prefix = Project Name Hash` trong Addressables Settings

---

## 7. SHARED ASSETS — Duplicate Detection

> Làm SAU khi đã tạo đủ prefab và build lần đầu.

- [ ] Build Addressables lần đầu (Play Mode = Use Asset Database trước)
- [ ] Chạy **Window → Asset Management → Addressables → Analyze**
- [ ] Run **Check Duplicate Bundle Dependencies**
- [ ] Asset nào xuất hiện nhiều bundle → move vào `SharedAssets` group:
  - Candidate: `Prefabs/Construction/Shared/` parts (Fence, WoodPanel...)
  - Candidate: Material dùng chung nhiều building
  - Candidate: VFX dùng chung nhiều crop
- [ ] Rebuild sau khi move → Analyze lại → không còn duplicate warning

---

## 8. WORKFLOW — Quy trình làm việc

### Thêm Crop mới

```
1. Tạo art raw tại Art/Plants/{CropName}/ (FBX, texture)
2. Tạo Prefab tại Prefabs/Crops/{DayFolder}/{CropName}.prefab
   - Gắn model từ Art/Plants/
   - Setup Animator (Growing → Ready state)
3. Tạo SO tại Game Data/Resource/Farming Product/{CropName}.asset
   - Set unlockDay → SmartAddresser tự assign group
   - Assign Prefab vào FarmingCropStat.defaultModelPlant
   - Set components (FarmingCropStat, AttackingCropStat nếu có)
4. Tạo Ammo Prefab tại Prefabs/Ammo/Normal/{CropName}/ (nếu có AttackingCropStat)
5. Assign icon tại Art/Sprites/Icons/Crops/{CropName}.png
6. Cập nhật CropRegistry.asset
7. SmartAddresser Validate → Addressables Analyze
```

### Thêm Building mới

```
1. Tạo art raw tại Art/Constructions/{BuildingName}/
2. Tạo Prefab tại Prefabs/Construction/{BuildingName}/{BuildingName}.prefab
   - Shared parts → reference từ Prefabs/Construction/Shared/
3. Tạo BuildingSO tại Game Data/Construction/{BuildingName}.asset
   - Set unlockDay
   - Tạo UpgradeOptionInfo SO tại Game Data/Upgrade/Options/{BuildingName}/
4. Verify: Shared parts có bị duplicate không → chạy Analyze
5. Cập nhật BuildingRegistry.asset
```

### Kiểm tra trước khi build

- [ ] SmartAddresser Validate — 0 warning
- [ ] Addressables Analyze → Check Duplicate — 0 warning
- [ ] Tất cả Registry SO không có null entry
- [ ] Tất cả RecipeData có đúng 3 slot
- [ ] Không có asset trong `Resources/` folder (conflict với Addressables)
- [ ] `Art/Resources/` đã đổi tên thành `Art/NaturalResourcesArt/`

---

## 9. CHECKLIST BUILD RELEASE

- [ ] Fix `Art/Resources/` → đổi tên (Unity Resources folder đặc biệt)
- [ ] Thống nhất `Prefabs/Product/` vs `Prefabs/Products/` → gộp 1
- [ ] Fix date corruption SO: fireRate, lifeTime, reloadSpeed (Carambola, Durian, Wheat, Grape, Bean, Tomato, Chili, Noni)
- [ ] Fix durabilityModifier: Iron → 1.5, GoldCrystal → 2.0
- [ ] Internal Asset Naming: **Dynamic** (release)
- [ ] Compression: Local **LZ4** · Remote/OTA **LZMA**
- [ ] Catalog Update on Startup: **enabled** (unchecked Disable)
- [ ] Remote groups: Prevent Updates **OFF** · Local: **ON**
- [ ] CRC: Local Disabled · Remote/OTA Enabled Excluding Cached
- [ ] Max Concurrent Web Requests: **5–8**
- [ ] Build Addressables → Build Player

---

## 10. ASSET COUNT TRACKER

| Loại | Có rồi | Cần tạo | Ghi chú |
|------|--------|---------|---------|
| Crop Prefab (garden model) | ~0 | 15 | Beetroot ở Ammo, kiểm tra lại |
| Ammo Prefab (bullet) | 1 (Beetroot) | ~9 | Carrot/Cabbage/Coconut không cần |
| Building Prefab | ~2 (Silo + Fabricate) | ~11 | |
| Gadget Prefab | 0 | 8 | |
| VFX Prefab (assembled) | 0 | ~15 | Trail, HitEffect per gun type |
| Natural Resource Node | unknown | ~10 | Check Prefabs/Natural Resources/ |
| Product/Pickup Prefab | unknown | ~30 | Check Prefabs/Products/ |
| Crop SO | ~some | 15 total | Check Game Data/Resource/Farming Product/ |
| Natural SO | ~some | 16 total | Check Game Data/Resource/Natural/ |
| Ingredient SO | unknown | 14 | |
| Food SO | unknown | 15 | |
| Bottle SO | unknown | 9 | |
| Building SO | ~1 (Garden) | 12 total | |
| Gadget SO | 0 | 8 | Cần tạo folder |
| Recipe SO | unknown | ~38 | |
| Registry SO | 0 | 4–5 | CropRegistry, BottleRegistry... |
| Icons | ~partial | ~68 total | Crop/Food/Natural/Gadget/Ingredient thiếu |
| Audio | 0 | TBD | Sau |
| JSON LiveConfig | 0 | 5 | |

---

*Crop Shooter — Addressables TODO v3.0 · Dựa trên project structure thực tế · GDD v300326 + DataSpec v3.0*
