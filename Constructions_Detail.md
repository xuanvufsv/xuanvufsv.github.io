# Construction & Upgrades

> 🎮 Crop Shooter · 📅 Phiên bản hiện tại · ✍️ Dành cho Designer đọc & chỉnh sửa

---

## Tổng quan hệ thống

Hệ thống công trình chia làm 3 nhóm chính. Mỗi công trình có thể mua Blueprint tại **Builder's Shop**, đặt lên map và nâng cấp dần qua các ngày in-game.

| Thông tin | Giá trị |
| --- | --- |
| Tổng số công trình | 12 công trình |
| Tiền tệ chính | Granumz (G) |
| Gadget có thể chế tạo | 8 gadgets (3 nhóm) |
| Demolish option | Trừ công trình có sẵn |

### Fabricate Gadget Flow

> **1.** Unlock Blueprint tại **Builder's Shop** → **2.** Vào **Fabricate Gadget** và nhấn Fabricate → **3.** Gadget được lưu lại (chỉ 1 cái tại một thời điểm) → **4.** Di chuyển ra vị trí chỉ định → **5.** Chọn điểm đặt lên map.

### Garden Flow

> **Pond / Natural Water Sources** (nước mặn) → **Water Purifier** (lọc thành nước ngọt) → **Garden** (tưới cây) → Thu hoạch trái cây.

### Bảng tất cả công trình *(sắp xếp theo ngày unlock)*

| # | Tên | Nhóm | Blueprint | Ngày Unlock | Số Upgrade | Chức năng chính |
| --- | --- | --- | --- | --- | --- | --- |
| 1 | Gear Upgrades | Base | — | Day 1 | 16 | Nâng chỉ số người chơi (HP, Water, Speed, Backpack) |
| 2 | Farm House | Base | — | Day 1 | — | Sleep để bỏ qua phần còn lại của đêm |
| 3 | Farm Market | Base | — | Day 1 | 1 | Bán trái cây / vật phẩm, dynamic pricing |
| 4 | Garden | Farming | — | Day 1 | 8 | Công trình farming chính, tối đa 4 plot |
| 5 | Water Purifier | Farming | — | Day 1 | 4 | Lọc salt water → fresh water |
| 6 | Refinery | Science Lab | — | Day 1 | — | Lưu trữ vật phẩm (chỉ bỏ vào, không lấy ra) |
| 7 | Treasure Pod | Base | — | Day 2 | 3 tiers | Rải khắp map, reward Granumz + Crops + Resources + Blueprint |
| 8 | Builder's Shop | Base | — | Day 4 | — | Mua Blueprint mở khoá công trình |
| 9 | Silo | Storing | — | Day 4 | 3 | Kho chứa vật phẩm, tối đa 4 port |
| 10 | Fabricate Gadget | Science Lab | — | Day 4 | — | Chế tạo và đặt Gadget ra map |
| 11 | Pond | Farming | — | Day 7 | 6 | Nguồn nước mặn tự nhiên |
| 12 | Coop | Farming | — | Day 7 | 4 | Nuôi gà lấy trứng và thịt, tối đa 6–12 gà |

---

## 🏠 Base Construction

Các công trình luôn hiện diện tại khu vực chính của farm. Không có Demolish option. Mở khoá từ Day 1 đến Day 4.

---

### ⚙️ Gear Upgrades

**Nhóm:** Base · **Mở:** Day 1 · **Blueprint:** Không cần.

Nâng cấp chỉ số cá nhân của người chơi. Mua trực tiếp qua UI, không cần blueprint, available từ Day 1.

> 🎨 **Design Note:** Các chỉ số này ảnh hưởng trực tiếp đến loop farming và combat. Cần cân bằng để người chơi có lý do nâng đều các module thay vì chỉ tập trung một loại.

---

#### Heart Module — Tăng max HP · Base: 50

| # | Tên | Effect | Cost | Day |
| --- | --- | --- | --- | --- |
| 1 | Heart Module Lv1 | +25 max HP | 350G | Day 4 |
| 2 | Heart Module Lv2 | +50 max HP | 500G | Day 7 |
| 3 | Heart Module Lv3 | +75 max HP | 750G | Day 12 |
| 4 | Heart Module Lv4 | +100 max HP (max) | 900G | Day 17 |

#### Water Module — Tăng sức chứa nước · Base: 100

