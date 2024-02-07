# Increasing Property Value for Homeowners

## Goal
This project is aimed at increasing property value for homeowners for the purpose of resale value. The measurement used to determine if property value was increased, was price. The data indicates that house grade, and the number of bathrooms are metrics that can be used to increase property value. 

## Data
This project used data from a data set called ‘kc_house_data’. PANDAS was used to import this dataset into Jupyter notebook. In this dataset there were twenty three columns. The information in these columns are provided below.

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

This data was analyzed, modeled, manipulated, computed, visualized, and plotted using many different library packages in python such as 'Statsmodels', 'PANDAS', 'NUMPY', 'OS', 'MATPLOTLIB', 'SEABORN', ‘SKLEARN, 'SPICY' and 'ARIMA'.

## Cleaning the Data
In this dataset there were a few columns that had duplicate values, or missing values. In order to properly analyze this dataset these rows were removed from the original dataset. Pre-cleaned data had 30,155 rows, after removing the missing or duplicate values, the dataset had 30,110 rows remaining. 

### Creating Dummy Variables for Categorical Data
In this project, several categorical variables such as 'condition', 'heat_source', 'renovation_status', 'grade', 'nuisance', and 'sewer_system' were present in the dataset. Statistical models typically require numerical input for interpretation and analysis. Therefore, in order to incorporate these categorical variables into the modeling process effectively, dummy variables were created using PANDAS. 

Dummy variables or binary variables were created for each of the categorical variables. These converted variables allows for statistical models to process the data appropriately, and allows for the user to make interpretation of the data's effect on the price of the home. 
