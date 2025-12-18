# Food Safety in Commercial Kitchens: PPE Compliance Detection

Automated PPE (Personal Protective Equipment) compliance monitoring system for commercial kitchens using computer vision. This project uses multi-model detection with geometric verification to identify whether workers are properly wearing gloves and hairnets.

## 📄 Paper

**Food Safety in Commercial Kitchens: Geometric Verification for Robust PPE Compliance Detection**  
Advanced Topics in Computer Vision, Fall 2025

## 🚀 Key Features

- **Multi-model detection pipeline**: 4 specialized models (hairnet, head, glove, hand detection)
- **Geometric verification**: IoU-based verification to distinguish PPE presence from PPE usage
- **Four-class output**: `glove`, `no_glove`, `hairnet`, `no_hairnet`
- **Robust to challenging scenarios**: Handles occlusion, varying angles, different PPE types

## 📦 Repository Contents

- `ATCV_Glove_Model.ipynb` - Glove detection model training
- `ATCV_Hairnet_Model.ipynb` - Hairnet detection model training
- `ATCV_KitchenHygiene_CombinedPPEDetection.ipynb` - Complete pipeline implementation
- `Hand_Detection.ipynb` - Hand detection experiments

## 🔗 Project Artifacts

**All trained models, datasets, and results**: [Google Drive](https://drive.google.com/drive/folders/14F9BIFiv-zfcYdcvuvS_9uquAzZOA0Rb?usp=sharing)

## 🏗️ Architecture

```
Input Image
    ↓
┌─────────────────────────────────────┐
│  Multi-Model Detection              │
│  • Hairnet (YOLOv8)                 │
│  • Head (YOLOv8)                    │
│  • Glove (YOLOv8)                   │
│  • Hand (Faster R-CNN + FPN)        │
└─────────────────────────────────────┘
    ↓
┌─────────────────────────────────────┐
│  Geometric Verification             │
│  • IoU(PPE, Body Part) > threshold  │
│  • Hairnet ∩ Head                   │
│  • Glove ∩ (Hand OR Person)         │
└─────────────────────────────────────┘
    ↓
Final Classification:
glove | no_glove | hairnet | no_hairnet
```

## 🛠️ Setup

1. **Open notebooks in Google Colab** (recommended)
2. **Mount Google Drive** and update paths to model files
3. **Install dependencies**:
   ```python
   pip install ultralytics detectron2
   ```

## 📊 Results

- **Hairnet Detection**: mAP@50 = 93.5% (after negative sample augmentation)
- **Glove Detection**: mAP@50 = 92.0%
- **Verification**: Successfully filters false positives where PPE is present but not worn

## 🙏 Acknowledgments

- **Dataset**: Kitchen Hygiene dataset from [Alashrafi et al., 2025](https://www.mdpi.com/1424-8220/25/19/6140)
- **Hairnet Dataset**: Roboflow Hair-Net-Detection-3
- **Hand Detection**: Based on [hand_detector.d2](https://github.com/ddshan/hand_detector.d2)
- **Training Data**: Fine-tuned on 100 Days of Hands dataset (instructor-recommended)

## 👥 Team

- Agustin Leon (al8937)
- Anup Raj Niroula (arn8147)
- Kavya Khurana (kk5554)
- Samridh Srivastava (ss18906)

**Course**: Advanced Topics in Computer Vision  
**Institution**: NYU Tandon School of Engineering
