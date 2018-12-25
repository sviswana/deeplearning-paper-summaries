# Fast R-CNN

Ross Girshick
(https://arxiv.org/pdf/1504.08083.pdf, 2015)

### TL;DR
- Proposes a Fast Region-based CNN (Fast R-CNN) for object detection. This architecture builds on the previous R-CNN work but employs techniques for faster training & better accuracy. Fast R-CNN trains VGG16 3x faster, tests 10X faster, and is more accurate.

### Main Contributions
- Main contribution is improving upon both R-CNN and SPP-net and solving several key problems: 1) Multi-stage pipeline, 2) expensive training in space & time, 3) slow detection due to features being extracted from each object proposal.
- Higher detection quality (mAP) than R-CNN, SPP-net
- Single-stage training, using multi-task loss
- Training updates ALL network layers (unlike SPP-net)
- No disk storage needed for feature caching

**My takeaway:** Fast R-CNN is vast improvement over both R-CNN and SPP-net with SOTA results on speed & accuracy.

### Relevant Architecture

[IMAGE]
- Fast R-CNN takes entire image as input, and processes the whole image to produce conv feature map. Proposals are identified from here, and warped into fixed-length via RoI pooling layer. Then two sibling output layers: softmax propoability estimate over classes + bbox regressor with 4 returned values.
- RoI pooling layer converts into feature map of size 7x7, for example.
- Starts with pre-trainined ImageNet network, replacing last max pooling layer with RoI pooling layer & softmax layer with two sibling layers described in previous section.
- Fine-tuned for detection, by training all network weights with back-prop. Possible because SGD min-batches are sampled hierarchically ( RoIs from same image share computation & memory)
- **Importantly:** Solves the SPP-net problem of not being able to update layers that precede spatial pyramid pooling.

#### Certain training details
- Multi-task loss with probability loss for class & bounding box regressor.
- Streamlined training process with one fine-tuning stage jointly optimizing softmax classifier & bbox regressor (rather than training softmax classifier, SVMs and regressors in three separate stages.)
- Paper experimented with 3 different pre-trained ImageNet models (CaffeNet, VGG, and VGG16). VGG16 performs the best.

### Results
- Fast R-CNN gives top result on VOC12 with mAP of 65.7%. Two orders of magnitude faster than all other methods.
- Fast R-CNN processes images 146x faster than R-CNN and reduces training time from 84 hours to 9.5
- Softmax slightly improves results over SVM.
- Sparse object proposals seems to be better than dense proposals.

### Future Work
- Future work can be done in investigating further into sparse proposals over dense proposals.
