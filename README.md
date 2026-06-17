<div align="center">
  <video src="https://github.com/user-attachments/assets/5d861314-ef58-433e-939c-03dc006e573d" autoplay loop muted playsinline width="100%"></video>
  
  # Multi-Layer Perceptron (MLP) for DNA Methylation Classification
  
  <i>A hands-on project based on the "Foundations of Deep Learning" course by NPTEL - Indian Institute of Science (IISc), Bengaluru.</i>
</div>

---

## 📌 Project Overview
This project implements a **Multi-Layer Perceptron (MLP)** to classify the methylation status of DNA sequences based on genomic features. The model is built using TensorFlow/Keras and incorporates best practices like **L2 Regularization** and **Early Stopping** to prevent overfitting, as taught in the IISc Deep Learning foundations course.

## 📊 Dataset Details
The model is trained on a dataset (`full_dataset.csv`) comprising **1,000 samples**. This dataset is a simplified genomics dataset where the goal is to predict whether a CpG site is methylated (`methylation_status`). 

DNA methylation occurs when a methyl group attaches to a Cytosine followed by a Guanine (a CpG site). It acts like a biological switch: more methylation generally means a gene is less active, while less methylation means it's more active.

**Target Variable:**
- `methylation_status` (Binary Classification)
  - **0**: Unmethylated (446 samples)
  - **1**: Methylated (554 samples)

**Input Features (4):**

1. **`cpg_density`** (Range: ~0.05 - 1.0)
   - **What is it?** Measures how many CpG sites are packed into a genomic region.
   - **Biological Intuition:** High density regions (CpG islands) are often found near gene promoters which need to be switched ON. Therefore, high density usually implies unmethylated, while low density implies methylated.

2. **`genomic_location`** (Range: 0.0 - 1.0)
   - **What is it?** Normalized position in a chromosome.
   - **Biological Intuition:** Different parts of chromosomes (gene-rich vs. repetitive DNA) behave differently. The model learns which locations are more likely to be methylated.

3. **`regulatory_score`** (Range: 0.0 - 1.0)
   - **What is it?** Measures how likely a DNA region regulates genes (e.g., promoters, enhancers).
   - **Biological Intuition:** Regulatory regions need to remain accessible, so heavy methylation would block them. High regulatory scores usually indicate less methylation.

4. **`conservation_score`** (Range: ~0.06 - 1.0)
   - **What is it?** Measures how similar a DNA region remains across species.
   - **Biological Intuition:** Highly conserved regions often contain important functional elements and have special methylation patterns. High conservation implies biological importance.

## 🧠 Model Architecture
The neural network follows a sequential architecture with the following layers:
- **Input Layer:** 4 neurons (matching the input features)
- **Hidden Layer 1:** 16 neurons, `ReLU` activation, L2 Regularization (penalty=0.001)
- **Hidden Layer 2:** 8 neurons, `ReLU` activation, L2 Regularization (penalty=0.001)
- **Output Layer:** 1 neuron, `Sigmoid` activation

## ⚙️ Training Configuration
- **Optimizer:** Adam
- **Loss Function:** Binary Crossentropy
- **Epochs:** 50 (with Early Stopping, patience=5)
- **Batch Size:** 32
- **Validation Split:** 20%

## 📈 Performance & Results
The model achieves exceptional performance on the holdout test set (20% of the dataset):
- **Final Test Accuracy:** **97.00%**
- **Precision:** ~0.98 (Methylated), ~0.96 (Unmethylated)
- **Recall:** ~0.96 (Methylated), ~0.98 (Unmethylated)
- **F1-Score:** ~0.97

## 🎓 Course Reference
This project was built following the concepts taught in the NPTEL lecture series:
- **Lec 10:** Hands-on on MLP for classification problem
- **Lec 09:** Regularization techniques in Neural Networks
- **Lec 08:** Variants of Gradient descent and Momentum based techniques
- **Lec 07:** Backpropagation in Neural Network
- **Lec 06:** Gradient descent algorithm
- **Lec 05:** Activation and Loss Functions
- **Lec 04:** Multi-Layer Perceptron