| # | Tên | Effect | Cost | Day |
| --- | --- | --- | --- | --- |
| 1 | Water Module Lv1 | +50 water capacity | 350G | Day 2 |
| 2 | Water Module Lv2 | +100 water capacity | 500G | Day 7 |
| 3 | Water Module Lv3 | +150 water capacity (max) | 750G | Day 12 |

#### Boost Module — Tăng tốc độ di chuyển · Base: Walk 5 / Run 7

| # | Tên | Effect | Cost | Day |
| --- | --- | --- | --- | --- |
| 1 | Boost Module Lv1 | +1 movement speed | 500G | Day 4 |
| 2 | Boost Module Lv2 | +2 movement speed (max) | 950G | Day 12 |

#### Backpack Module — Tăng sức chứa · Base: 50

| # | Tên | Effect | Cost | Day |
| --- | --- | --- | --- | --- |
| 1 | Backpack Lv1 | +15 capacity | 500G | Day 5 |
| 2 | Backpack Lv2 | +35 capacity | 950G | Day 9 |
| 3 | Backpack Lv3 | +65 capacity | 4,500G | Day 17 |
| 4 | Backpack Lv4 | +85 capacity (max) | 9,000G | Day 21 |

#### Energy Module — Tăng tốc hồi stamina · Base: 100, 10/s

| # | Tên | Effect | Cost | Day |
| --- | --- | --- | --- | --- |
| 1 | Energy Module Lv1 | +1 stamina regen | 300G | Day 5 |
| 2 | Energy Module Lv2 | +3 stamina regen | 600G | Day 10 |
| 3 | Energy Module Lv3 | +6 stamina regen (max) | 1,100G | Day 20 |

> - [ ] **TODO:** Xác định `BASE_UPGRADE_VALUE` — giá trị HP mỗi slot, stamina regen cụ thể cho từng level module.

---

### 🏡 Farm House

**Nhóm:** Base · **Mở:** Day 1 · **Blueprint:** Không cần.

**Sleep to skip** — bỏ qua phần còn lại của đêm, chuyển thẳng đến 7h sáng. Có thể ngủ sau khi dọn sạch quái hoặc từ 3h sáng. Khi thức dậy: hồi đầy HP và Energy.

> ⚠️ Ngủ sớm = mất phút farm ban đêm (drop Granumz, trái cây, blueprint). Cần cân bằng tốc độ farm để Sleep không bị spam.

---

### 🏪 Farm Market

**Nhóm:** Base · **Mở:** Day 1 · **Blueprint:** Không cần.

Bán trái cây và vật phẩm lấy Granumz. Hệ thống giá động sử dụng **Perlin Noise + chỉ số chênh lệch supply/demand**. Bán nhiều 1 loại → giảm giá. Khuyến khích người chơi đa dạng hoá cây trồng.

> 💡 **Dynamic Pricing:** Dùng Perlin Noise kết hợp chênh lệch số lượng bán giữa các loại vật phẩm. Bán nhiều 1 loại → sụt giá. Đa dạng hoá danh mục bán để giữ giá tốt.

| # | Tên | Effect | Cost | Day | Type |
| --- | --- | --- | --- | --- | --- |
| 1 | Selling Boost | +5% sell value trên tất cả vật phẩm (×2 lần) | Free | — | Unlock Event |

---

### 📦 Treasure Pod

**Nhóm:** Base · **Mở:** Day 2 · **Blueprint:** Free — rải cố định trên map.

Rải rác tại các vị trí cố định trên map, từ địa hình đơn giản đến hiểm trở (khe đá, cây cao…). Độ khó để tiếp cận khác nhau — yêu cầu kỹ năng điều khiển và HandGun. Reward: **Granumz + Trái cây + Potion + Blueprint Lv3 Fabricate Gadget**.

> 🎨 **Level Design:** Các vị trí Treasure Pod cần có gradient độ khó rõ ràng. Pod Lv3 phải yêu cầu skill ceiling cao — phần thưởng dành riêng cho hardcore player, cung cấp blueprint gadget cấp cao.

| # | Tier | Reward | Ngày xuất hiện | Type |
| --- | --- | --- | --- | --- |
| 1 | Treasure Pod Lv1 | Standard pod — common rewards | Day 2 | — |
| 2 | Treasure Pod Lv2 | Medium difficulty — better rewards | Day 8 | Milestone |
| 3 | Treasure Pod Lv3 | Hard reach — blueprint + rare item drop | Day 15 | Milestone |

