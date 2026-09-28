# Project Instructions

## General Instructions

Work on the generative modeling task described in `TASK.md`.

Read `TASK.md` before beginning implementation and follow its requirements exactly.

The final deliverable is the trained model artifact:

`task/results/model.joblib`

## Development Guidelines

- Use the provided training data only.
- Do not obtain additional datasets.
- Do not use internet access.
- Do not use the held-out evaluation data.
- Do not modify verification tests.
- Do not access hidden evaluation files.
- Keep the implementation reproducible.
- Ensure that the final model artifact is saved at the required path.

## Model Requirements

The final model must satisfy all requirements specified in `TASK.md`.

In particular, it must:

- model the 11 specified wine physicochemical features;
- use exactly 3 mixture components;
- use full covariance;
- use the original 11 input features;
- use appropriate preprocessing when necessary;
- provide a generative model capable of evaluating sample log probabilities;
- provide a generative model capable of producing synthetic samples.

## Artifact Requirements

The final artifact must be saved as:

`task/results/model.joblib`

The artifact must be loadable using:

```python
import joblib

model = joblib.load("task/results/model.joblib")
```
The loaded artifact must contain:
```python
model["scaler"]
model["gmm"]
```
The GMM must satisfy:
```python
model["gmm"].n_components == 3
model["gmm"].n_features_in_ == 11
model["gmm"].covariance_type == "full"
```
Do not replace the trained model with hard-coded evaluation results or precomputed outputs.

## Validation

Before completing the task, verify that the final artifact:

- Exists at the required path.
- Can be loaded successfully.
- Contains the required scaler and gmm objects.
- Uses exactly 3 mixture components.
- Uses full covariance.
- Operates on 11 input features.
- Produces finite log probabilities.
- Produces finite generated samples.
- Produces generated samples with the expected shape.
## Completion

The task is complete only after the trained model has been saved to:

`task/results/model.joblib`

and the requirements in TASK.md have been satisfied.