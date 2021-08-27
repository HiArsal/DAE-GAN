# DAE-GAN


Pytorch implementation for reproducing DAE-GAN results in the paper [DAE-GAN: Dynamic Aspect-aware GAN for Text-to-Image Synthesis] by Shulan Ruan, Yong Zhang, Kun Zhang, Yanbo Fan, Fan Tang, Qi Liu, Enhong Chen. (This work was performed when Ruan was an intern with Tencent AI Lab). 

<img src="framework.png" width="800px" height="250px"/>


### Dependencies
python 3.6

Pytorch

In addition, please add the project folder to PYTHONPATH and `pip install` the following packages:
- `python-dateutil`
- `easydict`
- `pandas`
- `torchfile`
- `nltk`
- `scikit-image`



**Data**

1. Download our preprocessed metadata for [birds](https://github.com/hiarsal/DAE-GAN) [coco](https://github.com/hiarsal/DAE-GAN) and save them to `data/`
2. Download the [birds](http://www.vision.caltech.edu/visipedia/CUB-200-2011.html) image data. Extract them to `data/birds/`
3. Download [coco](http://cocodataset.org/#download) dataset and extract the images to `data/coco/`



**Training**
- Pre-train DAMSM models:
  - For bird dataset: `python pretrain_DAMSM.py --cfg cfg/DAMSM/bird.yml --gpu 0`
  - For coco dataset: `python pretrain_DAMSM.py --cfg cfg/DAMSM/coco.yml --gpu 0`
 
- Train DAE-GAN models:
  - For bird dataset: `python main.py --cfg cfg/bird_attn2.yml --gpu 0`
  - For coco dataset: `python main.py --cfg cfg/coco_attn2.yml --gpu 0`

- `*.yml` files are example configuration files for training/evaluation our models.



**Pretrained Model**
- [DAMSM for bird](https://drive.google.com/open?id=1GNUKjVeyWYBJ8hEU-yrfYQpDOkxEyP3V). Download and save it to `DAMSMencoders/`
- [DAMSM for coco](https://drive.google.com/open?id=1zIrXCE9F6yfbEJIbNP5-YrEe2pZcPSGJ). Download and save it to `DAMSMencoders/`
- [DAE-GAN for bird](https://github.com/hiarsal/DAE-GAN). Download and save it to `models/`
- [DAE-GAN for coco](https://github.com/hiarsal/DAE-GAN). Download and save it to `models/`


**Validation**
- To generate images for all captions in the validation dataset, change B_VALIDATION to True in the eval_*.yml. and then run `python main.py --cfg cfg/eval_bird.yml --gpu 1`
- We compute inception score for models trained on birds using [StackGAN-inception-model](https://github.com/hanzhanggit/StackGAN-inception-model).
- We compute inception score for models trained on coco using [improved-gan/inception_score](https://github.com/openai/improved-gan/tree/master/inception_score).


**Examples generated by DAE-GAN**

<!--  bird example              |  coco example
:-------------------------:|:-------------------------:
![] -->
<img src="comparison.png" width="850px" height="300px"/>
