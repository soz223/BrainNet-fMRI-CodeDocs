==============================
Graph Construction Methods
==============================

This package supports a wide range of functional connectivity (FC) construction techniques, from simple correlations to advanced nonlinear and causal methods. The result of each method is a connectivity matrix, which is then transformed into a graph object.

----

.. contents:: **Available Methods**
   :depth: 2
   :local:

----

Correlation-Based Methods
==========================

**Pearson Correlation**

.. math::

    \rho(X_i, X_j) = \frac{\text{Cov}(X_i, X_j)}{\sigma_{X_i} \sigma_{X_j}}

Captures linear relationships between time series.

---

**Spearman Correlation**

.. math::

    \rho_s = 1 - \frac{6 \sum d_i^2}{n(n^2 - 1)}

Non-parametric rank-based correlation, robust to outliers.

---

**Kendall Correlation**

.. math::

    \tau = \frac{(C - D)}{\sqrt{(C + D + T)(C + D + U)}}

Measures the ordinal association between two measured quantities.

---

**Partial Correlation**

.. math::

    \rho_{ij \cdot rest} = -\frac{\Theta_{ij}}{\sqrt{\Theta_{ii} \Theta_{jj}}}

Where \(\Theta = \Sigma^{-1}\) is the inverse covariance matrix (precision matrix).

---

**Cosine Similarity**

.. math::

    \text{cos}(\theta) = \frac{X_i \cdot X_j}{\|X_i\| \|X_j\|}

Computes angular similarity between ROI signals.

---

**Correlations of Correlations**

This method computes the correlation between each ROI’s correlation profile (i.e., vector of its correlations with all other ROIs).

.. math::

    M_{ij} = \text{corr}(C_i, C_j)

Where \(C_i\) is the correlation vector of ROI \(i\).

---

**Associated High Order FC**

Also computes second-order correlation:

.. math::

    A_{ij} = \text{corr}(C_i, C_j)

Similar to `correlations_correlation`, but may differ in scaling.

---

Distance-Based & KNN
====================

**Euclidean Distance**

.. math::

    d(X_i, X_j) = \sqrt{\sum_{t=1}^{T} (X_{i,t} - X_{j,t})^2}

Distances are optionally inverted into similarity scores.

---

**K-Nearest Neighbors (KNN)**

Constructs a sparse graph based on neighborhood size \(k\). No edge weights unless distance is used.

---

Information-Theoretic Methods
=============================

**Mutual Information**

Estimates the mutual information:

.. math::

    I(X; Y) = \sum_{x \in X} \sum_{y \in Y} p(x, y) \log \frac{p(x, y)}{p(x)p(y)}

Captures nonlinear dependencies; estimated via binning or k-NN.

---

**Cross Correlation**

Computes time-lagged Pearson correlation:

.. math::

    \text{XCORR}_{ij}(\tau) = \frac{1}{T} \sum_{t=1}^{T-\tau} X_{i,t} \cdot X_{j,t+\tau}

You can set lag = 0 for classic correlation.

---

Causal & Synchrony-Based Methods
================================

**Granger Causality**

Time series \(X\) is said to Granger-cause \(Y\) if the past of \(X\) helps predict \(Y\):

.. math::

    Y_t = \sum_{i=1}^p a_i Y_{t-i} + \sum_{j=1}^q b_j X_{t-j} + \epsilon_t

If coefficients \(b_j\) are significant, then \(X \to Y\).

⚠️ Slower than simple correlation methods.

---

**LiNGAM**

Linear non-Gaussian Acyclic Model. Learns a causal graph by ICA + regression.

.. math::

    X = B X + E

Where \(B\) is strictly lower triangular and \(E\) are non-Gaussian errors.

⚠️ Very slow and sensitive to sample size.

---

**Patel’s Conditional Dependence Measures**

These methods estimate conditional dependency between variables under different statistical assumptions.

- **Patel’s Kappa** (\(\kappa\)): Strength of conditional dependence
- **Patel’s Tau** (\(\tau\)): Direction of dependence

⚠️ May require large sample sizes for stable estimation.

---

**Generalized Synchronization Matrix**

Estimates synchrony between dynamical systems by measuring mutual predictability between time series.

⚠️ Extremely slow; only recommended for small datasets.

----

.. note::
   All methods output a symmetric or directed connectivity matrix (depending on method).
   These matrices are post-processed into edge lists or PyTorch Geometric graphs.
   Use `--format pt` or `--format csv` to control output.

