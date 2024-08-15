### Assignment: Develop a Simple AI Model for Predicting Housing Prices

---

#### Problem Statement:

In the realm of Academic Research and Development, creating predictive models is a fundamental task. This assignment will focus on applying the concepts of machine learning and AI to develop a simple linear regression model that predicts housing prices based on historical data. This task will help you understand how AI can be used in real-world applications to make data-driven predictions, a crucial skill in AI research and development.

**Objective**: Utilize the principles of linear regression to predict housing prices using a dataset that includes features such as square footage, number of bedrooms, and location index.

---

#### Starter Code:

Below is the starter code to guide you in setting up the environment and beginning your implementation. You will build upon this framework to complete the assignment.

```python
# Starter code for developing a linear regression model for housing price prediction

import numpy as np
import pandas as pd
from sklearn.model_selection import train_test_split
from sklearn.linear_model import LinearRegression
from sklearn.metrics import mean_squared_error

# Load the dataset (you can replace this with your dataset)
data = pd.DataFrame({
    'SquareFootage': [1500, 2000, 2500, 1800, 2200],
    'Bedrooms': [3, 4, 4, 3, 5],
    'LocationIndex': [1, 2, 3, 2, 3],
    'Price': [300000, 400000, 500000, 350000, 450000]
})

# Step 1: Prepare the data
X = data[['SquareFootage', 'Bedrooms', 'LocationIndex']]
y = data['Price']

# Step 2: Split the data into training and testing sets
X_train, X_test, y_train, y_test = train_test_split(X, y, test_size=0.2, random_state=42)

# Step 3: Initialize the Linear Regression model
model = LinearRegression()

# Step 4: Train the model
model.fit(X_train, y_train)

# Step 5: Make predictions
predictions = model.predict(X_test)

# Step 6: Evaluate the model
mse = mean_squared_error(y_test, predictions)
print(f"Mean Squared Error: {mse}")

# Students will need to enhance this code by adding more features and evaluating different metrics.
```

---

#### Detailed Instructions:

**Step 1**: Enhance the dataset by adding more features that could influence housing prices such as 'YearBuilt', 'GarageSize', etc. Ensure that you preprocess the data appropriately.

**Step 2**: Modify the model to include these new features. Retrain the model and observe if there is an improvement in prediction accuracy.

**Step 3**: Implement additional evaluation metrics such as R-squared to assess the model's performance comprehensively.

**Step 4**: Improve the output by providing a detailed analysis of the model's predictions versus actual prices. Include visualizations like scatter plots to illustrate model performance.

---

#### Criteria for Success and Evaluation:

**Success Criteria**:
- The model should accurately predict housing prices based on the given features.
- The code should be clean, well-documented, and adhere to best practices in machine learning.
- The output should include a detailed evaluation of model performance with visual aids.

**Evaluation Rubric**:
- **Accuracy** (40%): The model's predictions are close to actual values.
- **Code Quality** (30%): Code is well-structured, readable, and follows Pythonic conventions.
- **Documentation** (15%): Clear comments and explanations are provided.
- **Output Presentation** (15%): Results are presented clearly with appropriate visualizations.

This assignment aims to reinforce your understanding of AI applications in predictive modeling within Academic Research and Development. By completing this task, you will gain practical experience in building and evaluating AI models using real-world data.