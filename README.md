# Increasing Property Value for Homeowners

## Goal
This project is aimed at increasing property value for homeowners for the purpose of resale value. The measurement used to determine if property value was increased, was price. The data indicates that house grade, and the number of bathrooms are metrics that can be used to increase property value. 

## Data
This project used data from a data set called ‘kc_house_data’. Pandas was used to import this dataset into Jupyter notebook. In this dataset there were twenty three columns. The information in these columns are provided below.

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

This data was analyzed, modeled, manipulated, computed, visualized, and plotted using many different library packages in python such as 'Statsmodels', 'Pandas', 'Numpy', 'OS', 'Matplotlib', 'Seaborn', ‘Sklearn, 'Spicy' and 'Arima'.

## Cleaning the Data
In this dataset there were a few columns that had duplicate values, or missing values. In order to properly analyze this dataset these rows were removed from the original dataset. Pre-cleaned data had 30,155 rows, after removing the missing or duplicate values, the dataset had 30,110 rows remaining. 

<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
</head>
<body>

<h2>Creating Dummy Variables for Categorical Data</h1>

In this project, several categorical variables such as 'condition', 'heat_source', 'renovation_status', 'grade', 'nuisance', and 'sewer_system' were present in the dataset. Statistical models typically require numerical input for interpretation and analysis. Therefore, in order to incorporate these categorical variables into the modeling process effectively, dummy variables were created using the Pandas library. 

Dummy variables or binary variables were created for each of the categorical variables. These converted variables allows for statistical models to process the data appropriately, and allows for the user to make interpretation of the data's effect on the price of the home. 

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
    <tr>
        <td>renovation_status_No Renovation</td>
        <td>Dummy variable indicating if the house has not been renovated</td>
    </tr>
    <tr>
        <td>renovation_status_Renovation</td>
        <td>Dummy variable indicating if the house has been renovated</td>
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
    <tr>
        <td>nuisance_NO</td>
        <td>Dummy variable indicating if the house has no recorded nuisances</td>
    </tr>
    <tr>
        <td>nuisance_YES</td>
        <td>Dummy variable indicating if the house has recorded nuisances</td>
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

</body>
</html>

## Search and Removal of Outliers

Utilizing Pandas, descriptive statistics were generated for each numeric variable to gain insights into their distributions and identify outliers. Based on these statistics, reasonable parameters were established, and outliers were subsequently removed from the dataset. Visualization of key statistical parameters such as the mean, standard deviation, and interquartile range was achieved using the Matplotlib library. This comprehensive approach ensured a thorough investigation of the data and facilitated informed decision-making in outlier handling. The below is an example of a visualiztion used to set outlier parameters for 'sqft_above'. Using the graph, as well as the discriptive statistics, the lower limit was set to 800 Sqft, and the upper limit was set to 3500 Sqft. Any data points falling outside of this range were determined to be outliers. 

![Screen Shot 2024-02-07 at 3 06 03 PM](https://github.com/jguzzo522/project2house/assets/75549456/1ae0140f-aecd-49d4-9651-2554c9d68ea7)

plt.legend()
plt.xticks(rotation=45, ha='right')  # Rotate x-axis labels for better readability
tick_positions = [0, 1000, 2000, 3000, 4000, 5000, 6000, 7000, 8000]
plt.xticks(tick_positions, rotation=45, ha='right')
plt.show()

## Removal of Additional Columns

This project was focused on increasing property value for homeowners though factors that homeowners could control. Consequently there were columns in the dataset such as Latitude, longitude, date, year built, year renovated, greenbelt, view, and waterfront, that were unrelated to this objective and therefore removed. 

## First Model Created Using StatsModels

Utilizing StatsModels, a Multiple Linear Regression model was constructed to explore the relationship between various predictor variables and the target variable, which was set to Price. Multiple Linear Regression is a statistical technique used to analyze the relationship between multiple independent variables and a single dependent variable.

The initial model accounted for approximately 39% of the variance in Price, suggesting a moderate level of explanatory power. There were many p-values associated with the coefficients that were statistically significant predictors (p < 0.05), indicating variables that have a significant effect on Price.

The coefficients in the model represent the estimated change in Price for a one-unit change in the respective predictor variable. Interpretation of these coefficients provides insights into the direction and magnitude of the relationship between predictors and Price.

After creating the initial model, a Tornado chart was generated to illustrate the influence of each coefficient on the house price. The chart reveals that an increase in the value of the variable 'grade_11 Excellent' has the most substantial positive effect on the price, indicating that houses with this grade experience a considerable price increase. Conversely, the presence of 'grade_4 Low' has the most pronounced negative impact on the price, suggesting that houses with this grade exhibit a substantial decrease in value. This visual representation underscores the importance of certain factors in determining house prices and provides valuable insights for homeowners.
![Screen Shot 2024-02-07 at 3 34 10 PM](https://github.com/jguzzo522/project2house/assets/75549456/97663077-fcfc-4f8a-92a0-a591525329f2)
