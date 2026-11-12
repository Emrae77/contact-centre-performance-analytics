# Analysis, Findings and Recommendations

## Objective
Evaluate contact centre efficiency and customer experience across 5,000 call records, focusing on abandonment patterns, response times, satisfaction and agent-level performance.

**Evidence basis:** Supplied screenshots of the Overview and Abandonment dashboard pages. Figures are rounded where read from plotted points. These are **descriptive observations**, not proven causes or realized business improvements.

## 1. Headline performance

| Metric | Dashboard result |
|---|---:|
| Call volume | 5,000 |
| Resolution rate | 89.94% |
| Abandonment rate | 18.92% |
| CSAT | 68.07% |
| Average speed of answer | 67.52 seconds |
| Average call handling time | 224.92 seconds |

**Interpretation:** The report supplies a baseline for tracking operational performance. Whether any metric is good or poor depends on service-level targets, comparable historical periods, and verified metric definitions, none of which are currently documented.

## 2. Finding: Abandonment varies by hour

**Observation:** The hourly abandonment visual shows a peak of approximately **21% around 12:00**, with the 09:00 period also above 20%. The displayed rate for 18:00 is about **14–15%**, but the volume at that hour is only **14 calls**.

**Investigation to perform:** Compare abandonment rates using underlying call counts and answered-call counts, then repeat by day/month. Determine whether midday peaks persist after excluding incomplete time periods.

**Business implication:** Certain hours may warrant closer inspection of service capacity and queue conditions.

**Recommendation:** Review the noon period with operations staff, including call-arrival patterns, scheduled staffing and queue-level service metrics where available. Do not infer understaffing solely from the dashboard.

## 3. Finding: Call demand changes across the day

**Observation:** Displayed hourly call counts are approximately **547 at 09:00, 590 at 11:00, 594 at 13:00, 499 at 14:00**, and **14 at 18:00**. Most full displayed hours fall in a relatively narrow high-volume range.

**Investigation to perform:** Verify the hour bucketing, determine whether 18:00 is a partial period, and compare typical hour-by-day demand rather than treating overall hourly totals as a staffing forecast.

**Business implication:** Understanding periods of elevated demand can support capacity planning and more precise monitoring.

**Recommendation:** Build an hour-by-weekday heatmap and compare it with actual staffing and service-level performance if those data become available.

## 4. Finding: Answer time and abandonment should be investigated together

**Observation:** The abandonment page compares hourly average speed of answer with hourly abandonment rates. The plotted points do not clearly establish a consistent upward relationship.

**Investigation to perform:** Review the underlying records and calculate comparable, volume-weighted rates. Check whether outlier hours or different populations are distorting the relationship. Ideally examine queue-level waiting-time distributions.

**Business implication:** Rising response time may be a useful warning metric, but this analysis alone cannot demonstrate that answer time caused abandoned calls.

**Recommendation:** Monitor ASA and abandonment together; investigate hours that breach internally agreed service thresholds rather than assuming a causal link.

## 5. Finding: Agent-level outcomes vary

**Observation:** The overview dashboard includes an agent comparison with total calls, abandoned-call percentage, answer speed, resolution rate and CSAT. Among visible rows, reported calls per agent range from approximately **582 to 666** and reported CSAT values from approximately **66.61% to 69.42%**.

**Investigation to perform:** Compare agent performance after accounting for differences in call topic, volume, shift coverage and customer mix. Verify whether satisfaction data exist for every call.

**Business implication:** Agent-level views help spot coaching questions and workflow differences but should not be used as standalone performance rankings.

**Recommendation:** Review agents with operations managers using a balanced scorecard: quality, resolution, customer feedback, volume and complexity, rather than a single KPI.

## 6. Customer satisfaction

**Observation:** Overall displayed CSAT is **68.07%**, and the satisfaction chart includes response groups such as Average, Good and Excellent, alongside Poor, Very Poor and Not Served.

**Investigation to perform:** Confirm the rating scale, whether unanswered calls count as Not Served, and how the CSAT percentage is produced. Segment satisfaction by topic, agent and resolution outcome only after confirming those definitions.

**Recommendation:** Identify themes linked to low satisfaction and review call-handling processes with operations teams. Do not claim that lower CSAT is caused by longer waits without supporting analysis.

## Recommended next actions

| Priority | Action | Evidence needed |
|---|---|---|
| 1 | Validate KPI definitions and denominators | Actual DAX expressions and dataset |
| 2 | Investigate the unusually low 18:00 call count | Call timestamps and report cutoff |
| 3 | Recheck the noon abandonment peak | Call-level or hourly answered/abandoned counts |
| 4 | Compare operational outcomes by topic and agent | Case mix and survey availability |
| 5 | Define monitoring thresholds | Historical benchmark or service-level targets |

## Limitations
- The analysis uses a fixed historical portfolio dataset, not current operational performance.
- No staffing roster, queue logs or service-level targets have been provided.
- Aggregated visuals cannot establish causal effects.
- Report screenshots cannot confirm the exact DAX definitions.
- No operational changes or measured post-implementation improvements are claimed.

## Portfolio takeaway
This project demonstrates the use of Power BI to organize contact centre performance metrics, investigate time-of-day patterns and compare operational segments. Its next analytical improvement is to verify the underlying measures and test potential explanations using record-level data rather than assuming that visual correlations prove business causes.
