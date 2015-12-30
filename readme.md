Text Features Library
======

**Objective**: Provide a comprehensive list of tokenizers, features, and general NLP things used for text analysis with examples. The initial focus on features used for twitter data and sentiment analysis.

**Packages Used**: `nltk`, `spacy`, `pandas`, `scikit-learn`

Notebooks
======
### Features  
(roughly in order of increasing complexity)

1. [Count of ALL CAPS words](notebooks/ALL CAPS.ipynb)
- [Count of Bible Verses](notebooks/Bible Verses.ipynb)
- [Word n-grams (Bag of Words)](notebooks/Word n-grams - Bag Of Words - BOW.ipynb)
- [Character n-grams](notebooks/Character n-grams.ipynb)
- [Hashtag Counts](notebooks/Hashtag Counts - Bag of Hashtags.ipynb)
- [Hashtag Bag of Words](notebooks/Hashtag BOW.ipynb)
- [Named Entity Counts](notebooks/Named Entities Count - Bag of Named Entities.ipynb)
- [Brown Word Cluster assignments](notebooks/TweetNLP - Brown Word Clusters.ipynb)
- [Bing Liu Lexicon Derived Features](notebooks/Bing Liu Lexicon Features.ipynb)
- [NRC Hashtag Sentiments (unigrams)](notebooks/Bing Liu Lexicon Features.ipynb)
- [NRC Hashtag Sentiments (bigrams)](notebooks/NRC Hashtag Sentiments - bigrams.ipynb)
- [NRC Emotion Lexicon Features](notebooks/NRC Emotion Lexicon Features.ipynb)

#### Notes on Features
- Each feature is demonstrated on the STS-Gold dataset (see *Datasets* below).
- Each feature is evaluated on `accuracy` using 5-fold cross validation with `MultinomialNB (Multinomial Naive Bayes)`, `BernoulliNB (Bernoulli Naive Bayes)`, and `SVC (Support Vector Classifier)` in comparison to selecting the most frequent class (`DummyClassifier`)
  - these are the most commonly used models I see for text classification tasks
- The lexicons used for some advanced features have links within the notebook as well as in the *Lexicons* table below.
  - *They are not hosted in this repository to respect the wishes and licenses of their creators.*

### Tokenizers
- NLTK's `casual` tokenizer (`TweetTokenizer`)
  - Good for a tweet tokenization, takes hashtags, mentions, and emoji into account.
- NLTK's `word_tokenize` (default is `TreebankWordTokenizer`)
  - Good for simplicity's sake. The de-facto industry-standard [Penn Treebank](https://www.cis.upenn.edu/~treebank/tokenization.html) tokenization
