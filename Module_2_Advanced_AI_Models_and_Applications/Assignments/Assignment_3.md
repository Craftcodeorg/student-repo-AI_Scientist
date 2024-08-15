### Assignment 3: Design a Reinforcement Learning System for Autonomous Vehicle Navigation

---

#### Problem Statement:

In this assignment, you will create a reinforcement learning (RL) agent that learns to navigate an autonomous vehicle through a simulated environment. The goal is to apply the concepts of Deep Q-Networks (DQN) and policy gradient methods as discussed in the lecture to develop a system that can make intelligent driving decisions. This task is directly relevant to the field of Academic Research and Development, particularly in the area of AI in Autonomous Vehicles.

Your task is to enhance the starter code provided, which simulates a basic driving environment, by implementing a reinforcement learning algorithm that improves the vehicle's navigation strategy over time.

---

#### Starter Code:

Below is the starter code that sets up a basic simulation environment using OpenAI's Gym library. You will build upon this framework to implement the RL agent.

```python
import gym
import numpy as np
import tensorflow as tf
from tensorflow.keras import layers

# Create a custom environment for autonomous vehicle navigation
class AutonomousVehicleEnv(gym.Env):
    def __init__(self):
        super(AutonomousVehicleEnv, self).__init__()
        # Define action and observation space
        # Actions: [steer_left, steer_right, accelerate, brake]
        self.action_space = gym.spaces.Discrete(4)
        # Observations: [velocity, distance_to_object, lane_position]
        self.observation_space = gym.spaces.Box(low=np.array([0, 0, -1]), high=np.array([100, 100, 1]), dtype=np.float32)
        
    def reset(self):
        # Reset the state of the environment to an initial state
        self.state = np.array([0.0, 50.0, 0.0])  # Example initial state
        return self.state
    
    def step(self, action):
        # Implement the logic for taking an action
        velocity, distance_to_object, lane_position = self.state
        
        # Update state based on action taken
        if action == 0:  # steer_left
            lane_position -= 0.1
        elif action == 1:  # steer_right
            lane_position += 0.1
        elif action == 2:  # accelerate
            velocity += 1.0
        elif action == 3:  # brake
            velocity -= 1.0
        
        # Calculate reward (simplified for demonstration)
        reward = -abs(lane_position) - (1 if distance_to_object < 10 else 0)
        
        # Check if episode is done
        done = bool(distance_to_object < 5 or abs(lane_position) > 1)
        
        # Update state
        self.state = np.array([velocity, distance_to_object - velocity, lane_position])
        
        return self.state, reward, done, {}

# Initialize environment
env = AutonomousVehicleEnv()

# Placeholder for DQN or policy gradient implementation
def train_rl_agent(env):
    # Implement your RL algorithm here
    pass

# Main execution
if __name__ == "__main__":
    train_rl_agent(env)
```

---

#### Detailed Instructions:

**Step 1:** Implement a Deep Q-Network (DQN) within the `train_rl_agent` function.
- Define a neural network model using TensorFlow/Keras that approximates the Q-value function.
- Implement an experience replay mechanism to store and sample past experiences.
- Utilize the Bellman equation to update Q-values and train the network iteratively.

**Step 2:** Enhance the agent's decision-making using policy gradient methods.
- Modify the network architecture to output probabilities for actions instead of Q-values.
- Implement a policy gradient algorithm such as REINFORCE to optimize the policy directly.

**Step 3:** Test and evaluate the RL agent's performance.
- Run multiple episodes to train the agent and observe its learning curve.
- Adjust hyperparameters (e.g., learning rate, discount factor) to improve performance.

---

#### Criteria for Success and Evaluation:

**Success Criteria:**
- The RL agent successfully navigates through the environment with minimal lane deviations and collisions.
- The code is well-structured, documented, and follows best practices in RL implementation.
- The agent demonstrates improved navigation capabilities over time as evidenced by increased cumulative rewards.

**Evaluation Rubric:**
- **Accuracy (40%)**: Correct implementation of RL algorithms and successful navigation.
- **Code Quality (30%)**: Code readability, organization, and adherence to best practices.
- **Innovation (20%)**: Application of advanced techniques or improvements beyond basic requirements.
- **Documentation (10%)**: Clear explanation of code functionality and design decisions.

This assignment provides a practical coding task that reflects industry practices in autonomous vehicle research, reinforcing the concepts from the lecture and helping you build practical skills in AI model development.