# 📋 Crop Shooter — Addressables Asset TODO List
> **Mục tiêu:** Chuẩn bị đầy đủ asset, SO data, folder structure và label để thực thi Addressables theo strategy: **Group theo Day · Label theo Type**
> 
> **Kiến trúc SO:** Component-based — `CollectableObjectStat` + components (`FarmingCropStat`, `AttackingCropStat`, `CraftedProductStat`, `NaturalResourceStat`, `BottleStat`)
>
> **Trạng thái:** `[ ]` Chưa làm · `[x]` Hoàn thành · `[~]` Đang làm · `[!]` Cần review

---

## 0. FOLDER STRUCTURE — Thiết lập Project

> Phải làm trước tất cả. Folder path quyết định SmartAddresser rule và Addressables group assignment.

- [ ] Tạo folder structure chuẩn trong `Assets/`:

```
Assets/
├── AddressableAssets/
│   ├── LocalCore/
│   │   ├── Bootstrap/          ← scene, PlayerController, HUD
│   │   ├── SharedUIData/       ← Registry SO + Icons
│   │   ├── Day1_4/             ← crop, natural, ingredient, building Day 1–4
│   │   └── Audio_Shaders/      ← core audio, shader, material
│   ├── Remote/
│   │   ├── Day5_6/
│   │   ├── Day7_9/
│   │   ├── Day10_12/
│   │   ├── Day13_16/
│   │   └── Day17_Plus/
│   └── OTA/
│       ├── Events/             ← seasonal skins, decoration
│       └── LiveConfig/         ← JSON balance data
├── Data/
│   ├── CollectableObject/      ← tất cả CollectableObjectStat SO
│   ├── Construction/           ← BuildingSO
│   ├── Gadget/                 ← GadgetSO
│   ├── Upgrade/
│   │   ├── Gear/               ← GearUpgradeInfo SO
│   │   └── Options/            ← UpgradeOptionInfo SO (concrete)
│   ├── Recipe/                 ← RecipeData SO
│   └── Enemy/                  ← EnemySO (TBD)
└── Art/
    ├── Icons/                  ← tất cả icon sprite (crop, bottle, building...)
    ├── Prefabs/
    │   ├── Crops/              ← model prefab của crop
    │   ├── VFX/                ← trail, hit effect, seed/grow VFX
    │   └── Buildings/          ← building prefab
    └── Audio/
```

- [ ] Đặt tên file theo quy ước: `snake_case` cho SO data, `PascalCase` cho prefab/script
- [ ] Không đặt suffix `SO` vào tên asset (theo DataSpec v3)
- [ ] Tạo file `AddressableAssetSettings` và configure Groups (xem Phần 1)

---

## 1. ADDRESSABLES GROUPS — Tạo và cấu hình

- [ ] Tạo **LocalCore** group
  - Type: Local · Bundle Mode: Pack Together · Prevent Updates: ON
  - Assign path: `Assets/AddressableAssets/LocalCore/`
- [ ] Tạo **Remote_Day5_6** group
  - Type: Remote · Bundle Mode: Pack Together · Prevent Updates: OFF
- [ ] Tạo **Remote_Day7_9** group
  - Type: Remote · Bundle Mode: Pack Together · Prevent Updates: OFF
- [ ] Tạo **Remote_Day10_12** group
  - Type: Remote · Bundle Mode: Pack Together · Prevent Updates: OFF
- [ ] Tạo **Remote_Day13_16** group
  - Type: Remote · Bundle Mode: Pack Together · Prevent Updates: OFF
- [ ] Tạo **Remote_Day17_Plus** group
  - Type: Remote · Bundle Mode: Pack Together · Prevent Updates: OFF
- [ ] Tạo **OTA_Events** group
  - Type: Remote · Bundle Mode: Pack Separately · Prevent Updates: OFF
- [ ] Tạo **OTA_LiveConfig** group
  - Type: Remote · Bundle Mode: Pack Separately · Prevent Updates: OFF
- [ ] Configure Remote Load Path: `https://cdn.cropshooter.com/[BuildTarget]/[hash]`
- [ ] Cài đặt **SmartAddresser** và tạo Layout Rule để auto-assign group theo folder path

---

## 2. SMARTADDRESSER — Layout Rules

> SmartAddresser tự động assign group + label khi asset được đặt đúng folder. Không cần drag & drop thủ công.

