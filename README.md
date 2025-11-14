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
- [Evaluation & Inference](#evaluation--inference)
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
#  Setup & Installation

Follow the steps below to run this project on any system.

---

## 1️ Install Dependencies
Make sure Python 3.8+ is installed.

```bash
pip install -r requirements.txt

##Download or Clone the Repository
``bash 
git clone https://github.com/<your-username>/<repo-name>.git
cd <repo-name>
```
##Add the Dataset
``bash
Pride_and_Prejudice-Jane_Austen.txt

```





















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







