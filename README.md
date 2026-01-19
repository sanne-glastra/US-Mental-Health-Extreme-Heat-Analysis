# US Mental Health & Extreme Heat — Analysis

This repository contains materials for an analysis of spatial relationships between extreme heat and mental-health-related outcomes in the United States. It currently includes a geospatial analysis notebook and a PDF report.

Summary of what I found
- Top-level README.md (this file)
  - https://github.com/sanne-glastra/US-Mental-Health-Extreme-Heat-Analysis/blob/main/README.md
- Geospatial-Analysis/ (folder)
  - README.md (empty / placeholder)  
    - https://github.com/sanne-glastra/US-Mental-Health-Extreme-Heat-Analysis/blob/main/Geospatial-Analysis/README.md
  - US_Mental_Health_Spatial_Analysis_Report.pdf — static report
    - https://github.com/sanne-glastra/US-Mental-Health-Extreme-Heat-Analysis/blob/main/Geospatial-Analysis/US_Mental_Health_Spatial_Analysis_Report.pdf
  - spatial_econometric_modeling.ipynb — interactive analysis notebook
    - https://github.com/sanne-glastra/US-Mental-Health-Extreme-Heat-Analysis/blob/main/Geospatial-Analysis/spatial_econometric_modeling.ipynb

Purpose
- Provide reproducible geospatial and spatial-econometric analyses exploring associations between extreme heat (temperature, heatwaves) and mental-health outcomes (e.g., hospital/ED visits, crisis calls, survey indicators).
- Offer an interactive notebook for exploration and a PDF report summarizing methods and results.

Getting started (recommended)
1. Clone the repository:
   - git clone https://github.com/sanne-glastra/US-Mental-Health-Extreme-Heat-Analysis.git
   - cd US-Mental-Health-Extreme-Heat-Analysis

2. Create a Python environment (recommended)
   - Using conda:
     - conda create -n us-heat-mental python=3.9 -y
     - conda activate us-heat-mental
   - Or using venv:
     - python -m venv .venv
     - source .venv/bin/activate  (or `.venv\Scripts\activate` on Windows)

3. Install typical packages required for geospatial and econometric notebook work
   - Example (conda + pip mix):
     - conda install -c conda-forge geopandas jupyterlab notebook pandas numpy matplotlib seaborn -y
     - pip install libpysal spreg esda statsmodels
   - Note: There is no environment/requirements.txt or environment.yml in the repo. I recommend creating one after verifying the exact dependencies used in the notebook.

4. Open the notebook
   - jupyter lab
   - In the file browser open: Geospatial-Analysis/spatial_econometric_modeling.ipynb

Data requirements & recommended layout
- This repository currently does not include raw or processed data files. For reproducible runs, adopt a consistent data layout:
  - data/
    - raw/        # original downloads (do not edit)
    - processed/  # cleaned files used by notebooks
- If the notebook downloads data or provides helper scripts, place them under src/ or data/scripts/.

Notes about the notebook & report
- The notebook `spatial_econometric_modeling.ipynb` appears to contain the core spatial analysis. Open it to confirm required packages and the expected data file paths.
- The PDF `US_Mental_Health_Spatial_Analysis_Report.pdf` is a compiled report that documents results and interpretation.

Recommended next steps (to improve reproducibility and usability)
- Add an `environment/requirements.txt` or `environment/environment.yml` with pinned versions used by the notebook.
- Populate `Geospatial-Analysis/README.md` with a short description of the notebook, expected data files, and any steps to reproduce figures/tables.
- Add a `data/` directory and small example datasets or download scripts (if permitted by data licenses) so other users can run parts of the analysis.
- Consider adding a `src/` folder with helper functions (data loading, cleaning, plotting) extracted from the notebook to make the analysis modular and easier to test.
- Add a LICENSE file and a CITATION or methods.md describing datasets and processing decisions.

Contributing
- Please open issues for bugs, environment problems, or feature requests.
- Suggested workflow:
  1. Fork the repository
  2. Create a branch: `git checkout -b feat/describe-deps`
  3. Add or update files (eg. requirements.txt, README updates)
  4. Open a pull request describing the changes

Privacy & ethics
- Ensure adherence to data use agreements and IRB requirements for any health or patient-level data.
- De-identify or aggregate sensitive data prior to sharing.

Contact / Maintainer
- Repository owner: sanne-glastra
- For questions or to request help reproducing analyses, please open an issue in this repository.

What I can do next (I can do any of these for you)
- Create a pinned `environment/requirements.txt` by scanning the notebook for imports and suggesting package versions.
- Populate `Geospatial-Analysis/README.md` with precise instructions tied to the notebook.
- Extract helper code from the notebook into `src/` modules and add runnable scripts.
- Add small synthetic example data and a minimal runnable pipeline so the notebook can be executed end-to-end.

If you want me to proceed with any of the above, tell me which and I will start by scanning the notebook for imports and data paths.
