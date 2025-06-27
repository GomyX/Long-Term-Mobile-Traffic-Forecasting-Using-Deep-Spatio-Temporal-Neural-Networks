# Long-Term-Mobile-Traffic-Forecasting-Using-Deep-Spatio-Temporal-Neural-Networks


## 📘 About This Repository

This repository contains a full implementation and partial replication of the research paper:
**“Long-Term Mobile Traffic Forecasting Using Deep Spatio-Temporal Neural Networks (DSTN+)”**

### 🎯 Project Objective

The primary aim of this project was to replicate the core methodology proposed in the DSTN+ paper and evaluate its forecasting performance on a selected cluster of mobile traffic data in Milan. The project also explores potential algorithmic enhancements and provides a detailed analysis of the model's effectiveness at a fine-grained cell level.

---

### ✅ Key Contributions

* **Data Processing**:

  * Processed 9 weeks of 10-minute interval mobile traffic data from the Milan telecom dataset.
  * Applied cubic interpolation and time-slot-based statistical imputation to address missing data.
  * Performed outlier filtering using IQR-based detection per cell and time slot.

* **Spatiotemporal Tensor Construction**:

  * Transformed traffic volume into 3D tensors of shape `(T, H, W)` corresponding to time and spatial layout.
  * Focused on a 10×10 grid (100 cells), selected from high-traffic urban blocks.

* **Model Implementation**:

  * Implemented a modified version of the DSTN+ model (DeepSTN+ v2) using TensorFlow.
  * Integrated Conv3D, ConvLSTM2D layers, and late fusion mechanisms.
  * Developed and applied the **Ouroboros Training Scheme (OTS)** for continual self-supervised fine-tuning.

* **Evaluation**:

  * Conducted recursive forecasting up to 200 steps ahead.
  * Performed quantitative and visual evaluation on **CellID 4956**, a representative high-traffic cell.
  * Achieved an **NRMSE of 0.2385** over a 60-timestep forecast horizon (\~10 hours).

---

### 📊 Comparison with Original Paper

| Feature                   | Original DSTN+ Paper                  | This Implementation                 |
| ------------------------- | ------------------------------------- | ----------------------------------- |
| Forecast Scope            | Entire Milan Province (10,000+ cells) | Focused 10×10 grid (100 cells)      |
| Forecast Horizon          | Up to 72 time steps                   | Up to 200 time steps                |
| Evaluation Granularity    | Aggregate metrics across all cells    | Per-cell analysis (CellID 4956)     |
| Methodology               | DeepSTN+                              | DeepSTN+ v2 + Ouroboros fine-tuning |
| Best Performance Reported | NRMSE across the full grid            | **NRMSE = 0.2385** for CellID 4956  |

> 📌 *Note: While the original paper focused on the entire cellular grid, our implementation emphasizes fine-grained evaluation and model behavior on individual cells, with a focus on practical deployment scenarios.*

---

### 🧪 Research Goals & Extensions

Beyond replication, this project aimed to:

* Assess the feasibility of long-term traffic forecasting on localized clusters.
* Evaluate DSTN+ performance in sparse or dense traffic conditions.
* Explore the impact of recursive self-prediction via the Ouroboros Training Scheme (OTS).
* Propose a scalable framework for mobile traffic prediction in smart city applications.

---

### 🧑‍🏫 Academic Context

This work was conducted as a group project for an undergrad level course in Deep Learning & AI in telecom. The project adheres to the following academic guidelines:

* Dataset coverage of **at least 100 grids** within the Milan province.
* Selection of cells based on **traffic density and relevance**.
* Clear documentation of **methodology, experiments, and results**.
