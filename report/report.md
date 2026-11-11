# Weather and Energy Production in Sweden

<!-- Group report. Sections: Introduction, Method, Results and discussion.
     Each section needs at least 200 words; whole report 600–1,000 words; 4–10 figures. -->

## Introduction and motivation

_To be written._

## Method

_To be written._


### Energy data and join

- **Source:** SCB table **TAB5644**, monthly electricity production in GWh, via the current PxWebApi v2 (`statistikdatabasen.scb.se/api/v2`).
- **Categories:** total, hydro, nuclear, wind and renewable thermal power. Solar and non-renewable thermal were left out because they are very small.
- **Period:** August 2024 – July 2026 (24 complete months), the same as the weather data.
- **Request:** one request per category, with period and category codes stored in a configuration table.
- **Unit:** read from the SCB response (GWh), not typed in by hand.
- **Preparation:** reshaped to one row per month and converted the month from `2024M08` to `2024-08` to match the weather table.
- **Checks before joining:** 24 rows, no duplicate months, no missing values, 5 categories with 24 months each.
- **Join:** energy and weather tables joined on `month`. All 24 months matched and no months were left over on either side.
- **Visualisation:** months were coloured by season (winter = Dec–Feb, spring = Mar–May, summer = Jun–Aug, autumn = Sep–Nov).

_to be written._

## Results and discussion

### Weather and energy

![Figure 2: Mean wind speed vs wind power production](figures/fig2_wind_scatter.png)

**Figure 2 – Wind speed vs wind power (scatter)**
- Weak link (r ≈ 0.2): windier months do not clearly produce more wind power.
- Wind speed only varies between 2.4 and 3.5 m/s, while production varies from 1,500 to 5,500 GWh.
- Summer months produce the least wind power; autumn and winter produce the most.
- Likely reasons: SMHI measures wind at 10 m near cities, while wind farms are mostly inland at 100 m or more, and monthly averages smooth out storms.

![Figure 3: Mean temperature vs total electricity production](figures/fig3_temp_scatter.png)

**Figure 3 – Temperature vs total production (scatter)**
- Strong negative link (r ≈ −0.93): the colder the month, the more electricity is produced.
- Winter months: 15,800–18,300 GWh. Summer months: 10,500–12,900 GWh.
- Reason: demand for heating and lighting rises in winter, and production follows demand.
- Temperature is a sign of season and demand, not a direct cause of production.

![Figure 4: Monthly electricity production by type](figures/fig4_production_line.png)

**Figure 4 – Production by type over time (line)**
- Total production peaks every January and is lowest in summer.
- Hydropower, the largest source, also peaks in winter: reservoirs store water and release it when demand is high.
- This explains why rainfall in a given month barely affects hydropower in the same month.
- Nuclear output drops every summer because of planned maintenance.
- Wind power changes irregularly from month to month.

![Figure 5: Correlation between weather and energy variables](figures/fig5_correlation_heatmap.png)

**Figure 5 – Correlations (heatmap; blue = positive, red = negative)**
- Temperature: strong negative correlation with every production type (r between −0.64 and −0.93).
- Precipitation: only weak correlations (r between −0.2 and −0.6).
- Wind speed: weak with wind power (r ≈ 0.2), but negative with hydropower (r ≈ −0.5), possibly because less hydropower is used when wind power is available.

**Limitations (energy and join)**
- Only 24 months, so the correlations are uncertain.
- Season drives most patterns; the results show associations, not causes.
- Four weather stations cannot represent where the power plants are.
- Production also depends on demand, exports, prices and maintenance, which are not in the data.

### Clustering

_To be written._
