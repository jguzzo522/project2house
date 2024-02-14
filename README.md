# Increasing Property Value for Homeowners based on analysis from Model 4

## Goal
This project is aimed at increasing property value for homeowners for the purpose of resale value. Using price as the measurement to determine property value, the data indicates that increasing the house grade and the number of bathrooms are metrics that can be used to raise overall property value. 

## Data
This project used existing data from a data set called ‘kc_house_data’ (below). Pandas library was used to import this dataset into Jupyter notebook. Twenty three columns served as variables in the ‘kc_house_data’ dataset.

<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
</head>
<body>

<h1>Data Description for King County Housing Dataset</h1>

<table border="1">
    <tr>
        <th>Column</th>
        <th>Description</th>
    </tr>
    <tr>
        <td>id</td>
        <td>Unique identifier for a house</td>
    </tr>
    <tr>
        <td>date</td>
        <td>Date the house was sold</td>
    </tr>
    <tr>
        <td>price</td>
        <td>Sale price (prediction target)</td>
    </tr>
    <tr>
        <td>bedrooms</td>
        <td>Number of bedrooms</td>
    </tr>
    <tr>
        <td>bathrooms</td>
        <td>Number of bathrooms</td>
    </tr>
    <tr>
        <td>sqft_living</td>
        <td>Square footage of living space in the home</td>
    </tr>
    <tr>
        <td>sqft_lot</td>
        <td>Square footage of the lot</td>
    </tr>
    <tr>
        <td>floors</td>
        <td>Number of floors (levels) in the house</td>
    </tr>
    <tr>
        <td>waterfront</td>
        <td>Whether the house is on a waterfront</td>
    </tr>
    <tr>
        <td>greenbelt</td>
        <td>Whether the house is adjacent to a green belt</td>
    </tr>
    <tr>
        <td>nuisance</td>
        <td>Whether the house has traffic noise or other recorded nuisances</td>
    </tr>
    <tr>
        <td>view</td>
        <td>Quality of view from the house</td>
    </tr>
    <tr>
        <td>condition</td>
        <td>Overall condition of the house (related to maintenance)</td>
    </tr>
    <tr>
        <td>grade</td>
        <td>Overall grade of the house (related to construction and design)</td>
    </tr>
    <tr>
        <td>heat_source</td>
        <td>Heat source for the house</td>
    </tr>
    <tr>
        <td>sewer_system</td>
        <td>Sewer system for the house</td>
    </tr>
    <tr>
        <td>sqft_above</td>
        <td>Square footage of the house apart from the basement</td>
    </tr>
    <tr>
        <td>sqft_basement</td>
        <td>Square footage of the basement</td>
    </tr>
    <tr>
        <td>sqft_garage</td>
        <td>Square footage of garage space</td>
    </tr>
    <tr>
        <td>sqft_patio</td>
        <td>Square footage of outdoor porch or deck space</td>
    </tr>
    <tr>
        <td>yr_built</td>
        <td>Year when the house was built</td>
    </tr>
    <tr>
        <td>yr_renovated</td>
        <td>Year when the house was renovated</td>
    </tr>
    <tr>
        <td>address</td>
        <td>Street address</td>
    </tr>
</table>

</body>
</html>

This data was analyzed, modeled, manipulated, computed, visualized, and plotted using different library packages in Python such as 'Statsmodels', 'Pandas', 'Numpy', 'OS', 'Matplotlib', 'Seaborn', ‘Sklearn, 'Spicy' and 'Arima'.

## Cleaning the Data
In this dataset there were a few columns that had duplicate values, or missing values. In order to properly analyze this dataset these rows were removed from the original dataset. The pre-cleaned data initially had 30,155 rows, and after removing the missing or duplicate values, 30,110 rows remained. 

<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
</head>
<body>

<h2>Making Categorical Data Interpretable</h1>

In this project, several categorical variables such as 'condition', 'heat_source', 'renovation_status', 'grade', 'nuisance', and 'sewer_system' were present in the dataset. Statistical models typically require numerical input for interpretation and analysis. Therefore, in order to incorporate these categorical variables into the modeling process effectively, dummy variables were created using the Pandas library.

The process of creating dummy variables allows for categorical data to be classified as numerical data, assigning values of 0 if the variable is not present, or 1 if the variable is present. Once Dummy variables are created, the original variable is expanded into subcategories. For instance, after transforming the categorical column of  'nuisance' into a Dummy variable, the column splits into two separate columns, one labeled 'nuisance_NO' and one labeled 'nuisance_YES'. If a 'nuisance' is present in the house, a number one would be coded in the 'nuisance_yes' column, and a zero would be coded in the 'nuisance_NO' column.

After transforming all categorical data into numerical data, the dataset had:

Five new columns for 'condition'

Seven new columns for 'heat_source'

Two new columns for 'renovation_status'

Thirteen new categories for 'grade'

Two new columns for 'nuisance'

Four new columns for 'sewer system'

This process enabled the categorical data to be effectively utilized in statistical modeling and analysis.
## Dummy Variables

