# 🎨 Artstyle Reference — Crop Shooter GDD Index

---

## Tổng quan phong cách

Giao diện theo hướng **"Pastel Kawaii Game UI"** — lấy cảm hứng từ Slime Rancher và các indie game cute, kết hợp giữa chiều sâu của glassmorphism nhẹ với sự vui tươi của màu pastel bão hòa vừa phải. Cảm giác tổng thể: **mềm mại, sống động, đáng tin cậy**.

---

## Typography

| Vai trò | Font | Weight | Dùng cho |
|---|---|---|---|
| Display / Title | **Fredoka One** | 400 (chỉ có 1 weight) | H1, H2, card title, logo, badge |
| Body | **Nunito** | 400 / 600 / 700 / 800 / 900 | Mọi text còn lại |
| Monospace | **Courier New** (system) | 400 | Filename chip |

**Quy tắc size:**

- Hero H1: `clamp(2.8rem, 7vw, 5rem)` — responsive
- Section H2: `1.4rem`
- Card title: `1.1rem` (Fredoka One)
- Body/desc: `0.8–0.88rem`
- Badge/label nhỏ: `0.68–0.75rem`, `letter-spacing: 1.5–3px`, `text-transform: uppercase`

---

## Color System

### Light Mode

```css
:root {
  /* Backgrounds */
  --bg:     #fdf6ff;   /* Nền chính — tím trắng cực nhạt */
  --bg2:    #f5edff;   /* Nền phụ, footer gradient */
  --cloud:  #ffffff;   /* Card surface */
  --border: #e2d0f8;   /* Border toàn trang */

  /* Brand / Accent */
  --purple: #9b72f5;   /* Màu chủ đạo — mọi CTA, active state */
  --pink:   #ff7ec7;   /* Accent 1 — gradient pair với purple */
  --teal:   #3dd6b0;   /* Accent 2 — construction section */
  --blue:   #52c5f7;   /* Accent 3 — ENG cards */
  --yellow: #ffc94a;   /* Accent 4 — summary/diagram */
  --orange: #ff8f5e;   /* Accent 5 — recipe/warm */
  --green:  #6ee083;   /* Accent 6 — ENG GDD */

  /* Text */
  --text:   #2d1f4e;   /* Body text — tím đậm thay vì đen */
  --muted:  #9a87b8;   /* Placeholder, desc, secondary */

  /* Utility */
  --shadow: rgba(155, 114, 245, 0.13); /* Box shadow chủ đạo */
}
```

### Dark Mode

```css
[data-theme="dark"] {
  /* Backgrounds */
  --bg:     #0f0a1e;   /* Nền chính — tím đen */
  --bg2:    #150d2a;   /* Nền phụ */
  --cloud:  #1a1035;   /* Card surface */
  --border: #2d1f4e;   /* Border */

  /* Brand / Accent — giữ nguyên hue, tăng lightness nhẹ */
  --purple: #a87ff8;
  --pink:   #ff8fd0;
  --teal:   #4de8c0;
  --blue:   #63d0ff;
  --yellow: #ffd166;
  --orange: #ff9f6e;
  --green:  #7ef094;

  /* Text */
  --text:   #ede8ff;   /* Gần trắng, ánh tím */
  --muted:  #7a6a9e;

  /* Utility */
  --shadow: rgba(155, 114, 245, 0.22);
}
```

---

## Gradient Patterns

Toàn trang dùng **2-stop diagonal gradient** theo công thức `135deg`. Không dùng gradient 3 màu cho component nhỏ — chỉ dùng ở hero title.

```css
/* Primary gradient — badge, pill, button active */
background: linear-gradient(135deg, var(--purple), var(--pink));

/* Hero title — duy nhất dùng 3 màu */
background: linear-gradient(135deg, var(--purple) 0%, var(--pink) 45%, var(--yellow) 85%);

/* Feature card background — Light */
background: linear-gradient(135deg, #f5f0ff 0%, #fce7f3 50%, #e0f7fa 100%);
/* Feature card background — Dark */
background: linear-gradient(135deg, #1a1035 0%, #1f1030 50%, #0f1a25 100%);

/* Footer fade */
background: linear-gradient(180deg, transparent, var(--bg2));

/* Section divider line */
background: linear-gradient(90deg, var(--border), transparent);
```

