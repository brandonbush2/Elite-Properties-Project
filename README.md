# Multiple Linear Regression at Elite Properties Group
# Overview
Elite Properties Group is a distinguished real estate agency specializing in assisting homeowners with buying and selling residential properties. With a strong reputation for exceptional service, market expertise, and a client-centric approach, Elite Properties Group has established itself as a trusted and preferred choice for clients seeking professional real estate guidance.

# Business Understanding
Elite Properties Group has the need to develop a reliable and accurate model that predicts the sale prices of residential properties based on their key attributes. By leveraging historical data, including features such as the number of bedrooms, bathrooms, square footage of living space, lot size, number of floors, property condition and year built, the agency aims to provide clients with precise pricing recommendations and maximize their returns on investment.

The primary objective of this project is to build a robust predictive model that accurately estimates the sale prices of residential properties listed by Elite Properties Group. By utilizing the available dataset, the agency aims to offer clients reliable and data-driven pricing advice, enhancing their confidence in the sales process and facilitating optimal pricing strategies.

After building the model, we will address the following descriptive questions through data visualization:

#### 1. Does the number of bathrooms have an impact on sale price?
Here, what is the relationship between bathrooms and sale price. Do home buyers prefer houses with more bathrooms?

#### 2. How does square feet of living room area impact sale price?
Here, does it mean if a house has a larger living room square feet that results to a higher sale price?

#### 3. Does presence or absence of a waterfront have an impact on saleprice?
Do home buyers prefer houses with a waterfront view or not?

# Data Understanding
To support their operations and decision-making processes, Elite Properties Group collects and analyzes various data related to the real estate market and property transactions. This data includes:
* Saleprice
* Number of Bedrooms
* Number of Bathrooms
* Year Built
* Date the house was sold
* Whether the house is on a waterfront
* Square footage of living space in the home
* Number of floors (levels) in house
* Quality of view from house

## Relevance of these features:
* **Saleprice:** This is the target variable, and it is of utmost importance as it represents the ultimate measure of a property's value. Predicting the sale price accurately is the primary objective of the project.
* **Number of Bedrooms:** The number of bedrooms is highly relevant for Elite Properties as it directly influences the size and functionality of the property. It is typically a significant factor in determining the value and desirability of a home.
* **Number of Bathrooms:** Similar to the number of bedrooms, the number of bathrooms is crucial for Elite Properties. It affects the convenience and comfort of residents, making properties with more bathrooms more attractive to potential buyers and potentially commanding higher sale prices.
* **Year Built:** The year a property was built provides important information about its age and potential condition. Elite Properties can consider the year built as a relevant feature as it can influence the perception of quality, maintenance requirements, and historical significance of a property.
* **Date the House Was Sold:** While the date of sale may not directly impact the predictive model, Elite Properties can use it for additional analysis, such as identifying seasonal trends or market fluctuations that may affect sale prices.
* **Whether the House Is on a Waterfront:** This feature is highly relevant for Elite Properties, especially if they specialize in waterfront or water-view properties. Being on a waterfront can significantly impact a property's value due to the premium associated with scenic views and direct access to water amenities.
* **Square Footage of Living Space:** The square footage of the living space is a key determinant of a property's size and functionality. Elite Properties can consider it as a significant feature, as larger living spaces often command higher sale prices.
* **Number of Floors (Levels) in the House:** The number of floors indicates the vertical layout of a property and can influence its overall appeal and functionality. Properties with multiple floors may be considered more desirable and can potentially have higher sale prices.
* **Quality of View from the House:** The quality of the view from a property, such as scenic landscapes or city skylines, can significantly impact its value. Elite Properties can consider this feature relevant, particularly if they deal with properties that offer exceptional views.

The column names and descriptions as provided can be found in the `column_names.md` file in this repository. For convenience they have been reproduced below.

### Column Names and descriptions for Kings County Data Set

* **id** - unique identified for a house
* **dateDate** - house was sold
* **pricePrice** - is prediction target
* **bedroomsNumber** - of Bedrooms/House
* **bathroomsNumber** - of bathrooms/bedrooms
* **sqft_livingsquare** - footage of the home
* **sqft_lotsquare** - footage of the lot
* **floorsTotal** - floors (levels) in house
* **waterfront** - House which has a view to a waterfront
* **view** - Has been viewed
* **condition** - How good the condition is ( Overall )
* **grade** - overall grade given to the housing unit, based on King County grading system
* **sqft_above** - square footage of house apart from basement
* **sqft_basement** - square footage of the basement
* **yr_built** - Built Year
* **yr_renovated** - Year when house was renovated
* **zipcode** - zip
* **lat** - Latitude coordinate
* **long** - Longitude coordinate
* **sqft_living15** - The square footage of interior housing living space for the nearest 15 neighbors
* **sqft_lot15** - The square footage of the land lots of the nearest 15 neighbors

# Modeling
Using an alpha/significance level of 0.05, created 4 models before finalizing the final model.

