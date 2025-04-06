===========
Demo Example
===========

You can try the package without any input data using the demo mode:

.. code-block:: bash

    construct-graph --demo

This generates synthetic BOLD data (100 time points × 10 ROIs), constructs a graph using Pearson correlation, and saves it as:

.. code-block:: bash

    ./demo_graph.csv  or  ./demo_graph.pt

--------------------
Visualizing the Graph
--------------------

To view the `.pt` result:

.. code-block:: python

    import torch
    import networkx as nx
    from torch_geometric.utils import to_networkx

    graph = torch.load("demo_graph.pt")
    G = to_networkx(graph)
    nx.draw(G, with_labels=True)

This will display a simple undirected graph showing brain region connectivity.
