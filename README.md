<div align=center>

# Artificial Intelligence Search Methods

[![License](https://img.shields.io/github/license/ADolbyB/ai-search-methods?label=License&style=for-the-badge)](https://github.com/ADolbyB/ai-search-methods/blob/main/LICENSE.md)
[![Python](https://img.shields.io/badge/Python-3776AB?style=for-the-badge&logo=python&logoColor=white)](https://www.python.org/)
[![Jupyter](https://img.shields.io/badge/Jupyter-F37626?style=for-the-badge&logo=jupyter&logoColor=white)](https://jupyter.org/)
[![Repo Size](https://img.shields.io/github/repo-size/ADolbyB/ai-search-methods?label=Repo%20Size&logo=Github&style=for-the-badge)](https://github.com/ADolbyB/deep-learning-python)

</div>

A collection of fundamental AI search algorithm implementations from an **Artificial Intelligence Applications** class. All implementations are written in Python using Jupyter Notebooks, covering the four major families of classical AI search: blind search, informed search, local search, and adversarial minimax search.

## Repository Structure

```
ai-search-methods/
├── BlindSearch/        # BFS and DFS implementations
├── InformedSearch/     # Uniform Cost Search, Greedy Best First, and A* implementations
├── LocalSearch/        # Hill Climbing and Simulated Annealing implementations
├── Minimax/            # Standard Minimax and Alpha-Beta Pruning implementations
├── .gitignore
└── README.md           # This file
```

## Search Methods Overview

### 1. Blind Search

Located in [`BlindSearch/`](BlindSearch/)

Uninformed search strategies that explore the state space without any problem-specific knowledge about the goal.

| Algorithm | Description |
|-----------|-------------|
| **BFS** — Breadth First Search | Explores all nodes at the current depth before moving deeper. Guarantees the shortest path in unweighted graphs. |
| **DFS** — Depth First Search | Explores as far as possible along each branch before backtracking. Memory-efficient but does not guarantee shortest path. |

### 2. Informed Search

Located in [`InformedSearch/`](InformedSearch/)

Heuristic-guided search strategies that use problem-specific knowledge to find solutions more efficiently.

Code adapted from [this GitHub Gist](https://gist.github.com/Nicholas-Swift/003e1932ef2804bebef2710527008f44).

| Algorithm | Description |
|-----------|-------------|
| **UCS** — Uniform Cost Search | Expands the lowest-cost node first. `f(N) = g(N)` Optimal for weighted graphs with non-negative edge costs. |
| **GBF** — Greedy Best First Search | Uses a heuristic `f(N) = h(N)` to always expand the node that appears closest to the goal. Fast but not guaranteed to be optimal. |
| **A\*** — A-Star Search | Combines path cost and heuristic estimate (`f(n) = g(n) + h(n)`). Optimal and complete when using an admissible heuristic. |

### 3. Local Search

Located in [`LocalSearch/`](LocalSearch/)

Optimization-based search strategies that operate on a single current state and move to neighboring states, without tracking full search paths.

Code adapted from [this GitHub Repo](https://github.com/TranDatDT/n-queens-simulated-annealing/blob/master/main.py).

| Algorithm | Description |
|-----------|-------------|
| **HC** — Hill Climbing | Iteratively moves to the best neighboring state. Efficient but can get stuck in local optima. |
| **SA** — Simulated Annealing | Probabilistically accepts worse states early on (based on a "temperature" schedule) to escape local optima. Modeled after the metallurgical annealing process. |

### 4. Minimax

Located in [`Minimax/`](Minimax/)

Adversarial search strategies for two-player, zero-sum games. Assumes both players play optimally.

Code adapted from [this web page](https://stackabuse.com/minimax-and-alpha-beta-pruning-in-python/).

| Algorithm | Description |
|-----------|-------------|
| **Minimax** | Recursively evaluates all possible game states, maximizing the AI's score and minimizing the opponent's score. |
| **Alpha-Beta Pruning** | An optimization of Minimax that prunes branches that cannot influence the final decision, significantly reducing the number of nodes evaluated. |

## Algorithm Comparison

| Algorithm | Complete? | Optimal? | Time Complexity | Space Complexity | Notes |
|-----------|-----------|----------|-----------------|------------------|-------|
| BFS | ✅ Yes | ✅ Yes (unweighted) | O(b^d) | O(b^d) | Best for shallow goals |
| DFS | ✅ Yes* | ❌ No | O(b^m) | O(bm) | *In finite spaces only |
| UCS | ✅ Yes | ✅ Yes | O(b^(1+⌊C*/ε⌋)) | O(b^(1+⌊C*/ε⌋)) | Optimal with non-neg costs |
| GBF | ❌ No | ❌ No | O(b^m) | O(b^m) | Fast but not optimal |
| A* | ✅ Yes | ✅ Yes | O(b^d) | O(b^d) | Best of both UCS & GBF |
| Hill Climbing | ❌ No | ❌ No | O(∞) | O(1) | Prone to local optima |
| Simulated Annealing | ✅ Yes* | ❌ No | O(∞) | O(1) | *With slow cooling schedule |
| Minimax | ✅ Yes | ✅ Yes | O(b^m) | O(bm) | Full game tree |
| Alpha-Beta | ✅ Yes | ✅ Yes | O(b^(m/2)) | O(bm) | ~Doubles search depth |

*b = branching factor, d = depth of shallowest goal, m = maximum depth, C* = optimal cost, ε = minimum edge cost*

## Key Concepts

- **State Space**: The set of all possible states reachable from the initial state via actions.
- **Heuristic Function h(n)**: An estimate of the cost from node `n` to the goal. Must be **admissible** (never overestimates) for A* to be optimal.
- **Admissibility**: A heuristic is admissible if `h(n) ≤ h*(n)` for all `n`, where `h*(n)` is the true cost to the goal.
- **Consistency (Monotonicity)**: A heuristic is consistent if `h(n) ≤ c(n, a, n') + h(n')` for every successor `n'`. Consistency implies admissibility.
- **Zero-Sum Game**: A game in which one player's gain is exactly the other player's loss — the foundation of Minimax.

## Requirements

- Python 3.7 or higher
- Jupyter Notebook or JupyterLab

### Setup

1. Clone the repository:
```bash
git clone https://github.com/ADolbyB/ai-search-methods.git
cd ai-search-methods
```

2. Install dependencies:
```bash
pip install notebook
```

3. Launch Jupyter Notebook:
```bash
jupyter notebook
```

4. Navigate to the desired folder and open the `.ipynb` file.

## License

This project is licensed under the MIT License - see the [LICENSE.md](https://github.com/ADolbyB/ai-search-methods/blob/main/LICENSE.md) file for details.

## Acknowledgments

- [Nicholas Swift's A* GitHub Gist](https://gist.github.com/Nicholas-Swift/003e1932ef2804bebef2710527008f44) — Informed Search base code
- [TranDatDT's N-Queens Simulated Annealing Repo](https://github.com/TranDatDT/n-queens-simulated-annealing/blob/master/main.py) — Local Search base code
- [Stack Abuse: Minimax and Alpha-Beta Pruning in Python](https://stackabuse.com/minimax-and-alpha-beta-pruning-in-python/) — Minimax base code
- *Artificial Intelligence: A Modern Approach* by Russell & Norvig — the canonical AI textbook these algorithms are drawn from

---

### Topics

`ai` `python` `jupyter-notebook` `ai-search` `ai-search-algorithms` `bfs-algorithm` `dfs-algorithm` `ucs-algorithm` `gbfs-algorithm` `a-star-algorithm` `hill-climbing` `simulated-annealing-algorithm` `minimax-algorithm` `alpha-beta-pruning` `local-search-algorithm` `agent` `reinforcement-learning`