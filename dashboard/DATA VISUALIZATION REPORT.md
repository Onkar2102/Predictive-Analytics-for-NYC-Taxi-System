# Data Visualization Report: NYC Taxi System Analytics Dashboard

## Executive Summary

This report presents a comprehensive analysis of the NYC Taxi System through an interactive Power BI dashboard, focusing on post-COVID operational insights and predictive analytics. The dashboard provides stakeholders with actionable intelligence for optimizing taxi operations, understanding demand patterns, and making data-driven decisions in the evolving urban transportation landscape.

## 🚖 Dashboard Pages and Analysis

### Page 1: Executive Overview (NYC Taxi System Insights)
![Executive Overview Dashboard](dashboard/screenshots/page1-executive-overview.png)

**Purpose**
A one-glance briefing for executives on the scale, revenue generation, and spatial-temporal patterns of NYC yellow-cab operations.

| Element | What it shows | Why it matters |
|---------|---------------|----------------|
| **Score-card KPIs** | • **Total Trips:** 197.81 K  • **Total Earnings:** $ 3.573 M  • **Total Tip:** $ 415.66 K  • **Total Distance Travelled:** 464.79 K mi | Quantifies overall business volume, cash-flow, and mileage in the selected time frame. |
| **Top Pickup Borough pie** | Manhattan 93.42 % (184.8 K), Queens 5.50 % (10.9 K), remainder < 1 % | Confirms where demand originates; highlights Manhattan dominance and niche pockets elsewhere. |
| **Top Drop-off Borough pie** | Manhattan 90.42 % (178.9 K), Queens 4.28 % (8.5 K), remainder < 3 % | Shows where trips end and whether flows mirror pick-ups (useful for re-positioning strategy). |
| **Trips Analysis combo chart** | Monthly bars split by special flags (`snow_season`, `rush_hour_trip`, `mid_night_trip`, `isAirportTrip`); blue line overlays total trip count | Reveals seasonal spikes (e.g., snow season), rush-hour demand curves, and airport-traffic impact month-by-month. |
| **Interactive Maps** | • Pick-up Locations (left) • Drop-off Locations (right) – circle markers coloured by borough, zoom/pan enabled | Visualises geographic density; helps spot underserved areas or imbalances between origins and destinations. |

**Interactive Filters (top-left panel)**
1. Pickup Time Range – slider (2019-08-01 → 2021-08-01)
2. Vendor – buttons 1, 2, 4
3. Passengers Count – buttons 0 – 4
4. Payment Mode – buttons 1 – 4
5. Drop-off Time of Day – radio buttons (Afternoon, Evening, Late Night, Morning)

**Key Take-aways for Stakeholders**
- Manhattan continues to dominate both pick-up and drop-off share (> 90 %), confirming the island as the revenue core.
- Earnings have topped **$ 3.5 M** over the ~24-month window, with tips contributing **~12 %** of fare revenue.
- February and March spikes driven by snow-season trips, while regular rush-hour volumes stabilise around **5–6 K** per month.
- Maps highlight concentration mid-town/downtown with noticeable pockets at the airports; filtering by `isAirportTrip` instantly isolates those corridors.
- KPI cards and slicers enable leaders to stress-test “what-if” scenarios—e.g., *How do tips vary for late-night rides paid in cash?*—without leaving the page.

---

### Page 2: Revenue & Distance Analysis
![Revenue & Distance Analysis Dashboard](dashboard/screenshots/page2-revenue-distance.png)

**Purpose**
Uncovers how mileage drives fare revenue, pin-points the neighbourhoods that earn the most, and quantifies the effect of special operating conditions.

| Element | What it shows | Why it matters |
|---------|---------------|----------------|
| **Trip Distance vs Total Amount** (scatter with trend-line) | Each dot is one ride; **x-axis = miles travelled**, **y-axis = dollars paid**. A dotted best-fit line highlights the upward slope. | Confirms the fare model scales with distance and flags high-value outliers (e.g., toll-heavy or surge-priced rides) worth deeper audit. |
| **Total Earnings Gauge** | Needle-less semicircle with a headline of **$ 3.57 M**. Scale annotations: **$ 0.31** (min) to **$ 18.06** (avg) | Shows aggregate cash-flow in context of fare distribution; quick health check against targets. |
| **Top 5 Zones by Revenue** (ranked card list) | Highest grossing taxi zones:<br/>1. East Harlem South – **$ 58.7 K**<br/>2. Midtown Center – **$ 102.9 K**<br/>3. TriBeCa / Civic Center – **$ 55.4 K**<br/>4. Upper East Side North – **$ 134.9 K**<br/>5. Upper East Side South – **$ 116.8 K** | Reveals where revenue concentrates, guiding driver allocation, flat-fare trials, or marketing campaigns in specific neighbourhoods. |
| **Condition Breakdown Matrix** | Two-row table comparing trips **N** (not flagged) vs **Y** (flagged) for:<br/>• `snow_season` **33 167 / 424**<br/>• `rush_hour_trip` **69 236 / 739**<br/>• `mid_night_trip` **23 943 / 241**<br/>• `isAirportTrip` **11 145 / 144**.<br/>Tip totals: **$ 411.5 K vs $ 4.2 K**. | Quantifies the operational load and revenue share of special scenarios—crucial for staffing, surge pricing, and incentive decisions. |
| **Month Selector Grid** | Clickable buttons **January – December** that act as a page-level filter. | Empowers analysts to isolate seasonality (e.g., winter storms) and instantly watch every other visual update, turning the page into an interactive what-if tool. |

