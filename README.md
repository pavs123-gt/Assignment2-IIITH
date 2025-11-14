
# Assignment 2 – LSTM Language Model (IIIT Hyderabad)

This repository contains my complete implementation for **Assignment 2: Statistical Language Modeling using LSTM Networks**.

## 📌 Overview
In this assignment, I built a word-level language model using a multi-layer LSTM. The model is trained on the text **“Pride and Prejudice – Jane Austen”**, and it learns to predict the next word in a sequence.

The project includes:
- Text preprocessing and vocabulary creation
- Sequence generation using a sliding window
- Train/validation/test split
- Custom PyTorch Dataset and DataLoader
- LSTM Language Model implementation
- Underfitting and overfitting experiments
- Loss curves for both experiments
- Model training and perplexity evaluation

---
## 📂 Project Structure

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







