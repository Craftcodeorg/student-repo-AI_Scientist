### Assignment: Design a Neural Network to Classify Handwritten Digits

---

#### Problem Statement:

In this assignment, you will apply concepts from the lecture on supervised learning to design and implement a neural network capable of classifying handwritten digits from the MNIST dataset. This task reflects a common real-world application in academic research and development, where machine learning models are used to interpret and classify visual data. Your goal is to build a neural network model that can accurately predict the digit represented by an input image.

#### Starter Code:

Below is the starter code framework to help you get started. This code sets up the environment and provides a basic structure for loading the MNIST dataset and building a simple neural network using TensorFlow and Keras. You will need to expand upon this code to complete the assignment.

```python
import tensorflow as tf
from tensorflow.keras import layers, models
from tensorflow.keras.datasets import mnist
import numpy as np

# Load the MNIST dataset
(train_images, train_labels), (test_images, test_labels) = mnist.load_data()

# Normalize the images
train_images = train_images / 255.0
test_images = test_images / 255.0

# Define the model architecture
def create_model():
    model = models.Sequential([
        layers.Flatten(input_shape=(28, 28)),
        # Add layers here
        layers.Dense(10, activation='softmax')
    ])
    return model

# Compile the model
model = create_model()
model.compile(optimizer='adam',
              loss='sparse_categorical_crossentropy',
              metrics=['accuracy'])

# Train the model (to be completed by student)
# model.fit(...)

# Evaluate the model (to be completed by student)
# test_loss, test_acc = model.evaluate(...)

# Print test accuracy (to be completed by student)
```

#### Detailed Instructions:

1. **Model Architecture**:
   - Step 1: Add two hidden layers with 128 and 64 neurons respectively, using the ReLU activation function.
   - Step 2: Ensure the output layer has 10 neurons with a softmax activation function to classify the digits 0-9.

2. **Model Compilation**:
   - Use 'adam' as the optimizer and 'sparse_categorical_crossentropy' as the loss function.
   - Track accuracy as a metric during training.

3. **Training**:
   - Train your model using `model.fit()` on the training data for at least 5 epochs.
   - Use a batch size of 32.

4. **Evaluation**:
   - Evaluate your model's performance on the test set using `model.evaluate()`.
   - Print out the test accuracy.

5. **Enhancements**:
   - Implement data augmentation techniques to improve model generalization.
   - Consider adding dropout layers to prevent overfitting.

#### Criteria for Success and Evaluation:

- **Model Performance**:
  - The neural network should achieve at least 95% accuracy on the test set.

- **Code Quality**:
  - Code should be clean, well-documented, and adhere to best practices.
  - Use meaningful variable names and include comments explaining each major step.

- **Output and Reporting**:
  - Clearly print the test accuracy after evaluation.
  - Provide insights into any challenges faced during model training and how you addressed them.

This assignment will help reinforce your understanding of supervised learning and neural networks, providing practical experience in implementing a classification task using real-world data.