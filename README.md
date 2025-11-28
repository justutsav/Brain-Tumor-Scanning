# Brain Tumor Scan Processing (exp_learning)

**Project purpose:** Demonstration notebook that loads a brain MRI image, applies block-based thresholding and basic image-processing steps to localize a tumor-like region, and visualizes results. This repository is a compact experimental project used for learning image preprocessing and simple segmentation techniques with OpenCV and matplotlib.

---

## Contents / Project structure

```
/ (repo root)
├─ exp_learning.ipynb      # Main Jupyter notebook (image processing pipeline & experiments)
├─ BrainTumor.jpg          # Example MRI scan (grayscale)
├─ BrainTumor.pnm          # Example MRI scan (alternate format)
├─ README.md               # This file
├─ requirements.txt        # Python libraries used
```

---

## Quick summary of the pipeline in the notebook

1. **Load image** using OpenCV (`cv2.imread`). Examples use `BrainTumor.jpg` and `BrainTumor.pnm`.
2. **Resize** images to fixed dimensions for stable processing (e.g., 400×400).
3. **Block-based thresholding:** the notebook demonstrates a custom function that divides the image into blocks and applies an intensity threshold per block to create a binary mask that highlights high-intensity regions (possible tumor areas).
4. **Visualization:** results are shown using `matplotlib.pyplot.imshow` with titles for clarity.
5. Several notebook cells contain small variations and experiments (resizing, dtype checks and alternate image-loading paths).

> Note: The notebook currently focuses on classical image-processing experiments and does not train or use a machine-learning model. It is exploratory code intended for learning and demonstration.

---

## Requirements

Create a Python environment (recommended: use `venv` or `conda`) and install dependencies:

```
pip install -r requirements.txt
```

Contents of `requirements.txt` (also included in this repo):

```
opencv-python
matplotlib
numpy
Pillow
notebook
```

---

## How to run

### Locally (recommended)

1. Clone the repo (see the section below for uploading to GitHub; or if you already cloned):
   ```bash
   git clone (https://github.com/justutsav/Brain-Tumor-Scanning.git)
   cd Brain-Tumor-Scanning
   ```
2. Create and activate a virtual environment:
   ```bash
   python -m venv .venv
   source .venv/bin/activate    # macOS / Linux
   .\.venv\Scripts\activate     # Windows PowerShell
   ```
3. Install dependencies:
   ```bash
   pip install -r requirements.txt
   ```
4. Start Jupyter Notebook and open `exp_learning.ipynb`:
   ```bash
   jupyter notebook
   ```
   Run cells interactively and explore outputs.

### Using Google Colab

If you prefer Colab, upload `exp_learning.ipynb` and the image files to Colab (or mount Google Drive) and run the notebook there. You may need to change the image path to match the Colab working directory (e.g., `/content/BrainTumor.jpg`).

---

## Suggestions & Improvements (next steps)

- Use standard segmentation methods for better accuracy:
  - Otsu thresholding, adaptive thresholding, Canny edge detection.
  - Morphological operations (open, close) to remove noise.
  - Watershed algorithm to split touching regions.
- Evaluate region proposals using contour area and circularity; compute bounding box and overlay on original image.
- If building a classifier: gather labeled dataset (MRI scans with tumor masks). Train a U-Net or a small CNN for semantic segmentation or classification.
- Add unit tests for core helper functions, and refactor repeated code into a Python module (e.g., `processing.py`) so the notebook imports functions instead of re-defining them.
- Save processed masks and visualizations to a `results/` folder automatically.
- Add clear kernel/system info at top and remove duplicated/unused cells for a clean final notebook.

---

## Notes about publishing the notebook to GitHub

- Clear large cell outputs before committing to keep repo size small (in Jupyter: `Edit -> Clear All Outputs`). Optionally use `nbstripout` to remove outputs on commit.
- Add a `.gitignore` to exclude virtual environments, `.ipynb_checkpoints`, and large data files if needed.
- Consider adding an appropriate license (e.g., MIT) if you want to share the code publicly.

---

## Reproducibility checklist

- `exp_learning.ipynb` should reference the included `BrainTumor.jpg` or `BrainTumor.pnm` in the same folder.
- If you change paths, update notebook cell(s) accordingly.
- Confirm installed OpenCV uses the correct image-reading mode (grayscale vs BGR); the notebook uses grayscale images (PIL reveals mode 'L').

---

## Contact / Author

Your name (add here) — feel free to customize the README with project description and links to your portfolio or demo.
