# A Real Estate metric to help Australian residential property investors

Please note, I did **not** use ChatGPT for this exercise. However, I did close my laptop overnight and the timer is still going. :\

## Pre-processing Data
Let's define an `Australian residential property investor` as someone who: 
* Has enough enablement to buy a property (credit score, deposit etc).
* Is **not** urgently looking for a property to live in, but a home to invest in (bring income). 
* Wants to look at a return of $200K over 12 years. 
* Investors are interested in properties up to $5m. 

Assuming we have all of the above dimensions, let's work with the following assumptions: 
* We have a database of every property that's ever been for sale in the last 30 years in Australia.
* We have metadata such as - history of sell, bedrooms, square feet, bathrooms, garage, pool, etc.
* We have adjacent community/census based data on the area - median household income, widowed/married/divorced/single households, unemployment rate etc.
* We have interest rate data over the years. 

That's 4 different types of dimensional data. 

From this, we can infer how much a home can inflate over N years and consequently, we can find a baseline of: 

* How much an investor can make on a property (with certain metadata) in a particular location over N years. 

For example, investing in a $4m home in Bondi can return $8 million over 12 years, as opposed to a home in Central Coast where a return over 12 years would be projected to be $400K. 

I would put all of this data into a spreadsheet and organise by LGA (simply because Census data is based on LGA) and it can be paired with property based data. 

I'd load this all into a CSV file. 
X axis would be items and Y axis would be dimensions such as: bedrooms, square feet, LGA, buy price, sell price, profit, median household income (for LGA at the time between buy and sell etc). 

Data set would look like this: 
LGA | median household income | year | unemployment rate | interest rate | flood levels (average) | bedrooms | median buy price | median sell price | median profit | schools nearby

## Hypothesis: Does community profile (by LGA) influence property attributes enables the best return on investment over 12 years?

## Analysis and methods

### Normalisation

I'd conduct tests to see if the dataset is normally distributed, ensure SDs are similar and this way we can use the data for prediction (as the data is considered normal). 

Other things I would look for in the datasets would be to see if there is inconsistencies in the years (for example, Cencus data was non existent in 2020, and there was 
significant changes between 2019 and 2021) so I would perform methods such as bootstrapping the data to ensure that the data set can be normalised.

### ANOVA: determine if we can predict profit based on location and community based attributes. 
I would use an ANOVA test to determine if things like LGA and community based attributes influence Y output -> profit. 

If the p-value is small, we reject the hypothesis and assume that community profile does influence property attributes. 

### Model Selection

We can also obtain the combination of factors with the highest profit margin. e.g. properties with 2-3 bedrooms closest in proximity to beaches are likely to yield better profits in the range of $1m-2m. 

Depending on certain factors (many correlated variables, only few predictors evident, feature selection required) we can use Lasso or Ridge Regression. 

### Predictions

If we had a high enough confidence interval, we can then predict future profits on a property with certain attributes for a given year using our normalised dataset. 

## Conclusion

N/A


# End Notes

Apologies for not deep diving into this exercise, I was unsure if I needed to do a more practical implementation using an open source tool, or a purely statistical approach, so I did a high level statistical approach 
to demonstrate my knowledge of data science and evidence based skills/decision making.