- [ ] Cài SmartAddresser qua Package Manager (git URL)
- [ ] Tạo Layout Rule: `Assets/AddressableAssets/LocalCore/**` → Group: LocalCore
- [ ] Tạo Layout Rule: `Assets/AddressableAssets/Remote/Day5_6/**` → Group: Remote_Day5_6
- [ ] Tạo Layout Rule: `Assets/AddressableAssets/Remote/Day7_9/**` → Group: Remote_Day7_9
- [ ] Tạo Layout Rule: `Assets/AddressableAssets/Remote/Day10_12/**` → Group: Remote_Day10_12
- [ ] Tạo Layout Rule: `Assets/AddressableAssets/Remote/Day13_16/**` → Group: Remote_Day13_16
- [ ] Tạo Layout Rule: `Assets/AddressableAssets/Remote/Day17_Plus/**` → Group: Remote_Day17_Plus
- [ ] Tạo Layout Rule: `Assets/AddressableAssets/OTA/Events/**` → Group: OTA_Events
- [ ] Tạo Layout Rule: `Assets/AddressableAssets/OTA/LiveConfig/**` → Group: OTA_LiveConfig
- [ ] Tạo Label Rules theo type (áp dụng theo SO class hoặc subfolder):
  - `CollectableObjectStat` có `FarmingCropStat` → label: `crop`
  - `CollectableObjectStat` có `AttackingCropStat` → label: `crop` (đã có farming thì không thêm ammo riêng)
  - `CollectableObjectStat` có `CraftedProductStat` + không có `BottleStat` → label: `ingredient` hoặc `food` (dựa theo subfolder)
  - `CollectableObjectStat` có `BottleStat` → label: `bottle`
  - `CollectableObjectStat` có `NaturalResourceStat` → label: `natural`
  - `BuildingSO` → label: `building`
  - `GadgetSO` → label: `gadget`
  - `TextAsset` trong `OTA/LiveConfig/` → label: `live_config`
  - `*` trong `OTA/Events/{eventName}/` → label: `seasonal_{eventName}`
- [ ] Validate Layout Rule bằng SmartAddresser Validate tool
- [ ] Test: tạo 1 asset mẫu → verify group và label được assign đúng tự động

---

## 3. SHARED UI DATA — Registry SO

> Ship cùng LocalCore. UI đọc từ đây để hiển thị danh sách — không cần load Remote bundle.

### 3.1 CropRegistry

- [ ] Tạo `CropRegistry.asset` (ScriptableObject)
  - Fields: `List<CropEntry>` với mỗi entry gồm: `baseID`, `displayName`, `icon`, `unlockDay`, `addressableAddress`
- [ ] Populate đầy đủ 15 crop: Berry, Wheat, Bean, Carrot, Cabbage, Coconut, Beetroot, Tomato, Grape, Carambola, Chili, Apple, Pepper, Durian(WIP), NoniFruit(WIP)
- [ ] Mark Addressable, assign vào LocalCore group, label: `ui_registry`

### 3.2 BottleRegistry

- [ ] Tạo `BottleRegistry.asset`
  - Fields: `List<BottleEntry>` với: `baseID`, `displayName`, `icon`, `unlockDay`, `compatibleGuns`, `effect`, `duration`, `addressableAddress`
- [ ] Populate 9 bottle: FrostBottle, RapidfireBottle, CritBottle, BlazeBottle, VenomBottle, ClusterBottle, CorrosionBottle, ArcBottle, MiasmaBottle
- [ ] Mark Addressable, assign LocalCore, label: `ui_registry`

### 3.3 BuildingRegistry

- [ ] Tạo `BuildingRegistry.asset`
  - Fields: `List<BuildingEntry>` với: `id`, `displayName`, `icon`, `unlockDay`, `buildCost`, `canDemolish`, `addressableAddress`
- [ ] Populate 12 building theo bảng DataSpec Section 7.2
- [ ] Mark Addressable, assign LocalCore, label: `ui_registry`

### 3.4 GadgetRegistry

- [ ] Tạo `GadgetRegistry.asset`
  - Fields: `List<GadgetEntry>` với: `id`, `displayName`, `icon`, `unlockDay`, `blueprintCost`, `group`, `addressableAddress`
- [ ] Populate 8 gadget: Drill, Pump, Apiary, CropTurret, MedStation, RefinaryLink, TurretLink, MarketLink
- [ ] Mark Addressable, assign LocalCore, label: `ui_registry`

### 3.5 Icons (Sprites)

- [ ] Export và import tất cả icon vào `Assets/Art/Icons/`
  - [ ] 15 crop icons
  - [ ] 16 natural resource icons
  - [ ] 15 ingredient icons
  - [ ] 15 food icons
  - [ ] 9 bottle icons
  - [ ] 12 building icons
  - [ ] 8 gadget icons
- [ ] Set import settings: Sprite, Max Size 128px, Crunch Compression
- [ ] Assign icon vào từng `CollectableObjectStat.icon` và Registry entry

---

## 4. COLLECTABLE OBJECT SO — Data Asset

> Tất cả đều là `CollectableObjectStat` với component bitmask phù hợp. Theo DataSpec v3.

### 4.1 Crops & Ammo (FarmingCropStat + AttackingCropStat)

**LocalCore — Day 1–3:**

- [ ] `Berry` — FarmingCropStat ✔ + AttackingCropStat (AR) ✔
  - Address: `"Berry"` · Label: `crop` · Group: LocalCore
- [ ] `Wheat` — FarmingCropStat ✔ + AttackingCropStat (SMG, multiplier=3) ✔
  - Address: `"Wheat"` · Label: `crop` · Group: LocalCore
- [ ] `Bean` — FarmingCropStat ✔ + AttackingCropStat (SMG) ✔
  - Address: `"Bean"` · Label: `crop` · Group: LocalCore
- [ ] `Carrot` — FarmingCropStat ✔ (no attacking)
  - Address: `"Carrot"` · Label: `crop` · Group: LocalCore
