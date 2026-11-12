# KPI Definitions and DAX Verification

## Purpose
This document records the metrics shown in the Contact Centre Performance Analytics Power BI dashboard and identifies what must be verified in the original DAX measures.

**Important:** The figures below are transcribed from the dashboard screenshot. The **actual DAX source expressions have not yet been inspected**. The formulas described here are *conceptual definitions to validate*, **not claimed copies of the author's DAX**.

## Dashboard KPI summary

| KPI | Displayed value | Calculation / verification requirement |
|---|---:|---|
| Total calls | 5,000 | Determine whether the measure counts rows or distinct call IDs |
| Resolution rate | 89.94% | Confirm resolved-call numerator and whether denominator is all or answered calls |
| Abandonment rate | 18.92% | Confirm mapping of unanswered/abandoned calls and denominator |
| CSAT | 68.07% | Confirm whether this is an average rating, share satisfied, or other transformation |
| Average speed of answer | 67.52 seconds | Confirm whether unanswered calls or blanks are excluded |
| Average call handling time | 224.92 seconds | Confirm whether this uses talk duration alone or includes hold/wrap-up time |

## Definitions that need confirmation

### Total calls
**Common definition:** Count of call records, preferably distinct `call id` when IDs are unique.

**Confirm in PBIX:** `Total calls` measure; whether duplicated rows could affect it.

### Abandonment rate
**Common definition:** Calls abandoned before being answered divided by eligible incoming calls × 100.

**Confirm in PBIX:** Whether `answered (Y/N) = N` is treated as abandonment; whether all calls form the denominator. The measure named `Abandoned` is visible in the Fields pane.

### Resolution rate
**Two plausible definitions:**
- Resolved calls ÷ answered calls × 100; or
- Resolved calls ÷ all calls × 100.

These are **not interchangeable**. The displayed resolution rate of 89.94% and abandonment rate of 18.92% can coexist if they use different populations or represent different stages of the call lifecycle.

**Confirm in PBIX:** The precise numerator, eligible population, treatment of unanswered calls, and whether `resolved` is blank for some records.

### Customer satisfaction (CSAT)
**Possible definition:** Satisfied respondents ÷ all valid survey respondents × 100.

The chart contains categories including **Not Served, Very Poor, Poor, Average, Good and Excellent**. Determine how those categories map to the `satisfaction rating` field and which count as satisfied.

**Confirm in PBIX:** Actual definition of the `CSAT` measure and whether missing or unanswered surveys are excluded. Do not call 68.07% the percentage of satisfied customers without verification.

### Average speed of answer (ASA)
**Common definition:** Mean time in seconds before answered calls are picked up.

**Confirm in PBIX:** Whether the measure averages `speed of answer` over answered calls only and whether zeros or blanks are handled correctly.

### Average call handling time (AHT)
**Common definition:** (Talk + hold + after-call work time) ÷ handled calls.

The screenshot exposes a `talkduration` field, but does **not** establish whether hold and after-call work are recorded. If only `talkduration` is used, the label **Average Talk Duration** may be more accurate than **Average Handling Time**.

**Confirm in PBIX:** All component fields and eligible calls.

## Existing model evidence
The screenshots show a dedicated `measures_table` with entries including:
- `Abandoned`
- `avg call handli...`
- `Avg speed of ...`
- `call abandone...`
- `call resolved %`
- `CSAT`
- `last call`
- `Poor CSAT`
- `Selected Hour`
- `Total calls`
- `total calls ans...`

There is also a `poor_csat_measures` table. Full measure names and DAX code require inspection of the actual model.

## DAX source appendix (to complete)
Paste exported expressions from Power BI after checking them. Suggested headings:

```dax
-- Actual DAX for [Total calls]:
-- Paste verified expression here.

-- Actual DAX for [call abandoned %]:
-- Paste verified expression here.

-- Actual DAX for [call resolved %]:
-- Paste verified expression here.

-- Actual DAX for [CSAT]:
-- Paste verified expression here.

-- Actual DAX for [Avg speed of Answer]:
-- Paste verified expression here.

-- Actual DAX for [avg call handling time]:
-- Paste verified expression here.
```

## Quality checks before publishing
- [ ] Verify each numerator and denominator
- [ ] Check whether rates are averages of groups or ratios of totals
- [ ] Check filtering behavior for agent, topic, month and weekday slicers
- [ ] Confirm the meaning and units of all time measures
- [ ] Reconcile displayed KPI values to the source records
- [ ] Replace this appendix with the actual DAX expressions
