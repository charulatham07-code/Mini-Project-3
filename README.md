NutriClass: Food Classification Using Nutritional Data
----------------------------------------------------------------------------------
Project Overview
---------------------------------------------------------------------------------

NutriClass is a Machine Learning-based Food Classification System that predicts food categories using nutritional attributes such as calories, protein, fat, carbohydrates, sugar, fiber, sodium, cholesterol, glycemic index, water content, and serving size.

The objective of this project is to analyze nutritional information and classify food items into predefined food categories using multiple machine learning algorithms. Various classification models were implemented and compared to identify the best-performing approach.

----------------------------------------------------------------------------------
Problem Statement
----------------------------------------------------------------------------------

Food products contain unique nutritional characteristics that can be used to identify their category. Manually classifying food items based on nutritional values can be difficult and time-consuming.

This project aims to automate food classification using machine learning techniques and evaluate the effectiveness of different classification algorithms.

-----------------------------------------------------------------------------------
Dataset Information
-----------------------------------------------------------------------------------

Dataset Name

Synthetic Food Dataset (Imbalanced)

Total Records
31,325 food samples
Features
Feature	Description
Calories	Energy content of food
Protein	Protein content
Fat	Fat content
Carbohydrates	Carbohydrate content
Sugar	Sugar content
Fiber	Dietary fiber
Sodium	Sodium content
Cholesterol	Cholesterol content
Glycemic_Index	Glycemic index
Water_Content	Water percentage
Serving_Size	Serving size
Meal_Type	Breakfast, Lunch, Dinner, Snack
Preparation_Method	Raw, Fried, Grilled, Baked
Is_Vegan	Vegan indicator
Is_Gluten_Free	Gluten-free indicator
Food_Name	Target Food Category

----------------------------------------------------------------------------------
Data Preprocessing
-----------------------------------------------------------------------------------

1. Missing Value Handling

Missing values were removed using:

df.dropna()

Result:

Final Records: 31,325

2. Outlier Treatment

Outliers were handled using the Interquartile Range (IQR) method.

Formula:

Lower Bound = Q1 − 1.5 × IQR

Upper Bound = Q3 + 1.5 × IQR

Instead of removing records, extreme values were capped within acceptable ranges.

Benefits:

Preserves dataset size
Reduces impact of extreme observations
Improves model stability

3. Encoding Categorical Features
Label Encoding

Applied on:

Is_Vegan
Is_Gluten_Free
Food_Name (Target Variable)
One-Hot Encoding

Applied on:

Meal_Type
Preparation_Method

4. Feature Scaling

StandardScaler was used for:

Logistic Regression
KNN
SVM
PCA

Formula:

z = (x − mean) / standard deviation
Principal Component Analysis (PCA)

PCA was applied to reduce dimensionality.

Before PCA
21 Features
After PCA
14 Principal Components
Variance Retained
97%

Purpose:

Reduce dimensionality
Remove redundant information
Improve computational efficiency

-----------------------------------------------------------------------------------------
Machine Learning Models
----------------------------------------------------------------------------------------

A total of 7 machine learning models were implemented.

1. Model 1: Logistic Regression
Why Logistic Regression?
Simple and efficient classifier
Suitable for multi-class classification
Works well on linearly separable data
Results
Metric	Value
Train Accuracy	99.48%
Test Accuracy	99.49%
Insights
Highest accuracy among all models.
Minimal difference between train and test accuracy.
Excellent generalization capability.
Nutritional features are highly separable.
Conclusion

Logistic Regression emerged as the best-performing model despite being the simplest algorithm.

2. Model 1A: Logistic Regression with PCA
Results
Metric	Value
Train Accuracy	99.15%
Test Accuracy	99.03%
Insights
PCA reduced dimensions from 21 to 14.
Retained 97% variance.
Slight drop in performance due to information loss.
Conclusion

PCA reduced feature dimensionality while maintaining strong classification performance.

3. Model 2: Decision Tree
Why Decision Tree?
Easy to interpret
Captures non-linear relationships
Provides visual decision-making process
Hyperparameter Tuning
max_depth = 10

Selected using GridSearchCV.

Results
Metric	Value
Test Accuracy	~99%
Insights
Highly interpretable.
Tree depth optimization improved generalization.
Minor class confusion observed.
Conclusion