**Key Insights for Stakeholders**
- **Distance drives dollars** – the clear positive slope validates mileage-based pricing; extreme dots hint at premium routes worth focused promos or audits.
- **Neighbourhood hot-spots** – five Manhattan-centric zones alone exceed **35 %** of total revenue, indicating where incremental drivers or EV-charging hubs will return the most.
- **Special-condition trips are few but influential** – airport rides (< 0.1 % of trips) punch above their weight in earnings, suggesting room for negotiated flat-rate or upsell packages.
- **Seasonality at your fingertips** – the month grid lets planners replay the year and see exactly when snow seasons spike costs or when late-night demand lulls, informing fleet scheduling.

---

### Page 3: Daily Earnings Drill-Down
![Daily Earnings Dashboard](dashboard/screenshots/page3-daily-revenue.png)

**Purpose**
Lets analysts zoom from monthly roll-ups down to day-level behaviour, revealing intra-month peaks, forecasted trends, and any special-condition spikes.

| Element | What it shows | Why it matters |
|---------|---------------|----------------|
| **Year & Month slicers** (button ribbons) | Quick selectors for **2019 – 2021** and the twelve months (e.g., *2020 · July* active). | Enables side-by-side comparison of any month/year combo without leaving the page—crucial for spotting pandemic-era anomalies or seasonal surges. |
| **Total Earning by Day** (line with forecast band) | Daily average fare for the chosen month; last few days are grey-shaded with a dashed projection (Power BI forecast). | Exposes weekday vs weekend patterns, sudden spikes (e.g., holiday events), and gives an early look at expected revenue for the rest of the month. |
| **Top 3 Zones** (ranked card list) | Highest-earning taxi zones within the selected month—e.g., **Lenox Hill East $3.75 K**, **Upper East Side North $4.60 K**. | Highlights where short-term marketing (promo codes, fleet re-balancing) will yield the biggest immediate return. |
| **Number of Trips for Certain Condition** (two-row matrix) | Counts of rides flagged **N** (no) vs **Y** (yes) for:<br/>• `snow_season` **0 / 0**<br/>• `rush_hour_trip` **2 676 / 22**<br/>• `mid_night_trip` **662 / 9**<br/>• `isAirportTrip` **305 / 2** | Quantifies the operational burden of special scenarios for the month, letting dispatch plan staffing and price surges at the right times of day. |

**Key Insights (July 2020 example)**
- **Mid-month spike (~Day 5)** pushes daily earnings above **$21 K**, likely tied to holiday travel; forecast suggests a smaller but steady uptick after Day 30.
- **Rush-hour dominance** – > 2.7 K rides occur in commuter windows, yet only 22 are marked with explicit “rush-hour” surcharge flags, hinting at missed premium-fare opportunities.
- **Airport runs**—though just 307 in total—remain lucrative on a per-ride basis; consider dedicated flat-rate or premium service marketing for LaGuardia/JFK during late July.

---

### Page 4: Time-of-Day & Day-of-Week Patterns
![Time-of-Day Earnings Dashboard](dashboard/screenshots/page4-day-of-week-earnings.png)

**Purpose**
Reveals when, during a typical week, each time-of-day slot is most lucrative and links those patterns to high-earning zones and special-condition workloads.

| Element | What it shows | Why it matters |
|---------|---------------|----------------|
| **Year & Month slicers** (button ribbons) | Quick filters for **2019 – 2021** and all 12 months. | Lets analysts isolate any calendar slice—crucial for comparing pre-/post-pandemic or peak-season behaviours. |
| **Average Total Earning per Day of Week** (multi-line chart) | Average fare on each weekday (**0 = Sun … 6 = Sat**) split by **Morning, Afternoon, Evening, Late-night**. | Highlights revenue-rich periods: late-night rides top the chart all week, while mornings trail until a Saturday uptick—guiding driver rostering and surge-pricing windows. |
| **Top 3 Zones** (ranked card list) | Highest-earning zones for the current filter—e.g., **Upper East Side North $134.9 K**, **Midtown Center $102.9 K** (third zone scrollable). | Pin-points neighbourhoods to target with time-based promos (e.g., weekend late-night incentives in Midtown). |
| **Number of Trips for Certain Conditions** (two-row matrix) | Counts **N vs Y** for:<br/>• `snow_season` **33 167 / 424**<br/>• `rush_hour_trip` **69 236 / 739**<br/>• `mid_night_trip` **23 943 / 241**<br/>• `isAirportTrip` **11 145 / 144** | Quantifies operational load tied to special scenarios during the selected slice—key for staffing and policy tweaks (e.g., winter night shifts). |

