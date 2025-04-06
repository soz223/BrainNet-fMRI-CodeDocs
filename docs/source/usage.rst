=====
Usage
=====

You can use `brainnet-graph` from either the command line or Python code.

-------------------
Command-line usage:
-------------------

Basic run:

.. code-block:: bash

    construct-graph --input bold.csv --output graph.csv --method pearson_correlation

Run demo with synthetic data:

.. code-block:: bash

    construct-graph --demo
    construct-graph --demo --format pt

CLI arguments:

.. list-table::
   :header-rows: 1

   * - Flag
     - Description
   * - --input, -i
     - Path to input file (.csv/.tsv/.pkl)
   * - --output, -o
     - Where to save output (.csv or .pt)
   * - --method, -m
     - One of pearson_correlation, partial_correlation, cosine_similarity
   * - --format, -f
     - Output format: csv or pt
   * - --demo
     - Run with generated synthetic data

----------------
Python API usage
----------------

.. code-block:: python

    from brainnet_graph.construction import load_data, validate_data, construct_graph, save_graph

    df = load_data("my_bold.csv")
    validate_data(df)
    graph = construct_graph(df, method_name="pearson_correlation")
    save_graph(graph, "graph.csv", fmt="csv")
