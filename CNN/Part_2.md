#  CNN – Part 2: Flattening & Classification

##  Where We Are

After Part 1, we have:

👉 Multiple **feature maps** (from stacked Conv + Pool layers)
👉 Each map highlights different patterns (edges, textures, shapes)

---

##  1. Important Clarification (Fix This Mental Model)

You said: *“each output acts as a candidate”*

👉 Slight correction:

* These are **not separate candidates**
* They are **different channels of information about the same image**

Think of it like:

* One map detects edges
* Another detects curves
* Another detects textures

👉 All of them together represent the image

---

##  2. Flatten Layer

Now we move to transition from CNN → ANN

### What Flattening Does

👉 Converts multi-dimensional feature maps into a 1D vector

Example:

* Feature maps shape: `(h × w × k)`
* After flattening → `(h * w * k, 1)`

### Why Needed?

* Fully connected layers (ANN) expect **1D input**
* So we convert spatial data → vector form

---

##  3. What Actually Happens

Let’s say:

* You have 10 feature maps
* Each is 5 × 5

👉 Total values = 10 × 5 × 5 = 250

👉 Flatten → **vector of size 250**

---

##  4. Fully Connected Layer (ANN Part)

Now comes the classification stage.

👉 This is just a standard neural network:

* Input → Flattened vector
* Pass through → Hidden layers
* Apply → Activation functions (ReLU, etc.)
* Final layer → Output layer

---

##  5. Output Layer

Depends on problem type:

### Binary Classification

* 1 neuron
* Activation → Sigmoid

### Multi-class Classification

* Multiple neurons
* Activation → Softmax

---

##  6. Complete Flow (Clean Pipeline)

```
Image
  ↓
Convolution + ReLU
  ↓
Pooling
  ↓
(Repeat multiple times)
  ↓
Feature Maps
  ↓
Flatten
  ↓
Fully Connected Layers (ANN)
  ↓
Output (Prediction)
```

---

##  7. Key Insight (Very Important)

👉 CNN = Feature extractor
👉 ANN = Decision maker

* CNN learns **“what is in the image”**
* ANN decides **“which class it belongs to”**

---

##  8. One More Subtle Improvement

You said:

> “we take each flattened feature map and pass it”

👉 More accurate version:

* We **combine all feature maps into ONE flattened vector**
* Then pass **that single vector** into ANN

Not separately.

---

