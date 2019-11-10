## Youtube Data Analysis
### Installation
* Anaconda is required; Non-standard libraries may be included in Anaconda distributions but not Miniconda
    * As far as possible, barring some exceptions, missing libraries should be installed with conda, instead of pip
* Non-standard libraries:
    * kaggle
    * pillow - NOTE: 'pillow' must be installed with pip and not conda, to avoid an import bug - https://github.com/python-pillow/Pillow/issues/2945
    * seaborn
    * numpy
    * pandas
    * matplotlib
    * scikitlearn
    * TensorFlow
    * nltk
* Link to GloVe Embeddings to be downloaded - http://nlp.stanford.edu/data/glove.twitter.27B.zip (Use the 200D one)
### Obtaining the Dataset
* data_scraper/kaggle.ipynb
    * Obtaining the dataset used
    * Unzip the file kaggle.7z into the main folder
    * OR to download the dataset from Kaggle - NOTE: you will need to [prepare your kaggle API credentials](https://github.com/Kaggle/kaggle-api) (kaggle.json)
        * Run the kaggle.ipynb located in the 'data_scraper' folder; Files will be output into the main folder
        * OR download them via command line: Enter `kaggle datasets download datasnaek/youtube -p <path to extract to> --unzip` into the command prompt
### Important Notebooks
It is recommended to execute the notebooks in the following order:
* EDA.ipynb
    * Exploratory Data Analysis
    * Outputs merged reviews.csv and videos.csv
* Category Prediction using comments.ipynb
    * Preprocess text + Stemming
    * Use TF-IDF as feature vectors to try various models
    * Best model is Logistic Regression 65.9%
* Category prediction using video title and tags Part 1/Part 2.ipynb
    * Similar preprocessing as comments except no stemming
    * Best model is Naive Bayes with 71.0%
* Category prediction with Ensemble Model.ipyb
    * We find that emsembling the top 9 models in the previous 2 notebooks gave an improved accuracy of 73.8%
* Mining Association Rules for Tags.ipynb
    * We implement FP-Tree from scratch
    * We find all maximal frequent itemsets of support count >= 31 (support of 0.01)
    * We notice that tags are "top-heavy": If you permutate all possible rules of a maximal frequent set for all maximal frequent sets, the worst confidence of any rule is 99.4%
    * Hence, we can simply analyze the maximal frequent itemsets. This is because for each item in the maximal frequent itemset, it predicts the rest of the items in the maximal frequent itemset with at least 99.4% confidence
* Analyze Relationship between Like_Dislike_View_Ratio and Sentiment.ipynb
    * We find a weak correlation between like/dislike-ratio to sentiment of text
* Word Map.ipynb
    * We find the most important/relevant words for each category in the form of a word cloud
    * We analyze the amount of profanity in the videos
### 
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