## Youtube Data Analysis
### Installation
* Anaconda is required; Non-standard libraries may be included in Anaconda distributions but not Miniconda
    * As far as possible, barring some exceptions, missing libraries should be installed with conda, instead of pip
* Non-standard libraries:
    * kaggle
    * pillow 
        * NOTE: 'pillow' must be installed with pip and not conda, to avoid an import bug - https://github.com/python-pillow/Pillow/issues/2945
    * seaborn
    * numpy
    * pandas
    * matplotlib
    * scikitlearn
    * TensorFlow
    * nltk
    * textblob
        * NOTE: pip install textblob instead of conda
* Link to GloVe Embeddings to be downloaded - http://nlp.stanford.edu/data/glove.twitter.27B.zip (Use the 200D one)
### Obtaining the Dataset
* data_scraper/0B - kaggle.ipynb
    * EITHER Unzip the file kaggle.7z found in data_scraper/kaggle into same directory
    * OR to download the dataset directly via Kaggle API - NOTE: you will need to [prepare your kaggle API credentials](https://github.com/Kaggle/kaggle-api) (kaggle.json)
        * EITHER Run the kaggle.ipynb located in the 'data_scraper' folder; Files will be output into a folder - 'kaggle'
        * OR download them via command line: Enter `kaggle datasets download datasnaek/youtube -p <path to extract to> --unzip` into the command prompt
### Important Notebooks
It is recommended to execute the notebooks in the following order:
* 1 - EDA.ipynb
    * Exploratory Data Analysis
    * Outputs merged reviews.csv and videos.csv
* 2 - Category Prediction using Comments.ipynb
    * Preprocess text + Stemming
    * Use TF-IDF as feature vectors to try various models
    * Best model is Logistic Regression 65.9%
* 3 - Category Prediction using Video Titles and Tags Part 1/Part 2.ipynb
    * Similar preprocessing as comments
    * Best model is Naive Bayes with 71.0%
* 4 - Category prediction with Ensemble Modelling.ipyb
    * We find that ensembling the top 9 models in the previous 2 notebooks gave an improved accuracy of 73.8%
* 5 - Mining Association Rules for Tags.ipynb
    * We implement FP-Tree from scratch
    * We find all maximal frequent itemsets of support count >= 16 (support of 0.005)
    * We notice that tags are "top-heavy": If you permutate all possible rules of a maximal frequent set for all maximal frequent sets, the worst confidence of any rule is 99.1%
    * Hence, we can simply analyze the maximal frequent itemsets. This is because for each item in the maximal frequent itemset, it predicts the rest of the items in the maximal frequent itemset with at least 99.1% confidence
* 7 - Analyze Relationship between Like or Dislike Ratio and Sentiment.ipynb
    * We find a weak correlation between like/dislike-ratio to sentiment of text
* 8 - Word Map Part 1/Part 2.ipynb
    * We find the most important/relevant words for each category in the form of a word cloud
    * We analyze the amount of profanity in the videos
### Git Workflow
* Fork this master repo to your own account
* Git clone from your own account repo
* Git add/commit on your computer as usual
* Git push to your account repo
* How to pull request properly:
   * Pull from master repo, resolve the conflicts
   * Push to your account repo
   * Submit pull request
* Even if you do not PR, you should still pull from master repo regularly to get updates from others