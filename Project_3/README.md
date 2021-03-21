# Background

Many people relies on reddit.com as their source of information when in doubt. Reddit gains its popularity due to the constant support of its fanbase who actively exchanging information and opinion about certain matters which continually increase the wealth of resources that it accumulates. Specifically, reddit.com provides a subchannel for its communities to discuss matter pertaining to specific topic on a platform called subreddit. Subreddit covers a variety of topics ranging from politics, science, entertainment, music, books, sports and many more. These subreddits, which are maintained by reddit administrators who spent considerable amount of resources ensuring no harrassment related posts ([source](https://en.wikipedia.org/wiki/Reddit)), attracts like-minded people and slowly develop to have distinct cultures from one another. 

This organically evolving culture, despite being mostly good as it promotes safe environment for the fanbase to express themselves, sometimes can feel foreign and may be daunting for new people who wants to seek information on the platform. Therefore, this project aims to understand the cultural aspect and semantic of differing subreddits through the lens of Natural Language Processing (NLP). The two subreddits of choice for the analysis are https://www.reddit.com/r/Buddhism/ and https://www.reddit.com/r/Christianity/ as the subreddits are two different yet somewhat similar topic about religion.

# Problem Statement

Buddhism and Christianity subreddits have been around since March 2008 and January 2008, accordingly. Over the pass 12 years, they have grown into an ecosystem where many people interested about the religion discuss about matters pertaining to life from the lense of each religion. Despite these similarities, the two subreddits have their uniqueness about what information being exchanged and the means that information is exchanged. Therefore, this project aims to obtain insight on the underlying linguistic and cultural pattern between the Christianity and Buddhism subreddits.

# Proposed Approach

To analyse the underlying cultural context of these two subreddits, the project is divided into two folds. 
1. Scrape post title, post text and comments from each subreddits and find which combination of data is able to provide the most distinctive difference between the subreddits.
2. Analyse the post for any cultural difference **using exploratory data analysis and NLP**. 
    - **NLP** through Count Vectorizer and Tf-idf Vectorizer is introduced to **analyse the frequency of word usage for both subreddits**.
    - The **strength of the difference** can be predicted by **how well the NLP model classify a series of posts** from the subreddits to their respective origin. If the NLP model is able to capture high accuracy in this classification activity, we can conclude that there is indeed a difference in subreddit word usage. 
    
The vectorization method described above only covers the means to separate a string of text into its composition words. Subsequently, machine learning classifiers are deployed and compared against each other to obtain the most suitable classifier for this context. **The most useful classifier would be one with high explainability, thus provides insight on different words used in each subreddit, but also have reasonable accuracy as a guarantee that the validity of our deduction.**

# Executive Summary

Subreddit within reddit.com provides a safe environment for like-minded people to exchange information on a specific topic. Given some time, these subreddits develops their own unspoken set of culture and linguistic uniqueness. This unique 'accent' may feel foreign to a subredditer with little familiarity to the subreddit and may be daunting for him/ her to post a question. 

Therefore, a similar yet contrasting subreddits are chosen to observe the possibility to identify distinct features on them based on **Exploratory Data Analysis and Natural Language Processing**. The two subreddits of choice are **Christianity and Buddhism** subreddits. They share similarities in terms of they are both religion-based subreddit but from a different religion doctrine. The result are promising as the analysis managed to uncover unique linguistic pattern and subtle cultural difference between the two subreddits. 

# Summary

To obtain insight on linguistic pattern and cultural difference on both subreddits, the project is broken down into two parts:

## Data Gathering and Selection

Dataset is obtained by web-scraping both subreddits using *requests* library. This way we are able to extract title, post text (selftext) and first few (earliest) comments on the subreddits. Subsequently, a function is created to automate the scrapping process to collect sufficient posts for our analysis. 

After a few iteration, it was found that the best set of data to train the model is to include title, selftext and three of the first comment on the posts. This results in a higher accuracy classification model which means that the data contains sufficient linguistic pattern to differentiate the subreddits.

## Linguistic Pattern Analysis through EDA and NLP

EDA steps on both subreddits uncovers a few observations:
- People on Buddhism subreddit are more likely to post empty selftext compared to in Christianity subreddit. 
    - Most of these empty posts are posts with pictures or videos.
- On average people on Christian subreddit share a slightly longer post than people on Buddhism subreddit. 
    - Meanwhile, peole tends to share a longer response comments on the post in Buddhism subreddit
- Buddhism subreddit is three times more likely to contain links to external resources, especially on the comment section compared to Christianity subreddit.

There are also some linguistic pattern observed on both subreddits after performing analysis wit the help of NLP:
- People on Buddhism subreddit frequently uses the word 'one' to refer to the meaning of 'an individual' in the context of providing people some advice. This is unseen in Christianity subreddit.
- Both subreddits spread positive sentiments especially on the comments section. 
    - There are also some depressing posts on both subreddits, i.e. relating to suicide, bad luck or misfortune. However, the communities on both subreddits have the tendency to provide consolation from the perspective of each religion.
- There are words that are frequently used more in one subreddit compared to the counterpart:

| Topic                                     | Token Primarily used in <br>Christian Subreddit | Token Primarily used in <br>Buddhism Subreddit              |
|:-------------------------------------------|:---------------------:|:---------------------------------:|
| Founder/ Supreme                          | Jesus, Christ, Lord | Buddha                          |
| Knowledge Transmission <br>and Repository | Bible               | Teaching, Dharma                |
| Believer                                  | Christian           | Buddhist, Monk                  |
| Doctrine                                  | Faith, sin          | Karma, Mind                     |
| Activity                                  | Pray, Church        | Practice, Meditation, Tradition |

The observation above are obtained using an NLP model built upon Tf-idf vectorizer and Logistic Regression classifier. The choice of the model is due to these reasons:
- Tf-idf vectorizer:
    - Provides weightage on the presence of each token relative of the frequency of the post and token resulting in a better model performance (lower bias and variance) on unseen data
- Logistic Regression classifier:
    - Provides a better model performance (lower bias and variance) on unseen data even on default hyperparameter values
    - Provides interpretability which can gives us an insight on which words are more closely related to each subreddit
    

## Model Limitation and Recommendation

Of course the model is not without limitation. Some posts that does not strictly talk about specific religion topics may be predicted wrongly. These posts are usually relating to life in general which may not contain any mention of a strong predictor words (jargons). It is more likely for a shorter post with little or no comments to be wrongly classified due to the lack of these jargons. 

However, some of these posts are relatively easily to be classified to the correct subreddit by human interpreter. If falsely classifying posts are not acceptable for some reasons, a few ways to improve the model are by:
- Let human interpreters to read through posts with similar prediction probability between both subreddits. However, for a bigger data, this may be too costly. 
- Build the model using Bidirectional Encoder Representation from Transformer (BERT) as it is a context-dependent model which performs the word embedding based on the neighboring words in which the word appear. This way, it will be able to capture the context of the discussion without being too reliant about a specific keywords.

Link to slides: https://docs.google.com/presentation/d/1vJjR-00NWs5335ncVJiF3lMP-Oo50paJSFY9kcFlGoQ/edit?usp=sharing