# Maxout Networks

Ian Goodfellow, David Warde-Farley, Mehdi Mirza, Aaron Courville, Yoshua Bengio
(https://arxiv.org/pdf/1302.4389v4.pdf, 2013)

### TL;DR
- Introduces maxout model (substitute for other activation functions) to be used with dropout which facilitates optimization & better accuracy. SOTA results on MNIST, CIFAR, SVHN.

### Main Contributions
- Provides a better activation function to be used with dropout.
- Argues that this technique is better optimized with dropoutt and actually improves the accuracy of the model averaging technique used by dropout.
- SOTA results on four benchmark datasets (compared to other rectifiers)

**My takeaway:**: It's worth trying maxout model if you are training with dropout.

### Relevant Architecture
There is no particular unique architecture used for testing the maxout model besides replacing ReLU activation functions with maxout unit (max z)
- 5 convolutional layers followed by 3 fully connected layers.
  - 1st layer: ReLU + response normalization + overlapping pooling
  - 2nd layer: ReLU + response normalization + overlapping pooling
  - 3rd layer: ReLU
  - 4th layer: ReLU
  - 5th layer: ReLU + overlapping pooling

#### Certain training details
- Network has 60 million parameters + 650K neurons
- Reducing overfitting:
  - Data augmentation to reduce overfitting (extracting patches + altering intensity via PCA)
  - Dropout of 0.5 used for first *2 FC* layers.
- Batch size of 128, momentum of 0.9, trained on 1.2 million images.

### Results
- ILSVRC-2010: Top-1 and top-5 rates of 37.5% & 17.0% (previous best was 47.1% & 28.2%)
- Averaging 5 CNNs gives ~1-2% improvement but of course takes more time.

### Future Work
- Adding unsupervised pre-training would improve results (but increase training time)
- Authors note that simply waiting for more data + faster GPUs will natural improve results since bigger networks can be trained.
