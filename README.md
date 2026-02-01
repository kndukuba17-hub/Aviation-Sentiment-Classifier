# ✈️ Aviation Sentiment & Behavioral Classifier

## 📌 Project Overview
In the aviation industry, speed and interpretability are key. This project utilizes a **Supervised Machine Learning pipeline** to classify passenger feedback into actionable categories, allowing airlines to distinguish between "operational delays" and "service quality" issues.

## 🛠️ Technical Architecture
* **Algorithm:** Logistic Regression (Selected for high interpretability and speed).
* **Feature Extraction:** CountVectorization (Bag-of-Words) analysis.
* **Processing:** NLTK for text cleaning, tokenization, and stop-word removal.
* **Validation:** 80/20 Train-Test split with Confusion Matrix evaluation.

## 📊 Business Insights
* **Efficiency:** The model processes 14,000+ records in seconds, enabling real-time feedback monitoring.
* **Accuracy:** Achieved **~80% accuracy**, providing a reliable baseline for automated customer service ticketing.

## 🚀 How to Run
1.  Load the `Airline-Sentiment-2-w-AA.csv` dataset.
2.  Run the `Aviation_Sentiment_Model.ipynb` notebook.
3.  View the generated Word Clouds and Sentiment Distribution charts.