<table border="1">
    <tr>
        <th>Column</th>
        <th>Description</th>
    </tr>
    <tr>
        <td>condition_Average</td>
        <td>Dummy variable indicating if the house is in average condition (related to maintenance)</td>
    </tr>
    <tr>
        <td>condition_Fair</td>
        <td>Dummy variable indicating if the house is in fair condition (related to maintenance)</td>
    </tr>
    <tr>
        <td>condition_Good</td>
        <td>Dummy variable indicating if the house is in good condition (related to maintenance)</td>
    </tr>
    <tr>
        <td>condition_Poor</td>
        <td>Dummy variable indicating if the house is in poor condition (related to maintenance)</td>
    </tr>
    <tr>
        <td>condition_Very Good</td>
        <td>Dummy variable indicating if the house is in very good condition (related to maintenance)</td>
    </tr>
</table>

### Heat Source Variables

<table border="1">
    <tr>
        <th>Column</th>
        <th>Description</th>
    </tr>
    <tr>
        <td>heat_source_Electricity</td>
        <td>Dummy variable indicating if the heat source for the house is electricity</td>
    </tr>
    <tr>
        <td>heat_source_Electricity/Solar</td>
        <td>Dummy variable indicating if the heat source for the house is electricity or solar</td>
    </tr>
    <tr>
        <td>heat_source_Gas</td>
        <td>Dummy variable indicating if the heat source for the house is gas</td>
    </tr>
    <tr>
        <td>heat_source_Gas/Solar</td>
        <td>Dummy variable indicating if the heat source for the house is gas or solar</td>
    </tr>
    <tr>
        <td>heat_source_Oil</td>
        <td>Dummy variable indicating if the heat source for the house is oil</td>
    </tr>
    <tr>
        <td>heat_source_Oil/Solar</td>
        <td>Dummy variable indicating if the heat source for the house is oil or solar</td>
    </tr>
    <tr>
        <td>heat_source_Other</td>
        <td>Dummy variable indicating if the heat source for the house is other</td>
    </tr>
</table>

### Renovation Status Variables

<table border="1">
    <tr>
        <th>Column</th>
        <th>Description</th>
    </tr>
    <tr>
        <td>renovation_status_No Renovation</td>
        <td>Dummy variable indicating if the house has not been renovated</td>
    </tr>
    <tr>
        <td>renovation_status_Renovation</td>
        <td>Dummy variable indicating if the house has been renovated</td>
    </tr>
</table>

### Grade Variables

<table border="1">
    <tr>
        <th>Column</th>
        <th>Description</th>
    </tr>
    <tr>
        <td>grade_2 Substandard</td>
        <td>Dummy variable indicating if the house grade is 2 (Substandard)</td>
    </tr>
    <tr>
        <td>grade_3 Poor</td>
        <td>Dummy variable indicating if the house grade is 3 (Poor)</td>
    </tr>
    <tr>
        <td>grade_4 Low</td>
        <td>Dummy variable indicating if the house grade is 4 (Low)</td>
    </tr>
    <tr>
        <td>grade_5 Fair</td>
        <td>Dummy variable indicating if the house grade is 5 (Fair)</td>
    </tr>
    <tr>
        <td>grade_6 Low Average</td>
        <td>Dummy variable indicating if the house grade is 6 (Low Average)</td>
    </tr>
    <tr>
        <td>grade_7 Average</td>
        <td>Dummy variable indicating if the house grade is 7 (Average)</td>
    </tr>
    <tr>
        <td>grade_8 Good</td>
        <td>Dummy variable indicating if the house grade is 8 (Good)</td>
    </tr>
    <tr>
        <td>grade_9 Better</td>
        <td>Dummy variable indicating if the house grade is 9 (Better)</td>
    </tr>
    <tr>
        <td>grade_10 Very Good</td>
        <td>Dummy variable indicating if the house grade is 10 (Very Good)</td>
    </tr>
    <tr>
        <td>grade_11 Excellent</td>
        <td>Dummy variable indicating if the house grade is 11 (Excellent)</td>
    </tr>
    <tr>
        <td>grade_12 Luxury</td>
        <td>Dummy variable indicating if the house grade is 12 (Luxury)</td>
    </tr>
    <tr>
        <td>grade_13 Mansion</td>
        <td>Dummy variable indicating if the house grade is 13 (Mansion)</td>
    </tr>
</table>

### Nuisance Variables

<table border="1">
    <tr>
        <th>Column</th>
        <th>Description</th>
    </tr>
    <tr>
        <td>nuisance_NO</td>
        <td>Dummy variable indicating if the house has no recorded nuisances</td>
    </tr>
    <tr>
        <td>nuisance_YES</td>
        <td>Dummy variable indicating if the house has recorded nuisances</td>
    </tr>
</table>

### Sewer System Variables

<table border="1">
    <tr>
        <th>Column</th>
        <th>Description</th>
    </tr>
    <tr>
        <td>sewer_system_PRIVATE</td>
        <td>Dummy variable indicating if the sewer system for the house is private</td>
    </tr>
    <tr>
        <td>sewer_system_PRIVATE RESTRICTED</td>
        <td>Dummy variable indicating if the sewer system for the house is privately restricted</td>
    </tr>
    <tr>
        <td>sewer_system_PUBLIC</td>
        <td>Dummy variable indicating if the sewer system for the house is public</td>
    </tr>
    <tr>
        <td>sewer_system_PUBLIC RESTRICTED</td>
        <td>Dummy variable indicating if the sewer system for the house is publicly restricted</td>
    </tr>