- [ ] `Cabbage` — FarmingCropStat ✔ (no attacking)
  - Address: `"Cabbage"` · Label: `crop` · Group: LocalCore
- [ ] `Coconut` — FarmingCropStat ✔ (no attacking)
  - Address: `"Coconut"` · Label: `crop` · Group: LocalCore

**Remote_Day5_6:**

- [ ] `Beetroot` — FarmingCropStat ✔ (no attacking) · unlockDay=5
  - Address: `"Beetroot"` · Label: `crop` · Group: Remote_Day5_6
- [ ] `Tomato` — FarmingCropStat ✔ + AttackingCropStat (Shotgun, bulletCount=5) · unlockDay=6, trigger: Kill300Monsters
  - Address: `"Tomato"` · Label: `crop` · Group: Remote_Day5_6
  - [ ] Set `UnlockTrigger = KillMonsters` trong SO

**Remote_Day7_9:**

- [ ] `Grape` — FarmingCropStat ✔ + AttackingCropStat (special) · unlockDay=8, trigger: OpenTreasurePod
  - Address: `"Grape"` · Label: `crop` · Group: Remote_Day7_9
  - [ ] Set `UnlockTrigger = OpenTreasurePod`

**Remote_Day10_12:**

- [ ] `Carambola` — FarmingCropStat ✔ + AttackingCropStat (Sniper) · unlockDay=10, trigger: DefeatBoss
  - Address: `"Carambola"` · Label: `crop` · Group: Remote_Day10_12
  - [ ] Set `UnlockTrigger = DefeatBoss`
  - [ ] Fix date corruption: `fireRate`, `lifeTime`, `reloadSpeed` (DataSpec note)
- [ ] `Chili` — FarmingCropStat ✔ + AttackingCropStat (Flamethrower) · unlockDay=10
  - Address: `"Chili"` · Label: `crop` · Group: Remote_Day10_12

**Remote_Day13_16:**

- [ ] `Apple` — FarmingCropStat ✔ + AttackingCropStat (Grenade) · unlockDay=15
  - Address: `"Apple"` · Label: `crop` · Group: Remote_Day13_16
- [ ] `Pepper` — FarmingCropStat ✔ + AttackingCropStat (ToxicGrenade) · unlockDay=15
  - Address: `"Pepper"` · Label: `crop` · Group: Remote_Day13_16

**Remote_Day17_Plus (WIP):**

- [ ] `Durian` — FarmingCropStat (WIP) · unlockDay=20
  - Address: `"Durian"` · Label: `crop` · Group: Remote_Day17_Plus
  - [ ] Fix date corruption khi data có (DataSpec note)
- [ ] `NoniFruit` — FarmingCropStat (WIP) · unlockDay=20
  - Address: `"NoniFruit"` · Label: `crop` · Group: Remote_Day17_Plus

### 4.2 Natural Resources (NaturalResourceStat)

**LocalCore — Day 1:**

- [ ] `MonsterMeat` — NaturalResourceStat · source: EnemyDrop · unlockDay=1
  - Address: `"MonsterMeat"` · Label: `natural` · Group: LocalCore
- [ ] `MetalScrap` — NaturalResourceStat · source: Mine/Ruins · unlockDay=1
- [ ] `Sand` — NaturalResourceStat · source: Mine/Beach · unlockDay=1
- [ ] `Trash` — NaturalResourceStat · source: Mine/Ruins · unlockDay=1
- [ ] `Iron` — NaturalResourceStat · source: Mine/Surface · unlockDay=1
  - [ ] Fix durabilityModifier → 1.5 (DataSpec note)
- [ ] `PowerShard` — NaturalResourceStat · source: Mine/Surface · unlockDay=1
- [ ] `Copper` — NaturalResourceStat · source: Mine/Surface · unlockDay=1
- [ ] `Wood` — NaturalResourceStat · source: Tree (WIP) · unlockDay=1
- [ ] `Stone` — NaturalResourceStat · source: Mine/Surface (WIP) · unlockDay=1

**LocalCore — Day 2:**

- [ ] `CoalShallow` — NaturalResourceStat · source: Mine/ShallowCaves · unlockDay=2

**Remote_Day7_9:**

- [ ] `Egg` — NaturalResourceStat · source: CoopProduct · unlockDay=7, trigger: BuildCoop
  - Address: `"Egg"` · Label: `natural` · Group: Remote_Day7_9
  - [ ] Set `UnlockTrigger = BuildCoop`
- [ ] `CoconutMilk` — NaturalResourceStat hoặc CraftedProductStat · unlockDay=3
  - [ ] Xác nhận: Coconut Milk được craft tại CraftingStation → CraftedProductStat

**Remote_Day10_12:**

- [ ] `Coal` — NaturalResourceStat · source: Mine/Caves · unlockDay=10
  - Address: `"Coal"` · Label: `natural` · Group: Remote_Day10_12
- [ ] `Honey` — NaturalResourceStat · source: GadgetProduct/Apiary · unlockDay=11, trigger: PlaceApiary
  - Address: `"Honey"` · Label: `natural` · Group: Remote_Day10_12
  - [ ] Set `UnlockTrigger = PlaceApiary`

