# aiml-vehicles
Used vehicles Price data with features
Goal: What factors make a car more or less expensive (what customers value)? Provide recommendations to a car dealer.

Business Understanding:
We have historical data of used cars prices with many attributes such as car model, year, condition, cylinders, fuel type, odometer, and many others. Our task is to determine which features impact the price of a car most. For keeping the task manageable, we would limit identifying at most four features that impact the price the most.

Data Understanding:
Vehicles data frame has the target column, price, and 17 features columns, most of which are non-numeric. Some of the rows in the data are null for some columns. Some of columns provide very granular vehicle specific info. such as id, VIN, paint_color, which may not have much impact on the price. Some columns are geographic such as region and state, they may impact the price but only when you change to geographical nature. Finally, the data is Not time-series as no tamest p info. Is included, so stochastic models are ruled out.

Data Preparation:
Based on the data understanding, I only decided to keep ['price', 'year', 'manufacturer', 'condition', 'cylinders', 'odometer', 'type'] columns and drop all others. Further, I see 'manufacturer', 'cylinders', and  'type' as categorical data with large number of cardinal values, so decided to drop them as well to keep the model simple. After, I am left with price, year, condition and odometer and will be applying col_transformer to condition feature. Finally, I dropped rows with null values, and now left with 250,851 entries, which is still more than 50% of the original data.


Modeling:
I splitted the data using test_train_split function into 70% for training and 30% for validation (test). The I used OrdinalEncoder for the “condition” of the vehicles and applied make_column_transformer. I fixed the model using Pipeline and LinearRegression().

Evaluation:
I used the Pipeline to predict both for training and test data and finally plotted both the real data and predict values. The predicted results are similar, except for some outliers.

Deployment:
Based on the data analysis and modeling, a Linear Regression model can be used to determine the appropriate price. The features that impact the price of a used car the most are ‘year’, ‘odometer’ and ‘condition’ of the vehicle.
