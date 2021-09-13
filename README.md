# Predicting Ames, Iowa Real Estate Prices with Linear Regression

## Contents
- [Problem Statement](#Problem-Statement)
- [Overview](#Overview)
- [Data Dictionary](#Data-Dictionary)
- [Model Performance](#Model-Performance)
- [Conclusions and Next Steps](#Conclusions-and-Next-Steps)
- [References](#References)

## Problem Statement
>There are certain aspects about a home that you simply can't change like lot size, age of the home, and square footage for the most part. Of course, there are endless features that you can add, fix or upgrade. As a homeowner, it can be overwhelming trying to evaluate the ROI for home improvement projects. This project not only aims to build a model for predicting sale prices for homes in Ames, Iowa, but also tries to determine if there are particular home qualities that have the potential to help increase a home's sale price for when you’re ready to sell it.

## Overview
For Project 2, I was tasked with creating a regression model based on the Ames Housing Dataset. The goals of this project are to create and iteratively refine a model as well as provide any insights that support our problem statement. This model predicts the sale price of a house on the market in Ames, Iowa. The Ames Housing Dataset contains over 70 columns of different features relating to houses that we can use in our model directly or through feature engineering. 

There's a lot of factors that go into a home's sale price. I know when I was searching to purchase a home 5 years ago, I couldn't have cared less about what the kitchen looked like! I had a smart realtor who prevented me from purchasing an apartment simply because of the kitchen quality and knowing I was not going to do any major renovations. It simply was not a good investment. This advice was based off her years of experience selling homes and helping buyers, however, predictive models can help make these same decisions! This project aims to identify what those major factors are for homes on the market in Ames, Iowa. We also can use the results to predict what home renovation projects might give you the best return on investment (ROI) based of similar homes and their respective sale price.

Models will be evaluated on Root-Mean-Squared-Error(RMSE) as well as other regression metrics that tell us how the model is performing between the predicted home sale price and the actual home sale price. There are five assumptions to a linear regression model that we will also be iterively checking during the EDA process as well as the Model Evaluation step.


## Data Dictionary
This data dictionary provides a quick overview of features/variables/columns used, alongside data types and descriptions. These are contained within the original train.csv, Ames_Clean_More_COLUMNS.csv (used for Production Model), Ames_Clean.csv, and Ames_Clean_No_Dummies.csv. The columns with an object datatype are broken down into subcategories within the csv files. For more information on these subcategories please refer to http://jse.amstat.org/v19n3/decock/DataDocumentation.txt.

|Feature|Type|Description|
|---|---|---|
|**Id**|*int*|Identification number for the property.|
|**SalePrice**|*float*|The property's sale price in dollars. This is the target variable|
|**Total SF**|*float*|Total combined sqft of livable space|
|**Porch**|*float*|Total combined porch sqft|
|**Total Bath**|*float*|Total combined number of bathrooms|
|**House Age**|*int*|House Age (Year Built - Year Sold)|
|**MS SubClass**|*object*|The building class|
|**Lot Frontage**|*float*|Linear feet of street connected to property|
|**Lot Area**|*float*|Lot size in square feet|
|**Alley**|*object*| Type of alley access to property|
|**LotShape**|*object*| General shape of property|
|**Neighborhood**|*object*|Physical locations within Ames city limits|
|**Condition 1**|*object*|Proximity to main road or railroad|
|**Condition 2**|*object*|Proximity to main road or railroad (if a second is present)|
|**Bldg Type**|*object*|Type of dwelling|
|**House Style**|*object*|Style of dwelling|
|**Overall Qual**|*object*|Overall material and finish quality|
|**Year Remod Add**|*int*|Remodel date (same as construction date if no remodeling or additions)|
|**Roof Style**|*object*|Type of roof|
|**Roof Mat l**|*object*|Roof material|
|**Exter Qual**|*object*|Exterior material quality|
|**Exter Cond**|*object*|Present condition of the material on the exterior|
|**Foundation**|*object*|Type of foundation|
|**Bsmt Qual**|*object*|Height of the basement|
|**Bsmt Exposure**|*object*|Walkout or garden level basement walls|
|**BsmtFin Type 1**|*object*|Quality of basement finished area|
|**BsmtFin SF 1**|*float*|Type 1 finished square feet|
|**BsmtFin Type 2**|*object*|Quality of second finished area (if present)|
|**BsmtFin SF 2**|*float*|Type 2 finished square feet|
|**Bsmt Unf SF**|*float*|Unfinished square feet of basement area|
|**Total Bsmt SF**|*float*|Total square feet of basement area|
|**Heating**|*object*|Type of heating|
|**Central Air**|*object*|Central air conditioning|
|**Low Qual Fin SF**|*float*|Low quality finished square feet (all floors)|
|**Gr Liv Area**|*float*|Above grade (ground) living area square feet|
|**Bedroom**|*int*|Number of bedrooms above basement level|
|**Kitchen**|*int*|Number of kitchens|
|**TotRms AbvGrd**|*int*|Total rooms above grade (does not include bathrooms)|
|**Fireplaces**|*int*|Number of fireplaces|
|**Fireplace Qu**|*object*|Fireplace quality|
|**Garage Type**|*object*|Garage location|
|**Garage YrBlt**|*int*|Year garage was built|
|**Garage Finish**|*object*|Interior finish of the garage|
|**Garage Cars**|*int*|Size of garage in car capacity|
|**Garage Area**|*float*|Size of garage in square feet|
|**Garage Cond**|*object*|Garage condition|
|**Paved Drive**|*object*|Paved driveway|
|**Wood DeckSF**|*float*|Wood deck area in square feet|
|**Porch**|*float*|All porch areas in square feet|
|**Pool Area**|*float*|Pool area in square feet|
|**Fence**|*object*|Fence quality|
|**Misc Val**|*float*|$Value of miscellaneous feature|
|**MoSold**|*int*|Month Sold|

## Model Performance
While my Lasso model had the best train and test R2 scores and my highest kaggle score, I think it reduced the weights to zero for several features and I'm not confident that it isn't overfit to predict on other data it hasn't seen yet. I ended up dropping a lot of the columns that Lasso reduced to zero in order to see if they improved the Linear Regression model, however, it really had minimal effect on the R2 scores. Dropping and adding features is clearly not the way to improve the linear regression model, but engineering new features and finding more interaction terms seems to be the most influential for increasing accuracy. Another benefit of finding interaction terms is that you reduce the amount of features going into the model which hopefully reduces the likelihood of too many features being collinear and the potential to overfit your model.

|Lasso Production Model|Interpretation|
|---|---|
|**Train R2 Score**|91.79% of variability can be explained by the model|
|**Test R2 Score**|90.61% of variability can be explained by the model|

## Conclusions and Next Steps
I was not able to conclusively determine which specific home improvement features would give you the greatest ROI. A lot of these features seemed to fluctuate in importance depending on the model and hyperparameters used. Overall Quality as well as Neighborhood seemed to be the most stable predictor for Sale Price. It's unfortunate the rating criteria used for Overall Quality was not super specific about how the ratings were graded so I'm not sure if I can recommend any specific home improvements other than take care of your home and use higher quality materials when applicable!

With respect to being able to use this model to predict Sale Prices in other cities, I do not think it will generalize well to other cities as is. The real estate market in Ames, Iowa cannot be compared to just any city in America. Perhaps it may perform ok on other midwestern cities comparable in size though! In order to make it more applicable to other midwestern cities, I think having census and population data would help. Since Neighborhoods seems to be a good predictor of Sale Price, you would need to find a way to classify and quantify Neighborhoods by something other than name. For example, gross income or other socioeconomic and demographic data.

In the future, I think I would take the opposite approach of building a model. I was overwhelmed by the amount of possible predictor columns that I think my strategy to initially throw everything into it and then try to take away was harder to keep the momemtum going. Next time I will try the approach of iteratively building the model up and adding each feature more purposefully to see the specific effect of each varible on the results.

## References
1. [http://jse.amstat.org/v19n3/decock/DataDocumentation.txt]
2. Pardoe , I. (2008), “Modeling home prices using realtor data”, Journal of Statistics Education Volume 16, Number 2 (2008). [http://jse.amstat.org/v16n2/datasets.pardoe.pdf]
3. [https://www.kaggle.com/fedi1996/house-prices-data-cleaning-viz-and-modeling]
4. [https://stats.stackexchange.com/questions/371529/interpreting-rmse-of-log-values]
5. [https://stats.idre.ucla.edu/other/mult-pkg/faq/general/faqhow-do-i-interpret-a-regression-model-when-some-variables-are-log-transformed/]
6. [https://data.library.virginia.edu/interpreting-log-transformations-in-a-linear-model/]