**Remote_Day13_16:**

- [ ] `Ruby` — NaturalResourceStat · source: Mine/DeepCaves · unlockDay=15
  - Address: `"Ruby"` · Label: `natural` · Group: Remote_Day13_16
  - [ ] Fix durabilityModifier nếu bị date corruption

**Remote_Day17_Plus:**

- [ ] `GoldCrystal` — NaturalResourceStat · source: Mine/Mountains · unlockDay=20
  - Address: `"GoldCrystal"` · Label: `natural` · Group: Remote_Day17_Plus
  - [ ] Fix durabilityModifier → 2.0 (DataSpec note)

### 4.3 Ingredients (CraftedProductStat, không có BottleStat)

**LocalCore — Day 1:**

- [ ] `Flour` — CraftedProductStat · Recipe: Wheat×3 + Wheat×3 + Wheat×3 (9 total, 3 slot)
  - Address: `"Flour"` · Label: `ingredient` · Group: LocalCore
- [ ] `PowerCore` — CraftedProductStat · Recipe: PowerShard×1 + MetalScrap×1 + Iron×1
  - Address: `"PowerCore"` · Label: `ingredient` · Group: LocalCore
- [ ] `Circuit` — CraftedProductStat · Recipe: PowerShard×1 + MetalScrap×1 + Copper×1
  - Address: `"Circuit"` · Label: `ingredient` · Group: LocalCore

**LocalCore — Day 3:**

- [ ] `BeanOil` — CraftedProductStat · Recipe: Bean×3 + Bean×3 + Bean×3 (9 total)
  - Address: `"BeanOil"` · Label: `ingredient` · Group: LocalCore
- [ ] `CoconutOil` — CraftedProductStat · Recipe: Coconut×3 + Coconut×3 + Coconut×3
  - Address: `"CoconutOil"` · Label: `ingredient` · Group: LocalCore
- [ ] `Margarine` — CraftedProductStat · Recipe: BeanOil×2 + CoconutOil×1 + BeanOil×1
  - Address: `"Margarine"` · Label: `ingredient` · Group: LocalCore
- [ ] `CoconutMilk` — CraftedProductStat · Recipe: Coconut×3 → xác nhận recipe 3 slot
  - Address: `"CoconutMilk"` · Label: `ingredient` · Group: LocalCore

**Remote_Day5_6:**

- [ ] `Sugar` — CraftedProductStat · Recipe: Beetroot×3 + Beetroot×3 + Beetroot×3 (9 total) · unlockDay=5
  - Address: `"Sugar"` · Label: `ingredient` · Group: Remote_Day5_6
- [ ] `GlassVialLv1` — CraftedProductStat · Recipe: Sand×3 + Sand×3 + Sand×3 (9 total) · unlockDay=5
  - Address: `"GlassVialLv1"` · Label: `ingredient` · Group: Remote_Day5_6
- [ ] `CabbageSauce` — CraftedProductStat · Recipe: Cabbage×4 + Sugar×1 + Cabbage×4 · unlockDay=6
  - Address: `"CabbageSauce"` · Label: `ingredient` · Group: Remote_Day5_6

**Remote_Day10_12:**

- [ ] `Cream` — CraftedProductStat · Recipe: CoconutMilk×3 + Sugar×1 + Egg×6 → chia 3 slot · unlockDay=10
  - Address: `"Cream"` · Label: `ingredient` · Group: Remote_Day10_12

**Remote_Day13_16:**

- [ ] `GlassVialLv2` — CraftedProductStat · Recipe: VialLv1×1 + Ruby×2 + VialLv1×1 · unlockDay=15
  - Address: `"GlassVialLv2"` · Label: `ingredient` · Group: Remote_Day13_16
- [ ] `PoisonShard` — CraftedProductStat · Recipe: Trash×6 + Sand×3 → chia 3 slot · unlockDay=15
  - Address: `"PoisonShard"` · Label: `ingredient` · Group: Remote_Day13_16
- [ ] `AcidShard` — CraftedProductStat · Recipe: Trash×6 + MetalScrap×3 → chia 3 slot · unlockDay=15
  - Address: `"AcidShard"` · Label: `ingredient` · Group: Remote_Day13_16

**Remote_Day17_Plus:**

- [ ] `GlassVialLv3` — CraftedProductStat · Recipe: VialLv2×1 + GoldCrystal×2 + VialLv2×1 · unlockDay=20
  - Address: `"GlassVialLv3"` · Label: `ingredient` · Group: Remote_Day17_Plus

### 4.4 Food (CraftedProductStat, filteredType=Crafted, có HP mechanic)

**Remote_Day5_6:**

- [ ] `Bread` — CraftedProductStat · Recipe: Flour×1 + Sugar×1 + Flour×1 · HP+5 · unlockDay=5
  - Address: `"Bread"` · Label: `food` · Group: Remote_Day5_6
- [ ] `SoggyBread` — CraftedProductStat · Recipe: Flour×1 + MonsterMeat×4 + (Flour?) · HP+30, STEALTH · unlockDay=5
  - [ ] Xác nhận recipe 3 slot
