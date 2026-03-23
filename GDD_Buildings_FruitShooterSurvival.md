# Buildings & Upgrades

> 🎮 Crop Shooter Survival · 📅 Phiên bản hiện tại · ✍️ Dành cho Designer đọc & chỉnh sửa

---

## 📋 Tổng quan hệ thống

Hệ thống công trình chia làm 3 nhóm chính. Mỗi công trình có thể mua Blueprint tại **Builder's Shop**, đặt lên map, và nâng cấp dần qua các ngày ingame.

| Thông tin | Giá trị |
|---|---|
| Tổng số công trình | 12 công trình |
| Tiền tệ chính | Granumz (G) |
| Gadget có thể chế tạo | 8 gadgets (3 nhóm) |
| Demolish option | Cần cho Farming buildings |

### Flow người chơi — Fabricate Gadget

> **1.** Mua Blueprint tại **Builder's Shop** → **2.** Vào **Fabricate Gadget** và nhấn nút Fabricate → **3.** Thiết bị được lưu lại (chỉ 1 cái) → **4.** Người chơi di chuyển ra vị trí chỉ định → **5.** Chọn 1 điểm để đặt gadget lên map.

### Flow nước — Garden

> **Pond** (nước mặn) → **Water Purifier** (lọc thành nước ngọt) → **Garden** (tưới cây) → Thu hoạch trái cây / nguyên liệu.

### Bảng tất cả công trình

| Tên | Nhóm | Blueprint | Mở ngày | Số upgrade | Chức năng chính |
|---|---|---|---|---|---|
| Gear Upgrades | Base | Free | Day 1 | 16 | Nâng chỉ số người chơi (HP, Water, Speed, Backpack) |
| Ranch House | Base | Free | Day 1 | — | Sleep để bỏ qua ngày/đêm |
| Farm Market | Base | 500G | Day 3 | 1 | Bán trái cây / vật phẩm, dynamic pricing |
| Treasure Pod | Base | Free | Day 1 | 3 tiers | Rải khắp map, reward Granumz + Blueprint |
| Builder's Shop | Base | Free | Day 1 | — | Mua Blueprint mở khoá công trình |
| Garden | Farming | Free | Day 1 | 8 | Công trình farming chính, tối đa 4 plot |
| Silo | Farming | 200G | Day 1 | 4 | Kho chứa vật phẩm, tối đa 4 port |
| Pond | Farming | 300G | Day 2 | 6 | Nguồn nước mặn tự nhiên |
| Water Purifier | Farming | 400G | Day 3 | 4 | Lọc salt water → fresh water |
| Coop | Farming | 500G | Day 5 | 4 | Nuôi gà lấy trứng, tối đa 12–20 gà |
| Refinery | Science Lab | — | Day 1 | — | Lưu trữ vật phẩm (chỉ bỏ vào, không lấy ra) |
| Fabricate Gadget | Science Lab | — | Day 1 | — | Chế tạo công trình / gadget |

---

## 🏠 Base Construction

Các công trình luôn hiện diện trong base của người chơi. Không cần Demolish option. Mở khoá từ ngày đầu.

---

### ⚙️ Gear Upgrades

**Nhóm:** Base · **Mở:** Day 1 · **Blueprint:** Free — không cần Blueprint

Nâng cấp chỉ số cá nhân của người chơi. Mua trực tiếp qua UI interaction, không cần blueprint, luôn available từ Day 1.

> 🎨 **Design Note:** Các chỉ số này ảnh hưởng trực tiếp đến loop farming + combat. Cần cân bằng để người chơi có lý do nâng đều các module thay vì chỉ focus một loại.

#### Heart Module — Tăng max HP

| # | Tên | Effect | Cost | Day |
|---|---|---|---|---|
| 1 | Heart Module Lv1 | +1 max HP slot | 150G | Day 1 |
| 2 | Heart Module Lv2 | +1 max HP slot | 300G | Day 4 |
| 3 | Heart Module Lv3 | +1 max HP slot | 600G | Day 9 |
| 4 | Heart Module Lv4 | +1 max HP slot (max) | 1,200G | Day 14 |

