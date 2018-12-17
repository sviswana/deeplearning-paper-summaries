# Rich feature hierarchies for accurate object detection and semantic segmentation

Ross Girshick, Jeff Donahue, Trevor Darrell, Jitendra Malik
(https://arxiv.org/pdf/1311.2524.pdf, 2013)

### TL;DR
- Proposes a new object detection approach improving relative SOTA by 30%. R-CNN technique involves using CNNs for region proposals for localization, and technique for training when labeled data is scarce.

### Main Contributions
- Previous object detection performance had stagnated (typically used ensembles / SIFT / HOG features). Novel approach called R-CNN - involves regions with CNN features.
- Suggests pretraining network (with supervision) for auxiliary task (i.e. imagenet classification), and then fine-tuning network for target task (i.e. object detection)

**My takeaway:** R-CNN is significant in that it combined DNNs with traditional classical computer vision techniques for 30+% SOTA improvement.

### Relevant Architecture
- General Algorithm:
1) Uses selective search for ~2000 region proposals.
2) Computes features for each proposal using CNN (as proposed in landmark Imagenet paper - summary here).
3) Classifies region using class-specific linear SVMs.
[INCLUDE IMAGE]

#### Certain training details
- First level is supervised pre-training, where ILSVRC dataset is used with image-level annotations. (ImageNet architecture).
- Domain specific fine-tuning is done using SGD using warped region proposals from first layer. Architecture itself is similar, while learning rate is started at 0.001.

### Results
- PASCAL VOC 2010: SOTA results (53.7%), compared to previous numbers around ~35%.
- Other general notes are the FC layers don't contain as much information as the features represented in the convolutional layers themselves.
- Detection error was improved with supervised pre-training.
- Also can extend results to semantic segmentation - VOC 2011 test set shows SOTA for 11/21 categories.

### Future Work
- More future work can definitely be done in further fine-tuning of the model (particularly for segmentation), and looking for innovative ways to combine both classical CV techniques + DNN architectures.
