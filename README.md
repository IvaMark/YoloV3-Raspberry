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

### Training files

* CFG file (YOLOv3 configuration)
* DATA file (raspberry set info)
* Names file (class list)
* Labels

Images and prebuilt weights are not included into repository because of file size. Please contact author in order to acquire these files.

#### Image detection

##### Good
![Upload](readme-images/detected-good.jpg?raw=true "Upload")

##### Bad
![Upload](readme-images/detected-bad.jpg?raw=true "Upload")

### Dockerized application

Besides training set repository contains dockerized application for image detection. Aplication contains upload form where user uploads image. Output is labeled image. User can select which weights will be used for detection. Available weights are:

* yolov3
* yolov3-spp
* yolov3-tiny
* raspberry

#### Example (yolov3 weights)

![Upload](readme-images/yolo-upload.png?raw=true "Upload")
![Result](readme-images/yolo-result.png?raw=true "Result")

#### Example (raspberry weights)

![Upload](readme-images/yolo-upload2.png?raw=true "Upload")
![Result](readme-images/yolo-result2.png?raw=true "Result")
