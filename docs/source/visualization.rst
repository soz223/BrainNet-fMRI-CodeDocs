=====================
Graph Visualization
=====================

.. image:: _static/demo_graph.png
   :alt: Example graph output
   :width: 400px
   :align: center

Visualize your graph using:

.. code-block:: python

    import torch
    import networkx as nx
    from torch_geometric.utils import to_networkx

    graph = torch.load('graph.pt')
    nx_graph = to_networkx(graph)
    nx.draw(nx_graph)

