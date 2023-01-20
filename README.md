# Best-Buy-Project-Week
Files related to Best Buy Project week

Code File 0 : Initial Data Exploration
● We examined the data and came up with the following insights
○ Sparsity: The daily unit sales is 0 for a large proportion of the time series
of the SKUs
○ Missing values: There exists many SKUs with disjoint time series for which
we imputed values
○ Trend/Seasonality indication: Examining factors influencing daily units like
month of year, day of week etc.
Code File 1 : Predictive Modeling using XGBoost
● In this script, we focus on feature engineering for a predictive modeling strategy.
We also use external data sources like Consumer Sentiment Index and Global
Supply Chain Pressure Index to factor in macroeconomic features.
● We create multiple lag variables using the demand variable to capture trend and
seasonality in the data.
● We finalize on using XGBoost model for our use-case as we know that
Tree-based models work effectively on tubular data and a boosting ensemble
model would make sure predictions have good accuracy without considerable
overfitting.

Code File 2 : Univariate Modeling using Croston
● Croston Model is a smoothing model(similar to Holt & Winters) specialized for
forecasting demand of products with intermittent sales.
● The function of Croston is defined in the code as well
● We achieve the RMSE score of **4.7** using Croston Model

Code File 3 : Ensemble Modeling Approach
● With the Ensemble strategy, we try to strike a midway between Croston,
XGBoost and Baseline (Mean demand as predictions) approaches.
● We score all the 3 models on a Hold-out dataset of the last 7 days in the training
dataset and calculate SKU-level RMSE values for all the 3 models.
● Based on the best performing model for each SKUs, we employ the appropriate
strategy to predict for SKUs in the Validation dataset. This strategy helps select
the most apt model for each SKU, depending on the nature of its time-series.


Code File 4 : Exploratory Data Analysis for variability in Daily Units
sold for SKU’s
● Analysis of SKUs which have very high variability in Daily units sold (those set of
SKUs which have daily units sold outside 2 standard deviations about the mean.
● Analysis of Inventory status on the overall sales/daily units sold of various SKUs.
● Analysis of SKUs which are very slow moving based on 2 attributes :
○ Percentage of days unsold since the launch of the product . These are
those SKU’s which remain unsold for more than 50% of the days since
their launch.
○ Average consecutive shelf life : This is defined in terms of the average
number of consecutive days for which a SKU remains unsold. We
analyzed 24 such SKUs with shelf life above 15 days.
