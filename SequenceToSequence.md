# Sequence to Sequence Learning with Neural Networks

Ilya Sutskever, Oriol Vinyals, Quoc V. Le
(https://papers.nips.cc/paper/5346-sequence-to-sequence-learning-with-neural-networks.pdf, 2014)

### TL;DR
- Landmark paper that uses multilayered LSTM to map input sequence to vector of fixed dimensionality, and another LSTM to decode target sequence from vector. BLEU score of 34.8, and up to 36.5 (close to SOTA) (first time pure neural translation system outperforms SMT based system for machine translation)

### Main Contributions
- Shows that DNNs (in particular, LSTMs) are effective for machine translation and for long sentences.
- Reversing order of source sentence (not target) improves LSTM dramatically.
- A large deep LSTM with limited vocabulary > standard SMT with unlimited vocabulary.
- Simple, straight forward approach can outperform SMT.

**My takeaway**: LSTMs can effectively be used for machine translation, and are particularly effective when source sentences are reversed.

### Relevant Architecture
LSTM is used to map input sequence to fixed size vector. Then another LSTM is used to map the vector to output sequence.

<img src="https://github.com/sviswana/deeplearning-paper-summaries/blob/master/paper-imgs/sequence2sequence.png" width="50%">

#### Certain training details
- Deep LSTMs perform better than shallow LSTMs (4 layers)
- Maximize log probability of correct translation T given source sentence S.
- Search for most likely translation with left-to-right beam search decoder.
- No momentum used + hard constraint on gradient norm (to prevent exploding gradient)

### Results
- Tested on WMT'14 English to French machine translation task.
- BLEU score of 34.8, while rescoring baseline gives close to SOTA (36.5)
- Best results on ensemble of 5 LSTMs

### Future Work
- Even unoptimized LSTM approach can outperform mature SMT, so focus can be on optimizing this network (i.e. different layers, fine-tuning params)
