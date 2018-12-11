# A Neural Conversational Model

Oriol Vinyals, Quoc Le
(https://arxiv.org/pdf/1506.05869.pdf, 2015)

### TL;DR
- Presents a simple approach to conversational modeling by predicting next sentence given previous sentence. Applies work from previous seq2seq approaches on larger conversational training datasets. Results are optimistic, though lack of consistency is common failure.

### Main Contributions
- Shows simple language model based on seq2seq can train conversational engine.
- Can generate simple/basic conversations without any extra rules concerning questions.
- Realistic conversations / personality are still out of reach though.

**My takeaway**: Traditionally conversational modeling undergoes major feature engineering, but this paper shows seq2seq approach can be very promising.

### Relevant Architecture
- Uses seq2seq model as I summarized from Sutskever paper [**here**](https://github.com/sviswana/deeplearning-paper-summaries/blob/master/SequenceToSequence.md).

#### Certain training details
- Tested on two different datasets: IT dataset (single layer LSTM with 1024 memory cells with SGD) & open movie subtitle dataset (two-layered LSTM with AdaGrad with 4096 memory cells)

### Results
- Paper showcases results comparing answers to CleverBot (popular rule-based bot) using human evaluations for 200 questions. Overall 97/200 selected this model, while 60/200 picked CleverBot.

### Future Work
- Overall, model does still have limitations regarding realistic conversations + developing a coherent personality.
