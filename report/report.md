# Introduction and Motivation

Weather conditions can have an important effect on electricity production in Sweden. As the country uses renewable energy sources such as hydropower and wind power, weather becomes an important factor in how much electricity can be generated. This study explores the relationship between monthly weather conditions and electricity production from August 2024 to July 2026. The aim is to identify possible patterns and seasonal changes rather than prove that weather causes changes in production.

_[Praj: Add 2–3 sentences here about Sweden's electricity production, its main energy sources and why it is useful to study monthly production.]_

Three main weather variables were selected from SMHI: temperature, precipitation and wind speed. Temperature matters because colder weather increases the need for heating, which can raise electricity demand and production from thermal power plants. Precipitation contributes to water availability for hydropower, and wind speed influences how much electricity wind turbines can produce. Sunshine duration would be relevant for solar power, but it was not included in our dataset.

Four weather stations were selected to cover different parts of Sweden (Figure 1). Stockholm represents an important electricity consumption centre, Göteborg represents the windy west coast, Malmö covers the southern region where wind and solar power are relevant, and Luleå represents the north, where hydropower is important. The 24-month period includes two complete annual cycles, making seasonal comparisons possible.

# Weather data

Weather data were collected from the SMHI Meteorological Observations API as one corrected-archive CSV file per station and weather variable. A configuration table listing the 12 data series (four stations and three variables) controlled a loop that built each URL and downloaded the file. The data were then filtered to August 2024 - July 2026, checked for duplicates and checked against plausible value ranges; neither check found any problems. Each station-month needed at least 90% data coverage, and the four Malmö station-months below this limit were left out of the national average instead of filling in missing values (Table 1, Figure 2). Monthly statistics were then calculated, including the mean, minimum, maximum and standard deviation, plus the monthly total and number of wet days for precipitation. Finally, the stations were combined using an equal-weight average to create monthly national weather values.

# Weather data limitations

- Only four stations were used, so they cannot represent all of Sweden. Each station was given equal weight, regardless of the population or electricity production in its region.
- Malmö was left out of the national average for temperature in August 2024 and for wind in August 2024, April 2025 and July 2025 because of insufficient data coverage. These monthly averages therefore lean towards the northern stations, and the August 2024 temperature may be slightly too low.
- Stockholm's wind data come from Stockholm-Bromma, about 5 km from the station used for temperature and precipitation.
- SMHI reports times in UTC, and the precipitation day runs from 06:00 to 06:00, which can move a small amount of data across month boundaries.
- Only SMHI's quality-controlled (corrected-archive) data were used, which limits the analysis to months that SMHI has already checked.
- 13 days and 783 wind hours were missing. Station-months with at least 90% coverage were kept, so a few monthly values are based on slightly fewer observations.
- Wind was measured 10 metres above ground at land stations, which may differ from wind conditions at turbine height and offshore.
