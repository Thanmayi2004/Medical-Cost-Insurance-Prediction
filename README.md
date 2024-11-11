# Medical-Cost-Insurance-Prediction
Medical insurance costs are influenced by various factors, including age, BMI, smoking status, and region. This project aims to build a predictive model to estimate individual insurance costs based on these factors, providing insights into which features impact the cost the most.

## Pre-Processing:
- **Encoding Categorical Variables:** The variables sex, smoker, and region were one-hot encoded to transform them into numerical formats suitable for machine learning models.
- **Data Splitting:** The data was split into training and testing sets to evaluate model performance on unseen data.

# Exploratory Data Analysis (EDA)
Conducted to identify key patterns and relationships in the data:

- **Correlation Heatmap:** This visualized correlations between variables, highlighting a strong positive correlation between smoker_yes and charges, indicating that smoking significantly increases insurance costs.
- **Age Distribution:** The histogram of ages showed that the dataset spans a diverse range of ages, helping ensure our model learns from a wide demographic.
- **Charges Distribution:** Charges were right-skewed, suggesting that a small number of individuals incur very high insurance costs.

#  Feature Engineering
Here, feature engineering was applied in the following ways:

- **Adding Interaction Terms:** A new feature, age_bmi, was created by multiplying age and BMI. This interaction term helps capture any combined effect of age and BMI on insurance costs, adding richer information to the dataset.
- **Polynomial Features and Scaling:** A polynomial transformation of degree 2 was applied to include squared terms and interactions, capturing non-linear relationships. This was followed by feature scaling, which standardizes the values across features for consistency, making them easier for models to interpret.


# Model Training and Evaluation

Models Used:
    -  Linear Regression 
    -  Ridge Regression
    -  Random Forest Regressor
    -  XGBoost Regressor
    
Evaluation Metrics Used:
    - **Root Mean Squared Error (RMSE):** Measures average error, with larger errors having a bigger impact.
    - **Mean Absolute Error (MAE):** Shows the average size of the errors, treating all errors equally.
    - **Mean Absolute Percentage Error (MAPE):** Shows errors as a percentage, making it easy to see how big the errors are relative to the actual values.


  Each model’s performance was measured, with the Random Forest model achieving the lowest RMSE and MAE, making it the best-performing model for our data.

# Feature Importance Analysis
In this analysis, we used a Random Forest model (Best-performing model) with 100 decision trees to identify the most influential features affecting the target variable. Random Forests are useful because they combine predictions from multiple independent trees, leading to more accurate and stable results. The "100 trees" in the model mean that we create 100 unique trees, each learning from a different subset of the data. 
The graph shows the relative importance of various features in the model. Higher importance values mean that a feature significantly impacts predictions, while lower values indicate less influence. 












- Key features listed at the top, like bmi, smoker_yes, and interactions such as smoker_yes age_bmi, were found to be highly influential. 
- The model also identified interaction terms like age_bmi (created by multiplying age and BMI) and polynomial features (e.g., age^2), which capture non-linear relationships.
- Each feature’s importance score in the bar plot reflects how much it contributes to accurate predictions. Features with higher bars are more impactful, while features with lower bars have less predictive power.


# Learning Curve Analysis
The learning curve is a graphical representation that helps us understand how well our model is learning from the training data. In our analysis, we utilized the plot_learning_curve function with a Random Forest model (best_rf).

Here are the key aspects :
- Cross-Validation (cv=5):
We specified cv=5, meaning we used 5-fold cross-validation. This technique splits the training data into five parts, training the model in four parts and validating it in the remaining part. This process is repeated five times, allowing us to assess the model’s performance more robustly as we can see all the five parts used a the testing part
- Training Sizes (10% to 100%):
The train_sizes parameter is set to span from 10% to 100% of the training data. This means we evaluated the model's performance as we gradually increased the amount of training data, helping us understand how additional data impacts learning.



**Error Metrics:**
We calculate two types of errors:
- Training Error: How well the model performs on the training data.
- Cross-Validation Error: How well the model performs on unseen data during validation.
These errors are plotted against the training set sizes, with RMSE (Root Mean Squared Error) used as the performance metric.

**Interpreting the Curves:**
- The blue curve represents training error, while the red curve indicates cross-validation error.
- A significant gap between these two curves may indicate that the model is overfitting, capturing noise in the training data rather than generalizable patterns.
- it’s important to consider other factors, such as model complexity, data quality, and variability, before drawing a definitive conclusion.

# Residual Analysis
Residual analysis was conducted to examine the quality of the predictions in which I plotted two graphs to understand it further. 

- Residual Distribution: The graph illustrates the distribution of residuals (the differences between actual and predicted values) from the Random Forest model's predictions. Overall, the distribution of residuals shows that the model has captured the trends in the data effectively, as evidenced by the high concentration of residuals around zero. This suggests that the Random Forest model is performing well, with a balanced mix of small underestimations and overestimations.


- Residuals vs Fitted Values (Predicted values): The scatter plot visualizing the relationship between residuals and fitted (Predicted) values reveals important insights into the model's performance. The red dashed line at y = 0 serves as a reference for accurate predictions.

The categorization highlights that the majority of the residuals fall into the "Far Below 0" and "Close to 0" categories, suggesting that the model primarily underestimates target values, with a substantial number of predictions being quite close to the actual values.The scatter plot of residuals against fitted values illustrates these findings, with points colored according to their categories. The plot shows a clustering of points below the line, which further confirms the model's tendency to underestimate the target values.










# Conclusion
This analysis has successfully demonstrated how various machine learning models can predict insurance costs based on demographic and health factors. 
Key takeaways include:
Best Model: Among the models evaluated, the Random Forest algorithm provided the most accurate predictions, achieving the lowest Root Mean Square Error (RMSE) and Mean Absolute Error (MAE). This highlights its effectiveness in capturing the complexities of the dataset.
Key Predictors: Age, Body Mass Index (BMI), and smoking status emerged as the most significant predictors of insurance costs. These findings align with established domain knowledge, reinforcing the importance of these factors in assessing risk.



