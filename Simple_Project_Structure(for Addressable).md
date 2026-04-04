# 📁 Project Directory Structure

---

## 🎨 Art

```
Art/
├── Accessories/
├── Animals/
│   └── Materials/
├── Characters/
│   └── Animation/
│       ├── Action/
│       └── Basic/
│           ├── Animator/
│           └── Used Animation/
├── Constructions/
├── Consumables/
├── Effects/
├── Fonts/
├── Materials/
│   ├── Materials/
│   └── Textures/
├── Monster/
│   ├── CommonStuffs/
│   │   ├── Materials/
│   │   ├── Prefab/
│   │   │   ├── Wave01/
│   │   │   │   ├── CharacterPA/
│   │   │   │   └── Weapons/
│   │   │   ├── Wave02/
│   │   │   │   ├── CharacterPA/
│   │   │   │   └── Weapons/
│   │   │   └── Wave03/
│   │   │       ├── CharacterMaskTint/
│   │   │       ├── CharacterPA/
│   │   │       └── Weapons/
│   │   ├── Shader/
│   │   └── Textures/
│   │       ├── DefaultPA/
│   │       └── MaskTintPA/
│   ├── Creeper/
│   │   └── Creeper Cute Series/
│   │       ├── FBX/
│   │       ├── Materials/
│   │       ├── Prefabs/
│   │       └── Textures/
│   ├── HDRP_URP/
│   │   └── URP/
│   │       └── CommonStuffs/
│   │           └── Prefab/
│   │               ├── Wave01/
│   │               │   ├── CharacterPA/
│   │               │   └── Weapons/
│   │               ├── Wave02/
│   │               │   ├── CharacterPA/
│   │               │   └── Weapons/
│   │               └── Wave03/
│   │                   ├── CharacterMaskTint/
│   │                   ├── CharacterPA/
│   │                   └── Weapons/
│   ├── RPGMonsterWave01Polyart/
│   │   ├── Animations/
│   │   │   ├── Bat/
│   │   │   ├── Dragon/
│   │   │   ├── EvilMage/
│   │   │   ├── Golem/
│   │   │   ├── MonsterPlant/
│   │   │   ├── Orc/
│   │   │   ├── Skeleton/
│   │   │   ├── Slime/
│   │   │   ├── Spider/
│   │   │   └── TurtleShell/
│   │   ├── Animators/
│   │   └── Meshes/
│   │       ├── Character/
│   │       └── Weapon/
│   ├── RPGMonsterWave02Polyart/
│   │   ├── Animations/
│   │   │   ├── Beholder/
│   │   │   ├── Black Knight/
│   │   │   ├── Chest Monster/
│   │   │   ├── Crab Monster/
│   │   │   ├── Flying Demon/
│   │   │   ├── Lizard Warrior/
│   │   │   ├── Rat Assassin/
│   │   │   ├── Specter/
│   │   │   ├── Werewolf/
│   │   │   └── Worm Monster/
│   │   ├── Animators/
│   │   └── Meshes/
│   │       ├── Character/
│   │       └── Weapon/
│   └── RPGMonsterWave03Polyart/
│       ├── Animation/
│       │   ├── BattleBee/
│       │   ├── BishopKnight/
│       │   ├── Cactus/
│       │   ├── Cyclops/
│       │   ├── DemonKing/
│       │   ├── Fishman/
│       │   ├── Mushroom/
│       │   ├── NagaWizard/
│       │   ├── Salamander/
│       │   └── StingRay/
│       ├── Animator/
│       └── Mesh/
│           ├── Characters/
│           └── Weapons/
├── Nature/
├── Packages/
│   └── com.unity.render-pipelines.universal/
│       ├── Runtime/
│       │   └── Materials/
│       └── Shaders/
├── Plants/
│   ├── Fruit Market/
│   │   ├── FBX/
│   │   ├── Materials/
│   │   ├── Prefabs/
│   │   └── Textures/
│   │       └── 1024 x 1024/
│   └── Packages/
│       └── com.unity.render-pipelines.universal/
│           ├── Runtime/
│           │   └── Materials/
│           └── Shaders/
├── Props/
├── Resources/
│   └── Natural Resources/
│       └── Animation/
├── Skybox/
├── Sprites/
│   ├── Background/
│   ├── Icon/
│   ├── Icons/
│   │   ├── Construction/
│   │   │   ├── Coop/
│   │   │   ├── Farm House/
│   │   │   ├── Farm Market/
│   │   │   ├── Garden/
│   │   │   ├── Gear Upgrades/
│   │   │   ├── Pond/
│   │   │   ├── Science Lab/
│   │   │   ├── Silo/
│   │   │   ├── Treasure Pod/
│   │   │   └── Water Purifier/
│   │   ├── Potions/
│   │   ├── Skills/
│   │   └── UI/
│   └── Weapon/
├── Textures/
├── UI/
│   ├── Animation/
│   │   ├── Backpack/
│   │   └── Login_Menu/
│   ├── Button/
│   └── Icon/
│       └── Fruit/
│           └── PNG/
└── Weapons/
    ├── Ammo/
    ├── Animation/
    │   ├── Aim/
    │   ├── Backup/
    │   │   └── Equip Weapon/
    │   ├── Equip/
    │   ├── Equip Weapon/
    │   ├── Hold/
    │   ├── Shooting/
    │   └── Shoot_Hit/
```

