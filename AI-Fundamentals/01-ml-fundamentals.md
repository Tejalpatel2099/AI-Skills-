# 01 · Classic ML Fundamentals

The questions asked directly at the new-grad level. Know these cold.

## Learning setups
- **Supervised** — labeled data; learn input → output (classification, regression).
- **Unsupervised** — no labels; find structure (clustering, dimensionality reduction).
- **Self-supervised** — labels generated from the data itself (how LLMs pretrain: predict the next token).

## Gradient descent
The optimizer. It nudges model weights in the direction that reduces the loss, step by step.
- **Learning rate** controls step size. Too high → overshoot/diverge; too low → slow, may get stuck.
- **SGD** updates on small batches instead of the whole dataset — faster, noisier, often generalizes better.

## Loss functions
- **MSE (mean squared error)** — regression (continuous outputs).
- **Cross-entropy** — classification (probability outputs). Penalizes confident wrong answers heavily.

## Bias / variance and overfitting
- **High bias (underfit)** — model too simple, misses patterns.
- **High variance (overfit)** — model memorizes training data, fails on new data.
- Fixes for overfitting: more data, **regularization** (L1/L2), **dropout**, early stopping, simpler model.

## Evaluation metrics (and when accuracy lies)
- **Accuracy** misleads on imbalanced data (99% "not fraud" by predicting "never fraud").
- **Precision** = of predicted positives, how many were right. **Recall** = of actual positives, how many you caught.
- **F1** = harmonic mean of precision and recall — use when classes are imbalanced.
- **ROC-AUC** = ranking quality across thresholds.

## Activations
- **ReLU** — default for hidden layers; cheap, avoids vanishing gradients.
- **Sigmoid** — squashes to (0,1); binary output.
- **Softmax** — turns a vector of scores into a probability distribution; multi-class output.

## Hands-on
Train logistic regression and a small tree/NN on one dataset in scikit-learn; compare precision/recall/F1, not just accuracy.
