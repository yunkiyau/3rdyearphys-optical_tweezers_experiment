# Optical Tweezers Brownian Motion Analysis

This repository contains a Jupyter notebook for analysing the Brownian motion of 1 µm and 3 µm polystyrene beads suspended in deionized water (0.04% CV), recorded using a **Thorlabs Portable Optical Tweezer** setup. The goal is to quantify bead displacements over time and estimate the effective viscosity of the medium. This experiment is one of the advanced experiments in the Senior Physics lab. I developed this workflow for the experiment which uses an add-on in Blender to perform the motion tracking of the beads from video recordings of the microscope. I found the standard motion tracking software listed in the manual (Viana.NET) to be unusable because it relies on tracking colours and I'm really not sure how any other student used it for this experiment. Hopefully future 3rd Physics students that come across this repo find it useful. Please feel free to reach out to me at yunki.yau@gmail.com if anything is unclear. 

## Workflow

1. **Motion tracking**  
   Videos (1280×1024 resolution, 15 FPS) were tracked in *Blender 2.8* (GNU GPL).  
   - Tracking add-on: [blenderMotionExport](https://github.com/Amudtogal/blenderMotionExport)  
   - Output: CSV files with bead trajectories.

2. **Analysis (this notebook)**  
   - Convert pixel coordinates → micrometres (11.66 px/µm, based on 3 µm bead diameter).  
   - Compute per-bead mean squared displacement (MSD) and time-averaged values.  
   - Average across beads of the same size.  
   - Plot ⟨r²⟩ vs time and fit a line through the origin.  
   - The fitted slope relates to diffusion and can be used to estimate effective viscosity.

## Repository structure

```
notebooks/
    BrownianMotionAnalysis.ipynb   # main analysis & plots
data/
    raw CSV files used in the analysis
README.md
```

## Requirements

- Python 3.10+  
- Jupyter Notebook  
- numpy  
- matplotlib  

Install with:
```bash
pip install numpy matplotlib jupyter
```

## Usage

1. Clone the repository and add your CSV tracking files into `data/`.  
2. Launch Jupyter and open the notebook:
   ```bash
   jupyter notebook notebooks/BrownianMotionAnalysis.ipynb
   ```
3. Run all cells to reproduce the analysis and plots.  

Figures are generated inline in the notebook.

## Notes & Limitations

- Frame-to-time conversion assumes **15 FPS** which is the speed of the Thorlabs camera in the kit.  
- Pixel-to-µm calibration (11.66 px/µm) is approximate; uncertainties due to bead depth (~20 µm well) and manufacturer CV (±5%) are **not yet propagated**.  
- Future work: add code to estimate **maximum trapping force** from the strongest bead trap event.

## Citation

If you use this repository in academic or research work, please cite:

**Yunki Yau**, *Optical Tweezers Brownian Motion Analysis*, GitHub, 2025.  
[https://github.com/yunkiyau](https://github.com/yunkiyau)

---
