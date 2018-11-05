# Big Mart Sales 

## References
[1] https://datahack.analyticsvidhya.com/contest/practice-problem-big-mart-sales-iii/

## Description and problem statement
The data scientists at BigMart have collected 2013 sales data for 1559 products across 10 stores in different cities. The aim is to build a predictive model and find out the sales of each product at a particular store. Using this model, BigMart can try to understand the properties of products and stores which play a key role in increasing sales.

## Data
Here are the features and their description.
![alt text](https://github.com/karinsasaki/Big-Mart-Sales/blob/master/features.png "Features")

## Imputing of missing values
Several of the features had missing values or values that needed to be corrected.

### Item_Weight

We impute the missing values of the Item_Weight by the average Item_Weight of each Item_Identifier. We can see that the values we have chosen to replace the missing weights are reasonable as the boxplot of the affected outlets now follows the same pattern as the other outlets.

![alt text](https://github.com/karinsasaki/Big-Mart-Sales/blob/master/missing_values_item_weight1.png "Item_Weight")

![alt text](https://github.com/karinsasaki/Big-Mart-Sales/blob/master/missing_values_item_weight2.png "Item_Weight")

### Outlet_Size

Grocery Stores and Supermarkets of Type 1 have missing values, as shown in the image below.

![alt text](https://github.com/karinsasaki/Big-Mart-Sales/blob/master/missing_values_outlet_size5.png "Outlet_size")

Grocery Stores All the non missing values in Grocery Stores are 'small'. So all the missing values in Outlet_Size of Grocery Stores are replaced with 'small'. 

All the other missing values in the rest of the data set are replaced with the mode values for each Store Type, from the pivot table below.

![alt text](https://github.com/karinsasaki/Big-Mart-Sales/blob/master/missing_values_outlet_size4.png "Outlet_size")


### Item_Visibility

The min value of Item_Visibility is 0, but this can not be as every item must have some visibility.

![alt text](https://github.com/karinsasaki/Big-Mart-Sales/blob/master/missing_values_item_visibility1.png "Item_Visibiity")

879 out of 14204 is a lot so we replace the 0 values for NAN values so the mean value is not affected.

We impute missing values for each Item_Type in each Outlet_Type, from the pivot table below.

![alt text](https://github.com/karinsasaki/Big-Mart-Sales/blob/master/missing_values_item_visibility2.png "Item_Visibiity")


### Item_Fat_Content

There are categories that can be conbined: Low Fat, low fat and LF are all Low Fat; reg and Regular are both Regular.

![alt text](https://github.com/karinsasaki/Big-Mart-Sales/blob/master/item_fat_content.png "Item_Fat_Content")


## Feature engineering

We did the following feature engineering:
- Converted the Outlet_Establishment_Years into how old the establishments are, feature Outlet_Age
![alt text](https://github.com/karinsasaki/Big-Mart-Sales/blob/master/feature_engineering_outlet_age.png "Outlet_Age")
- Created broader categories for type of item: Food, Drink and Non-Consumable. 
- Changed value of the 'Item_Fat_Content' of the items that are non-consumables, to Non-Edible
- Made a new category for items that reflect their sales: The Item_MRP illustrated in the image below clearly shows there are 4 different price categories. So we define them to be 'Low', 'Medium', 'High', 'Very High'.
![alt text](https://github.com/karinsasaki/Big-Mart-Sales/blob/master/feature_engineering_feature_engineering.png "sales_category")
- The Item_MRP does not change significantly accross the stores: 

![alt text](https://github.com/karinsasaki/Big-Mart-Sales/blob/master/analysis_mrp_outlet_type.png)

The Item_Outlet_Sales is the number of items sold times the Item_MRP. So we made a new variable with the number of items sold (by dividing the Item_Outlet_Sales by Item_MRP).

![alt text](https://github.com/karinsasaki/Big-Mart-Sales/blob/master/analysis_item_number_sales1.png)



## Preliminary Analysis

### Item_Number_Sales

![alt text](https://github.com/karinsasaki/Big-Mart-Sales/blob/master/analysis_item_number_sales1.png "")

![alt text](https://github.com/karinsasaki/Big-Mart-Sales/blob/master/analysis_item_number_sales2.png "")

![alt text](https://github.com/karinsasaki/Big-Mart-Sales/blob/master/analysis_item_number_sales3.png "")

### Item_outlet_sales and Item_MRP vs Item_Visibility

There is a positive correlation between Item_MRP and Item_Outlet_Sales and a negative correlation between Item_Outlet_Sales and visibility.

There is no correlation Item_MRP and Item_Number_Sales and there is a negative correlation between Item_Number_Sales and visibility.

![alt text](https://github.com/karinsasaki/Big-Mart-Sales/blob/master/analysis_mrp_vs_number_sales.png "")

![alt text](https://github.com/karinsasaki/Big-Mart-Sales/blob/master/analysis_mrp_vs_outlet_sales.png "")

![alt text](https://github.com/karinsasaki/Big-Mart-Sales/blob/master/analysis_visibility_vs_number_sales.png "")

![alt text](https://github.com/karinsasaki/Big-Mart-Sales/blob/master/analysis_visibility_vs_outlet_sales.png "")

Correlation between Item_MRP and Item_Outlet_Sales: 0.5675744466569193
Correlation between Item_MRP and Item_Number_Sales: 0.01114352701232483

Correlation between Item_Visibility and Item_Outlet_Sales: -0.14076174687662235
Correlation between Item_Visibility and Item_Number_Sales: -0.17440844918045084


## Preparation of data for model building
- Numerical and One-Hot Coding of Categorical Variables¶
- Standardisation of numerical data - More on this later
- Separate train and test datasets 


## Models

### Baseline models
- Average sales - Replace missing values by the average sales for all items. This is how the resulting data looks:

![alt text](https://github.com/karinsasaki/Big-Mart-Sales/blob/master/baseline_model_average.png "")

- Average Sales by Item_Type_Category - Replace missing values by the average sales per Item_Type_Category from this pivot table:

![alt text](https://github.com/karinsasaki/Big-Mart-Sales/blob/master/baseline_model_item_type_category2.png "")

This is how the resulting data looks:

![alt text](https://github.com/karinsasaki/Big-Mart-Sales/blob/master/baseline_model_item_type_category1.png "")

- Average Sales by Product_Type_Category in Particular Outlet_Type - Replace missing values by the average sales per Item_Type_Category in each Outlet_Type from this pivot table:

![alt text](https://github.com/karinsasaki/Big-Mart-Sales/blob/master/baseline_model_item_type_category_outlet_type2.png "")

This is how the resulting data looks:

![alt text](https://github.com/karinsasaki/Big-Mart-Sales/blob/master/baseline_model_item_type_category_outlet_type1.png "")

### Feature selection with Recursive Feature Elimination and a RandomForestRegressor

Hot-coding of the categorical variables leaves a total of 56 features in total (numerical and categorical). Using Recursive Feature Elimination (rfe) from the sklearn package we choose the top 16 predictive features to build the rest of the  predictive model, while avoiding over-fitting. These are the features chosen:

![alt text](https://github.com/karinsasaki/Big-Mart-Sales/blob/master/most_relevant_features.png '')

### Models performance comparison


| Model             | Parameter Values | Validation dataset RMSE | CV score  |
| ----------------- |:----------------:|:-----------------------:| :--------:|
| Average Sales | - | 1652 | - |
| Average Sales by Item_Type_Category | - | 1651 | - |
| Average Sales by Product_Type_Category in Particular Outlet_Type | - | 1417 | - |
| Regression | - |  1143 | Mean - 1222 (+/- 142.71), Std - 71.35, Min - 1028, Max - 1312 |   
| Regression Ridge | alpha = 0.001 | 1143 | Mean - 1222 (+/- 143.25), Std - 71.63, Min - 1026, Max - 1313 | 
| Decision Tree Regressor | max_depth = 10.6, min_samples_leaf = 0.01| 1103 | Mean - 1180 (+/- 151.02), Std - 75.51 , Min - 975.5, Max - 1282 | 
| Neural Network | layers = 3, nodes/layer = 100 | 1101 | - |


