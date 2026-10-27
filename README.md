# Student Performance Prediction with Machine Learning

A supervised machine-learning project comparing four classifiers for predicting pass/fail outcomes in Mathematics using the UCI Student Performance dataset.

## Project question

How well can K-Nearest Neighbors (KNN), Decision Tree, Support Vector Machine (SVM), and Artificial Neural Network (ANN) classify students as passing or failing Mathematics?

## Dataset

This project uses the Mathematics subset (`student-mat.csv`) of the [UCI Student Performance dataset](https://archive.ics.uci.edu/dataset/320/student+performance). The data was collected from two Portuguese secondary schools and contains student grades alongside demographic, family, social, and school-related attributes.

The dataset is distributed under **CC BY 4.0**. Please retain attribution to the original source:

> Cortez, P. (2008). *Student Performance* [Dataset]. UCI Machine Learning Repository. https://doi.org/10.24432/C5TG7T

## Target definition

The final grade `G3` ranges from 0 to 20. For this project, the target is defined as:

- `Pass = 1` when `G3 >= 10`
- `Pass = 0` when `G3 < 10`

The `G3` column is removed from the predictors to prevent direct target leakage. The predictors include `G1` and `G2`, which are grades from earlier periods. Consequently, this project predicts the final outcome using earlier academic results; it does not test prediction before any grades are available.

## Methods

The notebook includes:

1. Data inspection and missing-value checks
2. Exploratory analysis of class distribution and selected factors
3. One-hot encoding of categorical predictors
4. Stratified 80/20 train-test split
5. Four classifiers: KNN, Decision Tree, SVM, and ANN
6. Evaluation using accuracy, precision, recall, F1-score, confusion matrices, and 2-fold cross-validation
7. Decision Tree feature-importance analysis

Preprocessing is contained in scikit-learn pipelines so scaling is fitted separately inside each cross-validation fold.

## Repository structure

```text
student-performance-ml/
├── data/
│   └── raw/
│       └── README.md
├── notebooks/
│   └── student_performance_analysis.ipynb
├── .gitignore
├── LICENSE
├── requirements.txt
└── README.md
```

## How to run

### 1. Clone the repository

```bash
git clone https://github.com/YOUR-USERNAME/student-performance-ml.git
cd student-performance-ml
```

Replace `YOUR-USERNAME` with your GitHub username.

### 2. Create and activate a virtual environment

Windows PowerShell:

```powershell
python -m venv .venv
.venv\Scripts\Activate.ps1
```

macOS/Linux:

```bash
python3 -m venv .venv
source .venv/bin/activate
```

### 3. Install dependencies

```bash
python -m pip install --upgrade pip
pip install -r requirements.txt
```

### 4. Download the data

Download the UCI dataset from the source link above, extract the archive, and copy `student-mat.csv` into `data/raw/`.

The raw data file is excluded from Git in this starter repository. This keeps the repository focused on code and documentation while the README preserves the source and attribution.

### 5. Open the notebook

```bash
jupyter notebook
```

Open `notebooks/student_performance_analysis.ipynb` and run the cells from top to bottom.

## Results

Run the notebook to generate the current model comparison. Record the actual values from `results_df` here after executing the notebook in your environment. Model results can vary with software versions and implementation details.

When interpreting the results, compare precision, recall, F1-score, and confusion matrices in addition to accuracy. The best model depends partly on the consequences of false positives and false negatives.

## Limitations

- The dataset is relatively small and represents two Portuguese schools.
- A passing threshold of 10/20 is used as a project assumption.
- Earlier-period grades (`G1` and `G2`) are predictors and may account for a substantial portion of predictive performance.
- The analysis is observational; model importance does not imply causation.
- The model is for learning and demonstration, not for making consequential decisions about real students.

## Possible future improvements

- Compare models with and without `G1` and `G2`.
- Use repeated stratified cross-validation for a more stable performance estimate.
- Examine precision/recall trade-offs for identifying students at risk of failing.
- Test on Portuguese-course data as a separate experiment.
- Evaluate whether model performance differs across relevant student groups.

## License

The project code is released under the MIT License. The UCI dataset has its own CC BY 4.0 license and must be attributed to its original source.
