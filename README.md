# Problem: What emotion is directed towards which product

This project focuses on identifying emotions directed towards specific products from user-generated tweets. The dataset contains labeled examples with emotions and product mentions. The task includes performing Exploratory Data Analysis (EDA), augmenting the dataset, fine-tuning a pre-trained transformer model (DistilBERT), and making predictions on the test set.

## Dataset
The dataset consists of tweet texts, labeled with emotions and product mentions. It includes both training and test datasets:

* **Training Set:** Contains tweet text, whether an emotion is directed at a product, and product information.
* **Test Set:** Contains tweet text without labels (for predictions).

## Exploratory Data Analysis
EDA was performed to understand the data distribution, including:

* Dataset shape: (8589, 3)
* Tweet Length Distribution: Visualized the tweet text length to understand its variation.
  ![Tweets Distribution](https://github.com/gulshan-100/WYSA-AI-assignment/blob/main/Images/tweets.png)
* Emotions Distribution: A visualization of the different emotions in the dataset.
  ![Emotions Distribution](https://github.com/gulshan-100/WYSA-AI-assignment/blob/main/Images/emotions.png)
* Product Distribution: Analysis of which products are being mentioned.
  ![Product Distribution](https://github.com/gulshan-100/WYSA-AI-assignment/blob/main/Images/products.png)
* Null values: Null values were handled by dropping rows with missing tweet text.

## Data Preprocessing
The tweet text was preprocessed as follows:

* Lowercased the text
* Removed URLs and punctuation
* Removed stopwords
* Tokenized the text using word_tokenize from nltk
* The dataset was split into training and evaluation sets (80%-20%).

## Ways to improve the dataset further
* **Increase Dataset Size:**

  * Data Augmentation: Use techniques like paraphrasing or synonym replacement to create more examples.
  * Collect More Data: Scrape additional tweets or reviews from social media and e-commerce platforms.
  * Balance Classes:

* **Handle Class Imbalance:** Use oversampling or undersampling to ensure all emotions/products are adequately represented.
* **Text Preprocessing:**
  * Expand Contractions: Convert contractions (e.g., "can't" to "cannot") for consistency.
  * Spell Check: Correct typographical errors to ensure clean input data.

* **Incorporate Pretrained Embeddings:** Utilize word embeddings like GloVe or Word2Vec for better text representation.

## Model Fine-Tuning
The model used in this project is DistilBERT, a transformer-based model pre-trained on large text corpora. The model was fine-tuned using the transformers library to classify the emotion and/or product mentions from the tweets.

**Key steps:**

* **Tokenization:** The tweets were tokenized using DistilBertTokenizer.
* **Fine-tuning:** The model was fine-tuned on the training dataset for 5 epochs with a learning rate of 0.001.
* **Training Arguments:**
* **Learning Rate:** 0.001
* **Batch Size:** 16
* **Epochs**: 5
* **Warmup Ratio:** 0.1
* **Save and evaluation strategy:** On every epoch
* **Metrics:** The model was evaluated based on loss. The best model was saved based on evaluation loss.
The model and tokenizer were saved for future inference.

## Deployment Instructions
To deploy the model into production:
* **Flask API Creation:** Create a Flask application to serve the trained model. This application should load the model and provide an endpoint where users can send requests with text data to get predictions.
* **Containerization:** You can use Docker to containerize the model serving application. Create a Dockerfile that installs all necessary dependencies and serves the model.
* **Cloud Deployment:** You can deploy the container on services like AWS EC2, Google Cloud Run, or Azure App Services.
* **CI/CD Pipeline:** Automate the deployment process with a CI/CD tool such as GitHub Actions or CircleCI. Each code push can trigger a pipeline that builds, tests, and deploys the updated model.