- [ ] `BerryCake` — CraftedProductStat · Recipe: Flour×1 + Berry×8 + Sugar×1 · HP+20, → FrostBottle · unlockDay=5
  - Address: `"BerryCake"` · Label: `food` · Group: Remote_Day5_6
- [ ] `BurgerBerry` — CraftedProductStat · Recipe: Flour×1 + Cabbage×4 + Berry×8 · HP+25, → RapidfireBottle · unlockDay=6
  - Address: `"BurgerBerry"` · Label: `food` · Group: Remote_Day5_6

**Remote_Day7_9:**

- [ ] `Omelet` — CraftedProductStat · Recipe: Egg×6 + Egg×6 + Egg×6 (18 total) · HP+25, REGEN · unlockDay=7
  - Address: `"Omelet"` · Label: `food` · Group: Remote_Day7_9
- [ ] `HotBunny` — CraftedProductStat · Recipe: Carrot×4 + Margarine×1 + Carrot×4 · HP+15, CRAFT(1/3) · unlockDay=8
  - Address: `"HotBunny"` · Label: `food` · Group: Remote_Day7_9
- [ ] `CarrotCake` — CraftedProductStat · Recipe: Carrot×5 + CoconutMilk×3 + Sugar×1 · HP+40, CRAFT(2/3) · unlockDay=8
  - Address: `"CarrotCake"` · Label: `food` · Group: Remote_Day7_9
- [ ] `SweetGrapeball` — CraftedProductStat · Recipe: Grape×8 + Sugar×1 + Grape×8 · HP+20, → ClusterBottle · unlockDay=8
  - Address: `"SweetGrapeball"` · Label: `food` · Group: Remote_Day7_9

**Remote_Day10_12:**

- [ ] `TomatoSoup` — CraftedProductStat · Recipe: Tomato×8 + Margarine×1 + Sugar×1 · HP+75+REGEN, → CritBottle · unlockDay=10
  - Address: `"TomatoSoup"` · Label: `food` · Group: Remote_Day10_12

**Remote_Day13_16:**

- [ ] `Burnwich` — CraftedProductStat · Recipe: Flour×1 + Chili×8 + CabbageSauce×1 · HP+35, → BlazeBottle · unlockDay=13
  - Address: `"Burnwich"` · Label: `food` · Group: Remote_Day13_16
- [ ] `RedAlertSalad` — CraftedProductStat · Recipe: Chili×8 + Tomato×8 + Carrot×4 · HP+50, → VenomBottle · unlockDay=13
  - Address: `"RedAlertSalad"` · Label: `food` · Group: Remote_Day13_16
- [ ] `CarambolaCake` — CraftedProductStat · Recipe: Carambola×10 + CoconutMilk×3 + CabbageSauce×1 · HP+60, → ArcBottle · unlockDay=13
  - Address: `"CarambolaCake"` · Label: `food` · Group: Remote_Day13_16
- [ ] `ApplePie` — CraftedProductStat · Recipe: Apple×10 + Flour×1 + Cream×1 · HP+100, CRAFT(3/3) · unlockDay=16
  - Address: `"ApplePie"` · Label: `food` · Group: Remote_Day13_16
- [ ] `FreshSalad` — CraftedProductStat · Recipe: Tomato×8 + Carambola×10 + Pepper×10 · HP+150+REGEN, → CorrosionBottle · unlockDay=16
  - Address: `"FreshSalad"` · Label: `food` · Group: Remote_Day13_16
- [ ] `HoneyCake` — CraftedProductStat · Recipe: Honey×6 + Flour×1 + CoconutMilk×3 · HP+80, → MiasmaBottle · unlockDay=16
  - Address: `"HoneyCake"` · Label: `food` · Group: Remote_Day13_16

### 4.5 Bottles (CraftedProductStat + BottleStat)

**Remote_Day5_6:**

- [ ] `FrostBottle` — CraftedProductStat + BottleStat · Recipe: BerryCake×8 + VialLv1×1 + Iron×2 · unlockDay=5
  - Effect: Slow 30–70%, Freeze 30%, +50% dmg taken · Duration: 12s · Guns: SMG, AR
  - Address: `"FrostBottle"` · Label: `bottle` · Group: Remote_Day5_6
- [ ] `RapidfireBottle` — CraftedProductStat + BottleStat · Recipe: BurgerBerry×8 + VialLv1×1 + Iron×2 · unlockDay=6
  - Effect: +50% fire rate · Duration: 8s · Guns: AR, SMG, Shotgun
  - Address: `"RapidfireBottle"` · Label: `bottle` · Group: Remote_Day5_6

**Remote_Day10_12:**

- [ ] `CritBottle` — CraftedProductStat + BottleStat · Recipe: TomatoSoup×8 + VialLv1×1 + Iron×2 · unlockDay=11
  - Effect: 100% crit, ×2 damage · Duration: 10s · Guns: AR, Shotgun, Sniper
  - Address: `"CritBottle"` · Label: `bottle` · Group: Remote_Day10_12

**Remote_Day13_16:**

