# Installation Instructions

## Python Version

The reference solution was developed and tested with:

```text
Python 3.14.7
```

## Required Python Packages

Use the following package versions:
```text
numpy==2.5.3
pandas==3.0.6
scikit-learn==1.9.1
joblib==1.6.0
pytest==9.1.1
```
Install all required packages with:
```python
python -m pip install numpy==2.5.3 pandas==3.0.6 scikit-learn==1.9.1 joblib==1.6.0 pytest==9.1.1
Verify Installation
```
Run:
```python
python -c "import numpy, pandas, sklearn, joblib, pytest; print('Environment ready')"
```
A successful installation should print:
`Environment ready`

You can also verify the exact installed versions with:
```python
python -c "import sys, numpy, pandas, sklearn, joblib, pytest; print('Python:', sys.version); print('NumPy:', numpy.__version__); print('Pandas:', pandas.__version__); print('scikit-learn:', sklearn.__version__); print('joblib:', joblib.__version__); print('pytest:', pytest.__version__)"
```
## Expected versions:
```text
Python: 3.14.7
NumPy: 2.5.3
Pandas: 3.0.6
scikit-learn: 1.9.1
joblib: 1.6.0
pytest: 9.1.1
```
## Dataset

The training data is already provided at:

`data/train.csv`

No dataset download is required.

Do not use internet access to obtain additional data.

## Running the Solution

The final model artifact must be saved at:

`task/results/model.joblib`

The artifact can be loaded using:
```python 
import joblib

model = joblib.load("task/results/model.joblib")
```
The loaded artifact contains:
```python
model["scaler"]
model["gmm"]
```
The GMM provides the generative model over the 11 wine physicochemical features.

## Running Tests

Run the verification suite with:
```python
python -m pytest tests/ -v
```
## Environment Notes

The reference solution and verification tests were validated using the specified package versions.
