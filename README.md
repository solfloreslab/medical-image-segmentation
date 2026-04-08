# Medical Image Processing and Segmentation

Classical image processing and segmentation pipeline applied to pediatric chest X-rays (PneumoniaMNIST), from format selection to region delineation.

## Pipeline

1. **Format selection** — TIFF vs PNG vs JPEG: why lossy compression is unacceptable in medical imaging
2. **Dataset exploration** — Class distribution, intensity statistics, and visual comparison (normal vs pneumonia)
3. **Preprocessing** — Gaussian, median, histogram equalization, and CLAHE filtering before segmentation
4. **Segmentation** — Otsu thresholding, Sobel/Canny edge detection, and complete Watershed pipeline
5. **Evaluation** — Jaccard (IoU) and Dice metrics

## Dataset

[PneumoniaMNIST](https://medmnist.com/) (Yang et al., 2023): 5,856 pediatric chest X-rays (28x28 px, grayscale) from the Guangzhou Women and Children's Medical Center. Binary classification: normal (25.8%) vs pneumonia (74.2%).

## Key Findings

- Otsu and Watershed delineate recognizable anatomical structures (cardiac silhouette, lung fields) when sufficient internal contrast exists
- Extensive pulmonary opacities homogenize the image, reducing internal contrast and causing both methods to lose discrimination capability
- At 28x28 resolution, edge detection (Sobel/Canny) produces dense edge maps that are difficult to interpret — the limitation is resolution, not the algorithms
- Classical methods operate on pixel intensity without anatomical knowledge; current approaches like MedSAM (Ma et al., 2024) address this through learned representations

## Tools

Python, OpenCV, NumPy, Matplotlib, PIL, SciPy, MedMNIST API

## References

- Kermany et al. (2018). Identifying medical diagnoses and treatable diseases by image-based deep learning. *Cell*, 172(5).
- Yang et al. (2023). MedMNIST v2: A large-scale lightweight benchmark for 2D and 3D biomedical image classification. *Scientific Data*, 10(1).
- Ma et al. (2024). Segment anything in medical images. *Nature Communications*, 15.

## Acknowledgments

Developed with assistance from Claude Code (Anthropic).
