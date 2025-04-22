# Problem 1


## 🔧 **Option 1: Pseudocode for Equivalent Resistance Using Graph Theory**

### 🎯 Goal:
Reduce a graph (circuit) until it’s a single equivalent resistance between two terminals.

---

### ✅ **Key Concepts:**
- Nodes = Junctions
- Edges = Resistors (weighted by resistance)
- Series: Resistors on the same path (2 edges, same node degree)
- Parallel: Multiple edges between same two nodes or multiple paths between same two nodes (via cycles)

---

### 🧠 **Algorithm Overview:**
1. **Build the graph** from input (nodes and resistors).
2. **Repeat until only one equivalent resistance** is left between the source and target:
   - Detect and reduce **series** connections.
   - Detect and reduce **parallel** connections.
3. Return the total resistance between source and target.

---

### 📜 **Pseudocode:**

```plaintext
Function calculate_equivalent_resistance(graph, source, target):
    While graph has more than 2 nodes or multiple edges:
        For each node in graph:
            If degree(node) == 2:
                neighbors = list of connected nodes
                If only one path between neighbors:
                    Combine series: R_eq = R1 + R2
                    Replace with single edge
            For all pairs of nodes (u, v):
                If multiple edges exist:
                    Combine parallel: R_eq = 1 / (1/R1 + 1/R2 + ...)
                    Replace with single edge
    Return resistance between source and target
```

---

## 🧪 **Option 2: Python Implementation Using `networkx`**

Let’s implement this step-by-step.

### 📦 Required:
```bash
pip install networkx
```

### 🧾 **Full Python Code:**

```python
import networkx as nx

def combine_parallel(resistors):
    """Combine resistors in parallel."""
    return 1 / sum(1/r for r in resistors)

def reduce_series(G):
    changed = True
    while changed:
        changed = False
        for node in list(G.nodes):
            if node in G and G.degree(node) == 2 and node not in ('A', 'B'):
                neighbors = list(G.neighbors(node))
                if len(neighbors) == 2:
                    u, v = neighbors
                    r1 = G[u][node]['resistance']
                    r2 = G[node][v]['resistance']
                    new_r = r1 + r2
                    G.add_edge(u, v, resistance=new_r)
                    G.remove_node(node)
                    changed = True
                    break
    return G

def reduce_parallel(G):
    for u, v in list(G.edges()):
        parallel_edges = [data['resistance'] for key, data in G.get_edge_data(u, v).items()]
        if len(parallel_edges) > 1:
            combined = combine_parallel(parallel_edges)
            G.remove_edges_from(list(G.edges(u, v)))
            G.add_edge(u, v, resistance=combined)
    return G

def calculate_equivalent_resistance(graph, source, target):
    G = graph.copy()
    while True:
        before = G.number_of_edges()
        G = reduce_series(G)
        G = reduce_parallel(G)
        after = G.number_of_edges()
        if before == after:
            break
    return G[source][target]['resistance']
```

---

### 🧪 **Example 1: Simple Series**
```python
G = nx.Graph()
G.add_edge('A', '1', resistance=2)
G.add_edge('1', 'B', resistance=3)
print(calculate_equivalent_resistance(G, 'A', 'B'))  # Output: 5
```

---

### 🧪 **Example 2: Parallel**
```python
G = nx.MultiGraph()
G.add_edge('A', 'B', resistance=2)
G.add_edge('A', 'B', resistance=3)
print(calculate_equivalent_resistance(G, 'A', 'B'))  # Output: 1.2
```

---

### 🧪 **Example 3: Nested Configuration**

Series + Parallel:
```python
G = nx.MultiGraph()
G.add_edge('A', '1', resistance=1)
G.add_edge('1', '2', resistance=2)
G.add_edge('2', 'B', resistance=3)
G.add_edge('A', 'B', resistance=2)

# This will reduce parallel between:
# (A - 1 - 2 - B) = 6 and (A - B) = 2
# Parallel: 1 / (1/2 + 1/6) = 1.5

print(calculate_equivalent_resistance(G, 'A', 'B'))  # Output: 1.5
```

---

## ⚙️ **Handling Complex Circuits**
- Detecting **series** paths via node degree = 2
- Detecting **parallel** connections via multiple paths (using `MultiGraph`)
- Recursive reduction until minimal graph remains

---

## 📈 Efficiency Analysis

### Time Complexity:
- Series reduction: O(n)
- Parallel detection: O(m²) in worst-case (many edges between same nodes)
- Total ~ O(n²) for general graphs

### Potential Improvements:
- Use **Union-Find** or **Disjoint Set** to detect cycles
- Use **Kirchhoff’s laws** with matrix solutions (e.g., Laplacian matrix + pseudoinverse for generalized approach)
- Use **SPICE**-like simulation engines for more complex non-linear or dependent components

---

Would you like this turned into a full command-line tool or visualization next?