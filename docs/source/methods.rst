==============================
Graph Construction Methods
==============================

You can choose between multiple correlation-based methods for graph construction.

----------------------
Pearson Correlation
----------------------

Standard Pearson correlation:

.. math::

   \rho(X_i, X_j) = \frac{\text{Cov}(X_i, X_j)}{\sigma_{X_i} \sigma_{X_j}}

Captures linear association between ROI time series.

----------------------
Partial Correlation
----------------------

Removes influence of other variables:

.. math::

   \rho_{ij \cdot rest} = \frac{\rho_{ij} - \rho_{ik} \rho_{jk}}{\sqrt{(1 - \rho_{ik}^2)(1 - \rho_{jk}^2)}}

Used to infer direct connections.

----------------------
Cosine Similarity
----------------------

Measures angle between two time series:

.. math::

   \text{cos}(\theta) = \frac{X_i \cdot X_j}{||X_i|| \, ||X_j||}

Useful for directional or normed signal comparison.
