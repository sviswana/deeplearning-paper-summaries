# Neural Machine Translation by Jointly Learning to Align and Translate

Dzmitry Bahdanau, Kyunghyun Cho, Yoshua Bengio
(https://arxiv.org/pdf/1409.0473.pdf, 2014)

### TL;DR
- Proposes a soft-search approach for searing parts of source sentences relevant to predicting target word. Close to SOTA phrase-based systems with pure neural machine translation for English-French dataset.

### Main Contributions

- A novel extension to encoder-decoder model to align and translate jointly. Model predicts target word based on context vectors associated with source positions + previous target words.
- Builds on landmark Sutskever et al (Summary [here](https://github.com/sviswana/deeplearning-paper-summaries/blob/master/SequenceToSequence.md)) and Cho et al. (Summary [here](https://github.com/sviswana/deeplearning-paper-summaries/blob/master/LearningPhases-RNNEncoder-Decoder.md)) to add soft-searching to the model.
- Uses a bi-directional encoder + decoder with attention mechanism.
- Yields better results on longer sentences, and reveals the promise of NMT systems (better than traditional phrase based ones)

**My takeaway**: Soft-attention mechanism can help improve translation performance on longer sentences.

### Relevant Architecture
- Extension of RNN Encoder-Decoder with soft-alignment.
<img src="https://github.com/sviswana/deeplearning-paper-summaries/blob/master/paper-imgs/jointlyAlign-2.png" width="40%">
*Decoder*: based on previous hidden state, previous target word, and context vector. Context vector in turn is computed as weighted sum of annotations, where the weights are computed based on alignment model (single-layer MLP)

<img src="https://github.com/sviswana/deeplearning-paper-summaries/blob/master/paper-imgs/jointlyAlign-1.png" width="40%">

*Encoder*: Bi-directional RNN, where forward/backward hidden states are concatenated.
- Uses the simplified LSTM based unit described in Cho's paper ([summary](https://github.com/sviswana/deeplearning-paper-summaries/blob/master/LearningPhases-RNNEncoder-Decoder.md)).



#### Certain training details
- 1000 hidden units, multilayer network with single maxout hidden layer.
- Minibatch SGD (80 sentences) with Adadelta followed by beam search.

### Results
- New model outperforms conventional RNN Encoder-decoder model + close to BLEU scores from phrase-based systems.
- Better, meaningful translations for longer sentences (examples given in paper).

### Future Work
- Need to handle unknown, rare words better.
