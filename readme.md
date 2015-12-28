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
