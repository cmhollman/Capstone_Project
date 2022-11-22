![Header](https://github.com/cmhollman/Capstone_Project/blob/main/Images/header.jpeg)



# Climate Change Time Series Analysis 

**Author**: [Chris Hollman](mailto:chollman91@gmail.com)

## Overview

The goal of this project is to study the trends of our global climate. This will include an analysis of historical data, a prediction of future values, and a regresssion model to determine major temperature predictors.

## Business Problem

An environmentally focused nonprofit organization is seeking data-focused insight to better understand climate change. This includes long term outlook and contributing factors.


## Data

The data for this project comes from a variety of datasets, which are linked at the bottom of this readme. They come from two main sources:

**Kaggle:**

-Data/GlobalTemperatures.csv

-Data/historical_emissions.csv

-Data/gdp_growth.csv

**Our World In Data:**

-Data/world_population.csv

-Data/oil_consumption.csv

-Data/forest_area.csv

The data used for time series modeling consisted of average monthly land temperatures from 1750 to 2015. This is 3,180 values in total spanning 250 years. 

The data used for regression modeling came from a variety of sources but was pared down to annual values from 1990-2015. These values include:

-Average Global Temperatures(Farenheit)

-Global CO2 Emmissions(MTCO2e)

-Global GDP Growth Rate(%)

-Global Population

-Global Oil Consumption(TWH)

-Global Forest Area(% of land area)

## Methods

For time series decomposition we applied an LSTM model, as well as Facebook's Neural Prophet. For regression analysis we use an XGBoost regressor. For all models. Mean absolute error was the chosen metric to optimize. I chose MAE because it is easy to interpret, and errors in either direction are equally problematic.

## Time Series Results

For time series decomposition, the Prophet Model performed quite a bit better than the LSTM model. Prophet produced an MAE of .45 when predicting the final two years of global monthly averages whereas LSTM scored 2.89. Below you will find a plot visualizing predicted vs actual temperatures for the test set. For this reason, the Prophet model was used to predict future temperatures from 2016 to 2045. The predicted results are charted below. As you can see, the final Prophet model predicts that average temperatures will increase by another 1.5 degrees over the next 30 years. This is roughly on par with the predictions from the U.S. Global Change Research Program's 2016 Climate Science Special Report, which predicts an increase of 2 to 4 degrees by mid 21st century (2036-2065), depending on a number of factors. Also of note is the significant upward trend that begins in the early 1970s. This trend, the trend change rates, and the seasonality are all visible in the bottom set of charts. 

![proph_test](https://github.com/cmhollman/Capstone_Project/blob/main/Images/prophet_test.png)

![forecast](https://github.com/cmhollman/Capstone_Project/blob/main/Images/forecast.png)

![params](https://github.com/cmhollman/Capstone_Project/blob/main/Images/params.png)


## Regression Results

The regression component of this project also revealed some interesting insights. The first we evident prior to ever fitting a regression model to the data. Below is a clustermap (essentially a grouped heatmap) of correlation values. The strongest correlations actually those involving forest area, which has a strong negative correlation to population and oil consumption. The strongest correlation to average temp were population, forest area, and oil consumption. GDP growth rate was not strongly tied to anything other data in the table, and was dropped prior to modeling. The final model was able to predict the temperature of a given year with a test MAE of .43. This is relatively good performance. The F-Scores for the best performing features are listed below. Meaning that the model found these most useful when predicting temperature. 

![cluster](https://github.com/cmhollman/Capstone_Project/blob/main/Images/clustermap.png)

![cluster](https://github.com/cmhollman/Capstone_Project/blob/main/Images/regplots.png)

![f_scores](https://github.com/cmhollman/Capstone_Project/blob/main/Images/feature_importance.png)


## Conclusions
Based on the results of the models, the following insights stand out:

-**Temperature is trending upwards, especially after 1970** 

This is the most significant trend change present in the dataset and coincides with the beginning of automated production lines and mass production.

-**Correlations**

There is significant positive correlation between average temperature, population, oil consumption. All three of these have strong negative correlations with forest area. These values suggest that the world population is growing and consuming more fossil fuels on a year to year basis, while forest are is decreasing. None of these neccesarily coincide with a larger GDP.

-**Population, Oil Consumption, and Emissions are strong predictors of temperature**

While association does not equate to causation, these factors can be used to effectively predict average yearly temperatures.

## Next Steps

-**Further insight into emmissions**

Since the emissions don't have an instantaneous impact on temperature, it would be interesting to explore different lag periods to discover any sort of delay of cumulative effect that emissions may have. 

-**Population Studies**

Since population size seems to be a major contributor to rising global temperatures, comparing country population, growth rates, and consumption/emmissions of those countries may lead to ways to minimize the environmental impact of a growing population as well as indentifying which countries have environmental policies that should be emulated.

-**Seasonality Studies**

According to experts, the general trend of warming is likely to be accompanied by wider temperature swings and more extreme weather. Looking into shorter term weather data such as monthly highs, lows, and extreme weather events for smaller geographical areas would add more specific context to this study as well as examples of the real world impact of climate change. 

## For More Information

See the full analysis in the [Jupyter Notebook](https://github.com/cmhollman/Capstone_Project/blob/main/Global_Temp_Project.ipynb) 

or review this [presentation](https://github.com/cmhollman/Capstone_Project/blob/main/Capstone_Slides.pdf).

For additional info, contact Chris Hollman at [chollman91@gmail.com](mailto:chollman91@gmail.com)

## Data Links

-[Temperatures](https://www.kaggle.com/datasets/berkeleyearth/climate-change-earth-surface-temperature-data?select=GlobalTemperatures.csv)

-[GDP](https://www.kaggle.com/datasets/iamtushara/gdp-timeseries-data-for-various-countries?select=GDP_annual_growth_NEW.csv)

-[Emissons](https://www.kaggle.com/datasets/ankanhore545/carbon-dioxide-emissions-of-the-world)

-[Population](https://ourworldindata.org/world-population-growth)

-[Oil Consumption](https://ourworldindata.org/grapher/oil-consumption-by-country)

-[Forest Area](https://ourworldindata.org/deforestation)


## Repository Structure

```
├── Data
├── Images
├── Global_Temp_Project.ipynb
├── Capstone_Slides.pdf
└── README.md