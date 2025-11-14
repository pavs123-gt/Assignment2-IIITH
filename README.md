
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
│   └── overfit_loss.png                                   # Overfitting loss curve
│
├── Assignment2.ipynb                                     # Main Jupyter/Colab notebook
└── README.md                                              # Project documentation