## Model A
* Number of Features was 1. (sqft_living)
* Adjusted R-squared of 0.493( **49.3%** of variations were explained by this model)
* Root Mean Squared error(RMSE) of **261689.59** meaning that on average the actual price will be USD 261,689 more or less than our predicted price. 
* The coefficent of sqft_living is 280, which means that for every additional square-foot of living area, the price increases by USD 280.
* Built a scatter plot with the predicted y values and found that for smaller living areas our model looks decent but as the sqft_living value increases our model's performance declines. This shows that sqft_living is not a good enough predictor for larger houses.
![Scatter Plot with Predicted values](https://github.com/brandonbush2/Elite-Properties-Project/blob/master/Images/Scatter%20Plot%20with%20Predicted%20Y.png)

## Model B
* Used 9 Features.
* Adjusted R-squared of 0.648( **64.8%** of variations were explained by this model)
* Root Mean Squared error(RMSE) of **217893.79**.
* Created a QQ-plot of residuals.
![QQ plot of Residuals](https://github.com/brandonbush2/Elite-Properties-Project/blob/master/Images/QQ%20plot.png)
There appeared to be some issues with the residuals not being normally distributed.

## Model C
I tested for multicolinearity and remove features which are multicolinear with each other.
* Used 8 Features.
* Adjusted R-squared of 0.588( **58.8%** of variations were explained by this model)
* Root Mean Squared error(RMSE) of **235693.65**.

## Model D
Perform one hot encoding on columns that appeared to be categorical and noted differences if any.
* Used 28 Features.
* Adjusted R-squared of 0.604( **60.4%** of variations were explained by this model)
* Root Mean Squared error(RMSE) of **231070.21**.

## Final Model
Included data from the grade column and performed one hot encoding
* Used 38 Features
* Adjusted R-squared of 0.681( **68.1%** of variations were explained by this model)
* Root Mean Squared error(RMSE) of **207312.12**.

# Regression Results
Houses that are `grade_13` and `grade_12` as well as houses with 7 and 8 bathrooms tend to have the highest impact on Saleprice since they have the highest coefficients.

However, `sqft_living` and `sqft_lot` also have a high impact on SalePrice. They have low coefficients here since they are not in boolean unlike grade or bathrooms.
An increase by 1 square foot of living area results to an increase by 149.59 on Sale Price.
An increase by 1 square foot of lot size leads to a decrease bt 0.27 on Sale Price.
Houses that have a waterfront view are estimated to be worth from USD700,000 indicating that the Saleprice is also very dependent on waterfront access.
Houses off `grade_13` are worth around USD 2,000,000 while houses with 7-8 bedrooms are worth around USD1,400,000 and USD1,900,000.

# Visualization
### 1. Does the number of bathrooms have an impact on sale price?
![Bar plot of bathrooms and price](https://example.com/image.png)

From the barplot above, houses with 8 bathrooms have the highest SalePrice. Houses with fewer bathrooms have a lower Sale Price which would mean that home buyers would prefer houses with more bathrooms. Also from our model we identified that houses with more bathrooms i.e 7 and 8 have a higher coefficient and impact SalePrice more.

### 2. How does square feet of living room area impact sale price?
![Bar plot of sqft_living and price](https://github.com/brandonbush2/Elite-Properties-Project/blob/master/Images/Bar%20plot%20of%20sqft%20and%20price.png)

Houses with larger living room area square feet have a higher sale price. The price of houses increases with increase in square feet of living area.

### 3. Does presence or absence of a waterfront have an impact on saleprice?
![Bar plot of waterfront against price](https://github.com/brandonbush2/Elite-Properties-Project/blob/master/Images/Bar%20plot%20of%20waterfront%20and%20price.png)

From the graph above, houses with a view to a waterfront have a higher sale price than house with no view to a waterfront. This means that if a home owner's house has a waterfront view, the value to of that house may be higher than the one with no waterfront view.

Houses with no waterfront view are sold at a price not more than the average Sale Price, while those with a waterfront view are sold at a price mostly higher than the average Sale Price.

# Conclusion
### Summary of Findings and Recommendations
#### 1. Grade
The higher the grade assigned to a house, the higher the estimated value and potential selling price.
The grade of a house is an important factor influencing its market value and attractiveness to potential buyers.
Buyers are willing to pay more for houses with higher-grade ratings, indicating perceived quality and desirability.
Homeowners looking to increase the value of their properties may consider improving the overall grade by enhancing various features and amenities.

#### 2. Bathrooms
The greater the number of bathrooms in a house, the higher its estimated value and potential selling price.
Having more bathrooms is seen as a desirable feature by buyers, as it provides convenience and accommodates larger households.
Homeowners looking to increase the value of their properties may consider adding or upgrading bathrooms to attract potential buyers and command a higher sale price.

#### 3. Waterfront
Properties with a waterfront view are considered more desirable and offer a unique feature that attracts buyers.
The scenic beauty and recreational opportunities associated with waterfront properties contribute to their increased market value.
Homeowners who own properties with a waterfront view can expect a higher potential selling price.
Investing in a property with a waterfront view can potentially yield a higher return on investment compared to similar properties without such a feature.

#### 4. Square Foot of living area
The size of the living area is a significant factor in determining the market value and desirability of a property.
Buyers often prioritize spacious living areas, as they provide more room for living, entertaining, and accommodating their needs.
Larger living areas offer greater flexibility in furniture arrangement and potential for customization.
Homeowners who own houses with a larger square footage of living area can expect a higher potential selling price.






























