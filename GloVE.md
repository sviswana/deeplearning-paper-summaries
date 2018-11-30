# GloVe: Global Vectors for Word Representation

Jeffrey Pennington, Richard Socher, Christopher Manning
(https://nlp.stanford.edu/pubs/glove.pdf, 2014)

### TL;DR
- A new global log-bilinear regression model that obtains vector representation of words. It combines benefits of word2vec model AND exploits global corpus information using co-occurence matrix (75% on word analogy task).

### Main Contributions

- Current Techniques & their problems:
 - LSA (latent semantic analysis) - problem is bad on analogies (poor vector space structure)
 - word2vec, skig-gram model - problem is it doesn't use global statistics.
- Solution is a weighted least squares model that trains on global word-word co-occurrence counts.
- The unsupervised learning algorithm produces results better than word2vec in most cases - but is also much faster, which is very important.

My takeaway: The key insight appears to be that relationship of words can be examined by calculating the ratio of their co-occurrence probabilities, while at the same time working on analogies.

### Relevant Architecture

The training objective of GloVe is to learn word vectors such that their dot product equals the logarithm of the words' probability of co-occurrence.

General idea: Ratios of words illustrate relationship. If P(k|w) is probability that word k appears in the context of word w, ratio of P(solid | ice) / P(solid | steam) will be large, indicating solid is related to ice more than steam. Note that the formula operates on difference between word vectors (rather than individual words)

[alt text](http://url/to/img.png)

#### Certain training details
- Use a weighting function to ensure rare co-occurrences are not weighted as often.
- Complexity of the model is O(C^0.8) - where C is size of corpus. This is much better than O(C) which is typical of window based approaches.

### Results
GloVe does very well on the word analogy task (SOTA - 75%). Also succeeds on word similarity and entity recognition tasks. For same corpus, vocabulary size, and training time, GloVe outperforms word2vec.

### Future Work
Not explicitly mentioned in paper, but researchers have different preferences between predictive model used by word2vec  vs/ the count-based model supported by this paper.