#### Water Module — Tăng sức chứa nước

| # | Tên | Effect | Cost | Day |
|---|---|---|---|---|
| 1 | Water Module Lv1 | +25% max water capacity | 200G | Day 2 |
| 2 | Water Module Lv2 | +25% max water capacity | 400G | Day 7 |
| 3 | Water Module Lv3 | +25% max water capacity (max) | 800G | Day 12 |

#### Boost Module — Tăng tốc độ di chuyển

| # | Tên | Effect | Cost | Day |
|---|---|---|---|---|
| 1 | Boost Module Lv1 | +15% movement speed | 350G | Day 4 |
| 2 | Boost Module Lv2 | +15% movement speed (max) | 700G | Day 9 |

#### Backpack Module — Tăng sức chứa slot

| # | Tên | Effect | Cost | Day |
|---|---|---|---|---|
| 1 | Backpack Lv1 | +10 capacity per slot | 250G | Day 2 |
| 2 | Backpack Lv2 | +10 capacity per slot | 500G | Day 5 |
| 3 | Backpack Lv3 | +10 capacity per slot | 900G | Day 10 |
| 4 | Backpack Lv4 | +10 capacity per slot (max) | 1,600G | Day 16 |

#### Energy Module — Tăng tốc hồi stamina

| # | Tên | Effect | Cost | Day |
|---|---|---|---|---|
| 1 | Energy Module Lv1 | +stamina regen rate | 300G | Day 3 |
| 2 | Energy Module Lv2 | +stamina regen rate | 600G | Day 8 |
| 3 | Energy Module Lv3 | +stamina regen rate (max) | 1,100G | Day 13 |

- [ ] **TODO:** Xác định `BASE_UPGRADE_VALUE` — giá trị HP mỗi slot, % stamina regen cụ thể cho từng level module.

---

### 🏡 Ranch House

**Nhóm:** Base · **Mở:** Day 1 · **Blueprint:** Free

Chức năng chính: **Sleep to skip** — bỏ qua chu kỳ ngày/đêm. Quan trọng: cần cân bằng tốc độ farm để sleep không trở nên vô dụng (crop timer gắn với real time, không phải skip count).

> ⚠️ **Balance Warning:** Tránh để người chơi spam sleep để farm nhanh. Cần cơ chế giới hạn hoặc tied penalty khi skip quá nhiều lần.

---

### 🏪 Farm Market

**Nhóm:** Base · **Mở:** Day 3 · **Blueprint:** 500G · 🔴 Demolish required

Bán trái cây và vật phẩm lấy Granumz. Hệ thống giá động sử dụng **Perlin Noise + chỉ số chênh lệch supply/demand**. Bán nhiều 1 loại → giảm giá (inflation).

> 💡 **Dynamic Pricing:** Dùng Perlin Noise kết hợp chênh lệch số lượng bán giữa các loại vật phẩm. Bán nhiều 1 loại → sụt giá. Khuyến khích người chơi đa dạng hoá cây trồng.

| # | Tên | Effect | Cost | Day | Type |
|---|---|---|---|---|---|
| 1 | Selling Boost | +5% × 2 selling value trên tất cả vật phẩm | 800G | Day 7 | blueprint |

---

### 📦 Treasure Pod

**Nhóm:** Base · **Mở:** Day 1 · **Blueprint:** Free — rải cố định trên map

Rải rác tại các vị trí cố định trên map. Độ khó để reach khác nhau — yêu cầu kỹ năng điều khiển và tận dụng tối đa HandGun. Rewards: **Granumz + Trái cây + Potion + Blueprint Lv3 Fabricate Gadget**.

> 🎨 **Level Design:** Các vị trí Treasure Pod cần có gradient độ khó rõ ràng. Pod Lv3 phải yêu cầu skill ceiling cao — là phần thưởng dành cho hardcore player (cung cấp blueprint gadget cấp cao).