- [ ] `BlazeBottle` — CraftedProductStat + BottleStat · Recipe: Burnwich×8 + VialLv1×1 + Coal×2 · unlockDay=13
  - Effect: +30% dmg, fire trail 3/s×4s · Duration: 10s · Guns: Flamethrower, AR
  - Address: `"BlazeBottle"` · Label: `bottle` · Group: Remote_Day13_16
- [ ] `VenomBottle` — CraftedProductStat + BottleStat · Recipe: RedAlertSalad×8 + VialLv1×1 + Coal×2 · unlockDay=13
  - Effect: Poison cloud 4–10dmg/s · Duration: 12s · Guns: ToxicGrenade
  - Address: `"VenomBottle"` · Label: `bottle` · Group: Remote_Day13_16
- [ ] `ClusterBottle` — CraftedProductStat + BottleStat · Recipe: SweetGrapeball×8 + VialLv2×1 + Ruby×2 · unlockDay=15
  - Effect: Split → 3 targets 50% dmg · Duration: 8s · Guns: Grenade, Shotgun
  - Address: `"ClusterBottle"` · Label: `bottle` · Group: Remote_Day13_16
- [ ] `CorrosionBottle` — CraftedProductStat + BottleStat · Recipe: FreshSalad×10 + VialLv2×1 + Ruby×2 · unlockDay=16
  - Effect: Stack +2/4/6/8/10 dmg · Duration: 10s · Guns: Shotgun, Sniper
  - Address: `"CorrosionBottle"` · Label: `bottle` · Group: Remote_Day13_16

**Remote_Day17_Plus:**

- [ ] `ArcBottle` — CraftedProductStat + BottleStat · Recipe: CarambolaCake×10 + VialLv3×1 + GoldCrystal×2 · unlockDay=20
  - Effect: Chain 3 enemies 60% dmg · Duration: 8s · Guns: SMG
  - Address: `"ArcBottle"` · Label: `bottle` · Group: Remote_Day17_Plus
- [ ] `MiasmaBottle` — CraftedProductStat + BottleStat · Recipe: HoneyCake×8 + VialLv3×1 + PoisonShard×2 · unlockDay=21
  - Effect: Cloud 60% density 10dmg/s, 5m AoE · Duration: 12s · Guns: Grenade
  - Address: `"MiasmaBottle"` · Label: `bottle` · Group: Remote_Day17_Plus

---

## 5. RECIPE DATA SO

> Mỗi item được craft cần 1 `RecipeData` SO riêng. Quy tắc 3 slot bắt buộc.

- [ ] Tạo script `RecipeData.cs` (SO với `RecipeSlot[3]`)
- [ ] Tạo RecipeData cho tất cả **Ingredients** (14 SO)
- [ ] Tạo RecipeData cho tất cả **Food** (15 SO)
- [ ] Tạo RecipeData cho tất cả **Bottles** (9 SO)
- [ ] Verify tất cả RecipeData có đúng 3 slot — không để null slot
- [ ] RecipeData KHÔNG mark Addressable (là dependency của CollectableObjectStat, tự được pack)
  - **Ngoại lệ:** Nếu RecipeData dùng chung nhiều item → mark Addressable, assign SharedAssets group

---

## 6. BUILDING SO (BuildingSO / Construction)

**LocalCore — Day 1–4:**

- [ ] `Garden` — BuildingSO · unlockDay=1 · maxLevel=8 · canDemolish=true · providesSlots=4
  - [ ] Tạo 8 `UpgradeOptionInfo` SO cho Garden (PlotII, PlotIII, PlotIV, NutrientSoil, AlluviumSoil, Sprinkler, AutoHarvest, MiracleMix)
  - Address: `"Garden"` · Label: `building` · Group: LocalCore
- [ ] `WaterPurifier` — BuildingSO · unlockDay=1 · maxLevel=4
  - [ ] Tạo 4 `WaterPurifierUpgradeOptionInfo` SO
  - Address: `"WaterPurifier"` · Label: `building` · Group: LocalCore
- [ ] `FarmHouse` — BuildingSO · unlockDay=1 · canDemolish=false · maxLevel=0
  - Address: `"FarmHouse"` · Label: `building` · Group: LocalCore
- [ ] `FarmMarket` — BuildingSO · unlockDay=1 · canDemolish=false · isUnique=true · maxLevel=1
  - Address: `"FarmMarket"` · Label: `building` · Group: LocalCore
- [ ] `Refinery` — BuildingSO · unlockDay=1 · canDemolish=false · maxLevel=0
  - Address: `"Refinery"` · Label: `building` · Group: LocalCore
- [ ] `TreasurePod` — BuildingSO · unlockDay=2 · maxLevel=3 (Lv1/2/3)
  - Address: `"TreasurePod"` · Label: `building` · Group: LocalCore
- [ ] `BuildersShop` — BuildingSO · unlockDay=4 · canDemolish=false · maxLevel=0
  - Address: `"BuildersShop"` · Label: `building` · Group: LocalCore
- [ ] `Silo` — BuildingSO · unlockDay=4 · maxLevel=3 · providesSlots=4
  - [ ] Tạo 3 `UpgradeOptionInfo` SO cho Silo
  - Address: `"Silo"` · Label: `building` · Group: LocalCore
