### Todo
**General**
  - Create package of all features so they can be easily applied outside of notebooks
  - Determine accuracy / improvement of features and publish
  - Build out PMI sentiment scores for existing datasets
    - tested on STS-Gold, Validated on Sanders
  - Proofread documentation for features
  - Add sanity checks for all features
    - Verify Shape
    - Verify Sparsity
    - Verify min/max values
  - Package `HappyFunTokenizer`
  - Figure out unsupervised features
    - RAKE
    - LDA/others


**Features**
  - Count of elongated words ('sooooo', 'eeeeeasy')
  - Count of POS Tags (both [simple](http://stackoverflow.com/questions/5787673/python-nltk-how-to-tag-sentences-with-the-simplified-set-of-part-of-speech-tags) and complex)
  - Punctuation
    - the number of contiguous sequences of exclamation marks, question marks, and both exclamation and question marks;
    - whether the last token contains an exclamation or question mark;
  - MPQA Subjectivity Lexicon Features
  - Emoticon Polarity
  - Senti-Word-Net Features
  - Negated Contexts
  - Hashtag word separation (http://norvig.com/ngrams/ch14.pdf)
  - TFIDF... zzzzzz
  - word2vec/doc2vec?
  - AFINN
  - General Inquirer
