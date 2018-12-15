# Deep Neural Networks for Object Detection

Christian Szegedy, Alexander Toshev, Dumitru Erhan
(https://papers.nips.cc/paper/5207-deep-neural-networks-for-object-detection.pdf, 2013)

### TL;DR
- Proposes DNN for treating object detection as a regression problem (for bounding box masks). Involves a multi-scale inference procedure with SOTA results on Pascal VOC dataset.

### Main Contributions
- Novel DNN architecture with object mask regression + multi-scale course-to-fine procedure.
- Drawbacks include some extra computation training time (need to train network per object type per mask type)
- Focuses on localization of object itself (rather than classification like most DNNs do)

**My takeaway:** DNNs can be extended for object detection / localization efforts when treated as regression problem + fine-tuning results.

### Relevant Architecture
- At a high level, idea is to apply DNN-based regression towards an object mask. Then generate masks for full object as well as portions of object. Then further localize on a small set of large sub-windows.

*General Algorithm*:
  1) For various scales/windows of image, compute object box masks using DNN network (based off classic ImageNet paper (my summary [**here**](https://github.com/sviswana/deeplearning-paper-summaries/blob/master/ImageNetClassification.md)).
  2) For final set of detections, search through bounding boxes and keeps ones with strong score.
  3) Further refinement via 2nd stage of DNN regression where localizer applied on windows defined in initial stage.

#### Certain training details
- Classifier is replaced with mask generation layer, but does need a huge amount of training data (objects of different sizes + different locations)
- Mask generator - several thousand examples generated from each image (several thousand images themselves)
- Networks trained with SGD with Adagrad

### Results
- Pascal Visual Object Challenge (5K images + 20 classes)- paper compares DetectorNet to other approaches, which shows SOTA performance on most models (outperformed on 8 classes)  
- Excels at deformable objects (like bird, cat), but fails on similarly looking objects

### Future Work
Future work can look at reducing cost of training by having single network detecting objects of different classes (so can accommodate large array of classes)
