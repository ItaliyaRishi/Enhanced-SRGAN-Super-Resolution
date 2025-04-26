
#  Super-Resolution Using SRGAN and Enhanced SRGAN (Task 1 and Task 2)

This repository contains the source code, training scripts, evaluation logic, and comparison report for:
- **Task 1:** Replicating the original SRGAN paper results.
- **Task 2:** Enhancing the SRGAN architecture by integrating concepts from ESRGAN.

All experiments are conducted on the **DIV2K** dataset.

---

##  Project Structure

```
Super-Resolution-SRGAN/
│
├── srgan.ipynb                  # Task 1: SRGAN model training and evaluation
├── enhanced_srgan.ipynb          # Task 2: Enhanced model with ESRGAN ideas
│
├── data/                         # Contains HR and LR DIV2K images
│
├── results/
│   ├── srgan_outputs/           # Outputs from SRGAN model
│   ├── enhanced_outputs/        # Outputs from Enhanced model
│
├── README.md                     # Project overview (this file)
└── report_task1_task2.pdf         # Report comparing results (IEEE format)
```

---

##  Setup Instructions

### 1. Clone the Repository

```bash
git clone https://github.com/yourusername/Super-Resolution-SRGAN.git
cd Super-Resolution-SRGAN
```

### 2. Install Required Libraries

```bash
pip install torch torchvision numpy scikit-image matplotlib tqdm
```

---

##  Dataset (DIV2K)

We use the DIV2K dataset (high-resolution 2K images):

- **Download Links**:
  - HR Images: [DIV2K_train_HR.zip](http://data.vision.ee.ethz.ch/cvl/DIV2K/DIV2K_train_HR.zip)
  - LR Images (X4 bicubic): [DIV2K_train_LR_bicubic_X4.zip](http://data.vision.ee.ethz.ch/cvl/DIV2K/DIV2K_train_LR_bicubic_X4.zip)

**Directory Structure:**

```
data/
├── DIV2K_train_HR/               # High-Resolution Images
│   ├── 0001.png
│   ├── ...
├── DIV2K_train_LR_bicubic/X4/     # Low-Resolution Images (4x downsampled)
│   ├── 0001x4.png
│   ├── ...
```

---

##  How to Run

### A. Train SRGAN (Task 1)

Open and run the notebook:

```bash
srgan.ipynb
```

- **Model:** Original SRGAN with ResBlocks + BatchNorm
- **Loss:** MSE Loss
- **Optimizer:** Adam
- **Evaluation:** PSNR and SSIM on validation images.

---

### B. Train Enhanced Model (Task 2)

Open and run the notebook:

```bash
enhanced_srgan.ipynb
```

- **Model Enhancements:**
  - Residual-in-Residual Dense Blocks (RRDB) without BatchNorm
  - LeakyReLU activations
  - L1 Loss (more stable than MSE)
- **Evaluation:** PSNR and SSIM compared against Task 1.

---

##  Key Improvements (Task 2)

| Feature                  | SRGAN (Task 1)         | Enhanced SRGAN (Task 2) |
|---------------------------|------------------------|-------------------------|
| Residual Blocks           | Simple + BatchNorm      | RRDB (No BatchNorm)      |
| Loss Function             | MSE Loss                | L1 Loss                 |
| Upsampling Method         | Sub-pixel convolution   | Nearest Neighbor + Conv |
| Training Stability        | Moderate                | High                    |
| Evaluation Metrics        | PSNR, SSIM              | PSNR, SSIM              |

---

##  Results Summary

| Model             | PSNR (dB) | SSIM  |
|-------------------|-----------|-------|
| SRGAN (Task 1)     | ~21.00    | ~0.474 |
| Enhanced SRGAN (Task 2) | **~29.06** | **~0.829** |

- **Observation:** The enhanced model yields better sharpness, reduced blurriness, and higher structural similarity with ground truth.

---

##  References

- **SRGAN Paper:** [arXiv:1609.04802](https://arxiv.org/abs/1609.04802)
- **ESRGAN Paper:** [arXiv:1809.00219](https://arxiv.org/abs/1809.00219)
- **RCAN Paper:** [arXiv:1807.02758](https://arxiv.org/abs/1807.02758)

---

##  Future Directions

- Add adversarial and perceptual loss for enhanced realism.
- Train on larger datasets like Flickr2K.
- Fine-tune with Real-World Degraded Images (Real-ESRGAN).

---
