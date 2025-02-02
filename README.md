# 🚀 CIFAR-10 Classification | Analysis & Insights Report

This report provides an in-depth **analysis of CIFAR-10 classification using ResNet-32**, trained across multiple experiments with different hyperparameters. We used **Weights & Biases (W&B)** to track and compare model performance.

---

## 📢 **Project Links**
### 📂 **Google Colab Notebook**: [🔗 Open Colab](https://colab.research.google.com/drive/1YFFDvaYuUx-FVjWT_Qe0EBcsu_0MJURr?usp=sharing)
### 📊 **W&B Dashboard**: [🔗 View Experiments](https://wandb.ai/gauravengineer85-vellore-institute-of-technology/-Deep-Learning-Experiments-on-CIFAR-10)


---

## 📌 1. Overview
This report evaluates the **CIFAR-10 classification task using ResNet-32**, trained with different hyperparameters to optimize performance.

### **CIFAR-10 Dataset Description**
- **Dataset Size**: 60,000 32x32 color images
- **Classes**: 10 (airplanes, cars, birds, cats, deer, dogs, frogs, horses, ships, trucks)
- **Training Images**: 50,000
- **Testing Images**: 10,000
  

### **ResNet-32 Model Description**
- **Architecture**: Residual Network with 32 layers
- **Feature**: Shortcut connections to prevent vanishing gradients
- **Configuration**: Three groups of residual blocks
- **Specialty**: Effective for deep learning on small images like those in CIFAR-10

### **Key Performance Metrics**
| Run Name         | Optimizer | Learning Rate | Epochs | Test Accuracy | Train Accuracy | Validation Accuracy |
|-----------------|-----------|--------------|--------|--------------|--------------|-------------------|
| floral-surf-6   | SGD       | 0.1          | 85     | **91.62%**   | **98.94%**   | **91.78%**        |
| woven-snowball-5 | SGD      | 0.0005       | 10     | 62.63%       | 62.96%       | 61.86%            |
| different-haze-4 | SGD      | 0.001        | 10     | 69.82%       | 69.63%       | 69.00%            |
| clean-bee-3     | Adam      | 0.0001       | 12     | 72.93%       | 73.03%       | 71.75%            |
| rosy-plant-2    | Adam      | 0.5          | 10     | **10.04%**   | **10.45%**   | **9.97%**         |
| amber-breeze-1  | Adam      | 0.001        | 10     | 76.25%       | 81.39%       | 77.40%            |

---

## 📈 2. Experiment Comparisons Using W&B Dashboards
### **Key Observations**
- **Higher learning rates (0.5) caused extreme instability**, leading to poor performance (**rosy-plant-2: 10.04% accuracy**).
- **SGD with LR scheduling (`floral-surf-6`) provided the best performance**, achieving **91.62% test accuracy**.
- **Adam optimizer performed well for quick convergence**, but **plateaued around 76.25%** in `amber-breeze-1`.
- **Training with fewer epochs resulted in underperformance**, showing the importance of longer training runs.

---

## 🔬 3. How Hyperparameters Affected Performance

### **Impact of Learning Rate (LR)**
- **Best LR:** **0.1 (with decay at 50 & 75 epochs)** → Enabled **faster convergence and high accuracy**.
- **Worst LR:** **0.5** → Training was highly unstable, causing **extremely high loss and poor test accuracy (10.04%)**.

### **Optimizer Comparison: SGD vs. Adam**
- **SGD (momentum) outperformed Adam in longer runs**.
- **Adam was effective in short runs but plateaued below 80% accuracy**.

### **Effect of Training Epochs**
- **Less than 20 epochs led to underfitting**, with accuracy **below 70%** in most cases.
- **85 epochs provided strong generalization**, as seen in `floral-surf-6`.

---

## 🏆 4. Best Experiment & Why?
### **Best Performing Run: `floral-surf-6`**
- **Optimizer:** SGD (Momentum = 0.9)
- **Learning Rate:** 0.1 (with decay at 50 & 75 epochs)
- **Epochs:** 85
- **Test Accuracy:** **91.62%**
- **Validation Accuracy:** **91.78%**

### **Why was it the best?**
✅ **Effective LR Scheduling:** Allowed controlled optimization and smooth convergence.  
✅ **SGD with momentum stabilized training**, reducing variance in updates.  
✅ **Longer training (85 epochs) ensured strong feature extraction.**  

---

## 📌 5. Summary & Final Insights
- **SGD with momentum works best for longer training runs (85+ epochs).**  
- **High learning rates without decay lead to extreme instability.**  
- **Adam optimizer is effective but saturates below 80% accuracy.**  
- **The best accuracy achieved = 91.62% (`floral-surf-6`).**
