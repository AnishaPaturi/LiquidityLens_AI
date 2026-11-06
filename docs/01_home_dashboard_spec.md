# Screen 6: Home Dashboard — High-Fidelity UI Specification

> **Parent Specification:** `docs/00_master_ui_specification.md`  
> **Status:** Finalized for implementation review  
> **Target Platform:** Flutter Mobile (iOS & Android)

---

## 1. Spatial Structure & Layout Grid

- **Canvas Dimensions:** Standard mobile viewport `390 × 844 px` (responsive scaling from `360 px` to `430 px`).
- **Screen Margins:** `20 px` horizontal left/right margins.
- **Card Spacing:** `14 px` vertical spacing between primary dashboard cards.
- **Scroll Margin:** `96 px` bottom padding to prevent content from falling behind the floating navigation pill.

---

## 2. Component Hierarchy & Exact Breakdown

```
+--------------------------------------------------------------+
| [Header] Good evening, Anish        [Bell (dot)]  [Avatar]   |
|          Thu, 5 Nov                                          |
+--------------------------------------------------------------+
| [AVAILABLE BALANCE CARD]                                    |
|   AVAILABLE TRACKED BALANCE                          [Eye]   |
|   ₹42,850.00        [+8.4% vs last mo]                       |
|   ●●● 3 accounts tracked · Updated 12m ago                   |
+--------------------------------------------------------------+
| [FINANCIAL OUTLOOK CARD]                     [Next 30 Days]  |
|   ◉ FINANCIAL OUTLOOK                                        |
|   ₹24,300                                                    |
|   Projected lowest balance around 10 Dec                     |
|   [ ~ ~ ~ Mini Forecast Trajectory Sparkline ~ ~ ~ ]        |
|   High confidence · 60d records           VIEW FORECAST →    |
+--------------------------------------------------------------+
| [INCOME (NOV)]               | [EXPENSES (NOV)]              |
|   ₹35,000                    |   ₹18,250                     |
|   ↑ ₹2,500 vs Oct            |   52% of income spent         |
+--------------------------------------------------------------+
| [UPCOMING OBLIGATIONS]                        View All (3) → |
|   • House Rent       | 5 Dec  | ₹12,000 | [Confirmed]        |
|   • Car Loan EMI     | 10 Dec | ₹4,500  | [Confirmed]        |
|   • Cloud Storage    | 15 Dec | ₹499    | [AI Detected]      |
+--------------------------------------------------------------+
| [LIQUIDITYLENS INTELLIGENCE]                                 |
|   ◎ Obligations cluster in early December                    |
|   68% of outflows fall between Dec 5-10. Keep ₹18k buffer.   |
|   [ Simulate Cash Buffer ]               Why this insight? → |
+--------------------------------------------------------------+
|                          (Bottom spacer 96px)                |
+--------------------------------------------------------------+
| [  Home  |  Activity  |  Insights  |  Simulate  |  Copilot  ] |
+--------------------------------------------------------------+
```

---

## 3. Detailed Component Attributes

### 3.1 Top Header
- **Greeting:** `"Good evening, Anish"` (`17 px`, SemiBold, `#F5F5F0`).
- **Date Subtitle:** `"Thursday, 5 Nov"` (`12 px`, Regular, `#929292`).
- **Notification Icon Container:** `40 × 40 px`, Surface `#141414`, Border `1 px #222222`, Radius `12 px`.
  - Unread Indicator: `6 × 6 px` dot in `#E5FF00` at top right corner.
- **Avatar Container:** `40 × 40 px`, Border `1 px #333333`, Radius `12 px` or circular `20 px`.

### 3.2 Available Balance Card
- **Surface:** `#141414`, Border `1 px solid #222222`, Radius `20 px`, Padding `20 px`.
- **Top Bar:** Label `"AVAILABLE TRACKED BALANCE"` (`11 px`, SemiBold, `#929292`, `tracking: +0.08em`) with Eye toggle icon (`20 px`, `#929292`).
- **Amount:** `"₹42,850.00"` (`34 px`, SemiBold, `#F5F5F0`, tabular numerals).
- **Trend Chip:** `+8.4% vs last month` (`#42D392`, bg `rgba(66, 211, 146, 0.12)`, radius `8 px`, padding `4 px 8 px`).
- **Footer:** 3 source dots (`#929292`) + `"3 accounts tracked · Updated 12m ago"` (`12 px`, `#929292`).

### 3.3 Income & Expenses Metrics
- **Layout:** 2 equal cards separated by `12 px` horizontal gap.
- **Card Styling:** Surface `#141414`, Border `1 px solid #222222`, Radius `18 px`, Padding `16 px`.
- **Income Card:**
  - Label: `"INCOME (NOV)"` (`11 px`, `#929292`)
  - Amount: `"₹35,000"` (`20 px`, SemiBold, `#F5F5F0`)
  - Delta: `↑ ₹2,500 vs Oct` (`12 px`, Medium, `#42D392`)