| # | Tier | Reward | Unlock | Type |
|---|---|---|---|---|
| 1 | Treasure Pod Lv1 | Standard pod — common rewards | Day 1 | — |
| 2 | Treasure Pod Lv2 | Medium difficulty — better rewards | Day 8 | milestone |
| 3 | Treasure Pod Lv3 | Hard reach — blueprint + rare item drop | Day 15 | milestone |

---

### 🔨 Builder's Shop

**Nhóm:** Base · **Mở:** Day 1 · **Blueprint:** Free

Mua Blueprint để mở khoá việc xây dựng công trình mới và Fabricate Gadgets. Tất cả công trình đều cần mua Blueprint trước khi đặt.

> 💡 **Note:** Builder's Shop là điểm mua Blueprint bằng Granumz. Một số Gadget Lv3 (WarpTech) chỉ unlock được qua **Treasure Pod Lv3**, không mua được ở đây.

---

## 🌿 Farming Construction

> ⚠️ **Demolish Construction Option required** — Tất cả công trình Farming cần có tính năng Demolish trước khi đặt lại hoặc dời vị trí.

---

### 🌱 Garden

**Nhóm:** Farming · **Mở:** Day 1 · **Blueprint:** Free · 🔴 Demolish required

Công trình chính trong game. Bắt đầu với 1 plot. Mỗi plot trồng 1 loại cây. Trái cây = ammo + nguyên liệu chế biến. Tối đa 4 plot sau khi nâng cấp.

| # | Tên | Effect | Cost | Day | Type |
|---|---|---|---|---|---|
| 1 | Additional Plot II | Mở thêm plot thứ 2 | 300G | Day 2 | — |
| 2 | Nutrient Soil | +% max harvest yield cho mỗi crop | 600G | Day 5 | — |
| 3 | Additional Plot III | Mở thêm plot thứ 3 | 800G | Day 7 | — |
| 4 | Sprinkler | Auto-water tất cả plot — không cần tưới thủ công | 1,000G | Day 9 | — |
| 5 | Additional Plot IV | Mở thêm plot thứ 4 (max) | 1,200G | Day 12 | — |
| 6 | Alluvium Soil | -20% grow time vĩnh viễn cho tất cả cây | 1,500G | Day 14 | — |
| 7 | Auto Harvest | Tự động thu hoạch vào Garden Silo khi cây chín | 1,800G | Day 17 | — |
| 8 | Miracle Mix | +Rotten time · +Harvest count. *Yêu cầu achievement: giết 3 boss* | Free | Day 18 | achievement |

> 🏆 **Miracle Mix Achievement:** Mở khoá sau khi kill 3 boss (15 ngày ingame ≈ 5 giờ playtime). Đây là reward mid-game quan trọng — cần thiết kế các boss milestone rõ ràng.

- [ ] **TODO:** Xác định `BASE_UPGRADE_VALUE` — % yield tăng từ Nutrient Soil, giá trị giảm grow time từ Alluvium Soil.

---

### 🏚️ Silo

**Nhóm:** Farming · **Mở:** Day 1 · **Blueprint:** 200G · 🔴 Demolish required

Kho chứa vật phẩm. Mỗi Port chứa tối đa **150 vật phẩm cùng loại**. Bắt đầu với 1 Port, tối đa 4 Port.

| # | Tên | Effect | Cost | Day |
|---|---|---|---|---|
| 1 | Additional Storage I | Mở Port thứ 2 | 400G | Day 2 |
| 2 | Additional Storage II | Mở Port thứ 3 | 700G | Day 6 |
| 3 | Additional Storage III | Mở Port thứ 4 (max) | 1,100G | Day 11 |
| 4 | Bug Free Spring Grass | +% max egg production. Thức ăn tự nhiên cho gà — cũng dùng được ở Coop | 800G | Day 8 |