### Per-card color via CSS custom properties

Mỗi card nhận màu riêng qua inline style, cho phép mỗi section có "nhiệt độ màu" khác nhau trong cùng hệ thống:

```css
/* Gán trên element */
style="--c1: #3dd6b0; --c2: #52c5f7; --hover-color: #3dd6b0; --hover-glow: rgba(61,214,176,.2)"

/* Dùng trong CSS */
background: linear-gradient(90deg, var(--c1), var(--c2));  /* top accent bar */
color: var(--c1);                                           /* CTA text color */
box-shadow: 0 14px 40px var(--hover-glow);                 /* hover shadow */
border-color: var(--hover-color);                          /* hover border */
```

### Bảng màu theo section

| Section | `--c1` | `--c2` | Cảm giác |
|---|---|---|---|
| GDD Summary (featured) | `#9b72f5` purple | `#ff7ec7` pink | Chủ đạo |
| Construction VIE | `#3dd6b0` teal | `#52c5f7` blue | Mát, kỹ thuật |
| Construction ENG | `#52c5f7` blue | `#3dd6b0` teal | Đảo ngược pair |
| Summary diagram | `#ffc94a` yellow | `#ff8f5e` orange | Ấm, tổng hợp |
| GDD VIE | `#ff7ec7` pink | `#a78bfa` purple | Nhẹ nhàng |
| GDD ENG | `#6ee083` green | `#52c5f7` blue | Tươi, neutral |
| Recipe | `#ff8f5e` orange | `#ffc94a` yellow | Sáng tạo, food |
| Disabled / inactive | `#94a3b8` gray | `#cbd5e1` gray | Mờ, chưa có |

---

## Background FX

### Blob animation

4 hình tròn mờ, blur nặng, drift chậm theo hướng alternate:

```css
.bg-blob {
  position: absolute;
  border-radius: 50%;
  filter: blur(70px);
  opacity: 0.22;        /* Light: 0.22 | Dark: 0.15 */
  animation: blobFloat 14s ease-in-out infinite alternate;
}

/* Kích thước và màu 4 blob */
/* 1 */ width: 500px; height: 500px; background: #c084fc; top: -100px; left: -120px;
/* 2 */ width: 380px; height: 380px; background: #67e8f9; bottom: -60px; right: -80px;
/* 3 */ width: 300px; height: 300px; background: #fde68a; top: 38%; left: 58%;
/* 4 */ width: 220px; height: 220px; background: #f9a8d4; bottom: 28%; left: 8%;

@keyframes blobFloat {
  from { transform: translate(0, 0) scale(1); }
  to   { transform: translate(35px, 28px) scale(1.08); }
}
```

### Dot grid

Pattern chấm bi rất nhạt phủ toàn trang:

```css
.bg-dots {
  position: fixed; inset: 0; pointer-events: none; z-index: 0;
  background-image: radial-gradient(circle, #c084fc22 1.2px, transparent 1.2px);
  background-size: 36px 36px;
  /* Dark mode: dùng #c084fc11 — giảm opacity xuống một nửa */
}
```

---

## Component Recipes

### Navbar

```css
nav {
  position: sticky; top: 0; z-index: 100;
  height: 64px;
  background: rgba(253, 246, 255, 0.85);  /* Dark: rgba(15,10,30, 0.88) */
  backdrop-filter: blur(20px);
  border-bottom: 1.5px solid var(--border);
  box-shadow: 0 2px 20px rgba(155, 114, 245, 0.08);
}
```

### Card anatomy

