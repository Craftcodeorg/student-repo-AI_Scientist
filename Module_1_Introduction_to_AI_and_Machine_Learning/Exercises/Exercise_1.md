```markdown
# Module Title: Introduction to AI and Machine Learning

## Exercise 1: Create a Simple Classification Model using Scikit-learn

### Problem Statement

In this exercise, you will create a simple classification model using Scikit-learn to predict whether a given set of historical AI milestones can be classified as foundational or advanced. This exercise will reinforce your understanding of the historical evolution of AI technologies and their impact on modern research, particularly in areas like Quantum Machine Learning and neural networks.

**Scenario**: You are part of a research team analyzing the progression of AI technologies. Your task is to classify historical AI milestones into two categories: foundational (e.g., Turing Test, ELIZA) and advanced (e.g., Deep Blue, modern neural networks). This classification will help in understanding the trajectory of AI advancements and their implications for current research.

### Fill-in-the-Blank Starter Code

```python
from sklearn.linear_model import Perceptron
from sklearn.model_selection import train_test_split
from sklearn.metrics import accuracy_score

# Historical AI milestones data
# 0 represents foundational, 1 represents advanced
X = [[1950], [1966], [1997], [2012]]  # Years of key AI milestones
y = [0, 0, 1, 1]  # Classification labels

# Split data into training and testing sets
X_train, X_test, y_train, y_test = train_test_split(X, y, test_size=0.25, random_state=42)

# Initialize the Perceptron model
clf = Perceptron(tol=1e-3, random_state=0)

# Fit the model to the training data
clf.fit(X_train, y_train)

# Predict the classifications for the test data
y_pred = clf.predict(X_test)

# Calculate the accuracy of the model
accuracy = accuracy_score(y_test, y_pred)
print("Model Accuracy:", _______)
```

### Hints

1. **Data Splitting**: Ensure you understand how `train_test_split` works to divide your dataset into training and testing subsets.
2. **Perceptron Model**: Recall that a Perceptron is a type of linear classifier. Consider how it uses input features (in this case, years) to make predictions.
3. **Accuracy Calculation**: Use the `accuracy_score` function to compare predicted labels with true labels to assess model performance.

### Expected Outcome

Upon completing this exercise, you should be able to:

- Correctly fill in the blanks in the starter code to implement a simple classification model.
- Demonstrate an understanding of how historical AI milestones can be categorized using machine learning techniques.
- Achieve a model accuracy that reflects the ability to distinguish between foundational and advanced AI milestones.
- Write well-commented code that explains each step of the process, adhering to best practices in AI research and development.

### Integration

- Ensure your solution is structured with clear headings and sections.
- Comment your code thoroughly to explain your reasoning.
- Consider additional enhancements like error handling or exploring more complex models if time permits.

This exercise not only reinforces your understanding of AI's historical context but also aligns with your career goals by providing practical experience in applying machine learning techniques to real-world scenarios in academic research and development.
```