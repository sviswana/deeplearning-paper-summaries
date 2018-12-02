# Network in Network

Min Lin, Qiang Chen, Shuicheng Yan
(https://arxiv.org/pdf/1312.4400.pdf, 2013)

### TL;DR
- Introduces novel network-in-network model (NiN) that essentially replaces normal convolutional layers to multilayer perceptron and replaces the last fully connected layers to a global average pooling. SOTA results on CIFAR-10/100 (better than MaxoutNetwork - see my summary [here](https://github.com/sviswana/deeplearning-paper-summaries/blob/master/MaxoutNetworks.md), and reasonable performances on SVHN & MNIST.

### Main Contributions
- Proposes a novel deep neural network structure, by stacking multiple multi-layer perceptron layers, followed by global average pooling.
- Suggests a replacement to traditional convolutional layer, which is linear, to MLP, which has nonlinear activation functions, and can thus capture better abstractions.
- Global average pooling is easier to interpret and less prone to overfitting than traditional FC layers.
- SOTA results on CIFAR 10/100.

**My takeaway:** The paper was published right after Maxout networks - the authors point out that maxout networks assume convex input space, while MLPs are general function approximators. In general, this architecture seems to deliver SOTA for several datasets.

### Relevant Architecture
- Mlpconv layers (typically 3). Within each MLP layer, there is 3 layers perceptron, though these can be changes.
- All followed by global average pooling layer - where average of each feature map is fed directly into softmax layer. This enforces feature maps to be interpreted as categories confidence maps. (i.e. for 10 classes, there will be 10 averages fed to softmax layer)

<img src="https://github.com/sviswana/deeplearning-paper-summaries/blob/master/paper-imgs/networkInNetwork.png" width="60%">

#### Certain training details
- Dropout applied on outputs of all by last mlpconv layer.
- Most training procedure follows the Imagenet paper, as summarized [here](https://github.com/sviswana/deeplearning-paper-summaries/blob/master/ImageNetClassification.md)

### Results
- SOTA on CIFAR-10 - 1.0+% improvement compared to maxout networks (10.41% error). With data augmentation, this gives SOTA 8.81%.
- SOTA on CIFAR-100 - 35.68% error rate.
- SVHN - better than maxout, but not quite SOTA.
- MNIST - interestingly, maxout works better here (slightly, only by 0.02%), but likely because MNIST has already been tuned to very low error rate.

### Future Work
- Motivates possibility of performing object detection via NIN since feature maps from the last mlpconv layer are essentially confidence maps of the categories.
