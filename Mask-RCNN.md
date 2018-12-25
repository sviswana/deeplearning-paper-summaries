# Mask R-CNN

Kaiming He, Georgia Gkioxari, Piotr Dollár, Ross Girshick
(https://arxiv.org/pdf/1703.06870.pdf, 2017)

### TL;DR
- Mask R-CNN is a flexible framework for object instance segmentation. Extends Faster R-CNN (my summary [**here**](https://github.com/sviswana/deeplearning-paper-summaries/blob/master/Faster-RCNN.md) by adding branch for predicting object mask in **parallel** with existing branch for bbox recognition.

### Main Contributions
- Main contribution is adding a new branch to the Faster R-CNN architecture for predicting segmentation masks on each RoI in parallel with existing branch for classification/bbox regression.
- SOTA on all existing, single-model entries (top results in COCO), and runs at 5 fps.
- Mask R-CNN is effective for extracting bboxes, masks, **and** keypoints.

**My takeaway:** Mask R-CNN is a simple branch that extends Faster R-CNN and is useful for bounding box detection, instance segmentation, keypoint detection, and more.

### Relevant Architecture
<img src="https://github.com/sviswana/deeplearning-paper-summaries/blob/master/paper-imgs/mask-rcnn.png" width="50%">

-  2 stage procedure:
  1. 1st stage: - RPN (region proposal)
  2. 2nd stage: - Predict class & box offset & binary mask for RoI (all in parallel)

- Multi-task loss metric, based on L = L_cls + L_box + L_mask.
- **RoIAlign**, which is replacement for RoIPool to retain alignment. It removes quantization of RoIPool. In image (below), dashed grid represents feature map, and solid lines are RoI. RoIAlign computes value by bilinear interpolation from nearby grid points.

<img src="https://github.com/sviswana/deeplearning-paper-summaries/blob/master/paper-imgs/mask-rcnn-1.png" width="20%">

- Network architecture has a backbone + head. Backbone uses ResNet or ResNeXt (both were tested). While the head uses Faster R-CNN box head + extra branch for mask implementation.

#### Certain training details
- Image-centric training, where images are resized to 800 pixels. RPN anchors span 5 scales + 3 aspect ratios.
- Inference team involves 300 proposals.

### Results
- Instance segmentation: SOTA results for COCO datasets.
- Bounding Box: SOTA results again for COCO 2016 Detection challenge.
- Human Pose estimation: 0.9 points higher than COCO 2016 keypoint detection winner.

### Future Work
- More work can be done on further extensions on complex tasks, or potentially a more complex branch that could improve performance/accuracy even more.
