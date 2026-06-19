<div align="center">

<h1 align="center">🎯 Support Vector Machines — Course Presentation</h1>
<h3 align="center">Artificial Intelligence Course | Sharif University of Technology</h3>

[**GitHub**](https://github.com/javdaninasim/SupportVectorMachine_Presentation_Spring_2025) &nbsp; ⬩ &nbsp; [**University**](https://sharif.edu/)

</div>

---

### 📚 Course Overview

```python
class SupportVectorMachines:
    def __init__(self):
        self.institution = "Sharif University of Technology"
        self.instructor = "AI Faculty"
        self.semester = "Spring 2025"
        self.format = "Presentation Slides (PDF)"
        
    def topics_covered(self):
        return {
            "Fundamentals": ["Margin-based Learning", "Geometric Intuition", "Classification Problem"],
            "Hard-Margin SVM": ["Constrained Optimization", "Lagrangian Duality", "KKT Conditions"],
            "Soft-Margin SVM": ["Slack Variables", "Regularization Parameter C", "Bias-Variance Trade-off"],
            "Kernel Methods": ["Kernel Trick", "Feature Space Mapping", "Common Kernels"],
            "Multi-Class": ["One-vs-One Strategy", "One-vs-All Strategy", "Performance Comparison"],
            "Applications": ["Text Classification", "Image Recognition", "Bioinformatics"],
            "Comparisons": ["vs. Logistic Regression", "vs. Decision Trees", "vs. Neural Networks"]
        }
    
    def mission(self):
        return "Master Support Vector Machines from theoretical foundations to practical applications."
```

---

### 📂 Repository Structure

```
SupportVectorMachine_Presentation_Spring_2025/
│
└── 📊 SupportVectorMachine.pdf          # Complete presentation slides
    ├── Section 1: Motivation & Intuition
    ├── Section 2: Hard-Margin SVM Theory
    ├── Section 3: Soft-Margin SVM & Regularization
    ├── Section 4: Kernel Methods & Tricks
    ├── Section 5: Multi-Class SVM Strategies
    ├── Section 6: Real-World Applications
    └── Section 7: Comparative Analysis
```

---

### 🎓 Presentation Content Breakdown

| Section | Topic | Key Concepts | Slides |
| :---: | :--- | :--- | :--- |
| **1** | **Motivation & Intuition** | Classification problem, decision boundaries, margin maximization | 1-5 |
| **2** | **Hard-Margin SVM** | Quadratic optimization, support vectors, primal/dual formulation, KKT conditions | 6-15 |
| **3** | **Soft-Margin SVM** | Slack variables, regularization, parameter C, overfitting control | 16-25 |
| **4** | **Kernel Methods** | Kernel trick, implicit mapping, linear/polynomial/RBF/sigmoid kernels | 26-40 |
| **5** | **Multi-Class SVM** | One-vs-One (OvO), One-vs-All (OvA), strategy comparison | 41-50 |
| **6** | **Applications** | Text classification, image recognition, bioinformatics use cases | 51-65 |
| **7** | **Comparative Analysis** | SVM vs. logistic regression, decision trees, neural networks | 66-75 |

---

### 📝 Detailed Section Descriptions

#### **Section 1: Motivation & Intuition** 🎯

**Objective:** Establish the foundation for understanding SVMs through geometric and intuitive reasoning.

**Topics Covered:**
- **The Classification Problem**
  - Binary classification task definition
  - Need for optimal decision boundaries
  - Why maximize margin vs. minimize error?

- **Good Decision Boundary Characteristics**
  - Separates classes with maximum gap (margin)
  - Generalizes well to unseen data
  - Robust to noise and outliers

- **Geometric Intuition**
  - Decision boundary as a hyperplane in feature space
  - Distance from point to hyperplane calculation
  - Maximum-margin principle visualization
  - Support vectors: critical data points defining the boundary

---

#### **Section 2: Hard-Margin SVM Theory** 🧮

**Objective:** Understand the mathematical formulation of SVM for perfectly separable data.

**Mathematical Formulation:**

**Primal Problem:**
```
minimize: (1/2) ||w||²

subject to: y_i(w^T φ(x_i) + b) ≥ 1, for all i
```

Where:
- **w**: weight vector
- **b**: bias term
- **y_i**: class label (-1 or +1)
- **φ(x_i)**: feature mapping (initially identity)
- **Margin**: 2/||w||

**Key Concepts:**
- **Constraint formulation:** Each sample must be correctly classified with margin ≥ 1
- **Support Vectors:** Data points where y_i(w^T x_i + b) = 1 (on the margin boundary)
- **Sparsity:** Only support vectors affect the decision boundary; other points are irrelevant

**Dual Problem (via Lagrangian Duality):**
```
maximize: Σ α_i - (1/2) Σ Σ α_i α_j y_i y_j K(x_i, x_j)

subject to: Σ α_i y_i = 0
            0 ≤ α_i
```

**KKT Conditions:**
- Complementary slackness: α_i[y_i(w^T x_i + b) - 1] = 0
- Only support vectors have α_i > 0
- Provides optimality conditions for the solution

**Output:** Decision function: `f(x) = sign(Σ α_i y_i K(x_i, x) + b)`

---

#### **Section 3: Soft-Margin SVM & Regularization** 📊

**Objective:** Extend SVM to handle non-separable (overlapping) data.

**Motivation:**
- Real-world data is often not linearly separable
- Hard margins lead to infeasible optimization problems
- Need to allow some margin violations

**Slack Variables (ξ_i):**
- ξ_i ≥ 0: represents amount of violation for sample i
- ξ_i = 0: sample correctly classified with margin ≥ 1
- ξ_i ∈ (0, 1): sample within margin but correct side
- ξ_i > 1: sample misclassified

**Soft-Margin Primal Problem:**
```
minimize: (1/2) ||w||² + C Σ ξ_i

subject to: y_i(w^T x_i + b) ≥ 1 - ξ_i
            ξ_i ≥ 0
```

**Regularization Parameter C:**
- **C → ∞**: Hard margin (maximize margin, minimize errors equally)
- **C → 0**: Soft margin (focus on maximizing margin, allow more errors)
- **C moderate**: Balance between margin and training error

**Bias-Variance Trade-off:**
- **Small C:** High bias, low variance (underfitting risk)
- **Large C:** Low bias, high variance (overfitting risk)
- Cross-validation for optimal C selection

**Soft-Margin Dual Problem:**
```
maximize: Σ α_i - (1/2) Σ Σ α_i α_j y_i y_j K(x_i, x_j)

subject to: Σ α_i y_i = 0
            0 ≤ α_i ≤ C
```

---

#### **Section 4: Kernel Methods & The Kernel Trick** 🔮

**Objective:** Enable SVM to learn nonlinear decision boundaries efficiently.

**The Kernel Trick:**
- **Explicit approach:** Transform to high-dimensional space, then apply SVM
  - Computationally expensive: O(d') where d' >> d
  - Memory intensive for high-dimensional representations

- **Kernel approach:** Compute inner products in high-dimensional space without explicit mapping
  - Computational cost: O(d) (original space complexity)
  - "Free" high-dimensional feature space

**Kernel Definition:**
```
K(x, x') = φ(x)^T φ(x')
```

Where φ maps to potentially infinite-dimensional space, but K computes the dot product directly.

**Common Kernels:**

| Kernel | Formula | Parameters | Use Case |
| :--- | :--- | :--- | :--- |
| **Linear** | K(x,x') = x^T x' | None | Linearly separable data |
| **Polynomial** | K(x,x') = (x^T x' + c)^d | c (offset), d (degree) | Moderate nonlinearity |
| **RBF (Gaussian)** | K(x,x') = exp(-γ\|\|x-x'\|\|²) | γ (bandwidth) | High flexibility |
| **Sigmoid** | K(x,x') = tanh(κx^T x' + θ) | κ, θ | Neural network-like |

**Kernel Selection Guide:**
- **Linear SVM (Linear kernel):** High-dimensional sparse data, text classification, quick training
- **Polynomial SVM:** Interaction features, medium datasets
- **RBF SVM:** Default choice, flexible, works for most nonlinear problems
- **Custom kernels:** Domain-specific kernels for specialized applications

**Mercer's Theorem:**
- Kernel K is valid if it's positive semi-definite
- Guarantees existence of feature space φ

---

#### **Section 5: Multi-Class SVM Strategies** 🎪

**Objective:** Extend binary SVM to multi-class classification problems.

**Strategy 1: One-vs-All (OvA)**
```
For K classes:
  Train K binary classifiers
  Classifier i: class i vs. all others
  
Prediction:
  f(x) = argmax_i f_i(x)
  
Score-based decision function
```

**Advantages:**
- K classifiers needed (efficient)
- Works well with large margins
- Single training phase per class

**Disadvantages:**
- Imbalanced training data (1 positive vs. K-1 negatives)
- Ambiguous classification regions (multiple classes with positive score)
- May produce inconsistent predictions

**Strategy 2: One-vs-One (OvO)**
```
For K classes:
  Train K(K-1)/2 binary classifiers
  Each classifier i vs. j: for all i < j
  
Prediction:
  Voting scheme: each classifier votes for one class
  f(x) = class with most votes
```

**Advantages:**
- Balanced training data (1 positive vs. 1 negative)
- Each classifier works on smaller, more focused subset
- Better generalization for some datasets

**Disadvantages:**
- More classifiers: O(K²) complexity
- Slower prediction (K(K-1)/2 evaluations)
- Voting ties possible (rare, but need tie-breaking)

**Comparison Table:**

| Aspect | One-vs-All | One-vs-One |
| :--- | :---: | :---: |
| **Number of Models** | K | K(K-1)/2 |
| **Training Time** | Faster | Slower |
| **Prediction Time** | Faster | Slower |
| **Data Balance** | Imbalanced | Balanced |
| **Generalization** | Good | Often Better |
| **Recommended For** | Large K, efficiency | Accuracy-focused |

---

#### **Section 6: Real-World Applications** 🚀

**Application 1: Text Classification**

**Pipeline:**
1. **Feature Extraction:** Bag-of-words (BoW) representation
   - Vocabulary: {word1, word2, ..., word_d}
   - Document representation: term frequency or TF-IDF vectors
   - High-dimensional sparse features (d = vocabulary size)

2. **Model:** Linear SVM
   - Natural choice for sparse, high-dimensional data
   - Computational efficiency: O(d_nonzero)
   - Interpretable: feature weights show important words

3. **Examples:**
   - Spam detection (spam vs. non-spam)
   - Sentiment analysis (positive vs. negative reviews)
   - Topic classification (multiple categories)

**Performance:** Often competitive with neural networks, simpler to deploy

---

**Application 2: Image Recognition**

**Pipeline:**
1. **Feature Extraction:** Histogram of Oriented Gradients (HOG)
   - Captures edge and gradient information
   - Robust to lighting variations
   - Dimensionality: 1,500-2,000 features per image

2. **Model:** RBF SVM (Radial Basis Function)
   - Handles nonlinear decision boundaries
   - Effective for natural images
   - Good generalization with moderate training set

3. **Examples:**
   - Face detection and recognition
   - Digit recognition (handwritten)
   - Object classification

**Performance:** Before deep learning era, achieved state-of-the-art on many benchmarks

---

**Application 3: Bioinformatics**

**Pipeline:**
1. **Feature Extraction:** Protein/gene sequences
   - Sequence embedding or kernel methods
   - Physicochemical properties
   - Domain-specific features

2. **Model:** Kernel SVM (custom kernels for biological sequences)
   - String kernels for sequence comparison
   - Handles variable-length inputs
   - Kernel design captures domain knowledge

3. **Examples:**
   - Protein function prediction
   - Gene expression classification
   - Disease biomarker identification

**Performance:** Interpretable, works with small sample sizes (crucial in biology)

---

#### **Section 7: Comparative Analysis** ⚖️

**SVM vs. Logistic Regression**

| Aspect | SVM | Logistic Regression |
| :--- | :--- | :--- |
| **Decision Boundary** | Margin-based | Probabilistic boundary |
| **Loss Function** | Hinge loss | Log loss (cross-entropy) |
| **Nonlinearity** | Via kernels | Not native; requires feature engineering |
| **Interpretability** | Support vectors are interpretable | Probability outputs; coefficients interpretable |
| **Scalability** | Slower on very large datasets | Faster; can use SGD |
| **When to Use** | Medium datasets, complex boundaries | Large datasets, need probabilities |

---

**SVM vs. Decision Trees**

| Aspect | SVM | Decision Trees |
| :--- | :--- | :--- |
| **Decision Boundary** | Continuous hyperplanes | Axis-aligned rectangles |
| **Nonlinearity** | Global; via kernels | Local; naturally nonlinear |
| **Interpretability** | Less interpretable (support vectors) | Highly interpretable |
| **Feature Scaling** | Necessary (distances matter) | Not required |
| **Overfitting** | Less prone (max-margin principle) | Prone (pruning needed) |
| **When to Use** | Complex, high-dimensional data | Interpretability critical |

---

**SVM vs. Neural Networks**

| Aspect | SVM | Neural Networks |
| :--- | :--- | :--- |
| **Data Requirements** | Works well with small-medium datasets | Needs large datasets |
| **Training Time** | Relatively fast (convex optimization) | Slow (non-convex, many iterations) |
| **Convergence** | Guaranteed global optimum | Local minima possible |
| **Feature Learning** | Manual feature engineering or kernels | Automatic feature learning |
| **Hyperparameters** | Few (C, kernel choice) | Many (architecture, learning rate, etc.) |
| **When to Use** | Small-medium data, limited compute | Large datasets, deep learning tasks |

---

### 💡 Key Learning Objectives

After this presentation, you should understand:

- ✨ **Theoretical Foundation** – Mathematical formulation of SVM (primal and dual)
- 🧠 **Geometric Intuition** – Why maximum margin works and when
- 🔮 **Kernel Methods** – How kernel trick enables nonlinear learning without explicit mapping
- 📊 **Practical Trade-offs** – How to choose between kernel types and C parameter
- 🎯 **Multi-Class Learning** – Strategies for extending binary SVM to multiple classes
- 🚀 **Real Applications** – Text, image, and bioinformatics use cases
- ⚖️ **Model Comparison** – When to use SVM vs. alternatives

---

### ⚡ Technologies & Tools

<div align="left">
  <img src="https://img.shields.io/badge/PDF-1A1A1A?style=for-the-badge&logo=adobe&logoColor=FF0000" alt="PDF" />
  <img src="https://img.shields.io/badge/LaTeX-1A1A1A?style=for-the-badge&logo=latex&logoColor=008080" alt="LaTeX" />
  <img src="https://img.shields.io/badge/Mathematics-1A1A1A?style=for-the-badge&logo=wolfram&logoColor=DD1100" alt="Mathematics" />
  <img src="https://img.shields.io/badge/Optimization-1A1A1A?style=for-the-badge&logo=scientific&logoColor=4A90E2" alt="Optimization" />
</div>

<br>

> **Core Topics:** Quadratic Programming ⬩ Convex Optimization ⬩ Lagrangian Duality ⬩ Kernel Theory ⬩ Statistical Learning

---

### 📖 Presentation Highlights

**Visual Elements:**
- Mathematical equations with step-by-step derivations
- Geometric visualizations of margins and decision boundaries
- Kernel transformation diagrams
- Comparative algorithm flowcharts
- Real-world application examples with sample outputs

**Theoretical Rigor:**
- Complete primal-dual derivation
- KKT conditions for optimality
- Proof sketches for key theorems
- Convergence properties

**Practical Focus:**
- Kernel selection guidelines
- Hyperparameter tuning strategies
- Code examples and pseudo-algorithms
- Common pitfalls and how to avoid them

---

### 🎯 Use Cases & Scenarios

**When SVM is the Right Choice:**
- ✅ Small-to-medium sized datasets (< 1M samples)
- ✅ High-dimensional feature spaces (100s-1000s of features)
- ✅ Clear margin-based decision boundaries
- ✅ Limited computational resources
- ✅ Need for theoretical guarantees
- ✅ Interpretability through support vectors is important

**When to Avoid SVM:**
- ❌ Very large datasets (millions of samples) → slow training
- ❌ Need for probabilistic outputs → use logistic regression
- ❌ Interpretability is paramount → use decision trees
- ❌ Deep learning features needed → use neural networks
- ❌ Streaming/online learning → use online algorithms

---

### 📞 Course Information

| Detail | Information |
| :--- | :--- |
| **Institution** | Sharif University of Technology, Dept. of Computer Engineering |
| **Course** | Artificial Intelligence (AI) |
| **Semester** | Spring 2025 (Farvardin-Ordibehesht 1404) |
| **Format** | Presentation Slides (PDF) |
| **Prerequisites** | Linear Algebra, Calculus, Machine Learning Basics |
| **Delivery** | Classroom presentation with discussion |

---

### 📜 About This Presentation

This presentation provides a comprehensive introduction to **Support Vector Machines**, covering:

1. **Mathematical Foundations** – From motivation to rigorous formulation
2. **Algorithmic Details** – Primal and dual optimization, KKT conditions
3. **Extensions** – Soft margins, kernels, multi-class strategies
4. **Practical Applications** – Real-world use cases across domains
5. **Comparative Analysis** – When and why to use SVM over alternatives

The presentation balances theoretical rigor with practical intuition, making SVM accessible to students new to the topic while providing depth for advanced learners.

---

### 👤 Author

**Nasim Javdani**  
Student Number: 402170013  
**GitHub:** [@javdaninasim](https://github.com/javdaninasim)  
**LinkedIn:** [Nasim Javdani](https://linkedin.com/in/nasim-javdani-810a9932a)

---

### 📚 Further Reading

**Recommended Resources:**
- Vapnik, V. (1995). "The Nature of Statistical Learning Theory" – Foundational SVM theory
- Schölkopf & Smola (2002). "Learning with Kernels" – Comprehensive kernel methods
- Boyd & Vandenberghe (2004). "Convex Optimization" – Mathematical foundations
- Scikit-learn SVM Documentation – Practical implementation guide

---

<div align="center">
  <img src="https://capsule-render.vercel.app/api?type=waving&color=FF6B6B&height=100&section=footer" width="100%"/>
</div>
