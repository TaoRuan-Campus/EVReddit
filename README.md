# Replication Package
This is the replication package required by COMMTR for the article "Public Perception of Electric Vehicles on Reddit over the Past Decade".

## Raw data
The raw data for Reddit submission (RS) and Reddit Comments (RC) are from the Pushshift database (https://files.pushshift.io/reddit/), which contain all the data from Reddit platform. This raw dataset is too large to upload here, but you could download them from Pushshift directly. 

## Secondary data
Following the data filtering steps described in the manuscript, we provide the secondary Reddit data which is directly related to Electric vehicle (EV) discussions. They are stored as monthly dataset in the RS and RC folders. The overall Reddit comment dataset is also given with the name "df_reddit_extend.pkl", which merges all the monthly Reddit comments in RC folder.

Other necessary secondary data for the replication can also be found with .pkl format. You can easily look into all the secondary data by using Pandas Python package and one exmple is shown below:

```python
import pandas as pd
df_reddit_extend = pd.read_pickle("df_reddit_extend.pkl")
df_reddit_extend.head()
```

Explanation of important secondary data (**NOTE: we are sorry that we cannot provide all the secondary data in this repository but we provided a sample dataset for each of the secondary data. However, with the raw data and the processing steps in our manuscript, the audience can easily reproduce the full secondary data""):

**_df_reddit_extend.pkl_**: The merged Reddit comments that are related with EV and are filtered from raw data.

**_ldamallet.gensim_**: The topic model generated with the wrapper for Mallet LDA in the Gensim Python toolkit.

**_df_sentence_dataready_**: After tranditional data preprocessing described in the manuscript, some very short comments would be removed and the remaining Reddit comments from **_df_reddit_extend.pkl_** will be converted to this file. We need this dataset to combine the topic modeling and sentiment analysis

**_vader_df_topic_sents_keywords.pkl_**: This dataset contains the VADER sentiment score for each post in the **_df_sentence_dataready_**. The calculation process is contained in the code but this process took very long time so we stored the results to save time.

**_monthlyafinn.pkl, monthlyVADER.pkl_**: Similar to the **_vader_df_topic_sents_keywords.pkl_**, we calculated the monthly average AFINN and VADER sentiment scores in the **_df_sentence_dataready_**. The calculation process is also contained in the code and we stored the results to save time.

**_dic_subredditVADER.pkl_**: A dictonary file for the sentiment scores of all the posts in different subreddits to perform the subreddit clustering. We selected the top subreddits for EV discussion as described in the paper, the collection of all the sentiment scores in each subreddit took very long time and we stored the results in this file. The replication is easy since you only need to extract all the posts from each subreddit and calculate the sentiment scores of the posts.

## Code
The code for replication of main results is written with Python and can be found in the Reddit_Replication.ipynb file. This is a jupyter notebook (https://jupyter.org) file. You can download and check the code on your local machine. We have some headlines in the notebook to lead you to the visualization code. For example, after following the filtering steps in our manuscript then you are able to obtain the monthly Reddit comments and Reddit submissions. With the code below presented in the **_1.1  Monthly RC/RS (log) count_** section, you are able to generate the exact **Figure 2** in the paper. 

```python
import pandas as pd
import matplotlib.pyplot as plt

fig, ax1 = plt.subplots(figsize=(10,6))
color = 'tab:blue'
lns1 = ax1.plot_date(d[:112], monthly_RS[:112],linestyle='-',c=color,label='EV Reddit Submissions')
ax1.set_xlabel('Year', fontsize= 20)
ax1.set_ylabel('# of Submissions', color=color, fontsize= 20)
ax1.tick_params(axis='y', labelcolor=color, labelsize= 13)

ax2 = ax1.twinx()
color = 'deeppink'
lns2 = ax2.plot_date(d[:112], monthly_RC[:112],linestyle='-.',c=color,label='EV Reddit Comments')
ax2.set_ylabel('# of Comments', color=color, fontsize= 20)
ax2.tick_params(axis='y', labelcolor=color, labelsize= 13)

ax1.tick_params(axis='x', labelsize= 15) 
# added these two lines
lns = lns1+lns2
labs = [l.get_label() for l in lns]
ax1.legend(lns, labs, prop={'size': 15},loc=0)
#plt.xticks(x,df_curr['Date'])
plt.title('EV-related Submissions and Comments on Reddit in 2011-2020', size=15)
plt.show()
```

Any data that resides in a this GitHub repository is controlled and owned by the University of Colorado Boulder.


