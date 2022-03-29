# Trash-Mask-Detector

This repository is a reference for HKPolyU AAE FYP projects. Originial Repository is TACO(see below). 
We modified some code in detector.py to make it work for our own project.

# TACO

<p align="center">
<img src="https://raw.githubusercontent.com/wiki/pedropro/TACO/images/logonav.png" width="25%"/>
</p>

TACO is a growing image dataset of waste in the wild. It contains images of litter taken under
diverse environments: woods, roads and beaches. These images are manually labeled and segmented
according to a hierarchical taxonomy to train and evaluate object detection algorithms. Currently,
images are hosted on Flickr and we have a server that is collecting more images and
annotations @ [tacodataset.org](http://tacodataset.org)


<div align="center">
  <div class="column">
    <img src="https://raw.githubusercontent.com/wiki/pedropro/TACO/images/1.png" width="17%" hspace="3">
    <img src="https://raw.githubusercontent.com/wiki/pedropro/TACO/images/2.png" width="17%" hspace="3">
    <img src="https://raw.githubusercontent.com/wiki/pedropro/TACO/images/3.png" width="17%" hspace="3">
    <img src="https://raw.githubusercontent.com/wiki/pedropro/TACO/images/4.png" width="17%" hspace="3">
    <img src="https://raw.githubusercontent.com/wiki/pedropro/TACO/images/5.png" width="17%" hspace="3">
  </div>
</div>
</br>

For convenience, annotations are provided in COCO format. Check the metadata here:
http://cocodataset.org/#format-data

TACO is still relatively small, but it is growing. Stay tuned!

# Publications

For more details check our paper: https://arxiv.org/abs/2003.06975

If you use this dataset and API in a publication, please cite us using: &nbsp;
```
@article{taco2020,
    title={TACO: Trash Annotations in Context for Litter Detection},
    author={Pedro F Proença and Pedro Simões},
    journal={arXiv preprint arXiv:2003.06975},
    year={2020}
}
```

# Getting started

### Requirements 

To install the required python packages simply type
```
pip3 install -r requirements.txt
```
Install tensorflow gpu 1.15.0 version, if you have a nvidia GPU prepared, CUDA 11.0, CUDNN 8.0.5 installed:
```
pip3 install tensorflow-gpu==1.15 &&
pip install 'keras==2.16' --force-reinstall
```
### Download

To download the dataset images simply issue
```
python3 download.py
```

### Prepare models

Download the [models](https://drive.google.com/drive/folders/1042Qzq988frb61LwItuM4JjuYi-9KIcS?usp=sharing), create ``detector/models/`` directory, and put them under ``detector/models/`` directory, such as ``Trash-Detect-Mask/detector/models/mask_rcnn_coco.h5``

```
cd detector
mkdir models
```


### Trash Detection

The implementation of [Mask R-CNN by Matterport](https://github.com/matterport/Mask_RCNN)  is included in ``/detector``
with a few modifications. 
For example, run this inside the directory `detector` to test detecting trash:
```
./test.sh
```
Training detector on COCO dataset:
```
./train.sh
```
For further usage instructions, check ``detector/detector.py``.

As you can see [here](http://tacodataset.org/stats), most of the original classes of TACO have very few annotations, therefore these must be either left out or merged together. Depending on the problem, ``detector/taco_config`` contains several class maps to target classes, which maintain the most dominant classes, e.g., Can, Bottles and Plastic bags. Feel free to make your own classes.

<p align="center">
<img src="https://raw.githubusercontent.com/wiki/pedropro/TACO/images/teaser.gif" width="75%"/></p>

### Maintainer:
[Yurong Feng](https://www.polyu.edu.hk/researchgrp/cywen/index.php/en/people/current-members.html)(Dept.AAE,PolyU): yu-rong.feng@connect.polyu.hk <br />
