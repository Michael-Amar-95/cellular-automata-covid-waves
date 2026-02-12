# Cellular Automata – COVID-19 Waves Simulation

## Overview
This project implements a cellular automaton model that simulates the spread of COVID-19 in a population, with a focus on understanding the emergence of **epidemic waves** (repeated rises and falls in the number of infected individuals).

The simulation was developed as part of an academic exercise exploring how local interactions, movement, and adaptive behavior can lead to global, wave-like dynamics.

---

## Model Description

### Environment
- A 2D cellular automaton of size **200 × 200** cells.
- **Wrap-around (toroidal)** boundary conditions.
- Each cell may contain **at most one individual**.

### Population
- **N** individuals are randomly placed on the grid.
- An initial percentage **D%** of individuals start as infected.
- A fraction **R%** of individuals are *fast movers*.

### Movement Rules
- In every generation, each individual:
  - Moves to one of its 8 neighboring cells or
  - Remains in its current cell  
- All 9 options have equal probability.
- Fast-moving individuals move **10 cells per generation**.
- A collision-avoidance mechanism prevents two individuals from occupying the same cell.

### Infection Rules
- If a healthy individual is located in one of the 8 neighboring cells of an infected individual,
  there is a probability **P** of infection.
- The infection probability **P is adaptive**:
  - When the percentage of infected individuals is **below a threshold T**, infection probability is **high**.
  - When infection exceeds **T**, individuals behave more cautiously and **P decreases**.
- Two discrete infection probabilities are used:
  - `P_high`
  - `P_low`

### Disease Progression
- An infected individual remains infectious for **X generations**.
- After recovery, the individual:
  - Cannot be reinfected.
- The model assumes:
  - No vaccination
  - No virus variants

---

## Parameters

| Parameter | Description |
|---------|------------|
| N | Total number of individuals |
| D | Initial percentage of infected individuals |
| R | Percentage of fast-moving individuals |
| X | Number of generations before recovery |
| P_high | Infection probability when infection level is low |
| P_low | Infection probability when infection level is high |
| T | Infection percentage threshold for changing P |

---

## Goal of the Experiment
The main objective is to find combinations of parameters that lead to **wave-like behavior** in the infection curve —  
specifically, **at least three distinct cycles** of rising and falling infection levels during the simulation.

---

## Visualization
The simulation includes a graphical visualization that:
- Displays the automaton state in real time
- Allows the user to control model parameters
- Clearly distinguishes between healthy, infected, and recovered individuals

---

## Technologies
- Cellular automata
- Probabilistic modeling
- Simulation and data analysis
- Python\

---
