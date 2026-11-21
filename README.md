# Infectious-Skin-Disease-Dataset
A high-quality image dataset of infectious skin diseases. Includes clinical annotations, preprocessing scripts, and multi-class classification benchmarks for medical computer vision

Infectious Skin Disease Dataset

**A curated, high-quality image dataset of 1,428 clinical images across viral infections and healthy skin controls, optimized for training computer vision models.** This repository contains the documentation, metadata structure, and utility scripts for managing and utilizing the dataset in deep learning applications (such as CNNs, ViTs, and object detection frameworks).

---

🔍 About the Dataset

Infectious skin diseases remain a significant global health burden, especially in regions with limited access to dermatological care. Automated computer-aided diagnosis (CAD) systems require highly precise, well-annotated images to differentiate between viral exanthems and healthy skin. 

This dataset provides a standardized benchmark for medical computer vision research by gathering clinical images across major viral skin conditions alongside healthy control samples.

✨ Key Features

* **Multi-Class Classification:** Covers three major viral skin conditions and a healthy control class.
* **1,428 Total Images:** Highly focused image distribution specifically addressing lookalike viral rashes.
* **Preprocessed & Raw Formats:** Optimized image sizes ready for deep learning pipelines.
* **Balanced Split:** Includes suggested directory distributions for `train`, `val`, and `test` splits.

🗂️ Dataset Structure

The repository organizes data cleanly to allow rapid integration with standard frameworks like PyTorch, TensorFlow, and Hugging Face Transformers:

```text
Infectious-Skin-Disease-Dataset/
├── data/
│   ├── train/
│   │   ├── Monkeypox/
│   │   ├── Chickenpox/
│   │   ├── Measles/
│   │   └── Normal/
│   ├── val/
│   │   └── ... (structured by class)
│   └── test/
│       └── ... (structured by class)
├── metadata/
│   ├── class_labels.json
│   └── dataset_summary.csv
├── scripts/
│   ├── data_augmentation.py
│   ├── image_preprocessing.py
│   └── check_dataset_health.py
├── LICENSE
└── README.md
```

 🦠 Categories & Distribution

The dataset features a total of **1,428 images** distributed across four primary classes:

| Class Label | Condition / Virus | Image Count |
| :--- | :--- | :--- |
| **Monkeypox** | Monkeypox Virus (MPXV) | 543 images |
| **Normal** | Healthy Skin Controls | 508 images |
| **Chickenpox** | Varicella Zoster Virus | 207 images |
| **Measles** | Morbillivirus | 170 images |
| **Total** | — | **1,428 images** |



🚀 Getting Started

### 1. Prerequisites
Ensure you have the required dependencies installed for running the utility scripts:
```bash
pip install -r requirements.txt
```
*(Dependencies typically include: `numpy`, `pandas`, `opencv-python`, `pillow`, `scikit-learn`)*


 2. Preprocessing Images
To resize, normalize, and split your raw images according to the configurations:
```bash
python scripts/image_preprocessing.py --input_dir ./raw_images --output_dir ./data
```



3. Data Augmentation
Because medical imaging datasets often suffer from class imbalances, you can use the built-in augmentation script to artificially balance minor classes like Measles and Chickenpox:
```bash
python scripts/data_augmentation.py --target_class Measles --multiplier 2
```


📈 Baseline Implementation

This dataset is compatible with major deep learning backends. You can quickly pull the structured data into a PyTorch `ImageFolder` or a TensorFlow `image_dataset_from_directory` pipeline:

```python
# PyTorch Example
import torchvision.transforms as transforms
from torchvision.datasets import ImageFolder
from torch.utils.data import DataLoader

transform = transforms.Compose([
    transforms.Resize((224, 224)),
    transforms.ToTensor(),
    transforms.Normalize(mean=[0.485, 0.456, 0.406], std=[0.229, 0.224, 0.225])
])

train_dataset = ImageFolder(root='data/train', transform=transform)
train_loader = DataLoader(train_dataset, batch_size=32, shuffle=True)
```


⚖️ License & Ethical Use

* **License:** This dataset is distributed under the [MIT License](LICENSE) (or CC BY-NC-SA 4.0).
* **Medical Disclaimer:** This dataset is provided strictly for academic research and educational development. The models trained on this dataset should **not** be treated as professional medical advice or as a standalone diagnostic system in clinical workflows.
