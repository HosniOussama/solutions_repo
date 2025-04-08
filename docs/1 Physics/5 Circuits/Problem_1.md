# Problem 1

# Equivalent Resistance Using Graph Theory

## Introduction
Calculating equivalent resistance is a fundamental problem in circuit analysis. Traditional methods involve applying series and parallel resistance formulas iteratively. However, for complex circuits, graph theory provides a more systematic approach by representing circuits as weighted graphs.

In this document, we explore how to calculate equivalent resistance using graph theory, implement it programmatically, and visualize the circuit as a graph.

---

## Graph Representation of Circuits
A circuit can be represented as an undirected graph:
- **Nodes (Vertices)**: Represent junctions in the circuit.
- **Edges**: Represent resistors, with weights corresponding to resistance values.

Graph simplification involves:
- Identifying **series** and **parallel** resistor connections.
- Using algorithmic techniques to iteratively reduce the graph.

---

## Theoretical Background

### Series Resistance
For resistors in series, the equivalent resistance is:
$$
R_{eq} = R_1 + R_2 + \dots + R_n
$$

### Parallel Resistance
For resistors in parallel, the equivalent resistance is given by:
$$
\frac{1}{R_{eq}} = \frac{1}{R_1} + \frac{1}{R_2} + \dots + \frac{1}{R_n}
$$

### Graph Reduction Approach
1. **Identify series and parallel components** in the circuit graph.
2. **Reduce series and parallel resistors** iteratively.
3. **Continue simplification** until a single equivalent resistance remains.

---

## Python Implementation
The following Python script models a circuit as a graph and calculates the equivalent resistance.

```python
import networkx as nx
import matplotlib.pyplot as plt

def calculate_resistance(graph, start, end):
    paths = list(nx.all_simple_paths(graph, source=start, target=end))
    
    parallel_resistances = []
    for path in paths:
        series_resistance = sum(graph[path[i]][path[i+1]]['weight'] for i in range(len(path)-1))
        parallel_resistances.append(1 / series_resistance)
    
    return 1 / sum(parallel_resistances)

def visualize_circuit(graph):
    pos = nx.spring_layout(graph)
    labels = nx.get_edge_attributes(graph, 'weight')
    nx.draw(graph, pos, with_labels=True, node_color='lightblue', edge_color='black')
    nx.draw_networkx_edge_labels(graph, pos, edge_labels=labels)
    plt.title("Circuit Representation")
    plt.show()

# Create a sample circuit
graph = nx.Graph()
graph.add_edge('A', 'B', weight=5)
graph.add_edge('B', 'C', weight=10)
graph.add_edge('A', 'C', weight=15)  # Parallel path

visualize_circuit(graph)
print("Equivalent Resistance:", calculate_resistance(graph, 'A', 'C'))
```

---

## Example Circuits and Graphs

### Example 1: Simple Series Circuit
**Resistors:** $5Ω$, $10Ω$, $15Ω$ in series.

**Graph Representation:**

```
A --- 5Ω --- B --- 10Ω --- C --- 15Ω --- D
```

**Equivalent Resistance:**
$$
R_{eq} = 5 + 10 + 15 = 30Ω
$$

---

### Example 2: Parallel Circuit
**Resistors:** $5Ω$, $10Ω$ in parallel.

**Graph Representation:**

```
 A
 | \
 | 5Ω \
 |   \
 |    B
 |   /
 | 10Ω /
 | /
 C
```

**Equivalent Resistance:**
$$
\frac{1}{R_{eq}} = \frac{1}{5} + \frac{1}{10} \Rightarrow R_{eq} = 3.33Ω
$$

---

## Conclusion
By leveraging graph theory, we can systematically compute the equivalent resistance of complex circuits. This method is efficient for large networks and allows for automation in electrical circuit simulations.

---

## Further Exploration
- Extend the algorithm to handle more complex circuit configurations.
- Integrate Kirchhoff’s laws to analyze voltage and current distributions.
- Implement a graphical user interface (GUI) for interactive circuit analysis.

---

### References
- Network Analysis by M.E. Van Valkenburg
- Graph Theory Applications in Electrical Engineering

