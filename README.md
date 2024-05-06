# Network State Prediction Using Gaussian Processes

This repository contains a Python script that simulates and predicts the states of nodes in a randomly generated network graph. The nodes' states evolve over time based on trigonometric functions with randomly assigned coefficients, and the future state of these nodes is predicted using Gaussian Process regression.

## Methodology

### Graph Construction
A random graph is generated using the Erdős-Rényi model, where each pair of nodes has a fixed probability of being connected by an edge. This project uses a graph with 20 nodes and a connection probability of 0.15.

### State Simulation
Each node in the graph is assigned a set of coefficients for sine and cosine functions. These coefficients determine the state of the node at each time point based on the following formula:

$$ \[ S(t) = \text{clip}\left(\sum_{i=1}^5 a_i \cdot \sin(i \cdot t) + \sum_{i=1}^5 b_i \cdot \cos(i \cdot t) + 25, 0, 50\right) \]$$

where:
- $( a_i \)$ and $\( b_i \)$  are the coefficients for the sine and cosine terms, respectively.
- $( t \)$  is the current time point, linearly spaced between 0 and 10 over 101 points.
- $( S(t) \)$  is the computed state, clipped between 0 and 50 to ensure it remains within this range.

### Gaussian Process Regression
A Gaussian Process (GP) model is used to predict the state of each node at a future time point (t=101) based on its states from t=0 to t=100. The GP model employs a kernel composed of a Radial Basis Function (RBF) and a constant kernel, which are configured with specific length scales and variance bounds:

$$ \[ K(x, x') = \sigma^2 \exp\left(-\frac{(x - x')^2}{2l^2}\right) + c \]$$ 

where:
- $( \sigma \)$ and $( l \)$  are parameters of the RBF kernel controlling the variance and length scale, respectively.
- $( c \)$  is the constant term from the Constant Kernel.

The model is fitted for each node independently, using their respective time series data.

### Visualization
The network graph is visualized with nodes colored according to their true and predicted states at t=101. Two subplots are provided to compare the actual states and the Gaussian Process predictions side by side.

![image](https://github.com/SoroushOskouei/NetworkStateEstimation/assets/57323986/b919a994-c9e8-42a2-82a8-80620701f78b)

