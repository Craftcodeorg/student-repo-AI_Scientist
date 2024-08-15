### Assignment: Simulation of an Autonomous Vehicle Navigating Urban Environments

---

#### Problem Statement:

In this assignment, you will develop a simulation that models an autonomous vehicle's decision-making process as it navigates through an urban environment. Using AI techniques discussed in the lecture, particularly focusing on perception systems and decision-making algorithms, your task is to implement a function that processes sensor data to determine the safest path for the vehicle. The simulation should account for obstacles, traffic signals, and pedestrian crossings, reflecting real-world challenges faced by autonomous vehicles.

---

#### Starter Code:

Below is the starter code for your simulation. You will build upon this framework to complete the task. Comments are included to guide you on where to implement your solutions.

```python
import numpy as np

# Starter code for simulating autonomous vehicle navigation

def simulate_autonomous_navigation(sensor_data, traffic_signals, pedestrian_crossings):
    """
    Simulate decision-making for an autonomous vehicle navigating an urban environment.
    
    Parameters:
    - sensor_data: List of floats representing distances to obstacles.
    - traffic_signals: List of strings representing the state of traffic lights ('red', 'yellow', 'green').
    - pedestrian_crossings: Boolean indicating if a pedestrian crossing is active.
    
    Returns:
    - navigation_decision: String indicating the vehicle's decision ('stop', 'proceed', 'slow down').
    """
    
    # Step 1: Process sensor data to identify obstacles
    obstacle_distance = np.min(sensor_data)
    
    # Step 2: Analyze traffic signals
    current_signal = traffic_signals[0]  # Simplified for demonstration
    
    # Step 3: Determine if pedestrian crossing is active
    is_crossing_active = pedestrian_crossings
    
    # Placeholder for navigation decision logic
    navigation_decision = "proceed"  # Default decision
    
    # TODO: Implement decision-making logic based on sensor data, traffic signals, and pedestrian crossings
    
    return navigation_decision

# Example input data
sensor_data = [5.0, 3.5, 7.2, 2.8]  # Distances to obstacles in meters
traffic_signals = ['green', 'red', 'yellow']  # Current state of traffic lights
pedestrian_crossings = False  # Pedestrian crossing status

# Test the function
decision = simulate_autonomous_navigation(sensor_data, traffic_signals, pedestrian_crossings)
print(f"Navigation Decision: {decision}")
```

---

#### Detailed Instructions:

- **Step 1**: Implement logic to determine if the vehicle should stop based on the closest obstacle distance. If the obstacle is within 2 meters, the vehicle should stop.

- **Step 2**: Enhance the function to consider traffic signals. If the current signal is 'red', the vehicle should stop. If 'yellow', it should slow down.

- **Step 3**: Integrate pedestrian crossing status into the decision-making process. If a crossing is active, the vehicle must stop regardless of other conditions.

- **Step 4**: Refine the output to provide detailed feedback, including the reason for each decision (e.g., "Stopped due to red light").

---

#### Criteria for Success and Evaluation:

- **Correctness**: The function accurately determines the navigation decision based on sensor data, traffic signals, and pedestrian crossings.
- **Code Quality**: The code is clean, well-documented, and follows best practices in Python programming.
- **Output Clarity**: The output is clear and provides detailed feedback on the decision-making process.
- **Realism**: The simulation reflects realistic scenarios encountered by autonomous vehicles in urban environments.

By completing this assignment, you will gain practical experience in applying AI techniques to solve real-world problems in autonomous vehicle navigation, reinforcing your understanding of AI integration and ethical considerations in technology development.