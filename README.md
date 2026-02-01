# ✈️ Aviation Sentiment & Behavioral Classifier

## 🧠 Project Overview
Standard sentiment analysis often fails to capture the *cause* of customer frustration. In the aviation industry, a "negative" review could be due to a safety delay (acceptable) or rude staff (unacceptable).

This project utilises **Deep Learning (LSTM)** to go beyond simple polarity, classifying passenger feedback into actionable categories to inform service training and operational improvements.

## 🛠️ Technical Architecture
* **Model:** Long Short-Term Memory (LSTM) Neural Network.
* **Embeddings:** Word2Vec (to understand context, e.g., "gate" implies location).
* **Preprocessing:** NLTK for tokenization and stop-word removal.
* **Libraries:** TensorFlow/Keras, Pandas, Scikit-learn.

## 📊 Key Results
* **Accuracy:** Achieved **80% accuracy** on unseen test data (14,000+ records).
* **Business Impact:** Identified that 40% of negative sentiment was driven by "Information Clarity" rather than actual flight delays, suggesting a need for better communication protocols.

## 🚀 Usage
The notebook walks through the full pipeline:
1.  **Data Cleaning:** Handling unstructured text.
2.  **Vectorization:** Converting text to numeric sequences.
3.  **Training:** Model training with validation splits.
4.  **Evaluation:** Confusion Matrix and Loss/Accuracy plots.
