# Replication_COMMTR
This is the replication package required by COMMTR for the article "Public Perception of Electric Vehicles on Reddit over the Past Decade".

## Raw data
The raw data for Reddit submission (RS) and Reddit Comments (RC) are from the Pushshift database (https://files.pushshift.io/reddit/), which contain all the data from Reddit platform. This raw dataset is too large to upload here, but you could download them from Pushshift directly. 

Following the data filtering steps described in the manuscript, we provide the secondary Reddit data which is directly related to Electric vehicle (EV) discussions. They are stored as monthly dataset in the RS and RC folders. The overall Reddit comment dataset is also given with the name "df_reddit_extend.pkl", which merges all the monthly Reddit comments in RC folder.

# Secondary data
Other necessary secondary data for the replication can also be found with .pkl format. You can easily look into all the secondary data by using Pandas Python package and one exmple is shown below:

```python
import pandas as pd
df_reddit_extend = pd.read_pickle("df_reddit_extend.pkl")
df_reddit_extend.head()
```

Explanation of important secondary data:

**_df_reddit_extend.pkl_**: The merged Reddit comments that are related with EV and are filtered from raw data.

**_ldamallet.gensim_**: The topic model generated with the wrapper for Mallet LDA in the Gensim Python toolkit.

**_df_sentence_dataready_**: After tranditional data preprocessing described in the manuscript, some very short comments would be removed and the remaining Reddit comments from **_df_reddit_extend.pkl_** will be converted to this file. We need this dataset to combine the topic modeling and sentiment analysis

**_vader_df_topic_sents_keywords.pkl_**: This dataset contains the VADER sentiment score for each post in the **_df_sentence_dataready_**. The calculation process is contained in the code but this process took very long time so we stored the results to save time.

**_monthlyafinn.pkl, monthlyVADER.pkl_**: Similar to the **_vader_df_topic_sents_keywords.pkl_**, we calculated the monthly average AFINN and VADER sentiment scores in the **_df_sentence_dataready_**. The calculation process is also contained in the code and we stored the results to save time.

**_monthlyPolarity.pkl, monthlySubjectivity.pkl_**: Another commonly used sentiment score calculated from Python textblob package, we did not present the results in the manuscript but added here as another reference. 

**_LIWC2015_Results_df_reddit_extend.csv_**:Another commonly used sentiment score calculated from LIWC2015 software, we did not present the results in the manuscript but added here as another reference.. As showed in the jupyter notenook, all the monthly sentiment scores are highly consistent.

**_dic_subredditVADER.pkl_**: A dictonary file for the sentiment scores of all the posts in different subreddits to perform the subreddit clustering. We selected the top subreddits for EV discussion as described in the paper, the collection of all the sentiment scores in each subreddit took very long time and we stored the results in this file. The replication is easy since you only need to extract all the posts from each subreddit and calculate the sentiment scores of the posts.

# Code
The code for replication of main results is written with Python and can be found in the Reddit_Replication.ipynb file. This is a jupyter notebook (https://jupyter.org) file. If you want to run the file on your local machine, you need to install jupyter notebook and all other required packages in the requirements.txt file.




Any data that resides in a this GitHub repository is controlled and owned by the University of Colorado Boulder.


