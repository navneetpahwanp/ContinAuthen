# Continuous Authentication using Inertial-Sensors of Smartphones and Deep Learning

***Master Thesis,<br>
September 14th, 2021<br>
University of Sheffield (DE)<br>
Artificial Intelligence and Cybersecurity<br>***



## Project Description
**Description**<br>
Implementation of a "Continuous Authentication" approach based on inertial sensor data of smartphones. The proposed model is an ensemble of Siamese CNN for generating deep features with OCSVM for classification.

**Goals**<br>
Attempt to reproduce better results than the original study.<br>
Evaluate approach in scenario closer to real-world setting.<br>
Propose alternative variant of the original approach.<br>



## Project's directory structure


```
├── README.md          <- The top-level README for developers using this project.
├── LICENSE            <- MIT License.
├── data
│   ├── external       <- Data from third party sources. (Extracted H-MOG CSV files)
│   └── processed      <- The final, canonical data sets for modeling. (Transformed in HDF)
│
├── notebooks          <- Jupyter notebooks.
│
├── reports           
│   └── figures        <- Generated graphics and figures to be used in reporting
│
├── environment.yaml   <- The environment file for reproducing the analysis
|                         environment in theAnaconda distribution by executing
|                         `conda continauth create -f environment.yaml`
|
|
└── src                <- Source code for use in this project.
    │
    ├── data           <- Scripts to download or generate data
    │
    └── utility        <- Helper scripts

```

## Get it up and running
**Install environment:**
```bash
conda env create -f environment.yml
```
**Enter environment:**
```bash
conda activate continauth
```

> **NOTE:**
All following commands are expected to be executed inside this virtual environment `continauth` and with repository root (`./`) as current working directory!



```

**Download Dataset:**
- Download [H-MOG Dataset](http://www.cs.wm.edu/~qyang/hmog.html) and place the zip file as it is into the repository root.

**Run preprocessing steps:**
```bash
python src.data.make_dataset
```

This will run the following steps, which also can be executed manually:
- `python src.data.unzip_hmog_dataset` - Unzip into '/data/external' and optionally remove zip file.
- `python src.data.transform_to_hdf` - Reads CSVs, joins sensor data by time index and store it in HDF format in '/data/processed/' with table key `sensors_100hz`
- `python -m src.data.resample_dataset` - Reads data from HDF, resamples it to 25Hz and stores it as separate table `sensors_25hz` in the same HDF.

**Start Jupyter Lab:**
```bash
jupyter lab
```