- [ ] `FabricateGadget` — BuildingSO · unlockDay=4 · canDemolish=false · maxLevel=0
  - Address: `"FabricateGadget"` · Label: `building` · Group: LocalCore

**Remote_Day7_9:**

- [ ] `Pond` — BuildingSO · unlockDay=7 · maxLevel=6 · canDemolish=true
  - [ ] Tạo 6 `UpgradeOptionInfo` SO cho Pond
  - Address: `"Pond"` · Label: `building` · Group: Remote_Day7_9
- [ ] `Coop` — BuildingSO · unlockDay=7 · maxLevel=4 · canDemolish=true · providesSlots=12
  - [ ] Tạo 4 `UpgradeOptionInfo` SO cho Coop (HighWall, BugFreeSpringGrass, Vitamizer, ExpandCoop)
  - Address: `"Coop"` · Label: `building` · Group: Remote_Day7_9

---

## 7. GEAR UPGRADE SO

**LocalCore:**

- [ ] Tạo `GearUpgradeInfo` SO (hệ thống tổng)
  - `upgradeSystemId`: `"gear_system"` · `displayName`: `"Gear Upgrade"`
- [ ] Tạo `HeartModuleUpgradeOptionInfo` × 4 cấp:
  - [ ] `HeartOption_Lv1` — hpBonus=25, goldCost=350G, unlockDay=4
  - [ ] `HeartOption_Lv2` — hpBonus=50, goldCost=500G, unlockDay=7
  - [ ] `HeartOption_Lv3` — hpBonus=75, goldCost=750G, unlockDay=12
  - [ ] `HeartOption_Lv4` — hpBonus=100, goldCost=900G, unlockDay=17
- [ ] Tạo Water Module × 3 cấp (+50/+100/+150, Day2/7/12)
- [ ] Tạo Boost Module × 2 cấp (+1/+2, Day4/12)
- [ ] Tạo Backpack Module × 4 cấp (+15/+35/+65/+85, Day5/9/17/21)
- [ ] Tạo Energy Module × 3 cấp (+1/+3/+6 regen, Day5/10/20)
- [ ] Tất cả GearUpgrade SO → assign LocalCore, label: `building` (hoặc tạo label `upgrade`)

---

## 8. GADGET SO

**Remote_Day10_12:**

- [ ] `DrillGadget` — GadgetSO · group=Extractor · unlockDay=4 (blueprint Day4, nhưng asset cần từ Day 4 nên LocalCore)
  - [ ] Xác nhận: Drill unlock Day 4 → assign LocalCore
- [ ] `PumpGadget` — GadgetSO · group=Extractor · unlockDay=7 → Remote_Day7_9
- [ ] `ApiaryGadget` — GadgetSO · group=Extractor · unlockDay=7, trigger: PlaceApiary → Remote_Day7_9
- [ ] `CropTurret` — GadgetSO · group=Utility · unlockDay=10 → Remote_Day10_12
  - Address: `"CropTurret"` · Label: `gadget` · Group: Remote_Day10_12
- [ ] `MedStation` — GadgetSO · group=Utility · unlockDay=13 → Remote_Day13_16
  - Address: `"MedStation"` · Label: `gadget` · Group: Remote_Day13_16

**Remote_Day13_16:**

- [ ] `RefinaryLink` — GadgetSO · group=WarpTech · unlockDay=15 · blueprintOnly: TreasurePodLv3
- [ ] `TurretLink` — GadgetSO · group=WarpTech · unlockDay=16
- [ ] `MarketLink` — GadgetSO · group=WarpTech · unlockDay=18 → Remote_Day17_Plus (Day18 thuộc block này)
  - [ ] Xác nhận: Day18 trong block Day17+ → Remote_Day17_Plus

---

## 9. SPECIAL CRAFT SO

**Remote_Day13_16:**

- [ ] `AppleClearCarrotket` — CollectableObjectStat (special) · unlockDay=16
  - Recipe: HotBunny×1 + CarrotCake×1 + ApplePie×1
  - Effect: Giant carrot rocket AoE, one-use per night, long cooldown
  - [ ] Xác nhận SO type — có thể là class riêng hoặc CraftedProductStat với special flag
  - Address: `"AppleClearCarrotket"` · Label: `special` · Group: Remote_Day13_16

---

## 10. ART ASSETS — Prefab & VFX

> Art asset cần có trước khi assign vào SO fields. Phối hợp với Artist.

### 10.1 Crop Model Prefabs

- [ ] Tạo prefab cho mỗi crop với 2 state: `{CropName}_Growing.prefab` và `{CropName}_Ready.prefab`
- [ ] Assign vào `FarmingCropStat.growingBody` và `defaultModelPlant`
- [ ] Prefab nằm trong đúng day folder để auto-assign Addressable group

### 10.2 VFX Prefabs

- [ ] Seed outer effect (chung cho các crop cùng loại)
- [ ] Whole outer effect (chung hoặc riêng per crop)
- [ ] Trail tracer cho mỗi loại đạn (AR, SMG, Shotgun, Sniper, Grenade, Flamethrower, ToxicGrenade)
- [ ] Hit effect particle cho mỗi loại đạn
- [ ] Assign vào `AttackingCropStat.trailTracer`, `hitEffectPrefab`

