# PPEproject
# 🦺 PPE Detection using YOLOv11

A deep learning project to detect **Personal Protective Equipment (PPE)** — specifically safety vests — in images and videos using the YOLOv11 object detection model, trained on the Roboflow Safety Vests dataset.

---

## 📌 Project Overview

This project fine-tunes a YOLOv11 model to detect whether workers are wearing safety vests in real-time. It can be applied to construction sites, warehouses, and industrial environments to automate safety compliance monitoring.

---

## 🚀 Features

- ✅ Detects safety vests in images and videos
- ✅ Trained using YOLOv11 (Ultralytics)
- ✅ Dataset sourced from Roboflow Universe
- ✅ Inference on images and video files
- ✅ Model export and download support

---

## 🗂️ Project Structure

```
PPEproject/
│
├── PPE_detection.ipynb       # Main Jupyter Notebook (Google Colab)
├── runs/
│   └── detect/
│       └── train/
│           └── weights/
│               ├── best.pt   # Best trained model weights
│               └── last.pt   # Last epoch weights
└── README.md
```

---

## 🛠️ Tech Stack

| Tool | Purpose |
|------|---------|
| Python | Core language |
| YOLOv11 (Ultralytics) | Object detection model |
| Roboflow | Dataset management |
| Google Colab | Training environment |
| KaggleHub | Dataset download |
| Streamlit | Results download UI |
| FFmpeg | Video compression |

---

## 📦 Installation

```bash
pip install ultralytics roboflow kagglehub streamlit
```

---

## 🔑 Setup: Roboflow API Key

1. Go to [Roboflow](https://roboflow.com) and get your API key
2. In Google Colab, click the 🔑 **Secrets** icon in the left sidebar
3. Add a new secret: `ROBOFLOW_API_KEY` → paste your key
4. Turn **ON** the "Notebook access" toggle

---

## 🧠 Model Training

```python
from ultralytics import YOLO

model = YOLO('yolo11n.pt')
model.train(data='path/to/data.yaml', epochs=10, imgsz=640)
```

---

## 🔍 Running Inference

**On images:**
```bash
yolo task=detect mode=predict model=best.pt conf=0.25 source=test/images save=True
```

**On video:**
```bash
yolo task=detect mode=predict model=best.pt source=video.mp4 conf=0.25 save=True
```

---

## 📊 Results

Training results including confusion matrix, label distribution, and accuracy curves are saved in:
```
/runs/detect/train/
```

---

## 💾 Model Download

After training, download the best model weights:
```python
from google.colab import files
files.download('/content/runs/detect/train/weights/best.pt')
```

Or save to Google Drive:
```python
from google.colab import drive
drive.mount('/content/drive')
!cp /content/runs/detect/train/weights/best.pt /content/drive/MyDrive/best.pt
```

---

## 📁 Dataset

- **Source:** [Roboflow Universe — Safety Vests](https://universe.roboflow.com/roboflow-universe-projects/safety-vests)
- **Version:** 14
- **Format:** YOLOv11

---

## 👤 Author

**Sayan Laha**  
GitHub: [@Sayan-Laha-2005](https://github.com/Sayan-Laha-2005)

---

## 📄 License

This project is open-source and available under the [MIT License](LICENSE).
