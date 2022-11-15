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

### <em>n-grams</em>

An n-gram is the most frequently occurring sequence of N words in a corpus. The top-10 tri-grams (n=3) and quad-grams (n=4) extracted from each of the four datasets are listed in the Table 3, Table 4, Table 1, and Table 2. First, we observe that in both comments and submissions, that were published both before and after COVID-19 was officially declared to be a pandemic, the book written by Alan Carr called “Alan Carr’s Easy Way to Stop Smoking” (Carr 2004) is the most frequently referenced resource. Although all four tables share similarities in their n-grams, there is a subtle difference between Table 1 and Table 2 in terms of the polarity of the words in their n-grams. Table 2 contains n-grams that share their experiences while at the same time seeking advice from the community. On the other hand, when we consider polarity values, Table 1 contains n-grams that carry a more neutral tone and are also found in Table 2. This may suggest that staying at home during the pandemic might have caused them to seek extra emotional support and advice from their peers to achieve the goal of smoking cessation. No significant differences can be spotted between Tables 3 and Table 4 as the n-grams in both tables appear to be mostly positive.

<img src="images/RedditProj_ngram_subsBefore.png?raw=true"/>

<img src="images/RedditProj_ngram_subsDuring.png?raw=true"/>

<img src="images/RedditProj_ngram_commsBefore.png?raw=true"/>

<img src="images/RedditProj_ngram_commsDuring.png?raw=true"/>

### <em>Sentiment Polarity Analysis</em>

<img src="images/sentPolarityC.png?raw=true"/>
Figure 1: Plot, representing the monthly average sentiment polarity score of comments, overlaid on the histogram that shows the number of comments published each month since January 2018.
<br><br>
<img src="images/sentPolarityS.png?raw=true"/>
Figure 2: Plot, representing the monthly average sentiment polarity score of submissions, overlaid on the histogram that shows the number of submissions published each month since January 2018.
<br><br>

To further investigate how sentiment polarities changes, the average sentiment polarity value was plotted for each month for comments (shown in Figure 1) and for submissions (shown in Figure 2) separately. Both these plots show three main aspects – 1) average value of sentiment polarity per each month, 2) its moving average over time and, 3) distribution of total number of posts made in each month, as a histogram. Two main observations can be made on Figure 1. First, we see on the right edge of the plot that the average polarity for each month comes out to be positive. This suggests the responses to the submissions have been, by and
large, encouraging and empathetic. Secondly, we observe that the sentiment polarity score for the comments has decreased gradually since the start of the pandemic where the start date of the pandemic is marked with a vertical dashed line on the plot. Figure 2 shows that relative to comments, submission posts have lower positive polarity. This plot also shows that sentiment polarity score from month to month for submissions is more chaotic compared to the comments with no specific trend (p >0.05).

### <em>Topic Shifts</em>

Figure 3 shows the top-6 topics extracted from the four different subsets of data – before and during the pandemic for both comments and submissions separately. These topics highlight interesting aspects as follows. <b>Comments</b>: 1) before the pandemic, top-6 topics include vaping, how to fight cravings, reading Allan Carr’s books on ways to quit smoking, being drunk at a bar, different kinds of discomforts due to withdrawals, and triggers and cravings; 2) during the pandemic, top-6 topics include vaping, distracting themselves from cravings and resist, being drunk and hangovers, rambles about fighting addictions in general, smoking weed/cannabis, and fighting cravings; 3) When we compare the topics before and during the pandemic, discussions about drinking alcohol and hangovers jumped to be a more important topic during the pandemic than earlier; 4) Also, there is little to no discussion about reading books specific to ways on how to quit smoking; 5) We also noticed that discussion about marijuana/cannabis is one of the most important topics during the pandemic compared to earlier time period. These insights may suggest that at a high-level individuals might be fighting their urges to quit smoking but may be due to the pandemic, there are increased discussion about them consuming alcohol and hangovers as well as marijuana. Further analysis is required to investigate if individuals are using these alternatives as coping mechanisms during the pandemic while fighting the withdrawal symptoms and triggers on their journey to quit smoking. For <b>Submissions</b>: 1) the top topics of discussions before the pandemic are about vaping and cigarettes addictions, pulmonary issues including cough, asthma, and bronchitis, different withdrawal symptoms including depression, and anxiety, strong cravings to smoke, consuming alcohol (at a bar), failed to quit and relapsed; 2) during the pandemic,
the most important topic of discussion is about coughing, breathing and different pulmonary issues, seeking advice on how to quit and sharing their personal stories about when they started smoking, discussions about cravings, reading books about how to quit smoking, discussions about cravings, and drinking with friends and hangovers; 3) It is worth noticing that these topics during the pandemic are more personal through sharing their personal stories in order to seek advice on how to quit smoking and also sharing about consuming alcohol with their friends which we do not see clearly before the pandemic; 4) since some of the common symptoms of COVID-19 is shortness of breathe and cough, this might be the reason why we see discussions about pul- monary issues is the main topic of discussion; 5) stay-at-home orders to mitigate the spread of COVID-19 virus also
might be the factor for individuals to open up online and share more of their personal stories than earlier.

<img src="images/topicShift_commsBefore.png?raw=true"/>
Figure 3a: Topics for comments, before COVID-19.
<br><br>
<img src="images/topicShift_commsDuring.png?raw=true"/>
Figure 3b: Topics for comments, duriing COVID-19.
<br><br>
<img src="images/topicShift_subsBefore.png?raw=true"/>
Figure 3c: Topics for submissions, before COVID-19.
<br><br>
<img src="images/topicShift_subsDuring.png?raw=true"/>
Figure 3d: Topics for submissions, during COVID-19.
<br><br>
For more details see [GitHub Flavored Markdown](https://guides.github.com/features/mastering-markdown/).
