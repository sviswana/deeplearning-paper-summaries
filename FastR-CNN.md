# Fast R-CNN

Ross Girshick
(https://arxiv.org/pdf/1504.08083.pdf, 2015)

### TL;DR
- Proposes a new pooling strategy, spatial-pyramid-pooling, as part of a new network (SPP-net) that facilitates arbitrary sized images for training, and better object detection. SOTA results on Pascal VOC 2007 dataset, 2nd place in object detection in ILSVRC 2014, and method is 24-102x faster than R-CNN with similar accuracy.

### Main Contributions
- Main contribution is the idea of a new spatial pyramid pooling layer that is placed after all conv layers, but before the FC layer.
- SPP is flexible solution that handles different scales / aspect ratios. It not only allows varying images during testing, but also during training.
- Particularly effective in speeding up R-CNN because conv layer only needs to be run once over entire image, and SPP-net is run on feature maps (rather than repeated CNNs being run on different warped regions in image)
**My takeaway:** Spatial pyramid pooling not only improves many traditional architectures by allowing varying image sizes, but is also particularly helpful in speeding up object detection.

### Relevant Architecture

[IMAGE]
- The spatial pyramid pooling layer replaces the last pooling layer (since it's the FC's that require fixed-length vectors).
- Pools features together at various scales, and generates fixed-length output, which is fed to FC layers. This avoids need for cropping/warping at the beginning.

[IMAGE]
#### Certain training details
- Paper explores both single-size and multi-size training. For multi-size training, if two different image sizes exist, two fixed-size networks are trained to accommodate each size, alternating epochs.
- However, it's important to note that multi-size solution is only for training. For testing, it's straightforward to use SPP-net on any image size.
- Data is augmented via horizontal flipping + dropout on the two FC layers.

### Results
Paper explores both classification and object detection
- SPP improves accuracy of baseline architectures (i.e. ZF-5, Overfeat, etc.)
- SOTA results on Pascal VOC '07 & Caltech101 datasets, without fine-tuning, and 2nd place on ILSVRC 2014 dataset.
- **Note**: Major limitation of SPP-net is that back-propagation cannot tune any of the layers prior to the spatial pooling layer - this makes it difficult to fine-tune. This is fixed in subsequent Fast-RCNN paper (see my summary here)

### Future Work
- More future work can definitely be done in further fine-tuning of the model, and looking for further ways to integrate SPP into other popular architectures.