- Christopher Potts [Sentiment-Aware Tokenizer](http://sentiment.christopherpotts.net/tokenizing.html#sentiment) (`HappyFunTokenizer`)
  - Takes all tokens from NLTK's `TweetTokenizer`, and adds/changes:
    - HTML character resolution
    - HTML feature tokenization (ie. tags like <\b>)
    - Does not split contractions
  - Has [negation approximating method](http://sentiment.christopherpotts.net/lingstruc.html#approach) for additional semantic features
  - Updated to work with python 3
- spaCy's default [tokenizer](https://spacy.io/docs#api) (uses Penn Treebank)
  - Good for a faster tokenizing in comparison to NLTK's `word_tokenize`
- TweetNLP [Tokenizer](http://www.cs.cmu.edu/~ark/TweetNLP/) ([python port](https://github.com/myleott/ark-twokenize-py))
  - Haven't used, I imagine it's similar to `Sentiment-Aware` and `TweetTokenizer`
  - Additional POS tagging features available on website

Datasets
======
### Sentiment Classification
*Source: [Evaluation datasets for Twitter sentiment analysis: a survey and a new dataset, the STS-Gold](http://oro.open.ac.uk/40660/1/paper1.pdf)*

| Dataset 	| Description  	| Download Link 	| Sentiment Transformation* |
|----	|---	|----	|---- |
| [Stanford Twitter Sentiment Test Set](http://help.sentiment140.com/for-students) (STS-Test/Sentiment140)   	| The Stanford Twitter sentiment corpus, introduced by Go et al. consists of two different sets, training and test. The training set contains 1.6 million tweets automatically labelled as positive or negative based on emotions. For example, a tweet is labelled as positive if it contains :), :-), : ), :D, or =) and is labelled as negative if it contains :(, :-(, or : (. The test set (STS-Test), on the other hand, is manually annotated and contains 177 negative, 182 positive and 139 neutrals tweets. 	| [download link](http://help.sentiment140.com/for-students)   	| (0 = negative, 2 = neutral, 4 = positive) |
|[Sanders-Twitter](http://www.sananalytics.com/lab/twitter-sentiment/)    	| This free data set is for training and testing sentiment analysis algorithms. It consists of 5,513 hand-classified tweets. Each tweet was classified with respect to one of four different topics. **Download script was not fully functioning as of Dec 28, 2015. Do some creative googling to find a fuller dataset.**  	| [download script](https://github.com/acquayefrank/sanders-twitter)    	| None |
| [Sentiment Strength Twitter Dataset](http://sentistrength.wlv.ac.uk/) (SS-Tweet)   	| This dataset consists of 4,242 tweets manually labelled with their positive and negative sentiment strengths. i.e., a negative strength is a number between -1 (not negative) and -5 (extremely negative). Similarly, a positive strength is a number between 1 (not positive) and 5 (extremely positive). The dataset was constructed by ([source](http://onlinelibrary.wiley.com/doi/10.1002/asi.21416/abstract)) to evaluate [SentiStrenth](http://sentistrength.wlv.ac.uk/), a lexicon-based method for sentiment strength detection.  	| [download link](http://sentistrength.wlv.ac.uk/documentation/6humanCodedDataSets.zip)   	| *Positive* if `positive sentiment strength / negative > 1.5`, and *negative* otherwise. *Neutral* if `abs(positive / strength) = 1`
| [Health Care Reform](http://help.sentiment140.com/for-students) (HCR)   	| The Health Care Reform (HCR) dataset was built by crawling tweets containing the hashtag “#hcr” (health care reform) in March 2010. A subset of this corpus was manually annotated by the authors with 5 labels (positive, negative, neutral, irrelevant, unsure(other)) and split into training (839 tweets), development (838 tweets) and test (839 tweets) sets. 	| [download link](https://bitbucket.org/speriosu/updown/src/1deb8fe45f603a61d723cc9b987ae4f36cbe6b16/data/hcr/?at=default)   	| None |
| [Obama-McCain Debate](http://dl.acm.org/citation.cfm?doid=1753326.1753504) (OMD)   	| The Obama-McCain Debate (OMD) dataset was constructed from 3,238 tweets crawled during the first U.S. presidential TV debate in September 2008. Sentiment labels were acquired for these tweets using Amazon Mechanical Turk, where each tweet was rated by at least three annotators as either positive, negative, mixed, or other. 	| [download link](https://bitbucket.org/speriosu/updown/src/1deb8fe45f60/data/shamma/orig/debate08_sentiment_tweets.tsv?at=default&fileviewer=file-view-default)   	| Labels which two-third of the voters agree on are final labels of the tweets |
| [STS-Gold](http://oro.open.ac.uk/40660/1/paper1.pdf)   	|  The STSGold dataset contains 13 negative, 27 positive and 18 neutral entities as well as 1,402 negative, 632 positive and 77 neutral tweets. ([details in Section 3](http://oro.open.ac.uk/40660/1/paper1.pdf)) 	| [download link](http://tweenator.com/index.php?page_id=13)   	| 0=negative, 4=positive |

\* *transformations applied to convert various sentiment scores to sentiment labels*


### Lexicons
*Lexicons are typically used for feature creation for sentiment classification tasks.*
*Source: [NRC-Canada: Building the State-of-the-Art in Sentiment Analysis of Tweets](http://www.aclweb.org/anthology/S13-2053)*

| Lexicon | Description | Download Link |
|--- |--- |--- |
| NRC Emotion Lexicon | Both Word-Emotion and Word-Sentiment Association Lexicon | [NRC Word-Emotion Association Lexicon](http://saifmohammad.com/WebPages/lexicons.html#EmoLex)
|MPQA Lexicon | The Subjectivity Lexicon (list of subjectivity clues) that is part of OpinionFinder is also available for separate download. These clues were compiled from several sources (see the enclosed README). | [Subjectivity Lexicon](http://mpqa.cs.pitt.edu/lexicons/subj_lexicon/)|
| Bing Liu Sentiment Lexicon | A list of positive and negative opinion words or sentiment words for English (around 6800 words). This list was compiled over many years starting from our first paper (Hu and Liu, KDD-2004). | [Opinion Lexicon](https://www.cs.uic.edu/~liub/FBS/sentiment-analysis.html#lexicon) |
| NRC Hashtag Sentiment Lexicon | These lexicons were used to generate winning submissions for the sentiment analysis shared tasks of SemEval-2013 Task 2 and SemEval-2014 Task 9. | [NRC Hashtag Sentiment Lexicon](http://saifmohammad.com/WebPages/lexicons.html#EmoLex5)
| Sentiment140 Lexicon | Lexicon generated from the Sentiment140 dataset | [Sentiment140 Lexicon](http://saifmohammad.com/WebPages/lexicons.html#EmoLex5)

Literature / Papers
======
  - [NRC-Canada: Building the State-of-the-Art in Sentiment Analysis of Tweets](http://www.aclweb.org/anthology/S13-2053)
    - Winners of the SemEval 2013/2014 Twitter Sentiment Analysis tasks describe their methodology
  - [NRC-Canada-2014: Recent Improvements in the Sentiment Analysis of Tweets](http://www.saifmohammad.com/WebDocs/SemEval2014-Task9.pdf)
    - Winners of SemEval 2013/2014 Twitter describe additional improvements to sentiment analysis due to negation contexts (handling `***n't`, `not`, `no`, `never`, etc.)
  - [Harnessing Twitter ‘Big Data’ for Automatic Emotion Identification](http://knoesis.wright.edu/library/download/wenbo_socialcom_2012.pdf)
    - Some interesting feature ideas like splitting a tweet in half and doing 2 BOWs
    - *we also hypothesize that the words located towards the end of a tweet are more important than other words, because people usually summarize or highlight their points in the end. For example, “I hate it when stuff like that happens,.. ;/ thank god it worked out.<3 #thankful.”. Although “hate” appears in the first half of the tweet, the overall emotion is dominated by “thank” in the latter half. We encoded the position information into a feature by attaching a number (i.e, 1 or 2) to each n-gram to indicate whether it is in the first half or the second half of the tweet*
  - [On Assessing the Sentiment of General Tweets](http://protocols.netlab.uky.edu/~rvkavu2/research/kavuluru-cai-15.pdf)
    - *we include a new lexico-syntactic binary feature ``<w>-POS(w)`` where ‘w’ is a sentiment expressing word found in sentiment lexicons and POS(w) is its part-of-speech as observed in an input tweet. For such words, based on the dependency parse [5] of a tweet, we also introduce another lexico-syntactic binary feature ``<w>-<g/d>-<dtype>``, where ‘dtype’ is the type of a dependency relation involving ‘w’ and ‘g/d’ is determined based on whether the relation has ‘w’ as a governor (g) or dependent*
