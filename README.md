# 📘 Assignment 2 – LSTM Language Model (IIIT Hyderabad)

A complete implementation of a **word-level LSTM Language Model** trained on  
*“Pride and Prejudice – Jane Austen”* as part of **IIIT Hyderabad Assignment 2**.

---

# 📑 Table of Contents
- [Overview](#overview)
- [Dataset](#dataset)
- [Project Structure](#project-structure)
- [Setup & Installation](#setup--installation)
- [Preprocessing](#preprocessing)
- [Training](#training)
- [Evaluation](#evaluation)
- [Inference](#inference)
- [Results](#results)
- [Model Architecture](#model-architecture)
- [Download Links](#download-links)
- [Extra Credit Work](#extra-credit-work)
- [Author](#author)

---

#  Overview
This project builds a **statistical language model** using a multi-layer LSTM.  
The goal is next-word prediction based on a fixed sequence length.

The workflow includes:

- Text preprocessing  
- Vocabulary construction  
- Sequence generation using sliding window  
- Train/val/test dataset creation  
- Custom PyTorch `Dataset` + `DataLoader`  
- LSTM network for language modeling  
- Underfitting & Overfitting experiments  
- Loss curve visualization  
- Perplexity evaluation  

---

#  Dataset
The dataset is provided by IIIT Hyderabad:

**`Pride_and_Prejudice-Jane_Austen.txt`**

Located in:


---
##  Project Structure

```
Assignment2/
│
├── data/
│   ├── raw/
│   │   └── Pride_and_Prejudice-Jane_Austen.txt          # Original dataset
│   │
│   └── processed/
│       ├── train.pt                                      # Training samples
│       ├── val.pt                                        # Validation samples
│       ├── test.pt                                       # Test samples
│       └── itos.json                                     # Vocabulary (index → token)
│
├── outputs/
│   ├── best_model.pt                                     # Saved trained LSTM model
│   ├── underfit_loss.png                                 # Underfitting loss curve
│   └── overfit_loss.png                                  # Overfitting loss curve
│
├── Assignment2.ipynb                                     # Main Jupyter/Colab notebook
└── README.md                                              # Project documentation
```

---


##  Setup & Installation

Follow the steps below to set up and run the project.

---

### 1️ Install Dependencies

Make sure Python **3.8+** is installed.

```bash
pip install -r requirements.txt
```

---

### 2️ Download or Clone the Repository

```bash
git clone https://github.com/<your-username>/<repo-name>.git
cd <repo-name>
```



---

### 3️ Add the Dataset

Place the dataset file:

```
Pride_and_Prejudice-Jane_Austen.txt
```

inside:

```
data/raw/
```

(Create the folder if it does not exist.)

---

###  Preprocessing

Run the preprocessing script to generate vocabulary and dataset splits:

```bash
python src/preprocess.py
```

This will create:

```
data/processed/train.pt
data/processed/val.pt
data/processed/test.pt
data/processed/itos.json
```

---

##  Training 

After preprocessing is completed and the processed files are available in `data/processed/`, you can start training the model.

---

### 1️ Run the Training Script

To train the LSTM model:

```bash
python src/train.py
```

This will:

- Load the processed dataset (train/val/test)
- Build the LSTM model
- Train for the configured number of epochs
- Save the **best performing model** automatically as:

```
outputs/best_model.pt
```

---

### 2️ Training Outputs

During training, the following files will be generated inside the `outputs/` folder:

```
best_model.pt          → Best saved LSTM model
underfit_loss.png      → Loss curve for underfitting experiment
overfit_loss.png       → Loss curve for overfitting experiment
```

You may also print:

- Train loss per epoch  
- Validation loss per epoch  
- Perplexity score  

These logs will appear automatically in the terminal or Colab output.

---

### 3️ Changing Training Hyperparameters (Optional)

You can modify training settings inside **src/train.py**, such as:

```python
epochs = 3
batch_size = 64
embed_dim = 200
hidden_dim = 400
learning_rate = 0.001
```

  



---

### 4 Training Completion

When the training finishes, you will see output like:

``` bash
Epoch X | Train Loss: ... | Val Loss: ... | Perplexity: ...
Saved new best model!
```

You can now move to **evaluation and text generation**.

---
## Evaluation

After training is completed and `best_model.pt` is generated, you can evaluate the model's performance using perplexity.

Run:

```bash
python src/evaluate.py
```

This script will:

- Load the saved model (`outputs/best_model.pt`)
- Load the test dataset (`data/processed/test.pt`)
- Compute:
  - Test Loss
  - Test Perplexity
A lower perplexity indicates a better language model


---

##  Inference (Text Generation)

Once the model is trained, you can generate text using the inference script.

Run:

```bash
python src/generate.py --prompt 
```

Arguments:

| Argument | Description |
|---------|-------------|
| `--prompt` | Starting text for generation |
| `--length` | Number of words to generate |


---
## Required Files for Inference

Ensure the following files exist before running text generation:

```bash
outputs/best_model.pt
data/processed/itos.json     # Vocabulary mapping
```

Without these files, inference will not work.


---
##  Results

After training the LSTM Language Model on the *Pride and Prejudice* dataset, the following results were obtained.

### ✔️ Underfitting Experiment
A small model (low embedding size, hidden size, and fewer layers) was trained to **intentionally underfit** the dataset.

**Observed behavior:**
- Training loss decreases slowly  
- Validation loss stays high  
- Model struggles to learn long-term context  

**Loss Curve:**

![Underfit Loss](https://github.com/pavs123-gt/Assignment2-IIITH/blob/main/underfit.png?raw=true)

---

### ✔️ Overfitting Experiment
A larger LSTM model (higher embedding size, hidden dimension, more layers, dropout disabled) was trained to **intentionally overfit**.

**Observed behavior:**
- Training loss decreases rapidly  
- Validation loss remains higher  
- Model memorizes training data rather than generalizing  

**Loss Curve:**

![Overfit Loss](https://github.com/pavs123-gt/Assignment2-IIITH/blob/main/overfit.png?raw=true)

---

### ✔️ Perplexity Scores

| Model Type      | Train Perplexity | Validation Perplexity |
|-----------------|------------------|------------------------|
| Underfitting    | High             | Very High             |
| Overfitting     | Very Low         | Higher Than Training   |

Perplexity is a measure of how well the model predicts the next word.  
Lower perplexity → better language modeling.

---

### ✔️ Sample Generated Text

Below is an example of text generated using the trained model:

```
<your generated output will appear here after inference>
```

(Replace with your generated text once you run inference.)

---

## 📝 Summary

- The underfitting model lacked learning capacity.  
- The overfitting model memorized but did not generalize well.  
- Final trained model achieves reasonable perplexity and generates coherent text.  

---
## Model Architecture

This project implements a **word-level LSTM (Long Short-Term Memory) Language Model** created from scratch using PyTorch.

The model takes sequences of word indices as input and predicts the **next word** in the sequence.

---

### 🔹 Architecture Components

#### **1. Embedding Layer**
- Converts each word index into a dense vector representation.
- Embedding size: *configurable (e.g., 200 for overfitting model)*  
- Helps the model learn semantic meaning of words.

#### **2. Multi-Layer LSTM**
- 1–2 stacked LSTM layers depending on configuration.
- Hidden size: *configurable (e.g., 400 for overfitting model)*  
- Captures long-term dependencies and context in the text.
- `batch_first=True` for easier input formatting.
- Optional dropout between layers to reduce overfitting.

#### **3. Fully Connected Output Layer**
- Maps LSTM hidden state → vocabulary size.
- Produces logits for the next-word prediction.

---

### 🔹 Forward Pass Flow

```
Input word indices (batch)  
        ↓  
Embedding Layer  
        ↓  
LSTM Layers  
        ↓  
Final Hidden State  
        ↓  
Linear Output Layer  
        ↓  
Probability distribution over next word
```

---

### 🔹 Model Summary (Example)

```
LSTMLanguageModel(
  (embedding): Embedding(vocab_size, embed_dim)
  (lstm): LSTM(embed_dim, hidden_dim, num_layers=2, batch_first=True, dropout=0.3)
  (fc): Linear(hidden_dim → vocab_size)
)
```

---

### 🔹 Why LSTM?

LSTMs are effective for language modeling because they:
- Remember long-term dependencies  
- Reduce vanishing gradient problems  
- Capture sequential patterns in natural language  

---

### 🔹 Loss Function & Optimization

- **Loss:** Cross-Entropy Loss  
- **Optimizer:** Adam  
- **Evaluation Metric:** Perplexity (exp(loss))

---

This architecture forms the foundation of the training and generation modules used in the project.


##  Download Links

This project requires several files for **training**, **evaluation**, and **inference**.  
You can download all necessary resources from the links below.

---

### 🔹 1. Dataset  
Download the original text dataset:

👉 **Pride and Prejudice – Jane Austen**  
🔗 *[Download Dataset](https://github.com/pavs123-gt/Assignment2-IIITH/commit/0a7ca9c62e989b9f8dc69e189d577a111b703aea)*

Place the file in:

```
data/raw/Pride_and_Prejudice-Jane_Austen.txt
```

---

### 🔹 2. Trained Model  
Download the trained LSTM model:

👉 **best_model.pt**  
🔗 *[Download Trained Model](YOUR_MODEL_LINK_HERE)*

Save it in:

```
outputs/best_model.pt
```

---

### 🔹 3. Vocabulary File  
Token-to-word mapping:

👉 **itos.json**  
🔗 *[Download Vocabulary File](https://github.com/pavs123-gt/Assignment2-IIITH/blob/main/itos.json)*

Save in:

```
data/processed/itos.json
```

---
### 🔹 4. Preprocessed Data (val.pt, test.pt, itos.json): 


👉 val.pt  
https://github.com/pavs123-gt/Assignment2-IIITH/blob/main/val.pt

👉 test.pt  
https://github.com/pavs123-gt/Assignment2-IIITH/blob/main/test.pt

👉 itos.json  
https://github.com/pavs123-gt/Assignment2-IIITH/blob/main/itos.json
```
---
### 🔹 5. Loss Curves :
Underfitting and overfitting experiment results:

👉 **Loss Curve Images:**
```bash
- 🔗 *[underfit_loss.png](https://github.com/pavs123-gt/Assignment2-IIITH/blob/main/underfit.png?raw=true)
*
```
```bash
- 🔗 *[overfit_loss.png](https://github.com/pavs123-gt/Assignment2-IIITH/blob/main/overfit.png?raw=true)
```






