Decision Tree achieved excellent performance while maintaining interpretability.

4. Model 3: K-Nearest Neighbors (KNN) with PCA
Why KNN?
Instance-based learning algorithm
Classifies samples based on neighboring observations
Parameters
n_neighbors = 5
Metric = Euclidean Distance
Results
Metric	Value
Train Accuracy	99.07%
Test Accuracy	98.63%
Insights
Lowest accuracy among all models.
Sensitive to distance calculations.
Performance improved with PCA.
Conclusion

KNN performed well but was less effective than tree-based and linear models.

5. Model 4: Random Forest
Why Random Forest?
Ensemble learning algorithm
Reduces overfitting
Improves prediction stability
Results
Metric	Value
Train Accuracy	99.83%
Test Accuracy	99.44%
Insights
Strong generalization performance.
Feature importance analysis identified influential nutritional attributes.
Robust against overfitting.
Conclusion

Random Forest provided highly accurate and stable predictions.

6. Model 5: Gradient Boosting
Why Gradient Boosting?
Sequential learning algorithm
Each tree corrects errors from previous trees
Results
Metric	Value
Train Accuracy	99.80%
Test Accuracy	99.43%
Insights
Captured complex relationships effectively.
Very high precision and recall scores.
Few misclassifications.
Conclusion

Gradient Boosting demonstrated strong predictive capability and excellent classification performance.

7. Model 6: Support Vector Machine (SVM)
Why SVM?
Maximizes separation between classes
Effective in high-dimensional spaces
Parameters
C = 5
Results
Metric	Value
Train Accuracy	99.66%
Test Accuracy	99.43%
Insights
Excellent class separation.
High precision and recall.
Strong generalization performance.
Conclusion

SVM successfully identified optimal decision boundaries between food categories.

8. Model 7: XGBoost
Why XGBoost?
Advanced boosting algorithm
Handles complex patterns efficiently
Built-in regularization
Results
Metric	Value
Train Accuracy	99.83%
Test Accuracy	99.41%
Insights
Minimal overfitting.
High classification performance.
Effectively handled class imbalance.
Conclusion

XGBoost delivered near-perfect classification performance by learning complex nutritional relationships.

---------------------------------------------------------------------------------------
Model Comparison
--------------------------------------------------------------------------------------

Model	                Train Accuracy	        Test Accuracy
Logistic Regression	        99.48%	                99.49%
Logistic Regression + PCA	99.15%	                99.03%
Decision Tree	            ~99%	                 ~99%
KNN + PCA	                99.07%	                98.63%
Random Forest	            99.83%	                99.44%
Gradient Boosting	        99.80%	                99.43%
SVM	                        99.66%	                99.43%
XGBoost                 	99.83%	                99.41%

-----------------------------------------------------------------------------------
Best Model
----------------------------------------------------------------------------------
Logistic Regression
Reason
Highest Test Accuracy: 99.49%
Lowest Complexity
Fast Training
Excellent Generalization

Despite using advanced ensemble methods, Logistic Regression slightly outperformed all other models, indicating that food classes are highly separable based on nutritional attributes.


--------------------------------------------------------------------------------------
Technologies Used
--------------------------------------------------------------------------------------

Python
Libraries
Pandas
NumPy
Matplotlib
Seaborn
Scikit-Learn
XGBoost
Machine Learning Techniques
Data Cleaning
Outlier Treatment
Feature Encoding
Feature Scaling
Principal Component Analysis (PCA)
Classification Algorithms
Hyperparameter Tuning
Cross Validation

---------------------------------------------------------------------------------
Future Enhancements
---------------------------------------------------------------------------------
Deploy using Streamlit
Add real-time food prediction interface
Integrate nutritional recommendation system
Use deep learning approaches
Expand dataset with real-world food data

----------------------------------------------------------------------------------
Conclusion
---------------------------------------------------------------------------------

NutriClass successfully demonstrated the effectiveness of machine learning in food classification using nutritional attributes. Seven classification algorithms were evaluated, and all achieved excellent performance with accuracy above 98%. Logistic Regression achieved the highest test accuracy of 99.49%, making it the best-performing model for this dataset. The results confirm that nutritional information is highly effective for accurately identifying and classifying food categories.