# Multi-Commodity Military Logistics Optimization

> *A mixed-integer programming framework for multimodal logistics planning under deterministic, multi-objective, and stochastic demand.*

<p align="center">
<i><img width="427" height="277" alt="image" src="https://github.com/user-attachments/assets/a7e0d274-ac33-4d2b-afc4-d80021849066" />
</i>
</p>

---

## Abstract

Modern logistics planning requires balancing multiple competing objectives while operating under limited transportation resources and uncertain demand. As transportation networks grow in size and complexity, determining how commodities should be routed through geographically distributed supply chains becomes an increasingly challenging optimization problem.

This repository presents a mathematical optimization framework for planning the transportation of multiple commodities through a directed logistics network consisting of **Supply Locations (SLs)**, **Forward Stations (FSs)**, and **Delivery Locations (DLs)**. The framework models heterogeneous transportation connectors-including aircraft, boats, trains, and trailers-while accounting for connector capacities, transportation costs, maintenance costs, travel times, and routing restrictions.

Rather than addressing a single optimization problem, the project investigates several deterministic, multi-objective, and stochastic formulations that capture different operational planning objectives. The resulting models demonstrate how mathematical optimization can support strategic logistics planning across a broad range of operational environments.

---

## Motivation

Transportation planning rarely consists of minimizing cost alone. Operational planners must simultaneously consider delivery time, transportation resource availability, competing mission priorities, and uncertainty in future demand. Improving one objective frequently degrades another, making logistics planning fundamentally a multi-objective decision-making problem.

This project explores how a common mathematical modeling framework can be adapted to answer several distinct logistics planning questions. Beginning with a deterministic transportation model, progressively richer optimization formulations are developed to investigate time-critical deliveries, cost–time trade-offs, resource limitations, and uncertainty in operational demand.

The objective is not merely to obtain a single optimal transportation plan, but to demonstrate how mathematical optimization provides a flexible decision-support framework capable of addressing multiple planning scenarios within the same logistics network.

---

## Logistics Network

The transportation network follows a directed two-stage structure

```text
Supply Locations
        │
        ▼
Forward Stations
        │
        ▼
Delivery Locations
```

Supply Locations provide the available commodities, Forward Stations act as intermediate consolidation points, and Delivery Locations represent the final destinations where demand must be satisfied.

Transportation connectors travel along feasible network arcs while satisfying connector-specific routing restrictions, operating costs, maintenance costs, travel speeds, and capacity limitations.

---

## Optimization Framework

Eight optimization formulations are developed throughout the notebook, each addressing a different operational planning objective.

The framework begins with a deterministic cost-minimization model that identifies the least-cost transportation plan satisfying all delivery requirements. A complementary formulation then minimizes overall delivery completion time.

Recognizing that logistics planning often requires balancing competing objectives, the framework next investigates the relationship between transportation cost and delivery time through Pareto frontier analysis. Additional models maximize commodity delivery within prescribed planning horizons and determine the fastest feasible transportation strategy for individual commodities.

Finally, uncertainty is introduced through multiple demand scenarios. Two stochastic formulations are considered: an expected-cost model that minimizes average transportation cost across all scenarios and a minimax model that minimizes the worst-case transportation cost.

Together, these formulations illustrate how different operational objectives produce substantially different transportation strategies while relying upon the same underlying mathematical framework.

---

## Mathematical Modeling

Each optimization problem is formulated as a **Mixed-Integer Programming (MIP)** model using **GAMSPy**.

Binary decision variables determine whether transportation connectors are activated on specific routes, while continuous variables determine the quantity of each commodity transported throughout the logistics network.

The mathematical models incorporate operational constraints governing

- commodity flow conservation,
- connector capacities,
- transportation mode compatibility,
- supply availability,
- delivery demand satisfaction,
- connector utilization,
- routing feasibility,
- and delivery time requirements.

Geographic distances between all locations are computed using the **Haversine Formula**, allowing transportation costs and travel times to reflect realistic spatial relationships.

---

## Computational Implementation

The optimization framework is implemented entirely in **Python** using **GAMSPy** for mathematical modeling and optimization. Supporting libraries including **NumPy**, **Pandas**, **Matplotlib**, and **Plotly** are used for data management, visualization, and computational analysis.

The notebook develops the models incrementally, allowing readers to follow the complete progression from network construction through mathematical formulation, optimization, visualization, and computational experimentation.


---

## Example Results

The notebook produces several forms of output that illustrate the behavior of the optimization models, including

- geographic visualizations of transportation routes,
- commodity movement across the logistics network,
- connector utilization,
- Pareto frontiers illustrating cost–time trade-offs,
- expected-cost transportation plans,
- and worst-case (minimax) transportation strategies.

Representative figures and computational results will be included throughout this repository.

---

## Potential Applications

Although motivated by military logistics, the mathematical framework developed in this project is broadly applicable to transportation and network optimization problems arising in numerous domains. Similar formulations can support humanitarian aid distribution, disaster relief planning, healthcare logistics, emergency response operations, freight transportation, and supply chain network design.

Because the optimization model is independent of any particular application domain, modifying the network topology, transportation assets, or demand data allows the framework to be adapted to a wide variety of logistics planning problems.

---

## Reproducing the Results

Clone the repository

```bash
git clone https://github.com/YOUR_USERNAME/military-logistics-optimization.git
```

Install the required packages

```bash
pip install -r requirements.txt
```

Launch Jupyter Notebook

```bash
jupyter notebook
```

and execute

```text
notebook/military_logistics_analysis.ipynb
```

from beginning to end.

Running the optimization models requires a valid GAMSPy installation together with access to a compatible optimization solver.


---

## Future Work

Potential extensions include:

- Dynamic time-expanded logistics networks
- Inventory management at forward stations
- Vehicle routing and scheduling
- Robust optimization under uncertain travel times
- Distributionally robust optimization
- Multi-period stochastic programming
- Decomposition methods for large-scale optimization
- Machine learning-assisted demand forecasting

---

## Author

**Vivek Bhatia**

M.S. Industrial Engineering, Operations Research and Analytics

University of Wisconsin–Madison



## Disclaimer

This project was developed for educational and research purposes. The logistics network, transportation data, and demand scenarios are illustrative and are intended solely to demonstrate mathematical optimization techniques.
