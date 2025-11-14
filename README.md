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


```
---

##  Required Files for Inference

Ensure the following exist:

``` bash
outputs/best_model.pt
data/processed/itos.json        # Vocabulary mapping
```

Without these, generation will not work.

---
























## 🚀 Model Architecture
The final model uses:

- **Embedding dimension:** 200  
- **Hidden size:** 400  
- **Layers:** 2 LSTM layers  
- **Dropout:** 0.3  
- **Loss:** CrossEntropyLoss  
- **Optimizer:** Adam  
- **Batch size:** 64  
- **Sequence length:** 40 tokens  

---

## 📊 Results

### **✔ Main Model**
- **Validation Loss:** (value shown in notebook)  
- **Validation Perplexity:** (value shown in notebook)

### **✔ Underfitting Model**
- Small LSTM (embed=50, hidden=64, layers=1)
- High training & validation loss
- No learning → as expected

### **✔ Overfitting Model**
- Large LSTM (embed=300, hidden=600, layers=3)
- Training loss decreases fast
- Validation loss increases → overfitting detected

Loss curves for both experiments are included in:

---

## 📈 Loss Curves
- **Underfitting:** Slow/no learning  
- **Overfitting:** Training improves but validation worsens  
(Plots uploaded in outputs/ folder)

---

## 🧪 Evaluation
The final LSTM model was evaluated on a held-out **test split**, and perplexity is reported in the notebook.

---

## 📌 Files Included
- `Assignment2.ipynb` — Full implementation  
- `best_model.pt` — Saved best model (lowest validation loss)  
- `underfit_loss.png` — Underfitting plot  
- `overfit_loss.png` — Overfitting plot  
- Processed dataset files (`train.pt`, `val.pt`, `test.pt`, `itos.json`)

---

## ✔ Status
**All tasks from the assignment are completed successfully.**  
The repository contains the full solution along with results and model weights.







