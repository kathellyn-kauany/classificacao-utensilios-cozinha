# 🍴 Kitchen Utensil Classification via Computer Vision

>This repository contains experiments involving **kitchen utensil image classification**, developed using **Teachable Machine** and exported through **TensorFlow.js**.
The objective of this project is to analyze how the **quantity and diversity of the dataset** affect **overfitting** and the model's **generalization capability** in a computer vision classification task.

---

## 📁 Repository Structure

```text
.
├── README.md
├── v1_baseline/            # Initial model (reduced dataset)
│   ├── model.json
│   ├── weights.bin
│   └── metadata.json
└── v2_expanded/            # Final model (expanded dataset)
    ├── model.json
    ├── weights.bin
    └── metadata.json
```

---

## 🔬 Experiments Conducted

### Version 1: Baseline Model

**5 images per class**

* **Objective:** Establish an initial model with a minimal amount of data to evaluate its limitations.
* **Dataset:** 12 classes with 5 images each, totaling **60 images**.

#### ⚙️ Training Parameters

| Parameter         | Value |
| ----------------- | ----: |
| **Epochs**        |    50 |
| **Batch Size**    |    16 |
| **Learning Rate** | 0.001 |

### 🔎 Error Analysis and Identified Bias

#### Geometry Bias — Cutting Board

The model was trained exclusively with rectangular cutting boards. When tested with an oval cutting board, the model classified it as a **"plate"**.

This behavior indicates that feature extraction was strongly influenced by the **object's outline geometry**, rather than adequately considering its texture and context.

#### Color and Material Confusion

Highly reflective metal utensils exhibited cross-classification errors. Similarities in **reflections, colors, and surface textures** contributed to this confusion, particularly due to the limited size of the dataset.

#### Environmental Sensitivity

Due to the small number of training samples, the model showed a tendency to memorize environmental characteristics such as **lighting, background, and scene elements**.

As a result, classification confidence decreased when the model was exposed to environments different from those present in the training dataset.

---

### Version 2: Expanded Dataset

* **Objective:** Mitigate overfitting and improve recognition across different angles, shapes, and lighting conditions.
* **Dataset:** 12 classes with an expanded number of images per category.

#### ⚙️ Training Parameters

| Parameter         | Value |
| ----------------- | ----: |
| **Epochs**        | *TBD* |
| **Batch Size**    | *TBD* |
| **Learning Rate** | *TBD* |

**Status:** 🚧 In development and accuracy testing.

---

## 📊 Comparative Metrics

| Metric / Parameter      |                      Version 1 — Baseline | Version 2 — Expanded |
| ----------------------- | ----------------------------------------: | -------------------: |
| **Classes**             |                                        12 |                   12 |
| **Images per Class**    |                                         5 |                *TBD* |
| **Total Images**        |                                        60 |                *TBD* |
| **Shape Variance**      |           Low — Single geometry per class |           *Expanded* |
| **Primary Limitations** |     Overfitting and shape/background bias |         *In Testing* |
| **Generalization**      | Poor — Low confidence in new environments |         *In Testing* |

---

## 🛠️ Technologies Used

### Python / Google Colab

Used for **automated data extraction, sampling, and subfolder filtering** from datasets obtained from Kaggle.

### Teachable Machine

Used as an interactive tool for **training neural networks for image classification**.

### TensorFlow.js

Used for **exporting the trained model** and deploying it in web applications, enabling inference directly on the client side.

---

## 🎯 Experiment Objective

The experiment aims to demonstrate, in practice, the relationship between **data quantity, image diversity, overfitting, and generalization capability** in computer vision models.

The comparison between the two versions allows us to observe how expanding and diversifying the dataset can contribute to building a more robust model that is less dependent on specific characteristics of the images used during training.
