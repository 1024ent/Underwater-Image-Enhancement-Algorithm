================================================================================
PROJECT: UNDERWATER IMAGE ENHANCEMENT BENCHMARKING
================================================================================

1. OVERVIEW
-----------
This repository contains the codebase for evaluating traditional underwater 
image enhancement techniques (e.g., CLAHE, UCM) against established metrics 
(UCIQE, UIQM) using the UIEB dataset. It is designed to act as the baseline 
for subsequent deep learning evaluation.

2. ENVIRONMENT SETUP
--------------------
It is strictly recommended to run this project within an isolated Conda 
environment to prevent dependency conflicts, especially to ensure GPU 
acceleration is utilized correctly before future deployment to ARM architectures.

Step 2.1: Create and Activate the Environment
> conda create -n underwater_research python=3.10 -y
> conda activate underwater_research

Step 2.2: Install Core Deep Learning & GPU Libraries
> conda install pytorch torchvision torchaudio pytorch-cuda=11.8 -c pytorch -c nvidia -y

Step 2.3: Install Image Processing, Utility & Benchmarking Tools
> pip install opencv-python pillow jupyterlab matplotlib scipy scikit-image kornia pandas tqdm ipywidgets kaggle

Step 2.4: Register Kernel for Jupyter
> python -m ipykernel install --user --name underwater_research --display-name "Python (Underwater Research)"

3. RUNNING THE PROJECT
----------------------
Once the environment is active and libraries are installed, launch the 
interactive development environment:

> jupyter lab

Ensure that you select "Python (Underwater Research)" as your kernel when 
opening the .ipynb files in the `notebooks/` directory.

4. FILE STRUCTURE EXPLANATION
-----------------------------
Underwater_Project/
|
+-- data/
|   +-- raw/             # Contains unmodified source images (e.g., UIEB dataset). 
|   |                    # Treat this as read-only. NEVER overwrite files here.
|   +-- processed/       # Automated output directory for enhanced images and 
|                        # generated CSV metric matrices.
|
+-- notebooks/
|   +-- 01_histogram.ipynb   # Contains experiments and benchmarking for CLAHE/UCM.
|   +-- (Future Notebooks)   # Numbered sequentially for organized progression.
|
+-- utils/
|   +-- __init__.py          # Marks the directory as a Python package.
|   +-- filters.py           # Reusable enhancement logic (apply_clahe, apply_ucm).
|   +-- metrics.py           # Mathematical implementations for UCIQE and UIQM.
|
+-- README.txt           # This documentation file.

5. DATASET ACQUISITION
----------------------
To replicate the baseline testing, ensure the UIEB dataset is downloaded 
and extracted into `data/raw/uieb`.
================================================================================
