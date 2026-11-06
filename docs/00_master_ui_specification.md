# LiquidityLens AI — Final UI Design Specification (Product Locked)

## Product Foundation
- **Platform:** Flutter mobile application
- **Product Identity:** Financial Decision Intelligence
- **Core Concept:** *"See beyond your balance. Understand what happens next."*
- **Theme:** Deep Black (`#090909`) + Neon Yellow (`#E5FF00`)
- **Logo:** Abstract eye/lens symbol (Observation, Analysis, Forward-Looking Intelligence)
- **Dashboard Density:** Balanced
- **Bottom Navigation:** Hybrid Bubble Navigation (5 destinations)

---

## 1. Brand Identity & Visual Language

### 1.1 Color Tokens
- `Deep Black`: `#090909` (Primary background canvas)
- `Surface`: `#141414` (Cards, navigation, primary surfaces)
- `Elevated`: `#202020` (Nested cards, inputs, secondary surfaces)
- `Neon Yellow`: `#E5FF00` (Brand accent, primary actions, active bubble navigation, key forward insights)
- `Soft White`: `#F5F5F0` (Headings, primary text, financial numbers)
- `Muted Grey`: `#929292` (Subtitles, secondary labels, timestamps)

### Semantic Indicators (Separate from Neon Yellow Brand Accent)
- `Positive Movement`: `#42D392`
- `Risk / Deficit`: `#FF626C`
- `Caution / Due Soon`: `#FFAD55`
- `Neutral / Information`: `#65B9FF`

### 1.2 Typography (Inter with Tabular Figures `tnum`)
- Main balance: 32–36 px, semibold
- Screen heading: 25–28 px, semibold
- Card heading: 16–18 px, semibold
- Body: 14–15 px, regular
- Secondary labels: 12–13 px
- Buttons: 14–15 px, semibold

### 1.3 Component Radius Standards
- Cards: 18–22 px
- Primary Buttons: 14–16 px
- Inputs: 14 px
- Modal sheets: 24 px top corners
- Borders: 1 px subtle grey (`#222222` / `#282828`)
- Shadows: Minimal, floating elements only

---

## 2. Global Navigation: Hybrid Bubble Navigation
Five destinations:
1. `Home`
2. `Activity` (Transactions, Obligations, Imports)
3. `Insights` (Overview, Liquidity Forecast, Financial Health, Reports)
4. `Simulate` (What-if scenario engine)
5. `Copilot` (Conversational financial intelligence)

Interaction:
- Active destination expands into an animated neon bubble (`#E5FF00` background, `#090909` bold text/icon).
- Inactive destinations remain compact with outline icon and subtle label.
- Fixed floating bar above device safe area with background blur.

---

## 3. Screen Inventory (27 Screens)

### Group A — Entry, Onboarding & Authentication
- Screen 1: Splash Screen
- Screen 2: Welcome & Onboarding (3 slides)
- Screen 3: Registration
- Screen 4: Login
- Screen 5: Financial Profile Setup (4-step guided setup)

### Group B — Main Dashboard & Financial Activity
- Screen 6: Home Dashboard (Priority)
- Screen 7: Activity (Transactions, Obligations, Imports tabs)
- Screen 8: Add Transaction
- Screen 9: Transaction Details
- Screen 10: Data Import (CSV upload, manual entry, sample data)
- Screen 11: Import Preview & Column Validation
- Screen 12: Obligations Management
- Screen 13: Add / Edit Obligation

### Group C — Insights & Financial Intelligence
- Screen 14: Insights Overview (Trends & Breakdown)
- Screen 15: Liquidity Forecast (Core Differentiator: 7/15/30/90 days + uncertainty bands)
- Screen 16: Financial Health (Financial Stress Index + resilience metrics)
- Screen 17: Reports (Exportable print-friendly summaries)

### Group D — Scenario Simulator
- Screen 18: Simulator Home (What-if catalog)
- Screen 19: Scenario Configuration (Dynamic variable inputs)
- Screen 20: Scenario Results (Hypothetical cash-flow comparison)

### Group E — Financial Copilot
- Screen 21: Copilot Home (Analytical prompts & guidance)
- Screen 22: Copilot Conversation (Structured records, evidence cards)

### Group F — Account, Notifications & Privacy
- Screen 23: Notifications
- Screen 24: Profile & Preferences
- Screen 25: Data Management (Statements, deletion, export)
- Screen 26: Security & Privacy (Biometrics, credentials)
- Screen 27: Preferences (Currency, buffer, appearance)
