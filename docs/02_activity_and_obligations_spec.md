# Group B: Activity, Transactions, Data Import & Obligations Specification (Screens 7–13)

> **Parent Specification:** `docs/00_master_ui_specification.md`  
> **Status:** Approved with Required Refinements Incorporated  
> **Platform:** Flutter Mobile (iOS & Android)  
> **Reference Timeline Anchor:** Current Date = Friday, 6 November 2026

---

## 1. Unified Activity Workspace Philosophy

The Activity destination is an interconnected Financial Activity Engine linking three stages:
1. **Imports (Screen 10 & 11)**: Ingest raw data with atomic commits, rollback protection, and multi-signal duplicate prevention.
2. **Transactions (Screen 7, 8 & 9)**: Historical ground truth (cleared records).
3. **Obligations (Screen 12 & 13)**: Forward-looking commitments (Confirmed vs AI-Detected candidates).

### Forecast Inclusion Rules
- **Confirmed Obligations:** Included in baseline liquidity forecasts.
- **AI-Detected Candidates:** Excluded from baseline forecast until confirmed by the user.
- **Tentative / Optional Obligations:** Excluded from baseline forecast by default; can be toggled on in hypothetical simulator scenarios.
- **Payment Reconciliation:** When marking an obligation as paid, the system checks whether a corresponding transaction already exists in the same billing cycle to prevent double-counting.

---

## 2. Screen 7: Activity (Main Hub)

- **Reporting Period Header:** Cash-flow summary dynamically reflects the selected active filter period (e.g., `"1 Nov – 6 Nov 2026 (MTD)"` or custom date range), never a hardcoded month.
- **Dynamic Filter Counts:** Filter chips show live record counts based on current filters (e.g., `[ All (48) ]`, `[ Income (3) ]`, `[ Expenses (45) ]`).
- **Consistent Timeline:** All relative dates anchor strictly from `Friday, 6 Nov 2026`.
- **Item Cards:** Category icon, merchant name, masked account (e.g. `•••• 4012`), tabular amounts. If categorized by AI, shows subtle `AI ✦` chip only when classifier confidence exceeds calibrated threshold.

---

## 3. Screen 8: Add Transaction

- **Amount-First Entry:** Auto-focused 38px tabular figure.
- **Calibrated AI Suggestion:** Displays category suggestion with confidence score only when model outputs a calibrated probability (e.g., `✦ Suggested: Coffee & Snacks (94% confidence)`). Uncalibrated predictions display without arbitrary percentage values.
- **Recurring Toggle Refinement:** Enabling the recurring toggle does **not** create a confirmed obligation. It prompts for cadence/date and flags the item as an **AI/User Candidate**, requiring explicit confirmation before it affects forward forecasts.

---

## 4. Screen 9: Transaction Details & AI Inspector

- **Audit Trail:** Cleared timestamp, merchant, masked account (`HDFC Bank •••• 4012`), and masked reference ID (`UPI/••••••/8392`).
- **AI Classification Inspector:** Explains feature weights and historical pattern matching.
- **Action Renamed:** Button labeled `"Correct Category"`. Saving stores the override as labeled user feedback for asynchronous model training, with no false claim of instant on-device retraining.

---

## 5. Screen 10 & 11: Data Import & Validation

- **Accurate Processing Disclosure:** Accurately states where parsing occurs (client-side vs secure backend sandbox).
- **Dual-Column Support:** Supports Indian bank formats with separate Debit and Credit columns as well as single signed amount columns. Date format selector (`DD/MM/YYYY` vs `MM/DD/YYYY`).
- **Multi-Signal Duplicate Fingerprinting:** Evaluates Date + Amount + Debit/Credit direction + Normalized Payee description + Account ID + Reference ID. Flagged items open in a review drawer rather than being silently discarded.
- **Atomic Import & Safe Rollback:** If an import fails midway, the transaction rolls back cleanly with zero orphaned rows.

---

## 6. Screen 12: Obligations Management

- **Obligations Summary Banner:**
  - `Confirmed Upcoming:` ₹16,500 (Drives forecast)
  - `AI-Detected Candidates:` ₹499 (Excluded from forecast)
  - `Potential Total if Confirmed:` ₹16,999
- **Reconciliation Check:** Tapping `[ Mark as Paid ]` prompts: *"Matching cleared transaction of ₹12,000 detected on 5 Nov. Link to this payment to avoid double counting?"*

---

## 7. Screen 13: Add / Edit Obligation

- **Dynamic Liquidity Impact Banner:**
  - Labeled `"ESTIMATED FORWARD IMPACT · ILLUSTRATIVE SIMULATION"`.
  - Shows estimated impact on 30-day lowest balance with explicit assumptions disclaimer: *"Based on available records and recurring spending assumptions. Predictions subject to variance."*
  - If set to `Tentative/Optional`, displays: *"Excluded from baseline forecast. Available in Simulator."*
