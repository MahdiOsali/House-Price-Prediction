House Price Prediction in Tehran 🏠
This project uses linear regression to predict house prices in Tehran based on apartment features such as area, number of rooms, parking availability, warehouse availability, and address.
Dataset 📊
The dataset, sourced from "Apartments_information.csv", contains information about apartments in Tehran with the following columns:  

🏠 Area: Apartment area in square meters (initially string, converted to float).  
🛏️ Room: Number of rooms (integer).  
🚗 Parking: Availability of parking (True/False).  
📦 Warehouse: Availability of a warehouse (True/False).  
🛗 Elevator: Availability of an elevator (True/False).  
🏙️ Address: Apartment address (categorical, later encoded).  
💵 Price: Price in local currency (float).  
💲 Price(USD): Price in USD (float).

Initial size: 3479 rows; after preprocessing: 3452 rows.
Preprocessing ⚙️

Loaded the dataset from "Apartments_information.csv".  
Dropped rows with missing values (23 rows dropped initially, then 4 more after Area conversion).  
Converted Area from string to float, replacing commas with dots.  
Assumed log transformations for Area and Price (as Area_log and Price_log) to handle skewness.  
Applied target encoding to Address within cross-validation, using the mean Price_log per address from training data.

Model 🧠

Algorithm: Linear Regression (sklearn.linear_model.LinearRegression)  
Features:  
🛏️ Room  
📏 Area_log  
🚗 Parking  
📦 Warehouse  
🏙️ Address_encoded


Target: Price_log  
Evaluation: 5-fold cross-validation (KFold, shuffle=True, random_state=42)

Results 📈

R² Scores:  

Fold 1: 0.854  
Fold 2: 0.875  
Fold 3: 0.837  
Fold 4: 0.857  
Fold 5: 0.856  
Average R²: 0.856


MSE Scores:  

Fold 1: 0.164  
Fold 2: 0.142  
Fold 3: 0.183  
Fold 4: 0.172  
Fold 5: 0.169  
Average MSE: 0.166



Interpretation 💡

The model explains ~85.6% of the variance in Price_log (R² = 0.856), indicating a strong fit.  
The MSE of 0.166 on the log scale suggests reasonable prediction accuracy.  
A Pearson correlation of 0.81 between Area and Price highlights a strong positive relationship, visualized in the scatter plot below:

(Note: Save the scatter plot from the notebook and update the path.)
Usage 🚀
To run the code:  

Ensure the required libraries are installed (numpy, pandas, matplotlib, seaborn, sklearn).  
Place "Apartments_information.csv" in the working directory.  
Execute the Jupyter notebook (House_price_prediction.ipynb).

For the full code, refer to House_price_prediction.ipynb.
