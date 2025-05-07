# Equivalent Resistance Using Graph Theory

## 🔌 Problem Overview

Calculating the **equivalent resistance** in electrical circuits is essential for designing and analyzing efficient systems. While traditional methods work well for simple circuits, **graph theory** offers a powerful tool to handle **complex resistor networks**, especially with nested or looped configurations.

---

## 🧠 Motivation

- Traditional circuit analysis relies on identifying series and parallel components.
- This becomes difficult in large or irregular circuits.
- Graph theory provides a **systematic, programmable approach** using nodes (junctions) and edges (resistors).
- Enables **automation**, **visualization**, and **scalability**.

---

## 📊 Circuit as a Graph

- **Nodes** = electrical junctions
- **Edges** = resistors (with weight = resistance)
- Goal: Reduce graph to one equivalent edge between input and output nodes

![Graph Theory in Circuits](https://upload.wikimedia.org/wikipedia/commons/thumb/6/64/Resistor_Network.svg/1024px-Resistor_Network.svg.png)

---

## 🧮 Algorithm Description

### 🔁 Graph Simplification Strategy

1. **Detect series connections**: Nodes with degree 2 (except terminals)
2. **Detect parallel connections**: Multiple edges between same nodes or cycles
3. **Reduce step by step**:
   - Combine series: \( R_{eq} = R_1 + R_2 \)
   - Combine parallel: \( \frac{1}{R_{eq}} = \frac{1}{R_1} + \frac{1}{R_2} \)

### 🧾 Pseudocode

```pseudo
function simplify_circuit(graph, input_node, output_node):
    repeat:
        for each node in graph:
            if node is not input/output and has degree 2:
                merge series resistors
        for each pair of nodes with parallel edges:
            combine using parallel rule
    until no more simplifications
    return resistance between input_node and output_node
