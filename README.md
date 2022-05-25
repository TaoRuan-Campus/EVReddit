# Replication_COMMTR
This is the replication package required by COMMTR for the article "Public Perception of Electric Vehicles on Reddit over the Past Decade".

The raw data for Reddit submission (RS) and Reddit Comments (RC) are from the Pushshift database (https://files.pushshift.io/reddit/), which contain all the data from Reddit platform. This raw dataset is too large to upload here, but you could download them from Pushshift directly. 

Following the data filtering steps described in the manuscript, we provide the secondary Reddit data which is directly related to Electric vehicle (EV) discussions. They are stored as monthly dataset in the RS and RC folders. The overall Reddit comment dataset is also given with the name "df_reddit_extend.pkl", which merges all the monthly Reddit comments in RC folder.

Other necessary secondary data for the replication can also be found with .pkl format. You can easily look into all the secondary data by using Pandas Python package and one exmple is shown below:

```python
import pandas as pd
df_reddit_extend = pd.read_pickle("df_reddit_extend.pkl")
df_reddit_extend.head()
```

Explanation of important secondary data:

_df_reddit_extend.pkl_: The merged Reddit comments that are related with EV and are filtered from raw data.
<!-- ldamallet.gensim -->: The topic model generated with the wrapper for Mallet LDA in the Gensim Python toolkit


The code for replication of main results is written with Python and can be found in the Reddit_Replication.ipynb file. This is a jupyter notebook (https://jupyter.org) file. If you want to run the file on your local machine, you need to install jupyter notebook and all other required packages in the requirements.txt file.




Any data that resides in a this GitHub repository is controlled and owned by the University of Colorado Boulder.


