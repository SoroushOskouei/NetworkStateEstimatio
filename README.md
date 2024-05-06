##Ensemble Kalman Filter for Network State Estimation

This repository contains Python code implementing an Ensemble Kalman Filter (EnKF) to estimate the state of a network over time. The code also includes functions for simulating observations with positions and visualizing the true and predicted states of the network.

**Problem Description**
The problem tackled by this code is the estimation of the state of a network represented as a graph. Each node in the graph corresponds to a system or entity whose state needs to be estimated. The state of each node consists of a value and a position in space (x, y coordinates). The challenge is to estimate these states accurately over time, given noisy observations of the states and the network's dynamics.

**Methodology**
The Ensemble Kalman Filter (EnKF) is employed to estimate the network state. EnKF is a variant of the Kalman Filter suitable for nonlinear systems and large-dimensional state spaces. It works by maintaining an ensemble of state estimates (particles) and updating them recursively using prediction and observation steps.

#The steps involved in the Ensemble Kalman Filter include:

Initialization: Initialize an ensemble of state estimates for each node in the network.
Prediction Step: Predict the next state of each ensemble member based on the system's dynamics. In this code, a simple random walk model is used to predict the value, and small random movements are added to update the position.
Observation Update Step: Update the ensemble members using observed data. The ensemble members are adjusted based on the observations, taking into account the uncertainty in both the predicted states and the observations.


**The main components of the code include:**

simulate_observations_with_position: Function to simulate observations with positions over time for a given network.
ensemble_kalman_filter_with_position: Function implementing the Ensemble Kalman Filter with position updates.
draw_network_with_positions: Utility function to visualize the true and predicted states of the network.
To use the code, follow these steps:
Define Network: Create a network (graph) representing the system or entities of interest.
Initialize States: Initialize the states (values and positions) for each node in the network.
Simulate Observations: Use simulate_observations_with_position to simulate observations over time.
Run Ensemble Kalman Filter: Apply ensemble_kalman_filter_with_position to estimate the network states based on the observations.
Visualize Results: Use draw_network_with_positions to visualize the true and predicted states of the network.

**Dependencies:**
NumPy
NetworkX
Matplotlib

**Example**
An example demonstrating the usage of the code is provided in the main script. It creates a random graph, simulates observations with positions, applies the Ensemble Kalman Filter, and visualizes the true and predicted states of the network.

![image](https://github.com/SoroushOskouei/NetworkStateEstimatio/assets/57323986/058fc9f7-2126-4d91-909e-bce16aa5ab6e)