- **Expenses Card:**
  - Label: `"EXPENSES (NOV)"` (`11 px`, `#929292`)
  - Amount: `"₹18,250"` (`20 px`, SemiBold, `#F5F5F0`)
  - Ratio: `"52% of income spent"` (`12 px`, Medium, `#929292`)

### 3.4 Financial Outlook Card (Hero Intelligence)
- **Surface:** `#141414`, Border `1 px solid #2A2A2A`, Radius `20 px`, Padding `20 px`.
- **Top Row:** Sparkle glyph (`#E5FF00`, `16 px`) + `"FINANCIAL OUTLOOK"` (`12 px`, SemiBold, `#E5FF00`) and `"Next 30 Days"` pill badge (`#202020`, text `#F5F5F0`, `11 px`).
- **Lowest Projected Value:** `"₹24,300"` (`28 px`, SemiBold, `#F5F5F0`).
- **Projection Context:** `"Projected lowest balance around 10 Dec after rent & EMI payments"` (`13 px`, Regular, `#929292`).
- **Sparkline Preview:** Height `44 px`, solid grey historical line (`#929292`), neon dotted future trajectory (`#E5FF00`), orange dotted safety buffer threshold (`#FFAD55`).
- **Bottom Row:** Confidence indicator (`#929292`, `11 px`) + `"VIEW FORECAST →"` interactive button (`13 px`, SemiBold, `#E5FF00`).

### 3.5 Upcoming Obligations Card (Two-Tier Structure)
- **Surface:** `#141414`, Border `1 px solid #222222`, Radius `20 px`, Padding `18 px`.
- **Card Header:**
  - Left: `"UPCOMING OBLIGATIONS"` (`12 px`, SemiBold, `#929292`, tracking `+0.06em`).
  - Right: `"VIEW ALL →"` (`12 px`, SemiBold, `#E5FF00`).
- **Section 1: CONFIRMED (Active Forecast Drivers):**
  - Section header: `"CONFIRMED · 2 PAYMENTS"` (`11 px`, SemiBold, `#65B9FF`).
  - Item 1: House Rent | 5 December · Monthly | `₹12,000` | Badge `Confirmed` (`#65B9FF`, bg `rgba(101, 185, 255, 0.12)`)
  - Item 2: Car Loan EMI | 10 December · Monthly | `₹4,500` | Badge `Confirmed` (`#65B9FF`, bg `rgba(101, 185, 255, 0.12)`)
- **Section 2: AI-DETECTED (Candidate Detections · Excluded from Forecast until Confirmed):**
  - Section header: `"AI-DETECTED · NEEDS REVIEW"` (`11 px`, SemiBold, `#FFAD55`).
  - Item 3: Streaming Subscription | 15 December · Suggested recurring | `₹499` | Badge `AI Detected ✦` (`#E5FF00`, bg `rgba(229, 255, 0, 0.12)`)
  - Action Button: `"REVIEW SUGGESTION →"` (`12 px`, SemiBold, elevated `#202020`, text `#E5FF00`, radius `8 px`, padding `6 px 12 px`).

### 3.6 LiquidityLens AI Insight Card
- **Surface:** `#161616`, Accent Border `1 px solid rgba(229, 255, 0, 0.25)`, Radius `20 px`, Padding `18 px`.
- **Header:** Abstract Eye glyph (`#E5FF00`, `18 px`) + `"LIQUIDITYLENS INTELLIGENCE"` (`11 px`, SemiBold, `#E5FF00`, tracking `+0.06em`).
- **Headline:** `"Obligations cluster in early December"` (`15 px`, SemiBold, `#F5F5F0`).
- **Supporting Narrative:** `"68% of outflows fall between Dec 5-10 (₹16,500 out of ₹18,250). Maintain at least ₹18,000 liquid before 5 Dec to avoid dip anxiety."` (`13 px`, Regular, `#929292`).
- **Actions:** Button `"Simulate Cash Buffer"` (`#202020` elevated button, `#F5F5F0` text, radius `12 px`) and link `"Why this insight? →"` (`13 px`, `#E5FF00`).

---

## 4. Global Hybrid Bubble Navigation Spec

- **Placement:** Floating pill, `bottom: max(20px, env(safe-area-inset-bottom))`, horizontal margins `16 px`.
- **Dimensions:** Height `64 px`, Corner Radius `32 px`.
- **Material:** `#141414EE` with backdrop blur (`16 px`), border `1 px solid #262626`.
- **Destinations (5):**
  1. `Home`
  2. `Activity`
  3. `Insights`
  4. `Simulate`
  5. `Copilot`
- **Active State Animation:**
  - Selected item expands into an animated neon bubble (`#E5FF00`).
  - Active width: `104–112 px`, height `48 px`, radius `24 px`.
  - Icon & text color: `#090909` (Bold, `13 px`).
  - Animation: Spring / cubic ease `200 ms`.
- **Inactive States:**
  - Width: flex distributed (~`52 px`).
  - Icon: `20 × 20 px`, `#929292`.
  - Label: `10 px`, `#7A7A7A`.
