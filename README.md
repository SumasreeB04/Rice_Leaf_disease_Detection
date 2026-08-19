# 🌾 Rice Leaf Disease Detection

![Python](https://img.shields.io/badge/Python-3.x-blue?logo=python&logoColor=white)
![TensorFlow](https://img.shields.io/badge/TensorFlow-2.x-orange?logo=tensorflow&logoColor=white)
![Keras](https://img.shields.io/badge/Keras-Deep%20Learning-red?logo=keras&logoColor=white)
![License](https://img.shields.io/badge/License-MIT-green)
![Status](https://img.shields.io/badge/Status-Active-brightgreen)

A deep learning image classifier that detects and classifies rice leaf diseases from photos, using **transfer learning with MobileNetV2**. Built to help identify crop diseases early and support precision agriculture.

---

## 📋 Table of Contents

- [Overview](#-overview)
- [Demo](#-demo)
- [Tech Stack](#-tech-stack)
- [Project Structure](#-project-structure)
- [Dataset](#-dataset)
- [Installation](#-installation)
- [Usage](#-usage)
- [Model Architecture](#-model-architecture)
- [Results](#-results)
- [Future Improvements](#-future-improvements)
- [License](#-license)

---

## 🔍 Overview

Rice is one of the world's most important staple crops, and leaf diseases can significantly reduce yield if not caught early. This project uses a convolutional neural network (built on top of pretrained **MobileNetV2**) to automatically classify rice leaf images into disease categories, enabling fast, low-cost, image-based diagnosis.

## 🎥 Demo

> *Add a screenshot, GIF, or sample prediction output here once available.*

```
Input: leaf_sample.jpg  →  Prediction: Bacterial Leaf Blight (98.3% confidence)
```

## 🛠 Tech Stack

- **Language:** Python 3
- **Framework:** TensorFlow / Keras
- **Model:** MobileNetV2 (transfer learning, ImageNet weights)
- **Environment:** Jupyter Notebook

## 📁 Project Structure

```
rice-leaf-disease-detection/
├── Rice_Leaf_Disease_Detection.ipynb   # Main notebook (data prep, training, saving model)
├── PRCP-1001-RiceLeaf.zip              # Dataset (not included — see Dataset section)
├── rice_leaf_model.keras               # Trained model (generated after running)
└── README.md
```

## 📊 Dataset

- **Expected file:** `PRCP-1001-RiceLeaf.zip`
- Place the zip file in the project's root directory before running the notebook.
- The notebook automatically extracts it to `riceleaf_data/` and locates the folder containing the class subdirectories.
- Expected structure inside the zip (one folder per disease class):

```
riceleaf_data/
└── <root_folder>/
    ├── Bacterial_leaf_blight/
    ├── Brown_spot/
    ├── Leaf_smut/
    └── .../
```

> 💡 If your dataset has a different name or folder layout, just update the `zip_path` / `extract_dir` variables in the notebook, or point `root` directly to your data folder.

## ⚙️ Installation

```bash
git clone https://github.com/<your-username>/rice-leaf-disease-detection.git
cd rice-leaf-disease-detection
pip install tensorflow
```

Then place your dataset zip in the project folder and launch the notebook:

```bash
jupyter notebook Rice_Leaf_Disease_Detection.ipynb
```

## ▶️ Usage

1. Add `PRCP-1001-RiceLeaf.zip` (or your own dataset) to the project directory.
2. Run all cells in the notebook, in order.
3. The trained model is saved automatically as `rice_leaf_model.keras`.
4. Load the model for inference:

```python
import tensorflow as tf

model = tf.keras.models.load_model('rice_leaf_model.keras')
predictions = model.predict(your_image_batch)
```

## 🧠 Model Architecture

| Stage | Details |
|---|---|
| Input | 224×224×3 RGB images |
| Augmentation | Random horizontal flip, rotation (±10%), zoom (±10%) |
| Backbone | MobileNetV2 (pretrained on ImageNet, frozen) |
| Pooling | Global Average Pooling 2D |
| Regularization | Dropout (0.2) |
| Output | Dense layer, softmax activation (per-class probability) |
| Optimizer | Adam |
| Loss | Sparse Categorical Crossentropy |
| Epochs | 10 |

## 📈 Results

> *Add your training/validation accuracy and loss curves, plus a confusion matrix, once you've run the notebook on your dataset.*

| Metric | Value |
|---|---|
| Training Accuracy | TBD |
| Validation Accuracy | TBD |

## 🚀 Future Improvements

- [ ] Fine-tune top layers of MobileNetV2 for higher accuracy
- [ ] Add early stopping / learning rate scheduling
- [ ] Deploy as a web app (Streamlit / Flask) for real-time predictions
- [ ] Expand dataset with more disease classes and real-field images
- [ ] Add model evaluation notebook (confusion matrix, classification report)

## 📄 License

This project is licensed under the [MIT License](LICENSE).

---

⭐ If you find this project useful, consider giving it a star!
