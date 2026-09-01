---
title: "Minimum-Cost Flow and the Network Simplex Algorithm: a gentle start"
date: 2026-08-20
categories: [tutorials]
tags: [algorithms, optimization, python, networkx]
excerpt: "What minimum-cost flow is, why it shows up everywhere, and how to solve a small instance in a few lines of Python."
toc: true
toc_label: "Contents"
---

The **minimum-cost flow (MCF)** problem is one of those quiet giants of
optimization: once you learn to recognize it, you start seeing it everywhere —
in logistics, telecom routing, image segmentation, and even in how biological
transport networks organize themselves. This post gives the intuition and then
solves a tiny instance in Python.

## The problem in one paragraph

You have a directed graph. Each node has a **supply** (positive) or **demand**
(negative). Each edge has a **capacity** and a **cost per unit of flow**. The
goal: push flow from supply nodes to demand nodes so that every unit reaches its
destination, no edge exceeds its capacity, and the **total cost is minimized**.

Shortest path, max flow, transportation, and assignment problems are all special
cases. That generality is exactly why the **Network Simplex algorithm** — a
graph-specialized version of the simplex method — is such a useful tool: one
solver, many problems.

## A tiny example in Python

We'll use `networkx`, which ships a Network Simplex implementation.

```python
import networkx as nx

G = nx.DiGraph()

# Supplies (+) and demands (-). They must sum to zero.
G.add_node("A", demand=-4)   # source: produces 4 units
G.add_node("D", demand=4)    # sink: consumes 4 units
G.add_node("B", demand=0)
G.add_node("C", demand=0)

# add_edge(u, v, weight=cost_per_unit, capacity=max_flow)
G.add_edge("A", "B", weight=1, capacity=4)
G.add_edge("A", "C", weight=2, capacity=2)
G.add_edge("B", "D", weight=2, capacity=3)
G.add_edge("C", "D", weight=1, capacity=4)
G.add_edge("B", "C", weight=1, capacity=2)

cost, flow = nx.network_simplex(G)

print("Minimum total cost:", cost)
for u in flow:
    for v, f in flow[u].items():
        if f > 0:
            print(f"  {u} -> {v}: {f} units")
```

Running it prints the optimal cost and the flow on each edge. Try changing a
capacity or a cost and watch how the optimal routing shifts — that hands-on
poking is where the intuition really lands.

## Why I care

I am surveying the Network Simplex algorithm *horizontally* — across the many
domains that rediscover it — because the same combinatorial skeleton underlies
problems that look nothing alike on the surface. In later posts I'll connect MCF
to biological transport networks and to settlement flows in payment systems.

## Where to go next

- Read the classic treatment in Ahuja, Magnanti & Orlin, *Network Flows*.
- Explore `networkx`'s `min_cost_flow` and `max_flow` functions.
- Model a real problem you have as an MCF instance — that is the best exercise.

*Questions or corrections? Reach me by [email](mailto:claudiokaw@gmail.com).*
