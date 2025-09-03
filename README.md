# Uranium-235 Neutron Scattering: Differential Cross-Section Modeling

This repository contains an experimental dataset of **Uranium-235 neutron differential cross-sections** at different scattering angles, together with Python code that applies multiple **Machine Learning (ML)** and **Physics-Informed Neural Network (PINN)** models to interpolate and predict values between measured points.  

The aim is to compare how different approaches capture the underlying physics of the scattering process.

---

## 📂 Contents
- `U235_neutron_cross_section_PINN.ipynb` – Main Jupyter notebook with data loading, training, and visualization.
- `data.csv` – Experimental dataset (angles vs differential cross-sections).
- `README.md` – This file.

---

## ⚛️ Models Used

We implemented **nine models** for interpolation and regression. They can be grouped into three categories:

### 1. Classical Interpolation
1. **Linear Interpolation**  
   - Connects data points with straight lines.  
   - Fast, but may fail to capture smooth variations in physical data.

2. **Cubic Spline Interpolation**  
   - Fits piecewise cubic polynomials between points with smooth derivatives.  
   - Produces smooth curves, often used in physics when continuity is required.

---

### 2. Machine Learning Regressors (Scikit-learn)
3. **Polynomial Regression**  
   - Extends linear regression to higher-degree polynomials of the angle.  
   - Captures nonlinear trends but may overfit if degree is too high.

4. **k-Nearest Neighbors (kNN) Regression**  
   - Predicts a value by averaging the closest training points.  
   - Good for local interpolation, but results may look “blocky” for sparse data.

5. **Support Vector Regression (SVR)**  
   - Uses kernel functions (e.g., RBF) to map data into higher dimensions.  
   - Excellent for smooth nonlinear regression.

6. **Random Forest Regression**  
   - Ensemble of decision trees, averaging their outputs.  
   - Captures nonlinearities and interactions, robust against overfitting.

7. **Gaussian Process Regression (GPR)**  
   - Bayesian method that models distributions over functions.  
   - Provides both predictions and uncertainty estimates, highly flexible.

---

### 3. Neural Networks
8. **Feedforward Neural Network (MLP Regressor)**  
   - A standard dense neural network trained to map angle → cross-section.  
   - Learns nonlinear relationships but requires careful tuning.

9. **Physics-Informed Neural Network (PINN)**  
   - A neural network trained not only on data but also with **physics-based constraints** (e.g., smoothness, conservation, boundary conditions).  
   - Encourages physically consistent interpolation and generalization beyond data points.

---

## 🔍 Comparison of Models
- **Interpolation methods** (Linear, Spline) → Simple, deterministic, but not predictive outside given points.  
- **ML regressors** → Capture nonlinear patterns, provide flexibility, but may require hyperparameter tuning.  
- **PINN** → Best balance of data-fitting and physics consistency; especially useful when extrapolating.

---


