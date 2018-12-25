# You Only Look Once: Unified, Real-Time Object Detection

Joseph Redmon, Santosh Divvala, Ross Girshick, Ali Farhadi
(https://arxiv.org/pdf/1506.02640.pdf, 2015)

### TL;DR
- YOLO (You Only Look Once) is a landmark paper for unified, **real-time** object detection that uses a single neural network for predicting bounding boxes + class probabilities from a full image in one evaluation.

### Main Contributions
- Main contribution is proving an architecture for real-time object detection in real-time at 45 fps. Smaller version of network (Fast YOLO) processes 155 fps!
- One network for entire detection pipeline (no RPNS, or using selective search for region proposals).
- YOLO is slightly less than SOTA in accuracy, but is less likely to predict false positives on background, and is better at general object representation b/c it uses full image.

**My takeaway:** YOLO is a refreshingly simple architecture that trains on full images without using classifier-based approaches, and pushes SOTA in real-time object detection.

### Relevant Architecture

<img src="https://github.com/sviswana/deeplearning-paper-summaries/blob/master/paper-imgs/yolo.ong.png" width="60%">

- Unified single neural network, using features from entire image to predict bounding box.
- General process is:
  1. Divide input image into S x S grid (typically S = 7)
  2. Each grid cell predicts B bounding boxes (B = 2), and confidence score. In addition, grid cell predicts C class probabilities ( C = 20 for VOC dataset)
  3. Class probabilities multiplied with box confidence prediction to give class-specific confidence score.

- Network is inspired by GoogLeNet architecture, with 24 conv layers + 2 FC layers. The fast YOLO version uses 9 layers, but all train/test params are same.

#### Certain training details
- 20 Conv layers pretrained on ImageNet dataset for ~ 1 week. Then add 4 conv layers + 2 FC layers with random weights.
- Leaky RELU used for all layers (except for final layer, which uses linear activation function)
- Optimizes for sum-squared error, b/c easy to optimize.
- Trained for 135 epochs on VOC 2007 dataset, with batch size of 64.

### Results
- Falls behind SOTA compared to Fast-RCNN but much faster.
- Combining Fast R-CNN + YOLO (since YOLO makes fewer background mistakes) is better than Fast R-CNN alone.
- Known limitations are more localization errors and poor detection on small objects.

### Future Work
- More work could be done towards improving localization errors + optimizing for a better metric rather than sum-squared error.
