# Computational Methods 2 – SIR Model Project

This repository presents an implementation and analysis of the SIR epidemiological model, developed as part of the Computational Methods 2 course.  
The project was carried out in collaboration with Jan Szurczak and Szymon Kaczmarczyk.

---

## 1. Theory

### 1.1 Introduction
The SIR model describes the spread of infectious diseases in a closed population, dividing it into three compartments: Susceptible ($S$), Infected ($I$), and Recovered ($R$).  
The system is governed by nonlinear ODEs that relate infection and recovery rates through two parameters: the infection rate ($\beta$) and recovery rate ($\gamma$).

### 1.2 Model Equations
$
\frac{dS}{dt} = -\beta \frac{SI}{N}, \quad
\frac{dI}{dt} = \beta \frac{SI}{N} - \gamma I, \quad
\frac{dR}{dt} = \gamma I
$

### 1.3 Key Concepts
- Basic reproduction number: $r = \frac{\beta}{\gamma}$
- Epidemic condition: $r > 1$
- Equilibrium state: $(S, I, R) = (N, 0, 0)$
- Final epidemic size: $S_\infty = N e^{-\frac{r}{N}(N - S_\infty)}$

---

## 2. Project Overview

The project explores multiple computational approaches to solving and simulating the SIR model.

### 2.1 ODE Solvers
The deterministic SIR equations were solved using:
- a custom 2nd-order Runge–Kutta (RK2) implementation,  
- and the SciPy `solve_ivp` function.

Both solvers produce comparable epidemic trajectories for $S(t)$, $I(t)$, and $R(t)$.

### 2.2 Agent-Based Model
Each agent transitions between states probabilistically:
- Infection probability: $P_{inf} = \beta I / N$
- Recovery probability: $P_{rec} = \gamma$

This method introduces stochastic effects and individual-level dynamics.

### 2.3 Cellular Automata Model
A 2D grid representation where:
- Cells can be susceptible (0), infected (1), or recovered (2)  
- Infection probability depends on infected neighbors: $1 - (1 - \beta)^n$  
- Recovery occurs with probability $\gamma$

The CA captures spatial and local effects in epidemic spread.

### 2.4 Free Particle Model
Agents move randomly within a bounded domain and interact based on proximity.  
Infection occurs if susceptible agents come within a contact radius of infected ones, with recovery governed by $\gamma$.

---

## 3. Tools and Environment
- Python 3  
- NumPy, SciPy, Matplotlib  
- Jupyter Notebook

---

## 4. Authors
- Marcel Wilanowicz  
- Jan Szurczak  
- Szymon Kaczmarczyk

---

## 5. Summary
The project demonstrates the flexibility of the SIR framework across analytical, numerical, and simulation-based approaches.  
Comparing deterministic and stochastic implementations highlights how local interactions and randomness influence epidemic behavior.

---

## License
This repository is for educational purposes only and not licensed for redistribution or reuse.