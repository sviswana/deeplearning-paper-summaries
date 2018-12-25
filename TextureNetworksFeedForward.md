# Texture Networks: Feed-forward Synthesis of Textures and Stylized Images

Dmitry Ulyanov, Vadim Lebedev, Andrea Vedaldi, Victor Lempitsky
(https://arxiv.org/pdf/1603.03417.pdf, 2016)

### TL;DR
- Proposes an alternative approach to style transfer (found from Gatys et al.) that is much faster by using compact feed-forward CNNs.

### Main Contributions
- Proposes texture networks (fully-convolutional networks) that can generate textures & process images of arbitrary size.
- Single forward-pass + multi-scale generative architecture makes generation 100x faster.

**My takeaway:** A novel feed-forward only approach for generating complex textures + style transfer capabilities.


### Relevant Architecture
- Feed-forward *generator* network that takes noise sample as input, and produces texture sample.
- There are two networks: descriptor & generator network. Descriptor network is pre-trained for image classification. Only generator network is updated, which makes training easier.
- Loss function is based off Gatys et al. (see my summary [**here**](https://github.com/sviswana/deeplearning-paper-summaries/blob/master/TextureNetworksFeedForward.md))- texture loss alone is used when training generator network, and weighted combination of texture & content loss is used for generator network for stylization.

#### Certain training details
- Learning via SGD.
- Samples noise vectors & adjusts parameters of generator to minimize content + texture loss.

### Results
Most comparisons must be done in a qualitative manner. But evaluation of this technique only takes ~20 ms (while Gatys et al. takes ~10 sec).

<img src="https://github.com/sviswana/deeplearning-paper-summaries/blob/master/paper-imgs/textureNetwork.png" width="70%">

### Future Work
- Results sometimes don't match quality of Gatys et al. - better stylization losses could give better quality results.
