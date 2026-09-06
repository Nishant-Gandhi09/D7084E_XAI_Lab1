# Intrusion Detection Lab

This project builds a simple intrusion detection system using the CICIDS2017 dataset. The goal is to separate normal network traffic from malicious traffic using classic machine learning and a neural network.

The notebook in this repository loads the CSV files from the 'data/' folder, cleans the raw network-flow data, converts labels into a binary attack-vs-benign target, trains a few models, and compares their performance.

## Project structure

- 'intrusion_detector.ipynb' — main analysis notebook
- 'data/' — CICIDS2017 GeneratedLabelledFlows CSV files
- 'figures/' — output plots such as feature importance
- 'results/' — model comparison metrics saved as CSV
- 'requirements.txt' — required Python packages

## What the code does

1. Loads all CICIDS2017 CSV files from 'data/'
2. Removes metadata columns that are not useful as features
3. Strips and normalizes column names
4. Converts all label values into binary classes:
   - 'BENIGN' -> '0'
   - any other traffic type -> '1'
5. Handles missing values and invalid numeric values
6. Splits the data into train, validation, and test sets using stratification
7. Trains multiple models:
   - Logistic Regression
   - Random Forest
   - MLP neural network
8. Compares the models using accuracy, precision, recall, F1, FAR, and ROC-AUC
9. Saves the results table and a feature-importance plot

## Why this matters

This is a typical intrusion detection workflow in cybersecurity. Instead of inspecting packets manually, the model learns patterns in flow-level traffic. The goal is to detect suspicious behavior quickly and reliably, while keeping false alarms low.

## How to run it

1. Open the repository in VS Code or Jupyter
2. Make sure the environment has the dependencies installed
3. Import all CICIDS2017 CSV files from the TrafficLabelling dataset into the project's /data folder.
3. Run the notebook cells in order
4. The code will read the data folder automatically and generate outputs in 'figures/' and 'results/'

### Setup environmet

**Mac/Linux:**
\`\`\`bash
cd "D7084E_XAI_Lab1"
python3 -m venv .venv
source .venv/bin/activate
pip install -r requirements.txt
jupyter notebook
\`\`\`

**Windows:**
\`\`\`bash
cd "D7084E_XAI_Lab1"
python -m venv .venv
.venv\Scripts\activate
pip install -r requirements.txt
jupyter notebook
\`\`\`

### Running a Quicker Version

If you want to run a quicker version, change `USE_SAMPLE = False` to
`USE_SAMPLE = True`. This will make the code train on a smaller
random sample (25%) of the CSV data rather than the full dataset.
You can find this variable in the second cell.

### Run

Then open `intrusion_detector.ipynb` and run all cells.

## Notes

- The notebook is designed for the full CICIDS2017 dataset structure in this repo.
- The project uses a fixed random seed for reproducible results.
- The comparison is intentionally focused on the metrics that matter for imbalanced traffic data, especially F1 and false alarm rate.

This repo is meant to be a simple, readable lab project for learning how to build and evaluate a first intrusion detector from network traffic data.
