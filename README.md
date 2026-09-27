================================================================================
SUPPLEMENTARY MATERIAL: Quantitative XAI Metrics Reproduction Package
Paper Title: Quantitative Grad-CAM Analysis of a Data-Centric Pipeline for 
             Hard-Class Plant Leaf Disease Classification
Authors: Bambang Priambodo
================================================================================

OVERVIEW
--------
This package contains the Python source code and the deterministic list of 
157 diagnostic failure samples used to compute the quantitative spatial 
metrics (CAR, PCD, AE, LAR) and generate the statistical results reported 
in Table 5 and Table 6 of the main manuscript.

PREREQUISITES
-------------
- Python 3.8 or higher
- Required Python libraries: numpy, pandas, opencv-python, scipy, statsmodels

DIRECTORY STRUCTURE & INPUTS
----------------------------
To run the script successfully, please ensure the following directory structure 
is maintained relative to the `cam_metrics.py` script:

project_root/
│
├── cam_metrics.py                  (The main computation script)
── 157_sample_ids.csv              (The manifest of selected samples)
│
└── exp3/
    └── gradcam_s3_output/
        ├── cams/
        │   ├── baseline/           (Folder containing B0 Grad-CAM .npy files)
        │   │   └── [sample_id]_baseline_cam_pred.npy
        │   └── s3/                 (Folder containing P1 Grad-CAM .npy files)
        │       └── [sample_id]_s3_cam_pred.npy
        │
        └── selection_manifest.csv  (Symlink or copy of 157_sample_ids.csv)

NOTE ON TERMINOLOGY: 
In the code, the baseline model (B0) is tagged as "baseline", and the 
Leaf-Aware pipeline model (P1) is tagged as "s3". 

HOW TO RUN
----------
1. Install dependencies: pip install numpy pandas opencv-python scipy statsmodels
2. Place the Grad-CAM .npy files in the respective `cams/baseline` and `cams/s3` folders.
3. Ensure `157_sample_ids.csv` is renamed or copied as `selection_manifest.csv` 
   inside the `exp3/gradcam_s3_output/` directory.
4. Run the script from the project root:
   python cam_metrics.py

EXPECTED OUTPUTS
----------------
Upon successful execution, the script will generate:
1. cam_metrics.csv : Raw metric values for all 157 samples (B0 and P1).
2. table5_final.csv: The aggregated paired t-test results with BH correction 
                     (corresponds to Table 5 in the manuscript).
3. Console Output  : The per-class stratified analysis for C8, C31, and C35 
                     (corresponds to Table 6 in the manuscript).

CONTACT
-------
For any issues regarding the reproduction of these results, please contact 
the corresponding author at: 2436083026@webmail.uad.ac.id
