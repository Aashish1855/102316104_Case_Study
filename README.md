# 102316104_Case_Study
# Self-Pruning Neural Network

## Overview

This project implements a neural network that can prune its own weights during training using learnable gates and L1 regularization.

---

## Approach

* Each weight has an associated gate parameter.

* Gates are passed through a sigmoid function to keep values between 0 and 1.

* Final weight used in computation:

  weight × gate

* If gate value is close to 0, the weight is effectively removed.

---

## Loss Function

Total Loss = Classification Loss + λ × Sparsity Loss

* Classification Loss: Cross entropy
* Sparsity Loss: Sum of all gate values (L1)
* λ controls pruning strength

---

## Model

* Fully connected neural network (MLP)
* 3 layers:

  * 3072 → 512
  * 512 → 256
  * 256 → 10

---

## Results

| Lambda | Accuracy | Sparsity |
| ------ | -------- | -------- |
| 1e-5   | 0.5443   | 0.04%    |
| 1e-4   | 0.5366   | 0.07%    |
| 1e-3   | 0.5343   | 0.07%    |

---

## Observation

* Increasing λ slightly reduces accuracy
* Sparsity increase is very low
* Model is not pruning aggressively

---

## Conclusion

The model is able to learn and apply pruning, but current setup does not produce high sparsity. Further tuning of λ or training setup is required.
