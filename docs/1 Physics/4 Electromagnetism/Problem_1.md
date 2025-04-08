# Equivalent Resistance Using Graph Theory

## Motivation

Calculating equivalent resistance is a fundamental problem in electrical circuits, essential for understanding and designing efficient systems. While traditional methods involve iteratively applying series and parallel resistor rules, these approaches can become cumbersome for complex circuits with many components. Graph theory offers a powerful alternative, providing a structured and algorithmic way to analyze circuits. By representing a circuit as a graph—where nodes correspond to junctions and edges represent resistors with weights equal to their resistance values—we can systematically simplify even the most intricate networks. This method not only streamlines calculations but also opens the door to automated analysis, making it particularly useful in modern applications like circuit simulation software, optimization problems, and network design. Studying equivalent resistance through graph theory is valuable not only for its practical applications but also for the deeper insights it provides into the interplay between electrical and mathematical concepts. This approach highlights the versatility of graph theory, demonstrating its relevance across physics, engineering, and computer science.

## Task Options

**Option 2: Advanced Task – Full Implementation**

Implement the algorithm in a programming language of your choice. Ensure the implementation:

* Accepts a circuit graph as input.
* Handles arbitrary resistor configurations, including nested series and parallel connections.
* Outputs the final equivalent resistance.
* Test your implementation with examples, such as:
    * Simple series and parallel combinations.
    * Nested configurations.
    * Complex graphs with multiple cycles.

## Deliverables

* A detailed implementation and explanation of the algorithm.
* Description of how it handles complex circuit configurations on three input examples.
* A brief analysis of the algorithm's efficiency and potential improvements.

## Implementation (Python)

```python
import networkx as nx
import matplotlib.pyplot as plt

def calculate_equivalent_resistance(graph, start_node, end_node):
    """
    Calculates equivalent resistance between two nodes, visualizing each reduction step.
    """
    g = graph.copy()
    reduction_steps = [g.copy()]

    while len(g.nodes()) > 2:
        # 1. Series Reduction
        series_edges = []
        for node in g.nodes():
            neighbors = list(g.neighbors(node))
            if len(neighbors) == 2:
                series_edges.append((neighbors[0], node, neighbors[1]))

        for n1, mid, n2 in series_edges:
            if g.has_edge(n1, mid) and g.has_edge(mid, n2):
                r1 = g[n1][mid]['resistance']
                r2 = g[mid][n2]['resistance']
                g.remove_node(mid)
                if g.has_edge(n1, n2):
                    g[n1][n2]['resistance'] += r1 + r2
                else:
                    g.add_edge(n1, n2, resistance=r1 + r2)
        reduction_steps.append(g.copy())

        # 2. Parallel Reduction
        parallel_edges = []
        for n1, n2 in g.edges():
            if n1 != start_node and n2 != end_node:
                paths = list(nx.all_simple_paths(g, n1, n2))
                if len(paths) > 1:
                    parallel_edges.append((n1, n2))

        for n1, n2 in parallel_edges:
            paths = list(nx.all_simple_paths(g, n1, n2))
            if len(paths) > 1:
                resistances = [g[u][v]['resistance'] for u, v in g.edges(paths[0]) if (u,v) in g.edges(paths[0]) or (v,u) in g.edges(paths[0])]
                if all(g.has_edge(paths[0][i], paths[0][i+1]) for i in range(len(paths[0])-1)):
                    parallel_resistance = 1 / sum(1 / r for r in resistances)
                    for u, v in g.edges(paths[0]):
                        if g.has_edge(u,v):
                            g.remove_edge(u,v)
                    g.add_edge(n1, n2, resistance=parallel_resistance)
        reduction_steps.append(g.copy())

    if g.has_edge(start_node, end_node):
        return g[start_node][end_node]['resistance'], reduction_steps
    else:
        return float('inf'), reduction_steps

def visualize_graph(graph, title):
    pos = nx.spring_layout(graph)
    nx.draw(graph, pos, with_labels=True, node_color='lightblue', node_size=1500, edge_color='gray')
    edge_labels = nx.get_edge_attributes(graph, 'resistance')
    nx.draw_networkx_edge_labels(graph, pos, edge_labels=edge_labels)
    plt.title(title)
    plt.show()

# Complex Example Circuits
# Example 1: Balanced Bridge Circuit
graph1 = nx.Graph()
graph1.add_edge('A', 'B', resistance=10)
graph1.add_edge('B', 'C', resistance=20)
graph1.add_edge('C', 'D', resistance=30)
graph1.add_edge('D', 'A', resistance=40)
graph1.add_edge('B', 'D', resistance=50)
graph1.add_edge('A', 'C', resistance=60)

# Example 2: Ladder Network
graph2 = nx.Graph()
graph2.add_edge('A', 'B', resistance=10)
graph2.add_edge('B', 'C', resistance=20)
graph2.add_edge('C', 'D', resistance=30)
graph2.add_edge('D', 'E', resistance=40)
graph2.add_edge('E', 'F', resistance=50)
graph2.add_edge('A', 'C', resistance=15)
graph2.add_edge('C', 'E', resistance=25)
graph2.add_edge('B', 'D', resistance=35)
graph2.add_edge('D', 'F', resistance=45)

# Example 3: Star-Delta Transformation (Simplified)
graph3 = nx.Graph()
graph3.add_edge('A', 'B', resistance=10)
graph3.add_edge('B', 'C', resistance=20)
graph3.add_edge('C', 'A', resistance=30)
graph3.add_edge('A', 'D', resistance=40)
graph3.add_edge('B', 'D', resistance=50)
graph3.add_edge('C', 'D', resistance=60)

# Calculate and Visualize
for i, graph in enumerate([graph1, graph2, graph3]):
    print(f"\nExample {i+1}:")
    resistance, reduction_steps = calculate_equivalent_resistance(graph, 'A', 'D' if 'D' in graph.nodes() else 'C')
    print(f"Equivalent Resistance = {resistance} ohms")

    for step, g in enumerate(reduction_steps):
        visualize_graph(g, f"Example {i+1}, Step {step}")
```
