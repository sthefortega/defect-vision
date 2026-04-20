# Cable Defect Detection using Computer Vision

_TLDR:_
CNN-based defect detection on MVTec AD (cables) — benchmarking ResNet, Siamese Networks, and YOLO, with YOLO yielding the best results.

## Project description
Manufacturing processes require quality inspection to ensure parts meet fit, form and function requirements. Part of these quality inspections is visual inspection, when it isn't automated, it often requires operator's time, skill, training and sometimes, even experience.

This project proposes an industrial prototype for automated visual inspection of manufacturing defects in coaxial cables, using the **MVTec Anomaly Detection (MVTec-AD)** dataset — cables category. The project evaluates and compares three deep learning architectures for binary classification (defective cable vs. good cable), aiming at real-world industrial deployment to reduce time and investment costs in visual quality inspections. 

---

## Objective

Develop and compare computer vision models capable of identifying anomalies in manufacturing cables, determining which architecture delivers the best performance for an industrial quality control prototype.

---

## Dataset

**MVTec-AD — Category: Cables**

- **Source:** [MVTec Anomaly Detection Dataset](https://www.mvtec.com/company/research/datasets/mvtec-ad)
- **Task type:** Binary classification — `good` / `defective` OR anomaly detection, depending on model
- **Defect types included:** bent wire, cable cut, combined, missing wire, peel, among others (no defect subcategory distinction in the final label)
- **Preprocessing:** Data augmentation applied to the training set

---
## Evaluated Models

### 1. ResNet (Transfer Learning)
Deep convolutional neural network pretrained on ImageNet, fine-tuned for binary defect classification.

- **Framework:** PyTorch
- **Strategy:** Transfer learning with retrained final layers

### 2. Siamese Networks
Architecture designed for similarity learning, comparing cable images against defect-free reference samples.

- **Framework:** PyTorch, sklearn OCSVM.
- **Strategy:** One-shot learning with image pairs (defective / reference)

### 3. YOLO (You Only Look Once)
Real-time detection model adapted for binary anomaly classification.

- **Framework:** Ultralytics YOLOv8
- **Strategy:** Detection and classification in a single forward pass

---

## Results (best obtained)

| Model            | Accuracy | 
|------------------|----------|
| ResNet           | 66.7%      | 
| Siamese Networks | 71.3%      |
| **YOLO**         | **96.7%**  |

> ✅ **YOLO achieved the best overall performance**, excelling in accuracy and inference speed, making it seems to be the most suitable architecture for real-time industrial deployment among these three options.

---

## Technologies Used

| Tool               | Purpose                              |
|--------------------|--------------------------------------|
| Python 3.x         | Main programming language            |
| PyTorch            | ResNet and Siamese Networks          |
| Ultralytics YOLOv8 | YOLO-based detection                 |
| torchvision        | Data transforms and base models      |
| scikit-learn       | Evaluation metrics                   |
| matplotlib / seaborn | Results visualization              |

---

<a target="_blank" href="https://cookiecutter-data-science.drivendata.org/">
    <img src="https://img.shields.io/badge/CCDS-Project%20template-328F97?logo=cookiecutter" />
</a>
## Project Organization

```
├── LICENSE            
├── Makefile           <- Makefile with convenience commands like `make data` or `make train`
├── README.md          <- The top-level README for developers using this project.
│
├── docs               <- A default mkdocs project; see www.mkdocs.org for details
│
├── models             <- Trained and serialized models, model predictions, or model summaries
│
├── notebooks          <- Jupyter notebooks
│   ├── 1.0-eot-resnet50.ipynb        <- ResNET50 model
│   ├── 2.0-eot-siameseOCSVM.ipynb    <- Siamese Network with OCSVM model
│   └── 3.0-eot-YOLO.ipynb            <- YOLO model
│
├── pyproject.toml     <- Project configuration file with package metadata for 
│                         defect_vision and configuration for tools like black
│
├── references         <- Data dictionaries, manuals, and all other explanatory materials.
│
├── reports            <- Generated analysis as HTML, PDF, LaTeX, etc.
│   └── figures        <- Generated graphics and figures to be used in reporting
│
├── requirements.txt   <- The requirements file for reproducing the analysis environment, e.g.
│                         generated with `pip freeze > requirements.txt`
│
├── setup.cfg          <- Configuration file for flake8
│
└── defect_vision   <- Source code for use in this project.
    │
    ├── __init__.py             <- Makes defect_vision a Python module
    │
    ├── config.py               <- Store useful variables and configuration
    │
    ├── dataset.py              <- Scripts to download or generate data
    │
    ├── features.py             <- Code to create features for modeling
    │
    ├── modeling                
    │   ├── __init__.py 
    │   ├── predict.py          <- Code to run model inference with trained models          
    │   └── train.py            <- Code to train models
    │
    └── plots.py                <- Code to create visualizations
```

--------


## References

- Bergmann, P. et al. (2019). *MVTec AD — A Comprehensive Real-World Dataset for Unsupervised Anomaly Detection*. CVPR.: https://www.kaggle.com/datasets/ipythonx/mvtec-ad 
- Ultralytics YOLOv8 Documentation: https://docs.ultralytics.com
- PyTorch Documentation: https://pytorch.org/docs

