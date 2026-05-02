
#  CNN – Part 3: Loss, Backpropagation & Training

---

##  1. Where We Are

From Part 2, we get:

👉 Final output (prediction) from ANN

Example:

* Predicted: **Cat = 0.7, Dog = 0.3**
* Actual: **Cat = 1, Dog = 0**

---

##  2. Loss Function (Error Measurement)

We need to measure:

👉 *How wrong is the prediction?*

### Common Loss Functions

#### Binary Classification

* **Binary Cross Entropy**

#### Multi-class Classification

* **Categorical Cross Entropy**

---

###  Cross Entropy Formula

$$
L = -\sum y \log(\hat{y})
$$
Where:

* $ y $ = actual value
* $ \hat{y} $ = predicted value

---

###  Intuition

* If prediction is correct → loss is small
* If prediction is wrong → loss is large

👉 Goal: **Minimize loss**

---

##  3. Backpropagation (Core Learning Step)

Now comes the real learning.

👉 We update weights so that loss decreases

---

###  Step-by-Step Flow

1. Forward pass (prediction)
2. Compute loss
3. Calculate gradients (how much each weight contributed to error)
4. Update weights

---

###  Weight Update Rule

$$

W = W - \eta \cdot \frac{\partial L}{\partial W}

$$
Where:

* $ W $= weight
* $ \eta $ = learning rate
* $ \frac{\partial L}{\partial W} $ = gradient

---

##  4. How Backprop Works in CNN

This is where many get confused—keep it simple:

👉 Backprop flows **backwards through entire network**

### Flow:

```
Output Layer (ANN)
   ↑
Fully Connected Layers
   ↑
Flatten Layer
   ↑
Pooling Layer
   ↑
Convolution Layer
```

---

##  5. What Gets Updated?

### In Fully Connected Layers

* Weights updated normally (like ANN)

### In Convolution Layers

* **Filters (kernels) are updated**

👉 This is key:

* CNN doesn’t learn pixels
* It learns **filters that detect patterns**

---

##  6. What About Pooling Layer?

👉 Pooling has **no learnable parameters**

* No weights
* No updates

But gradients still pass through it

---

##  7. Epochs & Iterations

### Epoch

* One full pass over entire dataset

### Iteration

* One batch update

---

##  8. Optimizers

Instead of basic gradient descent, we use:

* SGD
* Adam (most popular)
* RMSprop

👉 They control **how weights are updated**

---

##  9. Complete Training Flow

```id="k9f2p1"
1. Input Image
2. Forward Pass (Conv → Pool → Flatten → ANN)
3. Get Prediction
4. Calculate Loss
5. Backpropagate Error
6. Update Weights (Conv filters + ANN weights)
7. Repeat (Epochs)
```

---

##  10. Key Insight (Very Important)

👉 CNN learns in two parts:

* **Feature Learning (Conv layers)**
  → Learns patterns automatically

* **Decision Making (ANN layers)**
  → Maps patterns to output

---
