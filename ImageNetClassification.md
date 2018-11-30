# ImageNet Classification with Deep Convolutional Neural Networks

Alex Krizhevsky, Ilya Sutskever, Geoffrey Hinton
(http://papers.nips.cc/paper/4824-imagenet-classification-with-deep-convolutional-neural-networks.pdf, 2012)

### TL;DR
- Landmark paper delivering SOTA results (top-1 error rate 37.5%, top-5 error rate 17.0%) for ImageNet dataset using deep convolutional NN's, compared to previous approaches using classifiers and SIFT features.

### Main Contributions
- Novel deep architecture (at the time) using deep CNN: 5 convolutional layers + 3 FC layers.
- Introduced 4 key approaches worth highlighting:
  1. ReLU prevents overfitting by faster learning.
  2. Trained on multiple GPUs, but communicate only in certain layers.
  3. Normalizing ReLUs (improves error rate by ~1.4%)
  4. Overlapping pooling

**My takeaway:**: Deeper is better - Laid the groundwork for deeper NN architectures for better results + prevalence of ReLU for faster training purposes.

### Relevant Architecture
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
