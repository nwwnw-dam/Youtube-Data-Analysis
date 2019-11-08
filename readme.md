## Youtube Analysis
### Setup/Install/Run
* Everything runs on anaconda base + add-ons
* As far as possible, missing libraries should be installed with conda installer not pip installer
* GloVe Embeddings to be downloaded are found here - http://nlp.stanford.edu/data/glove.twitter.27B.zip (use the 200D one)
### Important Notebooks
* EDA.ipynb
    * Exploratory Data Analysis
    * Gives you a merged reviews.csv and videos.csv
* Category Prediction using comments.ipynb
    * We preprocess the text + stemming
    * Use TF-IDF as feature vectors to try various models
    * Best model is Logistic Regression 65.9%
* Category prediction using video title and tags Part 1/Part 2.ipynb
    * Similar preprocessing as comments except no stemming
    * Best model is Naive Bayes with 71.0%
* Analyze Relationship between Like_Dislike_View_Ratio and Sentiment.ipynb
    * We find a weak correlation between like/dislike-ratio to sentiment of text
### Git Workflow
* Fork this master repo to your own account
* Git clone from your own account repo
* Git add/commit on your computer as usual
* Git push to your account repo
* How to pull request properly:
   * Pull from master repo, resolve the conflicts
   * Push to your account repo
   * Submit pull request
