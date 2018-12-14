# Very Deep Convolutional Networks for Large-Scale Image Recognition

Karen Simonyan, Andrew Zisserman
(https://arxiv.org/pdf/1409.1556.pdf, 2014)

### TL;DR
- Presents a novel VGG network that uses a very deep architecture with 3x3 convolutional filters. Resulted in 1st / 2nd place results in ImageNet 2014 Challenge. Results apply to other datasets as well.

### Main Contributions
- Demonstrates a more accurate ConvNet architecture that is deeper (16-19 layers) with much smaller conv layers.
- Extra depth appears to be more beneficial, and generalize well to a wide range of tasks / datasets.
- Smaller conv layers actually results in fewer parameters, which imposes a sort of regularization.

**My takeaway**: Novel VGG network with SOTA ImageNet 2014 results, showing deeper + smaller conv filters may be better than Google LeNet.

### Relevant Architecture
- Paper tested several different configurations, ranging from 11 weight layers (8 conv. & 3 FC layers), to 19 weight layers.
- Stride = 1 pixel, max-pooling done over 2x2 pixel window with stride = 2.
- All hidden layers use ReLU activation function.
- Width of conv layers starts from 64 in first layer and doubles, until reaching 512.

<img src="https://github.com/sviswana/deeplearning-paper-summaries/blob/master/paper-imgs/vgg-1.png" width="50%">

#### Certain training details
- Training mostly follows the landmark ImageNet paper (my [**summary**](https://github.com/sviswana/deeplearning-paper-summaries/blob/master/ImageNetClassification.md)), except for special sampling of input crops.
- Mini-batch gradient descent, with batch size of 256, and momentum to 0.9.
- Initialization of weights is very important - can make a difference in stability.
- Training image size: tried two approaches, fixing size, and multi-scale, where training image size is randomly sampled from certain range.

### Results
- Paper showcases SOTA results for single-net, particularly with training set "scale jittering" is performed. VGG got 2nd place in ILSVRC-2014 challenge (but note that ensembles were used by many other submissions). For single net, this architecture outperforms GoogLeNet.

### Future Work
- Confirms the importance of depth in visual representation - paves the way for perhaps more architectures with smaller conv filters.
