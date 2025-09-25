Air Quality Dataset Analysis Report

Introduction

This dataset tracks 153 daily measurements of ozone levels (in ppb), solar radiation (in lang), wind speed (in mph), temperature (in °F), month, and day from May to September in what seems to be one year. Ozone, a pollutant tied to sunlight and heat, is our focus—understanding how weather factors drive its levels can help predict bad air quality days. As a statistics graduate, I analyzed this data using R, cleaning it, summarizing key stats, checking correlations, visualizing trends, modeling ozone, and exploring monthly patterns. Here’s a breakdown of what I did, why, and what I found.

Step 1: Data Cleaning

load the dataset and found 37 missing ozone values and 7 missing solar radiation values, with no gaps in wind, temperature, month, or day. fill these gaps with the median of each column.

Why? Missing data messes with analyses like correlations or regressions by shrinking the sample or skewing results. Medians are robust for imputation since they’re not thrown off by outliers, like high ozone on a hot day, ensuring we keep all 153 rows without bias.

Results: After imputation, we had a complete dataset ready for analysis.

Step 2: Summary Statistics

calculate the min, max, mean, median, and quartiles for all variables to get a feel for the data.

Why? These stats show the range, typical values, and spread, helping spot outliers or patterns. For ozone, it tells us if most days are safe or if some hit risky levels.

Results: Ozone ranged from 1 to 168 ppb (median: 31, mean: 42), showing big swings. Solar radiation spanned 7 to 334 lang (median: 205). Wind speed went from 1.7 to 20.7 mph (median: 9.7). Temperature ranged from 56 to 97°F (median: 79). Months covered May (5) to September (9).

Step 3: Correlation Analysis

computed correlations between ozone, solar radiation, wind, and temperature to see how they’re related.

Why? Correlations reveal which factors move with ozone. Heat likely boosts ozone formation, while wind might clear it out. This guides our modeling and confirms key relationships.

Results: Ozone and temperature had a strong positive correlation (0.7), ozone and wind a moderate negative one (-0.6), and ozone and solar radiation a weaker positive link (0.3). Wind and temperature correlated negatively (-0.4).

Step 4: Exploratory Data Analysis

 the plots: ozone vs. temperature (scatter), ozone by month (boxplot), ozone vs. wind (scatter), and ozone vs. solar radiation (scatter).

Why? Plots make patterns pop. Scatters show how ozone changes with each factor, and the boxplot highlights seasonal differences, crucial since ozone often spikes in summer.

Results: The ozone-temperature scatter showed higher ozone on hotter days, matching the 0.7 correlation. The boxplot confirmed July and August had higher ozone (medians ~59 ppb) than May or September (~23–31 ppb), with some summer days hitting 135–168 ppb. The ozone-wind scatter showed lower ozone on windier days, supporting the -0.6 correlation. The ozone-solar radiation scatter showed a slight upward trend, consistent with the 0.3 correlation.

Step 5: Linear Regression

I built a regression model to predict ozone using solar radiation, wind, and temperature, then checked its fit and significance.

Why? Regression quantifies how much each factor affects ozone and whether it’s significant, helping us predict levels and pinpoint key drivers.

Results: The model explained 60% of ozone’s variation (R-squared = 0.60). Temperature had the biggest impact (1.65 ppb per °F, p < 0.001), followed by wind (-3.33 ppb per mph, p < 0.001). Solar radiation had a smaller effect (0.06 ppb per lang, p = 0.01).

Step 6: Monthly Trends

I averaged ozone, solar radiation, wind, and temperature by month to spot seasonal patterns.

Why? Ozone peaks in summer due to heat and sunlight, so monthly averages show when levels are highest, useful for air quality planning.

Results: Ozone peaked in July (60.1 ppb) and August (64.3 ppb), with higher temperatures (84.5–85.0°F) and lower winds (~9 mph). May and September had lower ozone (31.2–33.4 ppb) and temperatures (74.1–77.2°F).

Conclusions

Temperature strongly drives ozone (0.7 correlation, 1.65 ppb/°F), as heat fuels pollutant reactions. Wind reduces ozone (-0.6 correlation, -3.33 ppb/mph) by dispersing it. Solar radiation has a minor role (0.3 correlation). July and August see the highest ozone due to warmer weather. The model, explaining 60% of ozone variation, is useful for forecasting. These insights could guide air quality alerts on hot, calm days.

This analysis shows how weather shapes ozone, with clear seasonal peaks and practical implications for air quality management. Let me know if you want to dig deeper!
