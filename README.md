# Support Vector Machines — Course Presentation, Spring 2025

> Presentation for the **Artificial Intelligence** course at Sharif University of Technology, Spring 2025.  
> **Author:** Nasim Javdani · [GitHub](https://github.com/javdaninasim) · [LinkedIn](https://linkedin.com/in/nasim-javdani-810a9932a)

---

## Overview

This repository contains the slides for a course presentation on **Support Vector Machines (SVM)** — one of the most theoretically principled and practically powerful supervised learning algorithms. The presentation covers the mathematical foundations, geometric intuition, kernel methods, and real-world applications of SVMs.

---

## Repository Structure

```
SupportVectorMachine_Presentation_Spring_2025/
└── AI_Presentation.pdf     # Full presentation slides (PDF)
```

---

## Presentation Outline

### 1. Motivation & Intuition
- The classification problem and the need for a principled margin-based approach
- What makes a "good" decision boundary?
- Geometric intuition: maximum-margin hyperplane

### 2. Hard-Margin SVM (Linearly Separable Case)
- Formulation as a constrained quadratic optimization problem
- Support vectors and their role in defining the decision boundary
- Primal problem and its dual via Lagrangian duality
- KKT conditions and sparsity of the solution

### 3. Soft-Margin SVM (Non-Separable Case)
- Introduction of slack variables to handle overlapping classes
- The regularization parameter **C**: controlling the margin vs. misclassification trade-off
- Effect of C on the bias-variance balance

### 4. Kernel Methods
- The kernel trick: implicit mapping to high-dimensional feature spaces
- Common kernels:
  - **Linear**: `K(x, x') = xᵀx'`
  - **Polynomial**: `K(x, x') = (xᵀx' + c)^d`
  - **RBF (Gaussian)**: `K(x, x') = exp(-γ‖x − x'‖²)`
  - **Sigmoid**
- Choosing the right kernel for a given dataset

### 5. Multi-Class SVM
- One-vs-One (OvO) and One-vs-All (OvA) strategies
- Comparison of both approaches

### 6. Applications
- Text classification (bag-of-words + linear SVM)
- Image recognition (HOG features + RBF SVM)
- Bioinformatics (protein classification)

### 7. SVM vs. Other Models
- Comparison with logistic regression, decision trees, and neural networks
- When to use SVM: small-to-medium datasets, high-dimensional feature spaces

---

## Technologies

| Tool | Purpose |
|---|---|
| PowerPoint / LaTeX Beamer | Slide preparation |
| PDF | Distribution format |

---

## Course Info

- **Course:** Artificial Intelligence (AI)
- **Institution:** Sharif University of Technology, Department of Computer Engineering
- **Semester:** Spring 2025