---

### 🔨 Builder's Shop

**Nhóm:** Base · **Mở:** Day 4 · **Blueprint:** Không cần.

Mua Blueprint bằng Granumz để mở khoá xây dựng công trình mới và Fabricate Gadgets.

> 💡 **Lưu ý:** Một số Gadget WarpTech Lv3 chỉ unlock được qua **Treasure Pod Lv3**, không mua tại đây.

---

## 🌿 Farming Construction

> ⚠️ **Demolish required** — Tất cả công trình Farming đều có thể Demolish để người chơi phá huỷ và thay thế bằng công trình khác.

---

### 🌱 Garden

**Nhóm:** Farming · **Mở:** Day 1 · **Blueprint:** Không cần · 🔴 Demolish required.

Công trình farming chính. Bắt đầu với 1 plot — mỗi plot trồng 1 loại cây. Trái cây = đạn = nguyên liệu craft. Tối đa 4 plot sau khi nâng cấp.

| # | Tên | Effect | Cost | Day | Type |
| --- | --- | --- | --- | --- | --- |
| 1 | Additional Plot II | Mở thêm plot thứ 2 | 350G | Day 1 | — |
| 2 | Additional Plot III | Mở thêm plot thứ 3 | 350G | Day 1 | — |
| 3 | Additional Plot IV | Mở thêm plot thứ 4 (max) | 350G | Day 1 | — |
| 4 | Nutrient Soil | +25% max harvest yield cho tất cả cây | 500G | Day 5 | — |
| 5 | Alluvium Soil | -20% grow time vĩnh viễn cho tất cả cây | 900G | Day 8 | — |
| 6 | Sprinkler | Auto-water tất cả plot — không cần tưới thủ công | 1,500G | Day 10 | — |
| 7 | Auto Harvest | Tự động thu hoạch vào Silo khi cây chín | 1,800G | Day 15 | — |
| 8 | Miracle Mix | +Rotten timer · +Harvest count | Free | — | Achievement |

> 🏆 **Miracle Mix:** Unlock sau khi giết 4 boss (Day 5 / 10 / 15 / 20). Reward mid-game quan trọng — cần thiết kế các boss milestone rõ ràng.

> - [ ] **TODO:** Xác định `BASE_UPGRADE_VALUE` — % yield tăng từ Nutrient Soil, giá trị giảm grow time từ Alluvium Soil.

---

### 🏚️ Silo

**Nhóm:** Storing · **Mở:** Day 4 · **Blueprint:** Không cần · 🔴 Demolish required.

Kho chứa vật phẩm. Mỗi port chứa tối đa **150 vật phẩm cùng loại**. Bắt đầu với 1 port (Port I), tối đa 4 port.

| # | Tên | Effect | Cost | Day |
| --- | --- | --- | --- | --- |
| 1 | Additional Storage II | Mở Port thứ 2 | 500G | Day 4 |
| 2 | Additional Storage III | Mở Port thứ 3 | 500G | Day 4 |
| 3 | Additional Storage IV | Mở Port thứ 4 (max) | 1,100G | Day 4 |

> - [ ] **TODO:** Xác định max capacity tối ưu (hiện tại là 150 — *modify later*).

---

### 💧 Pond

**Nhóm:** Farming · **Mở:** Day 7 · **Blueprint:** Không cần · 🔴 Demolish required.

Chứa nước sinh ra từ nguồn tự nhiên. Có khả năng refill tự động với cooldown. Cung cấp **nước mặn (salt water)** — phải qua Water Purifier trước khi tưới Garden.

| # | Tên | Effect | Cost | Day |
| --- | --- | --- | --- | --- |
| 1 | More Water I | +20 max water capacity | 350G | Day 7 |
| 2 | Decrease Cooldown I | -20% refill cooldown | 350G | Day 7 |
| 3 | More Water II | +30 max water capacity | 500G | Day 7 |
| 4 | Decrease Cooldown II | -20% refill cooldown | 500G | Day 7 |
| 5 | More Water III | +50 max water capacity | 1,300G | Day 7 |
| 6 | More Water IV | +100 max water capacity (max) | 1,300G | Day 7 |

