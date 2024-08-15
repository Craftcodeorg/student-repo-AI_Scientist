## Module Title: Introduction to AI and Machine Learning

### Exercise Requirements

#### Exercise 2: Build a Basic Neural Network for Image Recognition

1. **Problem Statement**:  
   You are tasked with designing a basic neural network for image recognition to classify handwritten digits from the MNIST dataset. This exercise will apply concepts from supervised learning, as discussed in the lecture. Your goal is to construct a neural network using TensorFlow or PyTorch that can accurately classify images into their respective digit categories (0-9). The network should be trained on labeled data, demonstrating an understanding of supervised learning principles.

   **Scenario**:  
   Imagine you are developing a prototype for an AI-driven educational tool that helps students learn mathematics by recognizing handwritten solutions and providing instant feedback. Your task is to build the foundational image recognition model that will identify digits written by students.

2. **Fill-in-the-Blank Starter Code**:  
   Below is a starter code snippet for building a basic neural network using TensorFlow. Fill in the blanks to complete the functionality:

   ```python
   import tensorflow as tf
   from tensorflow.keras import layers, models
   from tensorflow.keras.datasets import mnist

   # Load and preprocess the MNIST dataset
   (x_train, y_train), (x_test, y_test) = mnist.load_data()
   x_train, x_test = x_train / 255.0, x_test / 255.0

   # Define the model architecture
   model = models.Sequential([
       layers.Flatten(input_shape=(28, 28)),  # Flatten the input data
       layers.Dense(128, activation='relu'),  # First hidden layer with ReLU activation
       layers.Dropout(0.2),                   # Dropout layer for regularization
       layers.Dense(10, activation='softmax') # Output layer with softmax activation
   ])

   # Compile the model with appropriate loss function and optimizer
   model.compile(optimizer='adam',
                 loss='sparse_categorical_crossentropy',
                 metrics=['accuracy'])

   # Train the model on the training data
   model.fit(x_train, y_train, epochs=5)

   # Evaluate the model on the test data
   test_loss, test_acc = model.evaluate(x_test, y_test)
   print(f'Test accuracy: {test_acc}')
   ```

3. **Hints**:
   - **Hint 1**: Remember that supervised learning involves training your model on labeled data. Ensure your dataset is properly labeled and preprocessed before feeding it into the model.
   - **Hint 2**: The `Flatten` layer transforms the 2D image data into a 1D array, which is necessary for feeding into dense layers.
   - **Hint 3**: Use `softmax` activation in the output layer to get probability distributions over multiple classes.
   - **Hint 4**: Consider adding dropout layers to prevent overfitting, especially when working with small datasets.

4. **Expected Outcome**:  
   By completing this exercise, you will have implemented a basic neural network capable of classifying images of handwritten digits with reasonable accuracy. The solution should demonstrate proficiency in applying supervised learning techniques and neural network architecture design principles. Ensure your final code includes error handling and comments explaining each step.

### Integration

- **Structure**: Ensure each section of the exercise is clearly delineated with headings such as "Problem Statement," "Starter Code," "Hints," and "Expected Outcome."
- **Resources**: Provide links to download the MNIST dataset and relevant TensorFlow or PyTorch documentation.
- **Markdown Formatting**: Use markdown syntax for headings, code blocks, and lists to ensure clarity and readability when integrated into the learning platform.