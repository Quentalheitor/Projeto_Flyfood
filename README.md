# FlyFood — Autonomous Drone Delivery Route Optimization

## Overview
**FlyFood** solves the Traveling Salesperson Problem (TSP) tailored for autonomous drone logistics across a discrete 2D matrix grid[cite: 1]. The system determines the minimum-cost route departing from a depot/restaurant (`R`), visiting every delivery coordinate exactly once, and returning to the departure point[cite: 1].

Distances across the grid are computed using the **Manhattan Distance** ($L_1$ norm):
$$\text{Distance}(P_1, P_2) = |x_1 - x_2| + |y_1 - y_2|$$

---

## Repository Architecture

The project explores and benchmarks multiple algorithmic paradigms to evaluate combinatorial trade-offs and runtime constraints[cite: 1]:

* **`flyfood_base.py`**: Baseline brute-force implementation exploring all permutations of delivery paths ($O(n!)$) to identify global optima[cite: 1].
* **`flyfood_falsoa*.py`**: Heuristic search implementation inspired by A*, leveraging greedy path evaluation to navigate combinatorial explosions[cite: 1].
* **`flyfood_final.py`**: Optimized search algorithm utilizing branch-and-bound pruning to discard suboptimal paths early and accelerate convergence[cite: 1].
* **`testador.py`**: Automated performance test runner measuring execution time and verifying path correctness against test inputs[cite: 1].
* **`flyfood_final_testador.py`**: Benchmark suite focused on stress-testing the finalized algorithm across varying matrix densities[cite: 1].
* **`mapa.txt`**: Matrix input file configuring grid dimensions, depot location (`R`), and designated delivery coordinates[cite: 1].
* **`prova_limite_recursao.txt`**: Empirical analysis and documentation of Python recursion stack boundaries and call-depth overhead[cite: 1].

---

## Technical Highlights

* **Combinatorial Optimization**: Formulation and solution of the metric TSP over discrete coordinate systems[cite: 1].
* **Branch-and-Bound Pruning**: Real-time pruning of partial paths whose accumulated Manhattan cost exceeds the recorded upper bound[cite: 1].
* **Runtime Benchmarking**: Empirical testing of memory allocation, recursion ceiling limits, and latency profiles[cite: 1].

---

## Getting Started

### Prerequisites
* Python 3.8+

### Execution
1. Configure your target grid matrix and delivery points in `mapa.txt`[cite: 1].
2. Execute the optimized solver:
   ```bash
   python flyfood_final.py
