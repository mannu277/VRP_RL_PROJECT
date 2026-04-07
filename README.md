# Code for Master's Thesis: Dynamic Vehicle Routing with RL-Augmented MILP

This repository contains the code used for my master's thesis on "Modern Reinforcement Learning Approaches to Dynamic Vehicle Routing under Uncertainty".

The thesis studies whether reinforcement-learning-based signals can improve dispatch decisions when combined with a MILP solver, instead of replacing optimization completely. The experiments focus on a simplified dynamic pickup-and-delivery / ride-dispatch setting inspired by ride-hailing.

## What is in this repository?

The code explores two main approaches:

- **Value Function Approximation (VFA):** a learned value estimate is added to the MILP objective
- **Policy Gradient (PG):** a learned policy modifies parts of the MILP, such as request priorities, before solving

These methods are compared against:
- a greedy heuristic
- a myopic MILP baseline

## Main files

| File | Purpose |
|---|---|
| `vfa.py` | Initial VFA implementation with MILP-embedded ReLU value approximation |
| `vfa_advantage_torch.py` | PyTorch-based VFA variant using advantage-style training |
| `vfa_sharing_vfa.py` | Ride-sharing extension of the VFA framework |
| `advantage_torch_9.py` | Additional VFA experiments / later architecture variants |
| `pg_1st_phase.py` | Policy-gradient approach with continuous modifiers |
| `pg_2nd_phase.py` | Policy-gradient approach with discrete candidate modes |

## Problem setting

The experiments use a simplified stochastic dynamic dispatch problem:
- requests arrive over time
- vehicles are assigned sequentially
- some variants include ride-sharing, deadlines, and capacity constraints
- assignments are decided using a MILP solved with Gurobi

## Requirements

- Python 3.8+
- Gurobi and a valid license
- PyTorch
- NumPy
- Matplotlib

Install dependencies with:
```bash
pip install gurobipy torch numpy matplotlib
```
