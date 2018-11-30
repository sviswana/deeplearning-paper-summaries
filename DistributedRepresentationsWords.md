# Distributed Representations of Words and Phrases and their Compositionality

Tomas Mikolov, Ilya Sutskever, Kai Chen, Greg Corrado, Jeffrey Dean
(https://papers.nips.cc/paper/5021-distributed-representations-of-words-and-phrases-and-their-compositionality.pdf, 2013)

### TL;DR
- Extends the popular skip-gram model to improve quality of vectors & training speed by subsampling frequent words (for speed) & using negative sampling (for accuracy). Results are better than the original Skip-gram model in almost all cases.

### Main Contributions
- Paper shows how to train distributed representations of words and phrases with skip-gram model (they have linear structure making analogical reasoning possible)
- Subsampling of frequent words results in faster training (allowing for more magnitudes of data to be trained)
- Proposes negative sampling algorithm has better alternative to hierarchical softmax.
- Represents phrases with single tokens, and finds them effective in learning good vector representations for them.

**My takeaway:** This paper provides valuable extensions to skip-gram that improve the quality and accuracy of the vector representations.

### Relevant Model Techniques

##### Negative sampling
- Traditionally hierarchical softmax is used. This basically takes log(W) time, where W is # of words. Another alternative is NCE (noise contrastive estimation) which uses logistic regression to distinguish noise vs data.
- Negative sampling is simplification of NCE b/c it uses only samples (and not probabilities of noise distribution).

[alt text](http://url/to/img.png) [INCLUDE IMAGE}}}
##### Subsampling
- Frequent words (like "the", "a") are not useful, so they are subsampled aggressively.

##### Phrase-based models
- Simply treat phrases (identified via data-driven approach of uni/bi gram counts) as individual tokens during training.
- The have additive compositionality as well. (i.e. Volga River + Russian + river --> word vector close to vector of "Volga river")


### Results
- On Skip-gram 300 dimensional models, negative sampling greatly outperforms Hierarchical softmax, and slightly outperforms NCE.
- With subsampling, hierarchical softmax improves quite a bit, but negative sampling still performs slightly better.

### Future Work
- Word vectors can be combined by simple vector addition without losing meaning - so further research in this area is promising.