**Key Take-aways**
- **Late-night dominates**: averages hover above **$21** every night, peaking on Sundays—clear evidence to keep more cabs on the road after midnight.
- **Weekend uplift**: **Morning** and **Afternoon** earnings jump on Saturdays (Day 6), hinting at tourist or leisure traffic.
- **Rush-hour intensity**: ~**70 K** weekday trips fall into commuter windows, yet only ~**1 %** carry the explicit rush-hour flag—an opportunity to refine surcharge rules.
- **Zone targeting**: Consistently high takings in Upper East Side North and Midtown suggest concentrating EV-charging hubs or promo codes there for late-night riders.

---

### Page 5: Descriptive Trip Trends
![Multi-Metric Trip Trends](dashboard/screenshots/page5-descriptive-analysis.png)

**Purpose**
Puts the five core ride-level metrics on a single time-series to visualise the pandemic dip, the recovery arc and long-term behaviour of NYC taxi demand.

| Element | What it shows | Why it matters |
|---------|---------------|----------------|
| **Multi-metric line chart – Descriptive Analysis of Trip** | Five lines tracked month-by-month (left axis for `tip_amount`, `total_amount`, `passenger_count`, `trip_distance`; right axis for `trip_duration`). | Lets decision-makers see how Covid (April 2020 collapse) slashed demand & spending, how quickly each metric rebounded, and whether ride length/duration patterns changed in tandem. |

**Key Insights**
- **Covid shock & rebound** – All metrics plunge in April 2020; revenue and distance start climbing again by June, while trip duration rises more slowly, reflecting shorter local rides during early reopening.
- **Passenger count stability** – The purple `passenger_count` line stays relatively flat, hinting that single-rider trips remained the norm both pre- and post-pandemic.
- **Duration vs distance divergence** – From late 2020 onward, `trip_distance` edges up but `trip_duration` jumps sharply, suggesting heavier traffic or more waiting time despite similar mileage—useful for fare model tweaks or driver pay adjustments.
- **Tip resilience** – The blue `tip_amount` line mirrors `total_amount`, showing riders continued tipping in proportion to fares even during downturns—reassuring for driver earnings.

### Page 6: Key Influencers – Tip Drivers
![Key Influencers (Tip Amount)](dashboard/screenshots/page6-key-influencers.png)

**Purpose**
Uses Power BI’s AI-driven *Key Influencers* visual to reveal which trip attributes most strongly drive higher **`tip_amount`** (and, by extension, total revenue). This equips managers with evidence-based levers for service improvements and targeted promotions.

| Element | What it shows | Why it matters |
|---------|---------------|----------------|
| **Key Influencers list** (left pane) | Automatically ranks the variables that cause `tip_amount` to increase. Example impacts:<br/>• `tolls_amount` > **$2.80** → average tip **+ $4.64**<br/>• **Drop-off zone = LaGuardia Airport** → **+ $4.38**<br/>• `isAirportTrip = 1` → **+ $3.74**<br/>• **Pick-up zone = JFK Airport** → **+ $3.70**<br/>• `trip_distance` > **3 mi** → **+ $1.96** | Pinpoints the strongest levers for boosting gratuities—e.g., airport rides with tolls yield far better tips, suggesting where to focus premium service or upsell efforts. |
| **Influence comparison chart** (right pane) | For the selected driver (e.g., `tolls_amount > $2.80`), bar chart contrasts average tip when the condition is met vs. not met. | Gives a tangible, side-by-side uplift figure that makes the statistical impact immediately clear to non-technical stakeholders, strengthening the case for policy changes (e.g., clearer toll disclosure). |
| **“Top segments” tab** | Clusters rides into homogeneous groups with the highest predicted tips. | Helps craft hyper-targeted promotions—e.g., late-night JFK pickups carrying 2–3 passengers who routinely tip above average. |

**Key Take-aways**
- **Tolls are the single biggest driver**—customers who pay > **$2.80** in tolls tip roughly **2.4×** the overall average (**$6.4 vs $1.9**).
- **Airport traffic matters**—both pick-ups and drop-offs at JFK or LaGuardia significantly boost tips, reinforcing the value of prioritising these routes.
- **Longer trips, bigger tips**—distances above **3 miles** correlate with a **$2** uplift, supporting mileage-based incentive structures for drivers.
- **Borough nuance**—Queens pick-ups outperform Brooklyn drop-offs, hinting at local rider tipping culture differences worth exploring.

---


