# Employer Feedback Sentiment Analysis

A Flask-based employer review sentiment analysis application. This repository includes training logic, NLP preprocessing helpers, a deployed web app, and a smoke test client.

## Overview

This project analyzes employer feedback from Glassdoor-style reviews and predicts overall sentiment using a machine learning model. It includes:

- `app.py`: Flask web application serving an HTML interface
- `train_model.py`: script to train the sentiment model from review data
- `nlp_utils.py`: text preprocessing and feature preparation utilities
- `smoke_test_client.py`: client-side smoke test for validating the running app
- `templates/`: Jinja templates used by the Flask app
- `glassdoor-companies-reviews.csv`: dataset used for training
- `sentiment_model.pkl`: serialized trained classifier
- `smoke_test_response.html`: expected smoke test HTML output

## Features

- Clean and preprocess employer review text
- Train a sentiment classifier from a Glassdoor review dataset
- Serialize and reuse a trained model
- Serve predictions through a Flask web UI
- Validate the app with a smoke test client

## Setup

1. Create a virtual environment:

   ```powershell
   python -m venv .venv
   .\.venv\Scripts\activate
   ```

2. Install required packages. A sample list is:

   ```powershell
   pip install flask pandas scikit-learn nltk
   ```

   If the project uses additional libraries, install them as needed.

3. If the text preprocessing code uses NLTK, download required data:

   ```powershell
   python -m nltk.downloader punkt stopwords wordnet
   ```

## Training the Model

Run the training script to build or update the sentiment model:

```powershell
python train_model.py
```

This script should:

- load `glassdoor-companies-reviews.csv`
- preprocess review text
- train a sentiment classification model
- save the trained model to `sentiment_model.pkl`

## Running the Web App

Start the Flask application:

```powershell
python app.py
```

Then open your browser to:

- `http://127.0.0.1:5000`

Enter a review or employer feedback message and submit to see the predicted sentiment.

## Smoke Test

Use the smoke test client to verify the app is running correctly:

```powershell
python smoke_test_client.py
```

If the smoke test passes, the app is responding and the expected output is generated.

## Repository Structure

- `app.py` - main Flask application
- `train_model.py` - model training and persistence script
- `nlp_utils.py` - natural language preprocessing functions
- `smoke_test_client.py` - simple web app test client
- `templates/` - HTML templates for the user interface
- `glassdoor-companies-reviews.csv` - training data source
- `sentiment_model.pkl` - saved trained model
- `smoke_test_response.html` - expected smoke test HTML response

## Notes

- If `sentiment_model.pkl` is missing or outdated, re-run `train_model.py`.
- Customize the web UI by editing `templates/index.html` and `templates/base.html`.
- Update dependencies if new packages are added to the codebase.

