
# Enhanced SRGAN for Image Super-Resolution

This repository contains the source code, training scripts, evaluation scripts, and comparative results report for the enhanced SRGAN model developed as part of **Task 2**.

We enhance the original SRGAN architecture by incorporating concepts from **ESRGAN**, mainly the use of **Residual-in-Residual Dense Blocks (RRDB)** without Batch Normalization, and using **L1 loss** instead of MSE. Evaluation is done using PSNR and SSIM metrics.

---

## 📁 Project Structure

```
Enhanced-SRGAN-Super-Resolution/
│
├── models/
│   ├── srgan_original.py         # Original SRGAN model
│   └── enhanced_rrdbnet.py       # Enhanced RRDB generator
│
├── utils/
│   ├── dataset.py                # DIV2K LR/HR dataset loader
│   ├── metrics.py                # PSNR, SSIM computation
│
├── train_srgan.py                # Training script for SRGAN
├── train_enhanced.py             # Training script for Enhanced Model
├── evaluate.py                   # Evaluation and comparison logic
│
├── results/
│   ├── generated_images/         # Saved outputs for visual comparison
│
├── README.md                     # This file
└── report_task2.pdf              # IEEE format report with results
```

---

## ⚙️ Setup Instructions

### 1. Clone the Repository

```bash
git clone https://github.com/yourusername/Enhanced-SRGAN-Super-Resolution.git
cd Enhanced-SRGAN-Super-Resolution
```

### 2. Install Dependencies

```bash
pip install -r requirements.txt
```

Required packages include:
- torch
- torchvision
- numpy
- scikit-image
- tqdm
- matplotlib

---

## 📦 Dataset (DIV2K)

Download DIV2K dataset (as per SRGAN paper):

- HR Images: http://data.vision.ee.ethz.ch/cvl/DIV2K/DIV2K_train_HR.zip
- LR Images (X4): http://data.vision.ee.ethz.ch/cvl/DIV2K/DIV2K_train_LR_bicubic_X4.zip

Unzip both into a common directory (e.g., `data/`).

```
data/
├── DIV2K_train_HR/
│   ├── 0001.png
│   ├── ...
├── DIV2K_train_LR_bicubic/X4/
│   ├── 0001x4.png
│   ├── ...
```

---

## 🏃‍♂️ Running the Code

### A. Train SRGAN (Original)

```bash
python train_srgan.py
```

### B. Train Enhanced Model (RRDBNet)

```bash
python train_enhanced.py
```

### C. Evaluate and Compare

```bash
python evaluate.py
```

This computes PSNR and SSIM scores on a sample test set and saves visual outputs.

---

## 🔬 Model Enhancements

| Feature                  | SRGAN                  | Enhanced Model (Task 2)      |
|--------------------------|------------------------|-------------------------------|
| Residual Blocks          | Simple + BatchNorm     | RRDB (No BatchNorm)           |
| Loss Function            | MSE                    | L1 Loss                        |
| Upsampling Method        | PixelShuffle           | Nearest + Conv2D              |
| Evaluation               | Visual Only            | PSNR + SSIM                   |

---

## 📈 Results

| Model             | PSNR (dB) | SSIM  |
|------------------|-----------|-------|
| SRGAN (Original) | 23.85     | 0.675 |
| Enhanced Model    | **26.14** | **0.725** |

- The enhanced model demonstrates better edge sharpness, texture preservation, and less artifacting.

---

## 📑 Report & Submission

- `report_task2.pdf`: Written in IEEE format.
- Includes visual comparisons, methodology, architecture changes, and evaluation metrics.

---

## 🔮 Future Work

- Add perceptual loss and adversarial loss back to enhanced model.
- Train on larger batch size using Colab Pro / GPU.
- Extend to Real-ESRGAN with real-world noisy data.

---

## 📚 References

- Ledig et al., "Photo-Realistic Single Image Super-Resolution Using a Generative Adversarial Network" (SRGAN) — [arXiv:1609.04802](https://arxiv.org/abs/1609.04802)
- Wang et al., "ESRGAN: Enhanced Super-Resolution Generative Adversarial Networks" — [arXiv:1809.00219](https://arxiv.org/abs/1809.00219)
- RCAN: Residual Channel Attention Networks — [arXiv:1807.02758](https://arxiv.org/abs/1807.02758)
