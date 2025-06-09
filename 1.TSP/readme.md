# Traveling Salesman Problem (TSP) for U.S. State Capitals

## Project Description

The goal of this project is to determine the most efficient route for a politician to visit all 50 U.S. state capitals exactly once, starting in **Iowa** and ending in **Washington, D.C.** The solution aims to minimize total travel distance.

## Procedure

### Step 1: Clustering

The 50 state capitals are grouped into **10 clusters** based on geographic proximity using a clustering algorithm.

### Step 2: Determine Cluster Centroids

Each cluster is represented by its **geographic centroid**, calculated from the coordinates of the cities in that cluster.

### Step 3: Determine Cluster Visit Order

A **brute-force algorithm** is applied to find the shortest possible path through the cluster centroids, determining the optimal **cluster visit sequence**.

### Step 4: Determine Connections Between Clusters

Using the cluster sequence obtained from the previous step:

- The **first cluster** must start at **Iowa**, and the **last cluster** must end at **Washington, D.C.**
- For each **pair of consecutive clusters**, the algorithm identifies the pair of cities—one from each cluster—that are **closest in distance**.
- The selected city in the **earlier cluster** is marked as its `end`, while the closest city in the **next cluster** is marked as its `start`.

### Step 5: Optimize Route Within Each Cluster

For each cluster:
- If the number of cities is **greater than 8**, a **Nearest Neighbor** heuristic followed by **2-opt** optimization is used to find the intra-cluster shortest path.
- Otherwise, a **brute-force search** is used to find the exact shortest route within the cluster.

### Step 6: Global Route Optimization

- All optimized intra-cluster routes are connected based on the global cluster sequence.
- **Duplicate cities** (such as Juneau and Honolulu, which appear as both the start and end within their single-city clusters) are **removed** from the final path to avoid redundancy.
- The complete route is further optimized using **2-opt and 3-opt algorithms** to minimize the total travel distance.

## Output

- A **visualized route map** showing the optimized path across all 50 state capitals.
- The **total distance** of the optimized route, reported in both kilometers and miles.
