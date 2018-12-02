# Effective Approaches to Attention-based Neural Machine Translation

Minh-Thang Luong, Hieu Pham, Christopher Manning
(https://arxiv.org/pdf/1508.04025.pdf, 2015)

### TL;DR
- Examines two different approaches for attention-based NMT (global & local) and analyzes their effectiveness. Ensemble model produces SOTA BLEU score of 25.9 (1.0+ improvement) for English to German translation.

### Main Contributions
- 2 novel types of attention models (that are also simple):
  1. global - all source words attended
  2. local - only subset of source words considered
- Both approaches are effects in WMT English <--> German task.
- Effective in long sentences, alignment quality, and output.
- General idea is to go from hidden state --> alignment vector --> context vector --> attentional hidden state.

**My takeaway:** Attention based NMT is definitely superior to non-attention approach, and both global & local architectures produce SOTA results for NMT.

### Relevant Architecture
- Uses stacking LSTM architecture, similar to Sutskever 2014 (my summary found [here](https://github.com/sviswana/deeplearning-paper-summaries/blob/master/SequenceToSequence.md))
- **General approach:** at each step *t* of decoding phase, take hidden state of top layer of stacking LSTM (h<sub>t</sub>)--> context vector (c<sub>t</sub>) --> predict target word (y<sub>t</sub>).
  - Global Attention: Compute *variable-length* alignment vector comparing target hidden state with each source hidden state.  Computes a content-based score function (i.e. dot, general, concat).  This is used to define context vector as weighted average.
  - Local Attention: Small subset of source positions for each target word. *fixed-length* alignment & context vector is weighted average of hidden states. Window is typically 10.

Global Attention:  
<img src="https://github.com/sviswana/deeplearning-paper-summaries/blob/master/paper-imgs/attention-1.png" width="40%">

Local Attention:
<img src="https://github.com/sviswana/deeplearning-paper-summaries/blob/master/paper-imgs/attention-2.png" width="40%">

#### Certain training details
- Various score functions experimented with for alignment vector. Paper finds general/dot product works better than generic location-based function.
- Most parameters are similar to Sutskever 2014.
- Input-feeding approach where attentional vectors are concatenated with inputs at the next time step.


### Results
- Tested on WMT translation for English <--> German. Global + local attention + dropout + reverse source sentence results in +5.0 BLEU points.
- local attention model with predictive alignments is most effective & gives lower alignment error rate.
- German to English is close to SOTA.

### Future Work
- Not explicitly mentioned in paper, but can explore different score functions and their efficacy (i.e. differentiating between dot, content-based, concat).