```
┌─ 4px gradient top bar (--c1 → --c2) ──────────────┐
│  [icon — 2.4rem emoji]                              │
│  [lang badge — gradient pill, 0.68rem uppercase]    │
│  [title — Fredoka One 1.1rem]                       │
│  [desc — Nunito 0.8rem, var(--muted)]               │
│  [filename — Courier New, bg #f5f0ff / #1a1035]     │
│  [CTA text — "Mở tài liệu →"]                      │
└─────────────────────────────────────────────────────┘
hover: translateY(-6px) + glow shadow + border-color change
```

### Border radius convention

| Element | Radius |
|---|---|
| Card | `22px` |
| Feature card | `28px` |
| Button / pill / badge | `99px` |
| Filename chip | `8px` |
| Blob | `50%` |

### Shadow convention

| Trạng thái | Shadow |
|---|---|
| Card resting | `0 2px 16px var(--shadow)` |
| Card hover | `0 14px 40px var(--hover-glow)` |
| Feature card | `0 4px 30px rgba(192,132,252,.12), 0 1px 0 #fff inset` |
| Active button | `0 2px 10px rgba(155,114,245,.4)` |
| Blob glow | `0 0 8px var(--pink)` |

### Disabled card

```css
.card.disabled {
  opacity: 0.38;
  filter: grayscale(0.4);
  pointer-events: none;
}
.card.disabled::after {
  content: attr(data-soon);       /* text lấy từ data attribute */
  position: absolute; inset: 0;
  display: flex; align-items: center; justify-content: center;
  font-family: 'Fredoka One', cursive;
  background: rgba(253, 246, 255, 0.65);  /* Dark: rgba(15,10,30, 0.65) */
  backdrop-filter: blur(2px);
}
```

---

## Dark Mode — Implementation

### Toggle JS

```javascript
function toggleTheme() {
  const isDark = document.documentElement.dataset.theme === 'dark';
  document.documentElement.dataset.theme = isDark ? '' : 'dark';
  localStorage.setItem('theme', isDark ? 'light' : 'dark');
}

// Restore on page load
if (localStorage.getItem('theme') === 'dark')
  document.documentElement.dataset.theme = 'dark';
```

### Các thành phần cần override thêm ngoài CSS variables

| Element | Light | Dark |
|---|---|---|
| Feature card bg | `linear-gradient(135deg, #f5f0ff, #fce7f3, #e0f7fa)` | `linear-gradient(135deg, #1a1035, #1f1030, #0f1a25)` |
| `.card-filename` bg | `#f5f0ff` | `#1a1035` |
| `.section-note` bg | `linear-gradient(135deg, #fef9c3, #fce7f3)` | `linear-gradient(135deg, #2a1f00, #2a1020)` |
| Blob opacity | `0.22` | `0.15` |
| Dot grid color | `#c084fc22` | `#c084fc11` |
| Nav background | `rgba(253,246,255, 0.85)` | `rgba(15,10,30, 0.88)` |
| Disabled card overlay | `rgba(253,246,255, 0.65)` | `rgba(15,10,30, 0.65)` |

---

## Animation Timing cheat sheet

| Animation | Duration | Easing | Ghi chú |
|---|---|---|---|
| Blob drift | `14–19s` | `ease-in-out infinite alternate` | Stagger bằng `animation-duration` khác nhau |
| Slime float | `5s` | `ease-in-out infinite` | Stagger bằng `animation-delay` |
| Hero title pop | `0.8s` | `cubic-bezier(.175,.885,.32,1.275)` | Chỉ chạy 1 lần khi load |
| Card hover | `0.22s` | `ease` (default) | transform + box-shadow + border |
| Feature card hover | `0.25s` | `ease` | transform + box-shadow |
| Button / pill hover | `0.2–0.22s` | `ease` | background + color |
| CTA arrow shift | `0.2s` | `ease` | `translateX(4px)` |

---

*File này dùng làm reference để tạo các page con cùng hệ thống. Mọi page mới import cùng 2 font (Fredoka One + Nunito), dùng cùng bộ CSS variables, và áp dụng cùng border-radius + shadow convention.*
