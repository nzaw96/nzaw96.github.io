## Reddit NLP Analysis of Posts/Submissions made by Users w/ Smoking Addiction

**Project description:** The goal of this project is to analyze changes in linguistic patterns of the Reddit users before and during the COVID-19 pandemic.
<br><br>
This project was presented at the ICWSM 2022 Conference, which was held in Atlanta, Georgia, USA. The code for this project can be found in <a href="https://github.com/nzaw96/Reddit-Addiction-Study">my Github repo</a> .

### 1. Project Motivation: Are people with smoking addiction getting the help and attention that they need during the COVID-19 pandemic?
The outbreak of the COVID-19 pandemic created global social distancing restrictions, which forced millions of people to stay at home. The imposed seclusion could cause further marginalization of the individuals with Substance Use Disorders (SUDs). With so much attention and prioritization of health-care services for the COVID-19 patients, it is likely that the individuals with SUDs, such as those with smoking addiction, who are feeling the secondary effects of the pandemic were forgotten. 

### 2. Project Workflow Chart
<img src=""/>

### 3. Data and Preprocessing

First, the Python Reddit API Wrapper <a href="https://praw.readthedocs.io/en/stable/">(PRAW)</a> was used to scrape all submissions and comments from the subreddit “r/stopsmoking” that were published on or after
January 1, 2018 until March 1, 2022. We consider the category of each post as either a comment post or a submission post. Submissions are the main posts made by a user that can start a discussion thread, whereas comments are responses to a given submission or a submission’s reply. A total of 35,425 submissions and 372,144 comments were retrieved. First, both submissions and comments were split into two subsets of data based on March 11th, 2020 – the date when COVID-19 was declared as a pandemic (therefore there were a total of 4 datasets). Next, the actual text bodies of each of the four datasets were cleaned by removing the punctuation, unicode characters, URLs and other non-alphanumeric characters. Different python NLP packages were used in this project: NLTK for n-grams, TextBlob for sentiment polarity computations, BERTopic for topic extraction, and gensim for Word2Vec embeddings.

### 4. Results

#### <em>n-grams</em>

An n-gram is the most frequently occurring sequence of N words in a corpus. The top-10 tri-grams (n=3) and quad-grams (n=4) extracted from each of the four datasets are listed in the Table 3, Table 4, Table 1, and Table 2. First, we observe that in both comments and submissions, that were published both before and after COVID-19 was officially declared to be a pandemic, the book written by Alan Carr called “Alan Carr’s Easy Way to Stop Smoking” (Carr 2004) is the most frequently referenced resource. Although all four tables share similarities in their n-grams, there is a subtle difference between Table 1 and Table 2 in terms of the polarity of the words in their n-grams. Table 2 contains n-grams that share their experiences while at the same time seeking advice from the community. On the other hand, when we consider polarity values, Table 1 contains n-grams that carry a more neutral tone and are also found in Table 2. This may suggest that staying at home during the pandemic might have caused them to seek extra emotional support and advice from their peers to achieve the goal of smoking cessation. No significant differences can be spotted between Tables 3 and Table 4 as the n-grams in both tables appear to be mostly positive.

<img src="images/RedditProj_ngram_subsBefore.png?raw=true"/>

<img src="images/RedditProj_ngram_subsDuring.png?raw=true"/>

<img src="images/RedditProj_ngram_commsBefore.png?raw=true"/>

<img src="images/RedditProj_ngram_commsDuring.png?raw=true"/>

<br><br>

#### <em>Sentiment Polarity Analysis</em>

<img src="images/sentPolarityC.png?raw=true"/>
Figure 1: Plot, representing the monthly average sentiment polarity score of comments, overlaid on the histogram that shows the number of comments published each month since January 2018.
<br><br>
<img src="images/sentPolarityS.png?raw=true"/>
Figure 2: Plot, representing the monthly average sentiment polarity score of submissions, overlaid on the histogram that shows the number of submissions published each month since January 2018.


<br><br>
For more details see [GitHub Flavored Markdown](https://guides.github.com/features/mastering-markdown/).
