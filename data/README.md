# Data

This project uses the **Twitter US Airline Sentiment** dataset (~14,640 labelled tweets).

- **Source:** originally published on Kaggle / Crowdflower.
- **How it's loaded:** the notebook fetches the CSV at runtime from public GitHub mirrors, with a fault-tolerant fallback across several mirror URLs. No manual download is required.
- **Why it isn't committed here:** raw data is deliberately kept out of version control (`.gitignore`) to keep the repo lightweight and avoid redistributing the dataset.

If you prefer to run offline, download `Tweets.csv` from Kaggle and place it in this folder, then point the loader at the local path.