- [ ] **TODO:** Xác định max capacity tối ưu (hiện tại là 150 — *modify later*).

---

### 💧 Pond

**Nhóm:** Farming · **Mở:** Day 2 · **Blueprint:** 300G · 🔴 Demolish required

Chứa nước sinh ra từ nguồn tự nhiên. Có khả năng refill với cooldown. Cung cấp **nước mặn (salt water)** — phải qua Water Purifier trước khi tưới Garden.

| # | Tên | Effect | Cost | Day |
|---|---|---|---|---|
| 1 | More Water I | +30% max water capacity | 400G | Day 4 |
| 2 | Decrease Cooldown I | -20% refill cooldown | 500G | Day 7 |
| 3 | More Water II | +30% max water capacity | 700G | Day 9 |
| 4 | Decrease Cooldown II | -20% refill cooldown | 800G | Day 12 |
| 5 | More Water III | +30% max water capacity | 1,000G | Day 14 |
| 6 | More Water IV | +30% max water capacity (max) | 1,300G | Day 17 |

---

### 🔬 Water Purifier

**Nhóm:** Farming · **Mở:** Day 3 · **Blueprint:** 400G · 🔴 Demolish required

Lọc nước từ Pond. Chuyển đổi **Salt Water → Fresh Water** để tưới cây trong Garden.

| # | Tên | Effect | Cost | Day |
|---|---|---|---|---|
| 1 | More Water Contain I | +30% tank capacity | 400G | Day 5 |
| 2 | Decrease Purifier Time | -25% purification duration | 600G | Day 7 |
| 3 | More Water Contain II | +30% tank capacity | 800G | Day 10 |
| 4 | More Water Contain III | +30% capacity (max) | 1,100G | Day 14 |

- [ ] **TODO:** Xác định `BASE_UPGRADE_VALUE` — capacity mặc định, thời gian purify ban đầu.

---

### 🐔 Coop

**Nhóm:** Farming · **Mở:** Day 5 · **Blueprint:** 500G · 🔴 Demolish required

Nuôi gà để lấy trứng và thịt. Tối đa **12 gà (base)**, có thể mở rộng lên 20. Cặp Gà mái + Gà trống → sinh sản mỗi 12h. Gà già sau 6 lần sinh sản → tự chuyển thành thịt.

| # | Tên | Effect | Cost | Day |
|---|---|---|---|---|
| 1 | High Wall | Ngăn Monster tấn công gà ban đêm | 600G | Day 6 |
| 2 | Bug Free Spring Grass | +% max egg production — gà ăn cỏ tự nhiên | 800G | Day 8 |
| 3 | Vitamizer | -20% breeding time · +10% egg production rate | 1,200G | Day 11 |
| 4 | Expand Coop | Tăng max gà từ 12 → 20 | 2,000G | Day 16 |

- [ ] **TODO:** Xác định `BASE_UPGRADE_VALUE` — số trứng/ngày cơ bản, tỉ lệ sinh sản, tốc độ grow từ gà con → gà lớn.

---

## 🧪 Science Lab — Fabricate Gadgets

Science Lab là khu vực tổng chứa 3 hệ thống con: **Refinery**, **Fabricate Gadget**, và **Builder's Shop**.

> 🔧 **Refinery:** Chỉ bỏ vào, không lấy ra được.
> **Builder's Shop:** Mở khoá blueprint (ngoài ra còn sưu tầm từ Treasure Pod).
> **Fabricate Gadget:** Tiến hành chế tạo gadget. Lưu 1 gadget tại 1 thời điểm, đặt lên map tại vị trí chỉ định.

---

### ⛏️ Extractors

Tự động khai thác tài nguyên. Đặt trên resource node hoặc gần công trình. Mỗi gadget có 3 level — level cao hơn tăng tốc độ và sản lượng.

#### Drill

**Mở:** Day 12 · **Blueprint:** 800G · Extract Time: 60s/cycle · Output: 1–2 ore/cycle

