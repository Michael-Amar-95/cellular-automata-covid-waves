# Cellular Automata – COVID-19 Waves Simulation

## Overview
This project implements a cellular automaton model that simulates the spread of COVID-19 in a population, with a focus on the emergence of epidemic waves (repeated rises and falls in infection levels over time).

The simulation demonstrates how local interactions, individual movement, and adaptive behavior can lead to complex global dynamics such as multiple infection waves.

---

## Model Description

### Environment
- A 2D cellular automaton grid of size **200 × 200**.
- **Toroidal (wrap-around)** boundary conditions.
- Each cell can contain **at most one individual**.

Cell states:
- `0` – Empty cell  
- `1` – Healthy individual  
- `5` – Infected individual  

---

### Population Initialization
- **N** individuals are randomly placed on the grid.
- An initial percentage **D%** of individuals are infected.
- A percentage **R%** are designated as fast-moving individuals.

---

## Movement Model

Each generation, every individual attempts to move according to its type:

### Regular Individuals
- Can move to one of the **8 neighboring cells** or stay in place.
- All 9 options have equal probability.

### Fast Individuals
- Can move up to **10 cells away** in a random direction.
- The candidate destination cells are generated accordingly.

### Collision Avoidance
To ensure that no two individuals occupy the same cell:
- Three candidate cells are randomly selected from the allowed movement range.
- If the chosen cell is occupied or identical to the current cell, the individual does not move.
- Otherwise, the move is executed.

Movement decisions are randomized using probabilistic selection.

---

## Infection Rules

Infection spreads locally through neighborhood interactions:

- If a healthy individual is located in one of the **8 neighboring cells** of an infected individual, infection may occur.
- Infection occurs with probability **P**.

### Adaptive Infection Probability
The infection probability dynamically changes according to the current infection level:
- If the percentage of infected individuals is **below threshold T** → infection probability is **P_high**
- If infection exceeds **T** → infection probability decreases to **P_low**

This models cautious population behavior when infection levels become high.

---

## Disease Progression
- An infected individual remains contagious for **X generations**.
- After recovery:
  - The individual becomes immune and cannot be reinfected.

Assumptions:
- No vaccination
- No virus variants
- Permanent immunity after recovery

---

## Parameters

| Parameter | Description |
|----------|-------------|
| N | Total number of individuals |
| D | Initial percentage of infected individuals |
| R | Percentage of fast-moving individuals |
| X | Recovery time (generations) |
| P_high | Infection probability when infection level is low |
| P_low | Infection probability when infection level is high |
| T | Infection percentage threshold that triggers behavioral adaptation |

---

## Program Flow

When the program starts, the user is prompted to:
1. Choose whether to display an **interactive visualization**.
2. Run the simulation with:
   - Default parameter values (preconfigured to produce epidemic waves), or
   - Custom user-defined parameters.

The interactive visualization shows:
- Real-time infection spread on the grid
- Number of infected individuals per generation

It is recommended to enable visualization to better understand the wave dynamics.

---

## Goal of the Experiment
The primary goal is to identify parameter combinations that generate **wave-like epidemic behavior**, defined as:
> At least three distinct cycles of rising and falling infection levels during the simulation.

---

## Observations and Insights

### Parameter Interdependence
Model parameters are interdependent; changing one parameter affects the influence of others.  
Therefore, experiments were conducted by fixing most parameters and varying one at a time to analyze its effect.

### Population Size
- Larger populations increase spatial density, leading to higher infection spread.
- In smaller populations, the percentage of fast movers has a stronger impact on dynamics.

### Initial Infection Rate & Recovery Time
These parameters significantly influence:
- Spread velocity of the disease
- Time until convergence (when most individuals are either recovered or healthy)

### Behavioral Adaptation Insight
A key insight from the model is the importance of adaptive population behavior:
- When infection probability is high but individuals become cautious once infection exceeds a threshold,
  the infection level remains relatively controlled.
- This mirrors real-world scenarios where behavioral changes reduce spread even when the disease is highly contagious.

---

## Visualization
The simulation includes an optional graphical interface that:
- Displays the automaton state in real time
- Differentiates clearly between healthy, infected, and recovered individuals
- Tracks infection counts across generations

---

## Technologies
- Cellular Automata
- Probabilistic Modeling
- Simulation and Visualization
- Python

---

## Summary
This project demonstrates how simple local rules governing movement, infection, and adaptive behavior can produce complex global epidemic wave patterns.  
The model highlights the critical role of behavioral adaptation and population mobility in shaping the long-term dynamics of infectious disease spread.
