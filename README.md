<img width="1919" height="760" alt="image" src="https://github.com/user-attachments/assets/3b676ecb-36f3-42fb-bef7-b9852dce3b6b" />

# Drone Path Optimisation Lab

A comprehensive simulation environment for testing and comparing autonomous drone navigation algorithms under real-world urban constraints and environmental uncertainty.

## Overview

The Drone Path Optimisation Lab is an interactive platform that explores how different pathfinding paradigms handle the complex challenge of urban drone navigation. Moving beyond clean, deterministic simulations, this lab introduces realistic constraints like wind drift, battery consumption, no-fly zones, and geofencing restrictions to evaluate which algorithms actually survive contact with reality.

## Why This Matters

Autonomous drone delivery sounds straightforward until you try to implement it. Unlike ground vehicles that stick to roads, drones operate in three dimensions while being constantly affected by wind, restricted by dynamic airspace regulations, and limited by battery constraints. This lab was built to answer a simple question: which navigation logic actually works when things get messy?

## Key Features

- **20×20 Grid Simulation**: Urban-inspired environment with obstacles and restricted zones
- **Environmental Uncertainty**: 80% action success rate simulating wind drift and sensor noise
- **Multi-Algorithm Comparison**: Test classical search (BFS, Dijkstra, A*) against probabilistic methods (MDP) and learning approaches (Q-Learning)
- **Real-Time Visualisation**: Watch algorithms think and adapt with adjustable playback speed (0.25x to 3.0x)
- **Live Analytics**: Event logging, reward tracking, and convergence visualization
- **Interactive Controls**: Speed slider, algorithm selection, and step-by-step execution

## Algorithms Implemented

### Deterministic Search Paradigms
- **Breadth-First Search (BFS)**: Explores all paths systematically but ignores costs
- **Dijkstra's Algorithm**: Cost-aware pathfinding that minimizes total weights
- **A* Search**: Heuristic-guided search using Manhattan distance for efficiency

### Markov Decision Process (MDP)
- **Value Iteration**: Computes optimal policies for every state using the Bellman equation
- Creates robust navigation that handles unexpected deviations
- Discount factor γ = 0.92 balances immediate costs with long-term rewards

### Reinforcement Learning
- **Q-Learning**: Model-free approach that learns through trial and error
- Epsilon-greedy exploration strategy
- Trains over 3,000 episodes to discover optimal behaviour

## Performance Highlights

| Algorithm | Path Cost | Nodes Expanded | Runtime (s) | Success Rate |
|-----------|-----------|----------------|-------------|--------------|
| BFS | 121 | 388 | 16.7 | 12% |
| A* | 34 | 199 | 10.8 | 15% |
| Value Iteration | 34 | N/A | 4.6 | 85% |
| Q-Learning | 34 | N/A | 2.2 | 98% |

**Key Finding**: Classical search algorithms like A* excel at speed but fail under uncertainty. Policy-based approaches (MDP, Q-Learning) sacrifice some computational efficiency for dramatically improved reliability in unpredictable environments.

## How It Works

### Reward System
- **Goal reached**: +100 points
- **Each move**: -1 point (battery cost)
- **No-fly zone**: -50 points (regulatory penalty)

### Environmental Model
The simulation includes stochastic transitions where commanded actions succeed 80% of the time, with 20% chance of drift to adjacent cells. This models real-world factors like wind gusts, GPS inaccuracy, and control imprecision.

### Visualization
- **Green tiles**: Current path or policy direction
- **Black tiles**: Physical obstacles (buildings)
- **Red tiles**: No-fly zones (restricted airspace)
- **Yellow tiles**: Nodes explored during search
- **Heatmap mode**: Value function visualization for MDP

## Getting Started

```bash
# Clone the repository
git clone https://github.com/DavidAkerele/KRR-Project-David-Akerele-Daniel-Emelike.git

# Navigate to project directory
cd KRR-Project-David-Akerele-Daniel-Emelike

# Open index.html in your browser
# No installation required - runs entirely client-side
```

## Usage

1. Select an algorithm from the navigation panel
2. Adjust the speed slider to control simulation playback
3. Click "Run" to start the simulation
4. Watch the analytics panel for real-time performance metrics
5. Compare different algorithms to see how they handle uncertainty

## Research Context

This project emerged from research into multi-paradigm optimization for autonomous systems. The findings demonstrate that:

- **Speed isn't everything**: A* finds paths 47% faster than Value Iteration but achieves only 15% success rate vs 85%
- **Brittleness is the enemy**: Deterministic paths collapse under uncertainty; policies provide resilience
- **Learning works**: Q-Learning achieves 98% success by discovering optimal strategies through experience
- **Discount factors matter**: γ values below 0.7 create overly risk-averse behaviour; 0.92 provides good balance

## Future Directions

- Spline-based trajectory smoothing for realistic flight paths
- Integration with actual drone flight controllers
- Multi-agent coordination and collision avoidance
- Dynamic obstacle and airspace updates
- Real-time weather integration

## Technical Stack

- Pure JavaScript for algorithm implementation
- HTML5 Canvas for visualization
- CSS Grid for responsive layout
- No external dependencies for core functionality

## Authors

**David Akerele** - Conceptualisation, Methodology, Software Development, Debugging, Writing

**Daniel Emelike** - Conceptualisation, Methodology, Software Development, Testing, Writing

School of Science & Engineering, Manchester Metropolitan University

## References

This project builds on foundational work in pathfinding (Hart et al., 1968), dynamic programming (Bellman, 1957), and reinforcement learning (Watkins & Dayan, 1992). For complete references, see the accompanying research paper.


## Acknowledgments

Special thanks to Manchester Metropolitan University for supporting this research into autonomous navigation systems.

---

*Built to bridge the gap between abstract equations and the practical reality of autonomous flight.*
