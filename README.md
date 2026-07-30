This repository contains the source code for one of my internship tasks centered on Deep Learning. To proceed with this task, I returned to the Telco-Customer-Churn dataset. However, instead of using standard machine learning frameworks, I designed and implemented a neural network from scratch using PyTorch.

# 1. Architectural Strategy
- Input Layer: Dynamically scales to match the exact dimensions of the one-hot encoded dataset features.
- Hidden Layer 1: Processes data through 32 neurons using ReLU activation, backed by a Dropout layer to prevent early overfitting and feature co-dependency.
- Hidden Layer 2: Uses 16 neurons with ReLU activation to capture deeper, more abstract feature interactions from the initial representations.
- Output Layer: Outputs a single raw logit through a linear node, specifically paired with BCEWithLogitsLoss for stable and efficient binary classification.

# 2. Experimental Tuning Log & Observations
- Setting the learning rate to 0.05 destroyed stability and caused the loss to diverge. Dropping it to 0.001 stabilized training but left the gradient descent crawling at an incredibly slow pace.
- Tracking the loss curves revealed clear overfitting around epoch 60, where validation loss flattened while training loss kept falling. I fixed this by implementing a 30% dropout rate and cutting the run short at 50 epochs as a manual early-stopping strategy.

# 3. Discoveries & Baseline Comparison
Final Neural Network Test Accuracy: Aprpoximately 79.91%
Logistic Regression Baseline Benchmark: 79.84%

Key Takeaway: The slight edge in accuracy from the neural network does not entirely justify the extra complexity. For clean, mid-sized tabular data, a well-tuned linear model essentially gives you the same results but is relatively faster to build, easier to maintain, and runs on a fraction of the computing power.