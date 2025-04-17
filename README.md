# Sentiment Analysis (WA responses)

This project performs sentiment analysis on user messages from a WhatsApp channel. It uses a manually labeled dataset to train a classification model capable of categorizing new incoming responses.

## Project Structure

All the logic is contained in a single Jupyter Notebook.

- **Data Extraction**: Messages are retrieved from BigQuery.
- **Preprocessing**: Text data is cleaned and transformed for modeling.
- **Labeling**: Messages are manually labeled into categories to create a training base.
- **Model Training**: A `Naïve Bayes` classifier is trained on the labeled data.
- **Evaluation**: The model is evaluated using standard classification metrics.
- **Visualization**: Charts and tables are generated to interpret model results and category distribution.

> Note: Although `KMeans` clustering was tested for automated label generation, manually labeled data provided better results and was used for training.

## Handling Class Imbalance

To address class imbalance and improve overall model performance:

- **Undersampling** was applied to reduce the number of majority class samples.
- **Class weights** were used to give more importance to minority classes during training.

This combination helped the model learn more effectively from all categories, reducing over-representation of the `"otro"` label. As a result:

- The number of predictions labeled as `"otro"` decreased.
- Recall for `"otro"` went down slightly.
- Precision and recall for the other, more informative categories increased significantly.

This trade-off led to better generalization and more accurate labeling across meaningful sentiment categories.

## Possible Improvements
- Increase labeled data for minority categories such as "spam", "interesado", "no interesado" and "grosero" to improve both training quality and evaluation metrics.
- Fine-tune a transformer model like BETO, a BERT model for Spanish, which could outperform Naïve Bayes if trained on a larger dataset.
- Experiment with other models such as Random Forest or Logistic Regression and perform hyperparameter tuning to explore potential performance gains.
- While Naïve Bayes is a strong baseline for text classification tasks, especially with small datasets, more advanced models might capture deeper patterns with sufficient data.

## Requirements

Install dependencies using:

```bash
pip install -r requirements.txt
```

