# Reproducibility Report: Impact of Releasing Code with Publications

This repository contains the reproduced data analysis and plotting scripts for the paper: 
["What is the Impact of Releasing Code with Publications? Statistics from the Machine Learning, Robotics, and Control Communities."](https://ieeexplore.ieee.org/document/10621946).

## 1. Reproducibility Status (Verified 2026)
This project has successfully completed the **5 Stages of Reproducibility**:
1.  **Download**: Repository cloned and data verified.
2.  **Installing**: Successfully resolved dependency conflicts for Python 3.13.
3.  **Running**: `main.py` executed successfully, processing JSON datasets for CDC, ICRA, and NeurIPS.
4.  **Experimenting**: Verified the statistical calculations for median and third-quartile citation growth.
5.  **Graphing**: Regenerated all primary figures (Figures 1-4) in `.png` format.

## 2. Environment & Installation
The original code was tested on legacy environments. To reproduce this on a modern system (e.g., macOS 13+ or Ubuntu 22.04+), follow these steps:

### Stable Setup
```sh
# Create a virtual environment
python3 -m venv venv_repro
source venv_repro/bin/activate

# Install compatible dependencies (Fixes NumPy 2.x and Matplotlib conflicts)
pip install "numpy<2" matplotlib==3.7.1 seaborn scikit-learn pandas scipy sympy pyyaml
```

### Critical Hotfixes applied in `analyze.py`
Due to deprecations in modern Python 3.10+ libraries, the following patches were implemented during the 2025 reproduction:
* **Matplotlib Patch**: Added a monkey patch for `common_texification` in `matplotlib.backends.backend_pgf`.
* **Tikzplotlib Bypass**: Commented out `tikzplotlib.save()` and replaced with `plt.savefig()` to avoid `AttributeError` and `webcolors` incompatibilities.

## 3. Usage
```sh
git clone https://github.com/utiasDSL/code-release.git
cd code-release/
python3 main.py
```
You may find other dependency problems, but it's rather a quick fix.

## 4. Citations
If you use this reproduction or the original data, please cite:
```sh
@ARTICLE{oscrelease2024,
      author={Zhou, Siqi and Brunke, Lukas and Tao, Allen and Hall, Adam W. and Bejarano, Federico Pizarro and Panerati, Jacopo and Schoellig, Angela P.},
      journal={IEEE Control Systems Magazine}, 
      title={What Is the Impact of Releasing Code With Publications? Statistics from the Machine Learning, Robotics, and Control Communities}, 
      year={2024},
      volume={44},
      number={4},
      pages={38-46},
      doi={10.1109/MCS.2024.3402888}
}
```
Reproduced by: Adhiya Radhin Fasya

Source Lab: Learning Systems and Robotics Lab (TUM/Toronto)
