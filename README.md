# YOLOv3 Raspberry set configuration

This repository contains YOLOv3 configuration based on raspberry images. Trained weights can detect following items:
- ripe raspberry
- unripe/rotten rasberry
- petiole
- unknown items other than raspberry (dirt, leafs, ...)

## Prerequisites

Configuration is for Ultralytics YOLOv3 implementation which is based on Python nad TensorFlow.

It can be installed by cloning following repository:

```
git clone https://github.com/ultralytics/yolov3.git
```

## Repository content

* CFG file (YOLOv3 configuration)
* DATA file (raspberry set info)
* Names file (class list)
* Labels

Images and prebuilt weights are not included into repository because of file size. Please contact author in order to acquire these files.