---

### 🔬 Water Purifier

**Nhóm:** Farming · **Mở:** Day 1 · **Blueprint:** Không cần · 🔴 Demolish required.

Lọc nước từ Pond hoặc Natural Water Sources. Chuyển đổi **Salt Water → Fresh Water** để tưới cây trong Garden. Chạy tự động trong Sleep phase.

| # | Tên | Effect | Cost | Day |
| --- | --- | --- | --- | --- |
| 1 | More Water Contain I | +25 tank capacity | 350G | Day 1 |
| 2 | Decrease Purifier Time I | -25% purification time | 350G | Day 5 |
| 3 | More Water Contain II | +25 tank capacity | 500G | Day 7 |
| 4 | More Water Contain III | +50 tank capacity (max) | 1,100G | Day 10 |

> - [ ] **TODO:** Xác định `BASE_UPGRADE_VALUE` — capacity mặc định, thời gian purify ban đầu.

---

### 🐔 Coop

**Nhóm:** Farming · **Mở:** Day 7 · **Blueprint:** Không cần · 🔴 Demolish required.

Nuôi gà để lấy trứng và thịt. Tối đa **6 gà (base)**, mở rộng lên 12. Cặp Hen + Rooster sinh sản mỗi 12h in-game. Gà già sau 6 lần sinh sản tự chuyển thành thịt.

| # | Tên | Effect | Cost | Day |
| --- | --- | --- | --- | --- |
| 1 | High Wall | Ngăn Monster tấn công gà ban đêm | 900G | Day 7 |
| 2 | Bug Free Spring Grass | +% max egg production — gà ăn cỏ tự nhiên | 900G | Day 7 |
| 3 | Vitamizer | -20% breeding time · +10% egg production rate | 1,200G | Day 7 |
| 4 | Expand Coop | Tăng max gà từ 6 → 12 | 2,000G | Day 7 |

> - [ ] **TODO:** Xác định `BASE_UPGRADE_VALUE` — số trứng/ngày cơ bản, tỉ lệ sinh sản, thời gian gà con → gà lớn.

---

## 🧪 Science Lab — Fabricate Gadgets

Science Lab là hub công nghệ trung tâm, gồm 3 hệ thống con: **Refinery**, **Fabricate Gadget** và **Builder's Shop**.

> **Refinery:** Kho lưu trữ trung tâm — chỉ bỏ vào, không lấy ra. Kết nối với Refinery Link để nạp từ xa.
> **Builder's Shop:** Mua Blueprint bằng Granumz. Một số Blueprint Gadget Lv3 chỉ có từ Treasure Pod.
> **Fabricate Gadget:** Chế tạo Gadget từ Blueprint đã mở. Lưu 1 Gadget tại một thời điểm, đặt lên map tại vị trí chỉ định.

---

### ⛏️ Extractors

Tự động khai thác tài nguyên. Đặt trên resource node hoặc gần công trình. Mỗi gadget có 3 level — level cao hơn tăng tốc độ và sản lượng.

---

#### Drill

**Mở:** Day 4 · **Blueprint:** 500G · Extract Time: 18h/cycle · Output: 10–40 items/cycle

| Level | Output | Cost |
| --- | --- | --- |
| Lv1 | 10–20 items | 450G |
| Lv2 | 20–30 items | 800G |
| Lv3 | 30–40 items | 1,300G |

#### Water Pump

**Mở:** Day 7 · **Blueprint:** 750G · Pump Time: 6h/cycle · Output: 100–200 water/cycle

| Level | Output | Cost |
| --- | --- | --- |
| Lv1 | 100 water | 450G |
| Lv2 | 150 water | 800G |
| Lv3 | 200 water | 1,300G |

#### Apiary *(Milestone)*

**Mở:** Day 11 · **Blueprint:** 1,000G · Honey Time: 12h/cycle · Output: 3–9 honey/cycle

| Level | Output | Cost |
| --- | --- | --- |
| Lv1 | 3 honey | 450G |
| Lv2 | 6 honey | 800G |
| Lv3 | 9 honey | 1,300G |

> - [ ] **TODO:** Xác định `BASE_UPGRADE_VALUE` cho Extractors — base max yield, upgrade value per level.

---

### 🛡️ Utilities

Gadget hỗ trợ combat và quality-of-life. Đặt gần base.

