# ✈️ Aviation Sentiment Classifier — NLP Pipeline

![Python](https://img.shields.io/badge/Python-3.10%2B-blue)
![scikit-learn](https://img.shields.io/badge/scikit--learn-Pipeline-orange)
![NLP](https://img.shields.io/badge/NLP-Bag--of--Words%20%7C%20Word2Vec-green)
![Status](https://img.shields.io/badge/Status-Complete-brightgreen)

Classifying airline customer feedback (negative / neutral / positive) from **real Twitter data**, so operational teams can automatically route unhappy passengers to an escalated support queue.

> **Behavioural angle:** social-media sentiment is a real-time signal of how customers *feel* about a service failure. This project turns unstructured, emotional text into a triage decision.

---

## 📊 Results (measured, not estimated)

| Model | Test Accuracy | Macro F1 | Notes |
|-------|--------------:|---------:|-------|
| **Bag-of-Words + Logistic Regression** | **80.4%** | **0.74** | Best model. Tuned with `GridSearchCV` (32 candidates, 3-fold CV). |
| Word2Vec (25-dim) + Logistic Regression | 70.8% | 0.56 | Semantic embeddings underperform BoW on short, noisy tweets. |

- **Dataset:** Twitter US Airline Sentiment — **14,640 real tweets** (loaded at runtime from public mirrors with a fault-tolerant fallback).
- **Class imbalance:** the data is heavily skewed toward *negative* sentiment (typical of customer-service channels), so the model is evaluated on **macro F1**, not accuracy alone.
- **Honest finding:** the simpler Bag-of-Words model beat Word2Vec here — short tweets with irregular grammar favour n-gram structure over a small-corpus embedding. This is discussed in the notebook rather than hidden.

---

## 🛠️ Technical Approach

1. **Data ingestion** — real dataset pulled from public mirrors.
2. **Structural feature engineering** — a custom `TextCounts` scikit-learn transformer extracts meta-features from raw tweets: word count, mention/hashtag/URL counts, capitalised words, emoji count, and `!`/`?` usage.
3. **Text cleaning** — a custom `CleanText` transformer strips mentions/URLs, removes punctuation and stopwords, and lowercases; the 22 tweets emptied by cleaning are imputed with a placeholder token.
4. **Feature union** — `FeatureUnion` concatenates the engineered structural features with the vectorised text so the model sees both signals.
5. **Modelling & tuning** — `GridSearchCV` over n-gram range, `max_df`/`min_df`, regularisation (L1/L2) and `C`.
6. **Deployment simulation** — the tuned pipeline is retrained on the full dataset and scored against unseen "live" tweets.

## 🧰 Tech Stack
Python · pandas · NumPy · scikit-learn (`Pipeline`, `FeatureUnion`, `GridSearchCV`, custom transformers) · gensim (Word2Vec) · NLTK · Matplotlib · Seaborn

---

## 📁 Repository Structure
```
├── README.md
├── requirements.txt
├── notebooks/
│   └── aviation_sentiment_classifier.ipynb   # full pipeline, top to bottom
├── src/                                       # reusable transformers (see roadmap)
├── data/                                      # fetched at runtime — see data/README.md
├── images/                                    # exported charts
└── docs/
```

## 🚀 How to Run
```bash
# 1. Clone
git clone https://github.com/kndukuba17-hub/Aviation-Sentiment-Classifier.git
cd Aviation-Sentiment-Classifier

# 2. Install dependencies
pip install -r requirements.txt

# 3. Launch the notebook
jupyter notebook notebooks/aviation_sentiment_classifier.ipynb
```
Run all cells — the dataset downloads automatically at runtime, so no manual CSV download is required. Runs on Jupyter or Google Colab.

## 🗺️ Roadmap
- Extract the `TextCounts` / `CleanText` transformers into `src/` as an importable module.
- Add a transformer-based baseline (DistilBERT) for comparison.
- Wrap the tuned pipeline in a small Streamlit demo for live tweet scoring.

---
*Dataset: Twitter US Airline Sentiment (originally published on Kaggle / Crowdflower). Used here for educational, non-commercial purposes.*