</table>

## Search and Removal of Outliers

Utilizing Matplotlib and Seaborn, histogram's were generated for each numeric variable to gain insights into their distributions and identify outliers. Based on these graphs parameters were established to remove outliers from the dataset. Visualization of key statistical parameters such as the mean, standard deviation, and interquartile range was achieved using the Matplotlib library. This comprehensive approach ensured a thorough investigation of the data and facilitated informed decision-making in outlier removal. (See graph below)

The strategy for numerical variables involved focusing on the 5th and 95th percentiles of 'price', 'bedrooms', 'bathrooms', and 'floors'. This method aimed to minimize the influence of extreme outliers while preserving a significant portion of the dataset.

When handling square footage ('sqft') variables, the approach was to preserve more values to prevent substantial data loss. Instead of removing the 5th and 95th percentiles, the focus was on the 2nd and 98th percentiles to accommodate extreme low and high values, respectively. This approach ensured that the full spectrum of variation in 'sqft' variables was captured while still addressing potential outliers at the distribution's extremes.

The decision to prioritize the removal of extreme values for bedrooms, bathrooms, and floors was driven by their comparatively smaller value ranges, which exerted a more pronounced impact on price data. Similarly, focusing on the 95th percentile for price enabled the filtering out of the most extreme price outliers while retaining a significant portion of the dataset for analysis.

The integration of Matplotlib and Seaborn significantly facilitated the decision-making process. These visualization tools allowed for comprehensive exploration of the data, and swifter outlier removal. Using histograms allowed for insights into the data's patterns and irregularities, guiding the outlier removal strategy effectively. 

![Screen Shot 2024-02-13 at 3 31 58 PM](https://github.com/jguzzo522/project2house/assets/75549456/03b350c0-2849-456e-9a3c-43cfd0af875d)


## Removal of Additional Columns

This project was focused on increasing property value for homeowners though factors that homeowners could control. Consequently, the columns in the dataset that were unrelated to this objective and removed included 'latitude', 'longitude', 'date', 'year built', 'year renovated', 'greenbelt', 'view', and 'waterfront'. 

## Model 4 Created Using StatsModels

Utilizing StatsModels, a Multiple Linear Regression model was constructed to explore the relationship between various predictor variables and the target variable, which was set to 'Price', enabling the ability to analyze the relationship between multiple independent variables and a single dependent variable.

This model accounted for approximately 38% of the variance in 'Price', suggesting a moderate level of explanatory power. All p-values associated with the coefficients that were statistically significant predictors (p < 0.05), indicating that the corresponding coefficient is statistically significant at the 95% confidence level.

The coefficients in the model represent the estimated change in 'Price' for a one-unit change in the respective predictor variable. Interpretation of these coefficients provide insights into the direction and magnitude of the relationship between predictors and 'Price'.

After creating model 4, a Tornado chart was generated through Matplotlib to illustrate the influence of each coefficient on the house price. The chart reveals that an increase in the value of the variable 'grade_12 Luxury' has the most substantial positive effect on the price, indicating that houses with this grade experience a considerable price increase. Conversely, the presence of 'grade_5 Fair' has the most pronounced negative impact on the price, suggesting that houses with this grade exhibit a substantial decrease in value. 
![Screen Shot 2024-02-13 at 3 39 17 PM](https://github.com/jguzzo522/project2house/assets/75549456/ed1d9dfb-7b36-4b1c-9682-9d1f72da0279)


## Testing the Accuracy of the Regression Model
### Mean Absoulte Error (MAE)
In order to analyze how well this predicted actual values, the MAE was calculated. This Model had an MAE of 266,610.52. This number indicates that the average absoulte difference between the predicted house prices and the actual house prices is approximately $266,610.52.
 ### Root Mean Squared Error for Residual (RMSE)
 In this project RMSE was used as a metric to asses the goodness of fit of the model by examining the errors of residuals. Residuals are the diffrences between observed values and perdicted values of the model. The RMSE for this model was 342,533.59. This indicates that the average difference between the observed values and the predicted values of the second model is approximately $342,533.59.


## Testing the Accuracy of the Regression Model


## Homoscedasticity Testing
To assess homoscedasticity in the model, a Q-Q plot was generated using Seaborn and Matplotlib libraries. The plot, with the blue line representing model residuals and the red line indicating the expected normal distribution, closely follows the red line across the range, suggesting the residuals are normally distributed. This confirms homoscedasticity, ensuring the model's reliability. Violating homoscedasticity can lead to biased parameter estimates, making this evaluation crucial for accurate predictions. The confirmation of homoscedasticity enhances the credibility of the model's predictions and the validity of statistical inferences.
![Screen Shot 2024-02-13 at 8 56 28 PM](https://github.com/jguzzo522/project2house/assets/75549456/f4bd091e-ac6e-4b12-a91c-9e6001061709)