| Level | Mô tả | Extract Time | Output | Cost |
|---|---|---|---|---|
| Lv1 | Basic drill | 60s | 1–2 | — |
| Lv2 | -25% cycle time | 45s | 2–3 | 600G |
| Lv3 | -40% cycle time (max) | 36s | 3–5 | 1,200G |

#### Water Pump

**Mở:** Day 7 · **Blueprint:** 500G · Pump Time: 45s/cycle · Output: 10 water/cycle

| Level | Mô tả | Pump Time | Output | Cost |
|---|---|---|---|---|
| Lv1 | Basic pump | 45s | 10 | — |
| Lv2 | -20% cycle time | 36s | 15 | 400G |
| Lv3 | -35% cycle time (max) | 29s | 22 | 900G |

#### Apiary *(milestone)*

**Mở:** Day 11 · **Blueprint:** 600G · Honey Time: 90s/cycle · Output: 1 honey/cycle

| Level | Mô tả | Honey Time | Output | Cost |
|---|---|---|---|---|
| Lv1 | 1 honey per cycle. Yêu cầu milestone *Place_ApiaryGadget* | 90s | 1 | — |
| Lv2 | -25% cycle time | 68s | 2 | 700G |
| Lv3 | -40% cycle time (max) | 54s | 3 | 1,400G |

- [ ] **TODO:** Xác định `BASE_UPGRADE_VALUE` cho Extractors — base max yield, upgrade value per level.

---

### 🛡️ Utilities

Gadget hỗ trợ combat và quality-of-life. Đặt gần base.

#### Crop Turret

**Mở:** Day 10 · **Blueprint:** 700G · Ammo Cap: 10 crops · Fire Rate: 1 shot/2s

> 🎨 **Design Note:** Nạp đạn trái cây vào để tự bán hỗ trợ người chơi buổi tối (defense phase). Các level cho phép nâng tier trái cây và số lượng.

| Level | Mô tả | Ammo Cap | Tier | Fire Rate | Cost |
|---|---|---|---|---|---|
| Lv1 | Basic turret | 10 | Basic only | 1/2s | — |
| Lv2 | Mid-tier crops allowed | 20 | Mid | 1/1.5s | 800G |
| Lv3 | All crop tiers (max) | 35 | All | 1/1s | 1,500G |

#### Med Station

**Mở:** Day 13 · **Blueprint:** 900G · Heal: 20 HP · Cooldown: 30s · Range: 3 tiles

> 🎨 **Design Note:** Khu vực hồi máu. Các level giảm cooldown và tăng lượng máu được hồi. Cần có cooldown giữa các lần dùng để tránh cheesing.

| Level | Mô tả | Heal | Cooldown | Range | Cost |
|---|---|---|---|---|---|
| Lv1 | Base heal station | 20 HP | 30s | 3 tiles | — |
| Lv2 | Improved healing | 35 HP | 20s | 4 tiles | 900G |
| Lv3 | Max healing (max) | 55 HP | 12s | 5 tiles | 1,800G |

- [ ] **TODO:** Xác định `BASE_UPGRADE_VALUE` — sát thương turret theo tier trái cây, cân bằng heal vs HP pool.

---

### 🌀 WarpTech

Công nghệ điều khiển từ xa cao cấp. **Tất cả đều yêu cầu Blueprint từ Treasure Pod Lv3.**

> 🗝️ **WarpTech Unlock:** Không mua được ở Builder's Shop. Chỉ unlock qua **Treasure Pod Lv3** (hard reach). Đây là late-game tech, tạo ra sự khác biệt giữa casual và dedicated player.

#### Refinery Link *(blueprint only)*

**Mở:** Day 15 · Range: Anywhere on map · Capacity: 10/transfer

| Level | Mô tả | Capacity | Cost |
|---|---|---|---|
| Lv1 | Bỏ vật phẩm vào Refinery từ xa | 10 items/transfer | — |
| Lv2 | -30% transfer cooldown | 25 items/transfer | 1,200G |

