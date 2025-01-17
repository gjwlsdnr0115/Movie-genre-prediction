# Movie-genre-prediction
Predicting a movie's genre from its synopsis by using NLP

## Summary
- Used movie data from IMDB
- Processed data to have one-to-one match between synopsis and genre
- Embeddings from BERT
- Training logistic regression model

## 1. Data preprocessing
[(notebook)](./data_preprocessing.ipynb)


**Genres**
- Used columns ["original_title", "overview", "genres"] from raw data
- Excluded all genres except the top 5
- Included "Documentary, Horror" due to their distinctiveness
- Combined "Drama" and "Romance" into "Drama/Romance"
- Movies in the data have multiple genres. Left every row with only 1 genre. The genre with the least count survives
- Gave an index number for each genre(0~5)

**Synopsis**
- Removed all unnecessary text
- Removed rows with no sysnopsis

## 2. Model training
**DistilBERT + Logistic Regression**

**DistilBERT** [(notebook)](./BERT_embeddings.ipynb)
- Used DistilBERT due to efficiency
- model = DistilBert
- pretrained_weights = 'distilbert-base-uncased'
- Added classification token([CLS])
- Genreated tensor embeddings of [CLS] token
- Used embeddings to train regression model

**Logistic Regression** [(notebook)](./regression.ipynb)
- Model from scikit-learn
- features = embeddings from bert
- label = genre index

## 3. Testing
**score:** 0.60

**Further improvements**
- Need more data per genre
- Bert fine-tuning
- less labels if possible