---

#### Crop Turret

**Mở:** Day 10 · **Blueprint:** 2,000G · Ammo Cap: 200 crops · Fire Rate: 1 shot/2s

> 🎨 **Design Note:** Nạp trái cây vào để tự động bắn quái trong phase đêm. Các level nâng tier trái cây được phép nạp và tổng ammo cap.

| Level | Mô tả | Ammo Cap | Tier | Fire Rate | Cost |
| --- | --- | --- | --- | --- | --- |
| Lv1 | Basic turret | 200 | Basic only | 1/2s | 1,300G |
| Lv2 | Mid-tier crops allowed | 250 | Mid | 1/1.5s | 4,000G |
| Lv3 | All crop tiers (max) | 350 | All | 1/1s | 9,000G |

#### Med Station

**Mở:** Day 13 · **Blueprint:** 900G · Heal: 100 HP · Cooldown: 4h · Range: 3m

> 🎨 **Design Note:** Khu vực hồi máu khi đứng gần. Các level giảm cooldown và tăng lượng HP hồi mỗi lần. Cần có cooldown giữa các lần dùng để tránh abuse.

| Level | Mô tả | Heal | Cooldown | Range | Cost |
| --- | --- | --- | --- | --- | --- |
| Lv1 | Base heal station | 100 HP | 4h | 3m | 500G |
| Lv2 | Improved healing | 125 HP | 3h | 4m | 900G |
| Lv3 | Max healing (max) | 150 HP | 3h | 5m | 1,300G |

> - [ ] **TODO:** Xác định `BASE_UPGRADE_VALUE` — sát thương Turret theo tier trái cây, cân bằng heal vs HP pool.

---

### 🌀 WarpTech

Công nghệ điều khiển từ xa cao cấp. **Tất cả đều yêu cầu Blueprint từ Treasure Pod Lv3**, không mua tại Builder's Shop.

> 🗝️ **WarpTech Unlock:** Chỉ unlock qua **Treasure Pod Lv3** (hard reach). Đây là late-game tech, tạo ra sự khác biệt giữa casual và dedicated player.

---

#### Refinery Link *(Blueprint only)*

**Mở:** Day 15 · **Cost:** 2,000G · **Range:** Toàn map · Không có upgrade.

Nạp vật phẩm vào Refinery từ xa. Giảm áp lực Backpack khi farm xa base.

#### Turret Link *(Blueprint only)*

**Mở:** Day 16 · **Cost:** 4,500G · Không có upgrade.

Tự động nạp trái cây từ 1 ô đất chỉ định vào Crop Turret gần nhất. Kết hợp với Garden Auto Harvest tạo ra automation loop hoàn chỉnh.

#### Market Link *(Blueprint only)*

**Mở:** Day 18 · **Cost:** 4,500G · Không có upgrade.

Bán vật phẩm từ xa — không cần di chuyển về Farm Market. Tiện khi farm ban ngày.

> - [ ] **TODO:** Xác định `BASE_UPGRADE_VALUE` cho WarpTech — transfer cooldown mặc định của Refinery Link.

---

## 💰 Kinh tế & Granumz

Tất cả chi phí upgrade sử dụng **Granumz (G)** — tiền tệ chính trong game. Nguồn thu chủ yếu từ Farm Market.

> ✅ **Tổng chi phí ước tính để max tất cả:**
> Gear Upgrades: ~22,500G · Garden: ~5,750G · Silo: ~2,100G · Pond: ~4,300G · Purifier: ~2,300G · Coop: ~5,000G · Farm Market: Free
> **Tổng Base + Farming: ~41,950G**
>
> Gadgets (Blueprint + Upgrades): Drill ~3,050G · Water Pump ~3,300G · Apiary ~3,550G · Crop Turret ~16,300G · Med Station ~3,600G · Refinery Link ~2,000G · Turret Link ~4,500G · Market Link ~4,500G
> **Tổng Gadgets: ~40,800G**
>
> **🏆 Tổng tất cả: ~82,750G**

> 🎨 **Dynamic Pricing System:** Farm Market sử dụng Perlin Noise + supply/demand tracking. Người chơi bán nhiều 1 loại quả → giá giảm (inflation). Khuyến khích đa dạng hoá cây trồng và tối ưu hoá danh mục bán hàng theo ngày.