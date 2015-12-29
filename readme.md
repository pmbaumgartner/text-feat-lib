Text Features Library
------

**Objective**: Provide a comprehensive list of tokenizers, features, and general NLTK things used for text analysis, with an initial focus on features used for twitter data.

**Packages Used**: `nltk`, `spacy`, `pandas`, `scikit-learn`

Notebooks
------
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

### Features
1. Traditional BOW
- Character n-grams
- Exclamations
- ALL CAPS
- Bible Verses
- Sentiment
- Named Entities
- POS BOW
- @mentions
- #hashtags
- #hashtags split (\#WhyImNotVotingForHillary > Why Im Not Voting For Hillary) BOW/n-gram

Datasets
------
### Sentiment Classification
*Source: [Evaluation datasets for Twitter sentiment analysis: a survey and a new dataset, the STS-Gold](http://oro.open.ac.uk/40660/1/paper1.pdf)*

| Dataset 	| Description  	| Download Link 	| Sentiment Transformation* |
|----	|---	|----	|---- |
| [Stanford Twitter Sentiment Test Set](http://help.sentiment140.com/for-students) (STS-Test)   	| The Stanford Twitter sentiment corpus (http://help.sentiment140.com/), introduced by Go et al. consists of two different sets, training and test. The training set contains 1.6 million tweets automatically labelled as positive or negative based on emotions. For example, a tweet is labelled as positive if it contains :), :-), : ), :D, or =) and is labelled as negative if it contains :(, :-(, or : (. The test set (STS-Test), on the other hand, is manually annotated and contains 177 negative, 182 positive and 139 neutrals tweets. 	| [download link](http://help.sentiment140.com/for-students)   	| (0 = negative, 2 = neutral, 4 = positive) |
|[Sanders-Twitter](http://www.sananalytics.com/lab/twitter-sentiment/)    	| This free data set is for training and testing sentiment analysis algorithms. It consists of 5,513 hand-classified tweets. Each tweet was classified with respect to one of four different topics. **Download script was not fully functioning as of Dec 28, 2015. Do some creative googling to find a fuller dataset.**  	| [download script](https://github.com/acquayefrank/sanders-twitter)    	| None |
| [Sentiment Strength Twitter Dataset](http://sentistrength.wlv.ac.uk/) (SS-Tweet)   	| This dataset consists of 4,242 tweets manually labelled with their positive and negative sentiment strengths. i.e., a negative strength is a number between -1 (not negative) and -5 (extremely negative). Similarly, a positive strength is a number between 1 (not positive) and 5 (extremely positive). The dataset was constructed by ([source](http://onlinelibrary.wiley.com/doi/10.1002/asi.21416/abstract)) to evaluate SentiStrenth (http://sentistrength.wlv.ac.uk/), a lexicon-based method for sentiment strength detection.  	| [download link](http://sentistrength.wlv.ac.uk/documentation/6humanCodedDataSets.zip)   	| *Positive* if `positive sentiment strength / negative > 1.5`, and *negative* otherwise. *Neutral* if `abs(positive / strength) = 1`
| [Health Care Reform](http://help.sentiment140.com/for-students) (HCR)   	| The Health Care Reform (HCR) dataset was built by crawling tweets containing the hashtag “#hcr” (health care reform) in March 2010. A subset of this corpus was manually annotated by the authors with 5 labels (positive, negative, neutral, irrelevant, unsure(other)) and split into training (839 tweets), development (838 tweets) and test (839 tweets) sets. 	| [download link](https://bitbucket.org/speriosu/updown/src/1deb8fe45f603a61d723cc9b987ae4f36cbe6b16/data/hcr/?at=default)   	| None |
| [Obama-McCain Debate](http://dl.acm.org/citation.cfm?doid=1753326.1753504) (OMD)   	| The Obama-McCain Debate (OMD) dataset was constructed from 3,238 tweets crawled during the first U.S. presidential TV debate in September 2008. Sentiment labels were acquired for these tweets using Amazon Mechanical Turk, where each tweet was rated by at least three annotators as either positive, negative, mixed, or other. 	| [download link](https://bitbucket.org/speriosu/updown/src/1deb8fe45f60/data/shamma/orig/debate08_sentiment_tweets.tsv?at=default&fileviewer=file-view-default)   	| Labels which two-third of the voters agree on are final labels of the tweets |
| [STS-Gold](http://oro.open.ac.uk/40660/1/paper1.pdf)   	|  The STSGold dataset contains 13 negative, 27 positive and 18 neutral entities as well as 1,402 negative, 632 positive and 77 neutral tweets. ([details in Section 3](http://oro.open.ac.uk/40660/1/paper1.pdf)) 	| [download link](http://tweenator.com/index.php?page_id=13)   	| 0=negative, 4=positive |

\* *transformations applied to convert various sentiment scores to sentiment labels*

### Literature / Papers
  - TBD
