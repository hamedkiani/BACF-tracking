
# <p align="center"> Learning Background-Aware Correlation Filters for Visual Tracking

### <p align="center"> Hamed Kiani, Ashton Fagg, and  Simon Lucey

### <p align="center"> ICCV 2017

## Abstract

Correlation Filters (CFs) have recently demonstrated excellent performance in terms of rapidly tracking objects under challenging photometric and geometric variations. The strength of the approach comes from its ability to efficiently learn - on the fly - how the object is changing over time. A fundamental drawback to CFs, however, is that the background of the target is not modeled over time which can result in suboptimal performance. Recent tracking algorithms have suggested to resolve this drawback by either learning CFs from more discriminative deep features (e.g. DeepSRDCF  and CCOT ) or learning complex deep trackers (e.g. MDNet and FCNT). While such methods have been shown to work well, they suffer from high complexity: extracting deep features or applying deep tracking frameworks is very computationally expensive. This limits the real-time performance of such methods, even on high-end GPUs. This work proposes a Background-Aware CF based on hand-crafted features (HOG) that can efficiently model how both the foreground and background of the object varies over time. Our approach, like conventional CFs, is extremely computationally efficient- and extensive experiments over multiple tracking benchmarks demonstrate the superior accuracy and real-time performance of our method compared to the state-of-the-art trackers.

## Core idea: learning from background patches

BACF learns from all possible positive and negative patches extracted from the entire frame. The shifting operator generates all circular shifts of the frame over all j = [0, ..., T-1] steps. T is the length of vectorized frame. P is the cropping operator (a binary matrix) which crops the central patch of each shifted image. The size of the cropped patches is same as the size of the target/filter (D), where T >> D. All cropped patches are utilized to train a CF tracker. In practice, we do not apply circular shift and cropping operators. Instead, we perform these operations efficiently by augmenting our objective in the Fourier domain. The red and green boxes indicate the negative (background) and positive (target) training patches.

<center> ![](http://www.hamedkiani.com/uploads/5/1/8/8/51882963/edited/bacf-2.png?1505151342)
</center>

## Evaluation result

#### (I) Success plots comparing BACF with the state-of-the-art HOG based trackers on (a) OTB50, (b) OTB100, and (c) TC128. The result of top 12 trackers is illustrated here. AUCs are reported in brackets.

![](http://www.hamedkiani.com/uploads/5/1/8/8/51882963/screen-shot-2017-09-11-at-1-40-00-pm_orig.png)

<br><br>

###  (II) Attribute based evaluation. Success plots compare BACF with state-of-the-art HOG based trackers on OTB100. BACF outperformed all the trackers over all attributes. AUCs are reported in brackets. The number of videos for each attribute is shown in parenthesis.

![](http://www.hamedkiani.com/uploads/5/1/8/8/51882963/screen-shot-2017-09-11-at-1-50-35-pm_orig.png)

<br><br>

### (III) Success rates (% at IoU > 0.50) of BACF compared to CF trackers with deep features

![](http://www.hamedkiani.com/uploads/5/1/8/8/51882963/screen-shot-2017-09-11-at-1-45-41-pm_orig.png)

<br><br>

### (IV) Tracking demo on OTB-100 dataset

<p align="center">
[![](http://img.youtube.com/vi/aertxlzMEPo/0.jpg)](http://www.youtube.com/watch?v=aertxlzMEPo "")
</p align="center">

<br><br>

### (V) Tracking result (MAT files) for OTB-50 and OTB-100​

### http://www.hamedkiani.com/bacf.html

<br>

## Running instructions

coming soon!

## Reference

```
@inproceedings{kiani2017learning,
  title={Learning background-aware correlation filters for visual tracking},
  author={Kiani Galoogahi, Hamed and Fagg, Ashton and Lucey, Simon},
  booktitle={Proceedings of the IEEE Conference on Computer Vision and Pattern Recognition},
  pages={1135--1143},
  year={2017}
}
```