### 10.3 Bullet Prefabs

- [ ] `Bullet_AR.prefab`, `Bullet_SMG.prefab`, `Bullet_Shotgun.prefab`...
- [ ] Assign vào `AttackingCropStat.bulletPrefab`

---

## 11. OTA LIVE CONFIG — JSON Files

> Đặt trong `Assets/AddressableAssets/OTA/LiveConfig/`. Auto-label: `live_config`.

- [ ] `CropPriceTable.json` — giá bán crop tại FarmMarket (Perlin Noise base)
- [ ] `MonsterStatTable.json` — HP, damage, speed của từng loại enemy
- [ ] `BottleBalanceData.json` — damage multiplier, duration, AoE của Bottle
- [ ] `DailyChallengeConfig.json` — daily challenge parameters
- [ ] `WeeklyChallengeConfig.json` — weekly challenge parameters
- [ ] Tạo C# class tương ứng để `JsonUtility.FromJson<T>()` deserialize
  - [ ] `CropPriceTable.cs`
  - [ ] `MonsterStatTable.cs`
  - [ ] `BottleBalanceData.cs`
  - [ ] `ChallengeConfig.cs`

---

## 12. WORKFLOW — Quy trình làm việc hàng ngày

### Thêm asset mới

```
1. Tạo SO tại Assets/Data/{Type}/
2. Đặt file vào đúng folder AddressableAssets/{Group}/
   → SmartAddresser tự assign Group + Label
3. Điền đầy đủ fields trong Inspector
4. Assign icon từ Assets/Art/Icons/
5. Cập nhật Registry tương ứng (CropRegistry, BottleRegistry...)
6. Chạy SmartAddresser Validate → không có warning
7. Chạy Addressables Analyze → không có duplicate
```

### Push OTA update (balance patch)

```
1. Cập nhật JSON file trong OTA/LiveConfig/
2. Chạy "Update a Previous Build" (KHÔNG full build)
3. Upload bundle mới lên CDN
4. Catalog tự động update → player nhận patch mỗi session startup
```

### Push seasonal event

```
1. Tạo folder OTA/Events/{eventName}/ (ví dụ: halloween2025)
2. Đặt asset vào folder → SmartAddresser assign label: seasonal_halloween2025
3. Chạy "Update a Previous Build"
4. Upload lên CDN
5. Enable event trong LiveConfig
```

### Kiểm tra trước khi build

- [ ] SmartAddresser Validate — không có warning/error
- [ ] Addressables Analyze → Check Duplicate Bundle Dependencies — no warning
- [ ] Addressables Analyze → Check Resources to Addressable Duplicate Dependencies
- [ ] Tất cả Registry SO đã populate đầy đủ (không có null entry)
- [ ] Tất cả RecipeData có đúng 3 slot (không có null slot)
- [ ] Icon đã assign cho tất cả CollectableObjectStat

---

## 13. CHECKLIST TRƯỚC KHI BUILD RELEASE

- [ ] Tất cả SO đã điền đầy đủ fields (không có field null quan trọng)
- [ ] Fix date corruption: `fireRate`, `lifeTime`, `reloadSpeed` của Carambola, Durian, Wheat, Grape, Bean, Tomato, Chili, Noni
- [ ] Fix `durabilityModifier`: Iron → 1.5, Gold → 2.0
- [ ] Internal Asset Naming Mode: **Dynamic** (không phải Full Path)
- [ ] AssetBundle Compression Local: **LZ4**, Remote: **LZMA**
- [ ] Disable Catalog Update on Startup: **unchecked** (tức là luôn check)
- [ ] Tất cả Remote group: Prevent Updates = **OFF**
- [ ] Tất cả Local group: Prevent Updates = **ON**
- [ ] CRC: Local = Disabled, Remote/OTA = Enabled Excluding Cached
- [ ] Max Concurrent Web Requests: **5–8**
- [ ] Build Addressables trước khi build Player
- [ ] Test Play Mode: Existing Build — verify load time thực tế

---

## 14. ASSET COUNT TRACKER

| Group | SO cần tạo | Prefab cần tạo | Đã xong | Còn lại |
|-------|-----------|----------------|---------|---------|
| LocalCore | ~30 SO | ~10 prefab | 0 | ~40 |
| Remote_Day5_6 | ~15 SO | ~5 prefab | 0 | ~20 |
| Remote_Day7_9 | ~21 SO | ~8 prefab | 0 | ~29 |
| Remote_Day10_12 | ~14 SO | ~5 prefab | 0 | ~19 |
| Remote_Day13_16 | ~23 SO | ~8 prefab | 0 | ~31 |
| Remote_Day17_Plus | ~11 SO | ~4 prefab | 0 | ~15 |
| OTA_Events | 0 (variable) | 0 | — | — |
| OTA_LiveConfig | 5 JSON | 0 | 0 | 5 |
| **TOTAL** | **~114 SO** | **~40 prefab** | **0** | **~154** |

---

*Crop Shooter — Addressables Asset TODO List · v1.0 · Dựa trên GDD v300326 + DataSpec v3.0*
