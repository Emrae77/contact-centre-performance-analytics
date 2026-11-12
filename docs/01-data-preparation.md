# Data Preparation and Validation

## Project context
This Power BI project examines **5,000 contact centre call records**. The published dashboard reports call volume, resolution, abandonment, customer satisfaction, speed of answer and handling time, with breakdowns by agent and hour.

**Evidence status:** This document is based on the supplied dashboard and Fields-pane screenshots. The original CSV, Power Query steps and PBIX model logic were not available for direct inspection while preparing this document. Items labelled **To verify** must be checked against the project files before describing them as completed work.

## Visible data fields
The screenshots show these fields in the call-centre dataset:

| Field | Intended analytical use |
|---|---|
| `call id` | Call-level identifier; uniqueness check |
| `agent` | Agent performance comparisons |
| `answered (Y/N)` | Answered-call eligibility and abandonment analysis |
| `resolved` | Resolution metric and segmentation |
| `satisfaction rating` | Customer satisfaction analysis |
| `speed of answer` | Response-time analysis in seconds |
| `talkduration` | Call-duration analysis |
| `topic` | Contact reason analysis |
| `date`, `datetime`, `time` | Time-series and hourly analysis |
| `day`, `hour`, `month` | Reporting categories and filters |
| `Hour Order By`, `month order`, `Weekday Order`, `Rating Order` | Sort columns for chronological and ordered visuals |

Some fields may be calculated columns rather than raw source fields.

## Report scope
- **Total displayed records/calls:** 5,000.
- **Visible latest-call timestamp:** March 31, 2021, 5:39:50 PM.
- **Reporting period:** **To verify** against minimum/maximum call timestamps in the source data.
- **Original source and redistribution terms:** **To verify**. The project folder filename suggests a PwC-themed practice dataset, but that alone does not establish origin, affiliation or publication rights.
- **Grain:** Assumed one row per call; **verify** that `call id` is unique.

## Data preparation to document from Power Query
Before finalizing this section, inspect **Transform Data → Applied Steps** and describe only steps present in the model:
1. Source ingestion and column types, especially timestamps and numeric durations.
2. Null handling for answered, resolved, satisfaction and timing fields.
3. Date/time derivations (`hour`, `day`, `month`) and sort columns.
4. Data normalization or text clean-up, if any.
5. Removed rows or filtered records, if any, including rationale.

Do not claim these actions were performed until confirmed in Power Query.

## Validation checklist

| Test | Why it matters | Result |
|---|---|---|
| Count records and distinct `call id` | Prevent duplicate call counts | **To verify** |
| Check null/blank IDs | Ensure identifiable calls | **To verify** |
| Inspect values of `answered (Y/N)` and `resolved` | Establish valid status mappings | **To verify** |
| Check whether unanswered calls have resolution values | Detect inconsistent source states | **To verify** |
| Check nonnegative `speed of answer` and `talkduration` | Exclude invalid timings | **To verify** |
| Inspect missing satisfaction ratings | Define CSAT denominator | **To verify** |
| Confirm date/time range and timezone | Interpret hourly/weekday trends correctly | **To verify** |
| Reconcile KPI values with source aggregations | Validate DAX output | **To verify** |

## Specific anomaly: 18:00 hour
The hourly call-volume visual shows **14 calls at 18:00**, compared with roughly **499–594** calls at each of the preceding displayed hours. The displayed 18:00 abandonment rate is also notably lower (approximately 14–15%).

This is **not evidence that service improved at 18:00**. Investigate whether this is a short or incomplete observation window, low sample size, a timestamp-grouping effect or a reporting cutoff. Avoid using that hour to make a staffing recommendation without further checks.

## Known limitations
- Staffing rosters, queue lengths and service-level targets are not visible in the supplied data.
- Hourly averages cannot establish that delayed answering *caused* abandonment.
- Per-agent comparisons may differ in volume and case mix.
- Interpret satisfaction only after confirming the rating scale and missing-data treatment.

## Reproducibility notes to complete
- [ ] Identify exact dataset source and licence
- [ ] Record Power Query transformation steps
- [ ] State report coverage dates and timezone
- [ ] Confirm uniqueness of call identifiers
- [ ] Document null handling and valid status values
- [ ] Validate and explain the 18:00 outlier
