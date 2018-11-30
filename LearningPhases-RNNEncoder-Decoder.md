# Learning Phrase Representations using RNN Encoder-Decoder for Statistical Machine Translation

Kyunghyun Cho, Bart van Merrienboer, Caglar Gulcehre, Dzmitry Bahdanau, Fethi Bougares, Holger Schwenk, Yoshua Bengio
(https://arxiv.org/pdf/1406.1078.pdf, 2014)

### TL;DR
- Proposes a novel neural network model, RNN Encoder-Decoder that contains two RNNs. The encoder & decoder trains on target sequences given source sequences (works on scoring phrases), and improves SMT approach.

### Main Contributions

- A novel RNN encoder-decoder architecture that learns mapping from source to target (either arbitrary lengths)
- Scores pair of sequences or generates target sequence.
- Proposes a novel hidden unit (with reset/update gate), that is simpler than LSTM unit.
- Proposed model learns semantic & syntactic representations of phrases & improves BLEU scores for English-French translation.

**My takeaway**: RNN Encoder-Decoder architecture is a viable approach for better scoring of candidate translations, though it appears Sequence To Sequence paper (summary HERE) is used more widely.

### Relevant Architecture
- 2 model approach, where encoder encodes variable source input to vector representation, and decoder decodes representation into sequence of symbols. Decoder takes in hidden state, previous target output, and hidden state summary of input.
[INCLUDE IMAGE] [alt text](http://url/to/img.png)
- Novel hidden unit which is a bit simpler than LSTM unit.

#### Certain training details
- 1000 hidden units, 100 dimensional word-embedding
- Batch size of 64 sentences used in training.

### Results
- Baseline + CSLM + RNN gives best results, with RNN giving better target phrases.
- Papers shares various figures/charts to illustrate syntactic + semantic structure between phrases.

### Future Work
- Let RNN Encoder-Decoder propose target phrases (rather than scoring)
- Apply model to other cases like speech transcription.
