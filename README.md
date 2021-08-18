# Leiden-based WBFM for ASN CD
Basing on theoretical results we propose a well-tunable Leiden-based algorithm implementing the WBFM.

In the simplest way, the input of the algorithm is a structural graph
G_s, attributive graph G_a and the value of ρ indicating
the desired impact of the structure and the
attributes on the CD results within the WBFM.

G_s and G_a can be initial data, or created from node-attributed graph by using utilities functions.
## Installation

You can clone the repository and use examples in the
jupyter notebook or create your own in the same working space.

## Usage

```python
import model
import networkx as nx
import random

# structural graph
G_structure = nx.gnp_random_graph(3000, 0.1, seed=10)
# attributive graph
G_attributes = nx.gnp_random_graph(3000, 0.4, seed=7)

# assigning random weights
for e in G_structure.edges():
    G_structure[e[0]][e[1]]['weight'] = random.randint(0,10)

for e in G_attributes.edges():
    G_attributes[e[0]][e[1]]['weight'] = random.randint(0,10)
    
# rho value to specify the desired balance
rho = 0.25

partition, metrics_report = model.leiden_wbfm(G_structure, G_attributes, rho=rho)
```