#### Turret Link *(blueprint only)*

**Mở:** Day 16 · Tile: 1 designated · Capacity: 10 crops stored

> 🎨 **Design Note:** Tự động nạp trái cây từ 1 ô đất cụ thể — chỉ cần có trái cây rơi ra là tự nạp vào Turret. Kết hợp với Garden Auto Harvest tạo ra automation loop hoàn chỉnh.

| Level | Mô tả | Capacity | Tier | Cost |
|---|---|---|---|---|
| Lv1 | Auto-loads 1 tile | 10 | Basic | — |
| Lv2 | Mid tier allowed | 20 | Mid | 1,000G |
| Lv3 | All tiers (max) | 35 | All | 2,000G |

#### Market Link *(blueprint only)*

**Mở:** Day 18 · Sell Delay: +5s vs direct · Batch: 5 items/transaction

| Level | Mô tả | Batch | Delay | Cost |
|---|---|---|---|---|
| Lv1 | Bán vật phẩm từ xa | 5 items | +5s | — |
| Lv2 | Không phạt giá | 15 items | +2s | 1,500G |

- [ ] **TODO:** Xác định `BASE_UPGRADE_VALUE` cho WarpTech — transfer cooldown mặc định của Refinery Link.

---

## 📊 Balance Notes — Chỉ số cần xác định

Danh sách các giá trị đang để ngỏ (`BASE_VALUE` / `BASE_UPGRADE_VALUE`) cần designer/balancer điền vào trước khi implement.

### Gear Upgrades — Base Values

| Module | Chỉ số cần điền | Ghi chú |
|---|---|---|
| Heart Module | HP mỗi slot = ? | Base HP max khi chưa upgrade |
| Water Module | Base water capacity = ? | +25% mỗi level, cần base |
| Boost Module | Base movement speed = ? | +15% mỗi level |
| Backpack | Base capacity per slot = ? | +10 mỗi level |
| Energy Module | Base stamina regen rate = ? / +% mỗi level = ? | Chưa định % tăng cụ thể |

### Farming — Base Values

| Building | Chỉ số cần điền | Ghi chú |
|---|---|---|
| Garden / Nutrient Soil | +% yield = ? | Base yield per harvest trước |
| Silo | Max capacity = 150? | Đang để "modify later" |
| Coop | Trứng/ngày cơ bản = ? / Tỉ lệ sinh sản = ? / Grow time = ? | 12h breeding time sau Vitamizer |
| Pond / Purifier | Base capacity (trước upgrade) = ? | +30% per upgrade, cần base |

### Fabricate Gadgets — Base Values

| Gadget | Chỉ số cần điền | Ghi chú |
|---|---|---|
| Extractor (Drill/Pump/Apiary) | Base max yield = ? / Upgrade value per level = ? | Thời gian cycle đã có, cần yield % |
| Crop Turret | Sát thương theo tier trái cây = ? | Basic / Mid / High tier damage |
| Med Station | Cân bằng heal vs HP pool | Heal 20/35/55 HP — cần test |
| Refinery Link | Transfer cooldown mặc định = ? | Lv2 giảm 30%, cần base cooldown |

---

## 💰 Kinh tế & Granumz

Tất cả chi phí upgrade sử dụng **Granumz (G)** — tiền tệ chính trong game. Nguồn thu chủ yếu từ Farm Market.

> ✅ **Tổng chi phí ước tính để max tất cả:**
> Gear Upgrades: ~9,000G · Garden: ~8,200G · Silo: ~3,000G · Pond: ~4,700G · Purifier: ~2,900G · Coop: ~4,600G · Farm Market: ~1,300G
> **Tổng Base + Farming: ~33,700G**

> 🎨 **Dynamic Pricing System:** Farm Market sử dụng Perlin Noise + supply/demand tracking. Người chơi bán nhiều 1 loại quả → giá giảm (inflation). Khuyến khích đa dạng hoá cây trồng và tối ưu hoá danh mục bán hàng theo ngày.
