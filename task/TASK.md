# Wine Quality Generative Modeling Task

## Objective

Build a generative model of the physicochemical properties of red wine using the provided training dataset.

Your solution must learn a probability distribution over the 11 wine physicochemical features and provide both:

1. A method for evaluating the log probability of input samples.
2. A method for generating new synthetic samples.

The submitted model will be evaluated on a held-out dataset and on the statistical properties of generated samples.

---

## Dataset

The training data is provided in:

`data/train.csv`

The dataset contains the following 11 input features:

- `fixed acidity`
- `volatile acidity`
- `citric acid`
- `residual sugar`
- `chlorides`
- `free sulfur dioxide`
- `total sulfur dioxide`
- `density`
- `pH`
- `sulphates`
- `alcohol`

The `quality` column is not an input feature and must not be used as an input to the generative model.

Do not download additional datasets or use internet access.

---

## Required Model

Your solution must produce a generative model with:

- exactly 3 mixture components;
- full covariance for each component;
- 11 input features.

The generative model should be implemented using a Gaussian mixture model (GMM).

The model may use appropriate preprocessing or feature scaling internally.

The model should be trained using only the provided training data.

---

## Required Artifact

Save the final trained model artifact to exactly:

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
where:

`model["scaler"]` is the preprocessing/scaling object used by the generative model.
`model["gmm"] `is the fitted Gaussian mixture model.

The GMM must satisfy:
```python
model["gmm"].n_components == 3
model["gmm"].n_features_in_ == 11
model["gmm"].covariance_type == "full"
```
## Log Probability

The submitted model must support evaluation of the log probability of samples represented using the original 11 input features.

For an input array:

X

with shape:

`(n, 11)`

the model should:

Transform X using the submitted scaler.
Evaluate the GMM log probability in the transformed feature space.
Account for the change of variables introduced by the feature scaling.

The resulting log-probability values must have shape:
```python
(n,)
```
and must be finite.

## Sample Generation

The submitted model must generate synthetic samples using the fitted GMM.

For example:
```python
samples_scaled, _ = model["gmm"].sample(100)
samples = model["scaler"].inverse_transform(samples_scaled)
```
The resulting samples must:

have `shape (100, 11)`;
be represented using the original feature units;
contain only finite values.
## Expected Behavior

The model should learn a useful approximation of the probability distribution represented by the training data.

The generated samples should reproduce the overall statistical characteristics of the training data.

The model should assign meaningful probability values to previously unseen samples from the same data distribution.

Both probability evaluation and sample generation must produce finite numerical values.

## Output Requirements

Before finishing, ensure that the final trained model exists at:

`task/results/model.joblib`

The artifact must contain the trained scaler and generative model.

You may create additional files during development, but the required final model artifact must be located at the exact path above.

## Restrictions
- Use only the provided training data.
- Do not use the held-out evaluation data.
- Do not access or modify the verification tests.
- Do not access or modify hidden evaluation files.
- Do not hard-code evaluation results.
- Do not use internet access to obtain additional data.
- Do not use the quality column as an input feature.
- The final artifact must contain an actual trained generative model rather than a collection of precomputed evaluation outputs.

You are responsible for training and saving the final model artifact.

## Completion Check

Before completing the task, verify that:

- task/results/model.joblib exists.
- The artifact can be loaded with joblib.load.
- The artifact contains scaler and gmm.
- The GMM has exactly 3 mixture components.
- The GMM uses full covariance.
- The GMM operates on 11 input features.
- Probability evaluation returns one value per input sample.
- Probability values are finite.
- Generated samples have shape (n, 11).
- Generated samples are represented in the original feature units.
- Generated samples are finite.