---

## 🗃️ Game Data

```
Game Data/
├── Ammo/
│   └── Normal/
├── Construction/
│   └── Garden/
├── Enemy/
├── Recipe/
├── Resource/
│   ├── Crafting Product/
│   ├── Farming Product/
│   └── Natural/
└── Weapon/
```

---

## 🧩 Prefabs

```
Prefabs/
├── Ammo/
│   ├── Normal/
│   │   └── Beetroot/
│   └── Pack/
├── Animals/
├── Construction/
│   ├── Fabricate Gadgets/
│   │   └── Parts/
│   ├── Gear Upgrades/
│   │   └── Parts/
│   ├── Shared/
│   │   └── Parts/
│   └── Silo/
│       ├── Parts/
│       └── Upgrades/
├── Environment/
├── Environments/
├── Natural Resources/
├── NFTs/
├── Product/
├── Products/
│   ├── Normal/
│   └── Pack/
├── Temp Object/
├── Temp Objects/
│   └── Weapon/
└── UI/
```

---

## 📜 Scripts

```
Scripts/
├── Common/
│   └── Ultilities/
├── Core/
│   ├── CrossSceneReference/
│   │   ├── Editor/
│   │   ├── Runtime/
│   │   └── Samples/
│   ├── Interfaces/
│   │   └── Suckable/
│   ├── Pattern/
│   │   ├── Factory/
│   │   ├── Observer/
│   │   ├── Pooling/
│   │   ├── Singleton/
│   │   ├── State/
│   │   └── Strategy/
│   ├── SceneManagement/
│   │   └── Editor/
│   └── Stat/
├── Game/
│   ├── Audio/
│   ├── Camera/
│   │   ├── Controller/
│   │   └── Shaking/
│   ├── Construction/
│   │   ├── Garden/
│   │   └── WaterPurifier/
│   ├── Crafting/
│   ├── DOTAnimation/
│   ├── Enemy/
│   ├── Event/
│   ├── Farming/
│   │   ├── General/
│   │   ├── ObjectState/
│   │   │   ├── Crop/
│   │   │   ├── Resource/
│   │   │   └── Water/
│   │   └── Resource/
│   ├── FeedbackEffect/
│   ├── GameManager/
│   │   ├── Economic/
│   │   ├── Progress/
│   │   ├── Scene/
│   │   └── Time/
│   ├── GeneratedScripts/
│   │   └── Pool/
│   ├── Interacting/
│   ├── Inventory/
│   ├── Player/
│   ├── Stat/
│   │   ├── CollectableObject/
│   │   ├── Construction/
│   │   │   └── Upgrade/
│   │   │       ├── Coop/
│   │   │       ├── Fabricate Gadgets/
│   │   │       │   ├── Apiary/
│   │   │       │   ├── Crop Turret/
│   │   │       │   ├── Drill/
│   │   │       │   ├── Med Station/
│   │   │       │   └── Water Pump/
│   │   │       ├── Farm Market/
│   │   │       ├── Garden/
│   │   │       ├── Gear Upgrades/
│   │   │       ├── Pond/
│   │   │       ├── Silo/
│   │   │       ├── Treasure Pod/
│   │   │       └── Water Purifier/
│   │   ├── Enemy/
│   │   ├── FeedbackEffect/
│   │   ├── Player/
│   │   └── Weapon/
│   ├── UI/
│   │   ├── Crafting/
│   │   ├── DisplayItem/
│   │   ├── HUD/
│   │   ├── Interactive/
│   │   ├── Item/
│   │   ├── MonitorGarden/
│   │   ├── Responsive/
│   │   └── Weapon/
│   ├── Vehicle/
│   └── Weapon/
│       ├── Ammo/
│       ├── Collector/
│       ├── General/
│       ├── Grenade/
│       ├── HandGun/
│       └── Primary/
├── Networking/
├── Persistence/
│   ├── Data/
│   │   ├── Authoring/
│   │   │   ├── CsvSheets/
│   │   │   │   └── csv/
│   │   │   │       └── vitsehland-data/
│   │   │   └── GoogleSheets/
│   │   └── Game/
│   └── Editor/
├── Utilities/
└── Web3Manager/
```

---

## ✨ VFX

```
VFX/
├── Materials/
├── Prefabs/
└── Textures/
```
