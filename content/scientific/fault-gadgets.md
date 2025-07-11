---
title: "fault-gadgets - A library to model faults and related constructions for PyZX"
draft: false
author: "Maximilian Rüsch"
date: 2025-07-11
language: en
markup: 'mmark'
summary: "A library developed during the masters thesis, facilitating comprehensive modeling of faults on ZX-diagrams. Key features include checking fault-equivalence of rewrites and constructing the tanner graph of diagrams."
---

Introducing the [`fault-gadgets`](https://github.com/maximilianruesch/fault-gadgets) library built on top of [`pyzx`](https://github.com/zxcalc/pyzx) to reason about faults and fault models for ZX-diagrams.
Related constructions are available as well, including key features such as automatically determining if a rewrite is fault-equivalent or computing the tanner graph of a diagram:

```python
import generate
import pyzx as zx
from faultgadget.query.tannergraph import tanner_graph

g = generate.zweb(3, 3)
tanner = tanner_graph(g)
print(f"There are {len(tanner.get_undetected_faults())} undetected atomic faults in total!")

for edge, pauli in tanner.get_faults():
    violated = tanner.get_violated_detectors(edge, pauli)
    if len(violated) > 0:
        print(f"The {pauli} fault on {edge} violates the detectors [{', '.join(map(str, violated))}]!")
    else:
        print(f"The {pauli} fault on {edge} violates no detectors!")
```

Available now on [GitHub](https://github.com/maximilianruesch/fault-gadgets)!
