# Delivery Route Optimization for E-commerce  

### Project Overview
This capstone project implements a **complete end-to-end logistics optimization system** for an e-commerce delivery network using **multiple algorithmic strategies** as required by the ENCA351 assignment.

The solution intelligently combines:
- **Greedy 0/1 Knapsack** → Maximizes profit under vehicle capacity
- **Dynamic Programming** → Validates time window feasibility
- **Dijkstra & Prim's MST** → Network analysis and shortest paths
- **TSP (Brute Force + Held-Karp)** → Exact and approximate route optimization

**Key Insight:** We do **not** deliver to all customers. C3 is correctly **rejected** by greedy (lowest value/weight ratio), resulting in a **superior solution** of **17 km** (vs 18 km if forcing all deliveries).

---

### Project Structure
```
Delivery-Route-Optimization/
│
├── delivery_optimization.ipynb          ← Main notebook (100% working)
├── images/                               ← All generated visualizations
│   ├── full_network.jpg
│   ├── dijkstra.jpg
│   ├── prim_mst.jpg
│   ├── knapsack_scatter.jpg
│   ├── optimal_route.jpg
│   ├── gantt_chart.jpg
│   └── complexity_growth.jpg
├── requirements.txt                      ← pip install -r requirements.txt
├── README.md                             ← This file
└── delivery_optimization.html            ← Optional exported HTML version
```

---

### Final Optimized Solution
| Metric                    | Value                   | Status    |
|---------------------------|-------------------------|---------|
| Selected Customers        | C1, C2                  | Selected |
| Rejected Customer         | C3 (value/weight = 2.0) | Rejected |
| Total Profit              | **$110**                | Maximum |
| Vehicle Capacity Used     | 30/30 kg (100%)         | Full     |
| Optimal Route             | W → C1 → C2 → W         | Optimal  |
| **Total Distance**        | **17 km**               | **FINAL ANSWER** |
| Return Time               | ~9:34 AM                | On Time  |
| Time Windows              | All satisfied           | Satisfied|

> **Full TSP on all customers = 18 km** → shown only for Unit 4 demonstration  
> **Our solution = 17 km** → **better business outcome**

---

### Algorithm Summary Table

| Unit | Algorithm              | Purpose                            | Key Result           | Complexity       |
|------|------------------------|------------------------------------|----------------------|------------------|
| 1    | Recurrence Relation    | Estimate cost to visit all         | 18 km                | O(n!)            |
| 2A   | Greedy 0/1 Knapsack    | Profit maximization                | $110, 30kg           | O(n log n)       |
| 2B   | DP Time Windows        | Feasibility check                  | Feasible             | O(n × T)         |
| 3A   | Dijkstra               | Shortest paths from warehouse      | C1:4, C2:8, C3:6 km  | O(V²)            |
| 3B   | Prim's MST             | Minimum connectivity               | 12 km                | O(V²)            |
| 4A   | TSP Brute Force        | Exact tour (all customers)         | 18 km                | O((n-1)!)        |
| 4B   | Held-Karp DP           | Exact TSP with better complexity   | 18 km                | O(n² × 2ⁿ)       |
| **Final** | **Greedy + Reduced TSP** | **Real-world optimal**         | **17 km**            | **Best**         |

---

### Visualizations (All Generated Automatically)

| Visualization                    | Description                                      | File                     |
|----------------------------------|--------------------------------------------------|--------------------------|
| Full Network Graph               | Complete distance graph with warehouse           | `images/full_network.jpg` |
| Dijkstra Shortest Paths          | Bold green paths from warehouse                  | `images/dijkstra.jpg`     |
| Prim's MST                       | Minimum spanning tree (12 km)                    | `images/prim_mst.jpg`     |
| Knapsack Profit vs Weight        | C3 clearly rejected (red)                        | `images/knapsack_scatter.jpg` |
| Optimal Route (17 km)            | Final delivery route highlighted                 | `images/optimal_route.jpg` |
| Professional Gantt Chart         | Delivery timeline with exact times               | `images/gantt_chart.jpg`  |
| TSP Complexity Growth            | Brute force vs Held-Karp scaling                 | `images/complexity_growth.jpg` |

---

### How to Run

```bash
# 1. Clone repository
git clone https://github.com/yourusername/Delivery-Route-Optimization.git
cd Delivery-Route-Optimization

# 2. Install dependencies
pip install -r requirements.txt

# 3. Launch Jupyter
jupyter notebook

# 4. Open delivery_optimization.ipynb
# 5. Run All Cells → All graphs auto-save to /images/
```
