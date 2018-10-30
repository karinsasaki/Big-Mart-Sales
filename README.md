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

![alt text](https://github.com/karinsasaki/Big-Mart-Sales/blob/master/missing_values_item_weight1.png "Item_Weight")

![alt text](https://github.com/karinsasaki/Big-Mart-Sales/blob/master/missing_values_item_weight2.png "Item_Weight")

### Outlet_Size

![alt text](https://github.com/karinsasaki/Big-Mart-Sales/blob/master/missing_values_outlet_size1.png "Outlet_size")

![alt text](https://github.com/karinsasaki/Big-Mart-Sales/blob/master/missing_values_outlet_size2.png "Outlet_size")

![alt text](https://github.com/karinsasaki/Big-Mart-Sales/blob/master/missing_values_outlet_size3.png "Outlet_size")

![alt text](https://github.com/karinsasaki/Big-Mart-Sales/blob/master/missing_values_outlet_size4.png "Outlet_size")

### Item_Visibility

![alt text](https://github.com/karinsasaki/Big-Mart-Sales/blob/master/missing_values_item_visibility1.png "Item_Visibiity")

![alt text](https://github.com/karinsasaki/Big-Mart-Sales/blob/master/missing_values_item_visibility2.png "Item_Visibiity")

### Item_Fat_Content

![alt text](https://github.com/karinsasaki/Big-Mart-Sales/blob/master/item_fat_content.png "Item_Fat_Content")

## Feature engineering
- Combine Low Fat, low fat and LF to Low Fat and reg and Regular to Regular
- Convert the Outlet_Establishment_Years into how old the establishments are
- Create broader category for type of item
- Change value of the 'Item_Fat_Content' of the items that are non-consumables
- Make a new category for items that reflect their sales - very high, high, medium, low.
![alt text](https://github.com/karinsasaki/Big-Mart-Sales/blob/master/feature_engineering_feature_engineering.png "sales_category")
- Item_Number_Sales


## Preliminary Analysis

### Item_MRP

![alt text]( "")

### Item_Outlet_Sales

### Item_Number_Sales

![alt text](https://github.com/karinsasaki/Big-Mart-Sales/blob/master/analysis_item_number_sales1.png "")

![alt text](https://github.com/karinsasaki/Big-Mart-Sales/blob/master/analysis_item_number_sales2.png "")

![alt text](https://github.com/karinsasaki/Big-Mart-Sales/blob/master/analysis_item_number_sales3.png "")

### Item_outlet_sales and Item_MRP vs Item_Visibility

![alt text](https://github.com/karinsasaki/Big-Mart-Sales/blob/master/analysis_mrp_vs_number_sales.png "")

![alt text](https://github.com/karinsasaki/Big-Mart-Sales/blob/master/analysis_mrp_vs_outlet_sales.png "")

![alt text](https://github.com/karinsasaki/Big-Mart-Sales/blob/master/analysis_mrp_vs_outlet_type.png "")

![alt text](https://github.com/karinsasaki/Big-Mart-Sales/blob/master/analysis_visibility_vs_number_sales.png "")

![alt text](https://github.com/karinsasaki/Big-Mart-Sales/blob/master/analysis_visibility_vs_outlet_sales.png "")

### Categorical Data¶

![alt text](https://github.com/karinsasaki/Big-Mart-Sales/blob/master/analysis_categorical_data.png "")


## Preparation of data for model building
- Numerical and One-Hot Coding of Categorical Variables¶
- Standardisation of numerical data
- Separate train and test datasets 


## Models

## Baseline models
- Average sales
![alt text](https://github.com/karinsasaki/Big-Mart-Sales/blob/master/baseline_model_average.png "")
- Average Sales by Item_Type_Category
![alt text](https://github.com/karinsasaki/Big-Mart-Sales/blob/master/baseline_model_item_type_category1.png "")
![alt text](https://github.com/karinsasaki/Big-Mart-Sales/blob/master/baseline_model_item_type_category2.png "")
- Average Sales by Product_Type_Category in Particular Outlet_Type
![alt text](https://github.com/karinsasaki/Big-Mart-Sales/blob/master/baseline_model_item_type_category_outlet_type1.png "")
![alt text](https://github.com/karinsasaki/Big-Mart-Sales/blob/master/baseline_model_item_type_category_outlet_type2.png "")

## Feature selection with Recursive Feature Elimination and a RandomForestRegressor
![alt text](https://github.com/karinsasaki/Big-Mart-Sales/blob/master/most_relevant_features.png '')

## Models performance comparison

| Model             | Parameter Values | Validation dataset RMSE | CV score  |
| ----------------- |:----------------:|:-----------------------:| :--------:|
| Regression | - |  1143 | Mean - 1222 (+/- 142.71), Std - 71.35, Min - 1028, Max - 1312 |   
| Regression Ridge | alpha = 0.001 | 1143 | Mean - 1222 (+/- 143.25), Std - 71.63, Min - 1026, Max - 1313 | 
| Decision Tree Regressor | max_depth = 10.6, min_samples_leaf = 0.01| 1103 | Mean - 1180 (+/- 151.02), Std - 75.51 , Min - 975.5, Max - 1282 | 
| Neural Network | coming soon | coming soon | coming soon |


