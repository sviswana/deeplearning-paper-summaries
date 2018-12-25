# A Neural Algorithm of Artistic Style

Leon A. Gatys, Alexander S. Ecker, Matthias Bethge
(https://arxiv.org/pdf/1508.06576.pdf, 2015)

### TL;DR
- Landmark paper for style transfer (artistic imagery), and proposes a novel way to combine both content and style of an image using CNNs.

### Main Contributions
- One of the first papers to show how NNs could be used to create artistic images of high perceptual quality
- Representation of content & style are separable in CNNs.


### Relevant Architecture
- Content is represented through layers in the network (higher layers in network capture high-level content in terms of objects)
- Style is represented by correlations between different filter responses over spatial extent of feature maps.

#### Certain training details
- VGG-network was used (with 16 conv layers + 5 pooling layers). No FC layers used.
- To visualize image information, gradient descent is performed on white noise image to find another image matching feature responses of the original image. Then squared loss is used between the two feature representations.
- For style loss, mean squared distance is minimized between Gram matrix (Gram matrix is inner product between feature map)
- **Back-prop** is used to update weights.

### Results
[IMAGE]
### Future Work
- This work offers a path forward to an algorithmic understanding of how humans create / perceive artistic imagery.
