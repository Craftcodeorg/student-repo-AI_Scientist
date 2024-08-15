```markdown
## Exercise 3: Implement a Reinforcement Learning Algorithm in a Simulated Environment

### Problem Statement

In this exercise, you will implement a reinforcement learning algorithm to enable a robotic agent to navigate a dynamic environment. The objective is to apply the concepts discussed in the lecture on Reinforcement Learning in Robotics and Autonomous Systems. You will simulate a scenario where the agent must learn to navigate through a maze, avoiding obstacles and reaching a designated goal. This exercise will require you to integrate reinforcement learning principles with neural networks, similar to the techniques used in autonomous vehicles.

Your task is to:
- Develop a reinforcement learning model using Deep Q-Networks (DQN).
- Train the model in a simulated maze environment.
- Evaluate the agent's performance and optimize its policy for better navigation.

### Fill-in-the-Blank Starter Code

Below is the starter code for implementing the reinforcement learning algorithm. Fill in the blanks to complete the functionality. Comments and guidance are provided to assist you in integrating neural networks with reinforcement learning principles.

```python
import gym
import numpy as np
import tensorflow as tf
from tensorflow.keras.models import Sequential
from tensorflow.keras.layers import Dense
from collections import deque
import random

# Define the neural network model for the DQN
def build_model(state_size, action_size):
    model = Sequential()
    model.add(Dense(24, input_dim=state_size, activation='relu'))
    model.add(Dense(24, activation='relu'))
    model.add(Dense(action_size, activation='linear'))
    model.compile(loss='mse', optimizer=tf.keras.optimizers.Adam(lr=0.001))
    return model

# Initialize the environment
env = gym.make('CartPole-v1')
state_size = env.observation_space.shape[0]
action_size = env.action_space.n

# Initialize the DQN model
model = build_model(state_size, action_size)

# Define hyperparameters
gamma = 0.95  # Discount factor
epsilon = 1.0  # Exploration rate
epsilon_min = 0.01
epsilon_decay = 0.995
batch_size = 32
memory = deque(maxlen=2000)

# Function to choose action based on epsilon-greedy policy
def choose_action(state):
    if np.random.rand() <= epsilon:
        return random.randrange(action_size)
    act_values = model.predict(state)
    return np.argmax(act_values[0])

# Training loop
for e in range(1000):
    state = env.reset()
    state = np.reshape(state, [1, state_size])
    
    for time in range(500):
        # Uncomment to render the environment (optional)
        # env.render()
        
        # Choose action and take step
        action = _________(state)
        next_state, reward, done, _ = env.step(action)
        reward = reward if not done else -10
        next_state = np.reshape(next_state, [1, state_size])
        
        # Store experience in memory
        memory.append((state, action, reward, next_state, done))
        
        state = next_state
        
        if done:
            print(f"Episode: {e}/{1000}, Score: {time}, Epsilon: {epsilon:.2}")
            break
        
        if len(memory) > batch_size:
            minibatch = random.sample(memory, batch_size)
            for state, action, reward, next_state, done in minibatch:
                target = reward
                if not done:
                    target = (reward + gamma * np.amax(model.predict(next_state)[0]))
                target_f = model.predict(state)
                target_f[0][action] = target
                model.fit(state, target_f, epochs=1, verbose=0)
            
            if epsilon > epsilon_min:
                epsilon *= epsilon_decay

env.close()
```

### Hints

1. **Choosing Actions**: Remember that the `choose_action` function should implement an epsilon-greedy policy. This means balancing exploration and exploitation.

2. **Experience Replay**: Utilize experience replay by sampling random batches from memory to break correlation between consecutive experiences and stabilize training.

3. **Neural Network Training**: Ensure that your neural network is trained using the mean squared error loss function and an Adam optimizer with a small learning rate.

4. **Hyperparameters Tuning**: Pay attention to the hyperparameters like `gamma`, `epsilon`, and `batch_size`. Adjust them based on the agent's performance during training.

### Expected Outcome

By completing this exercise, you should be able to demonstrate an understanding of how reinforcement learning concepts can be applied to real-world scenarios involving robotics and autonomous systems. Your solution should include:
- A well-functioning DQN model that effectively learns to navigate the simulated environment.
- Proper implementation of the epsilon-greedy policy for action selection.
- Efficient use of experience replay to improve learning stability.
- Clear documentation and comments explaining each step of your code.

This exercise will help solidify your knowledge of reinforcement learning and prepare you for advanced AI research projects in Academic Research and Development.
```