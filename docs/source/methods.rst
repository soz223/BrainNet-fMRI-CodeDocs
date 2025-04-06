==============================
Graph Construction Methods
==============================

This package supports multiple methods to compute brain connectivity matrices from BOLD time-series signals. The resulting matrices are converted into graph structures.

.. list-table::
   :header-rows: 1
   :widths: 25 75

   * - **Method**
     - **Description**
   * - ``pearson_correlation``
     - Classic Pearson correlation: linear association

       .. math::

          \rho(X_i, X_j) = \frac{\text{Cov}(X_i, X_j)}{\sigma_{X_i} \sigma_{X_j}}

   * - ``spearman_correlation``
     - Rank-based Spearman correlation
   * - ``kendall_correlation``
     - Kendall's Tau: rank correlation robust to outliers
   * - ``partial_correlation``
     - Removes the effect of other variables (precision matrix)
   * - ``cosine_similarity``
     - Angular similarity between ROI vectors
   * - ``correlations_correlation``
     - Second-order correlation between ROI profiles
   * - ``associated_high_order_fc``
     - Correlation between functional connectivity vectors
   * - ``euclidean_distance``
     - Distance-based similarity (converted to weight)
   * - ``knn_graph``
     - Graph constructed from K-nearest neighbors
   * - ``mutual_information``
     - Captures nonlinear dependencies
   * - ``cross_correlation``
     - Time-lagged correlation analysis
   * - ``granger_causality``
     - Temporal causality analysis via Granger’s test
   * - ``generalised_synchronisation_matrix``
     - Measures synchrony across systems (**slow**)
   * - ``patels_conditional_dependence_measures_kappa``
     - Conditional dependency (\(\kappa\)) based on Patel's method
   * - ``patels_conditional_dependence_measures_tau``
     - Conditional dependency (\(\tau\)) based on Patel's method
   * - ``lingam``
     - LiNGAM causal inference (**slow**, directional)

----

.. note::

   - Some methods (e.g., ``lingam``, ``generalised_synchronisation_matrix``) are computationally expensive and slow for large inputs.
   - All methods return a square connectivity matrix which is post-processed into a graph using edge index + edge weight.
   - You can save graphs in `.pt` (PyTorch Geometric) or `.csv` formats.

