# Deep Residual Learning for Image Recognition

Kaiming He, Xiangyu Zhang, Shaoqing Ren
(https://arxiv.org/pdf/1512.03385.pdf, 2015)

### TL;DR
- Landmark paper delivering SOTA results (3.57% error rate on ImageNet dataset, 28% relative improvement on COCO object detection) using a novel deep residual net architecture.

### Main Contributions
- Novel architecture proposing use of residual networks to fix the problem of degradation for deep networks.
- Deep residual nets are easy to optimize (they also converge faster) & don't add additional parameters or computational cost.
- The deep residual nets benefit from the greatly increased depth, and return SOTA on ImageNet / COCO datasets.

**My takeaway:** Residual nets allow for deeper neural nets without the side-effect of degradation of training accuracy.

### Relevant Architecture
See IMAGE below...
- General idea is to compute a residual mapping (i.e. instead of solving for H(*x*), we solve for F(*x*) = H(*x*) - *x*, and then add *x* at the end.)
- The paper hinges on comparing plain (traditional) networks to the new residual networks.
  - Plain networks are inspired by VGG net - have 34 parameters layers with 3x3 filters, global average pooling, and 1000-way FC layer connected softmax.
  - Residual network where every 2 layers a shortcut is inserted. These shortcuts can be identity mappings or projections (identity works fairly well and is simpler)

- Note: the paper also explores much deeper architectures (100 - 1000 layers). These use the bottleneck architecture, where 3 layers are stacked together, rather than 2.

#### Certain training details
- Much of the training follows the landmark ImageNet paper (summarized HERE)
- Batch normalization is used extensively.
- No maxout OR dropout - in general, excessive regularization is avoided to focus on testing the network depth.
- Batch size of 128, momentum of 0.9, trained on 1.28 million images.

### Results
- ImageNet: 34-layer res-net resulted in top-5 error rate of 3.57% which won ILSVRC'15.  
- CIFAR-10: Tested with 100 and 1000 layers. 100 layers gives close to SOTA results, while 1000 layers leads to overfitting.
- COCO: 6.0% increase in metrics (equivalent to 28% relative gain) shows resnets are useful for object detection as well, and better alternative to VGG-16.

### Future Work
- Lot of potential for this network to be applied to not just images, but other areas (like speech, nlp, etc.)
- Regularization could improve results further for very deep layers (paper doesn't use dropout or maxout) - only batch norm.
