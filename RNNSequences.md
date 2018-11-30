# Generating Sequences With Recurrent Neural Networks

Alex Graves
(https://arxiv.org/abs/1308.0850, 2013)

### TL;DR
- Long Short-term (LSTM) models with RNNs can use its memory to generate complex sequences with long-range structure (i.e. Wikipedia summaries, handwriting, etc.)

### Main Contributions

- This paper shows LSTM RNN's can generate both discrete and real-valued sequences with complex, long-range structure using next-step prediction.
- It tests this prediction network on various datasets (i.e. Penn Treebank + Hutter Prize), and works for word, character, and handwriting prediction.
- For handwriting, focus is on IAM database, and showcases 2 techniques:
-- Novel convolutional technique for conditioning predictions based on annotations.
-- "Priming"/biasing samples for better legibility.

My takeaway: LSTM RNN's are surprisingly good at generating complex sentences that are human-readable (i.e. Wiki articles)

### Relevant Architecture
Basic prediction network architecture discussed in paper.

#### Certain training details
- Stack multiple LSTM layers with skip connections
- Clip gradients to a range to prevent exploding gradients.

[alt text](http://url/to/img.png)


### Future Work
- Speech synthesis rather than just handwriting synthesis.
- Better understanding of internal representation (b/c much of this is treated as black box)/
