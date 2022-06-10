


---
# PFENet
This is the implementation of our paper [**PFENet: Prior Guided Feature Enrichment Network for Few-shot Segmentation**](http://arxiv.org/abs/2008.01449) that has been accepted to IEEE Transactions on Pattern Analysis and Machine Intelligence (TPAMI). 

# Get Started

### Environment
+ torch==1.4.0 (torch version >= 1.0.1.post2 should be okay to run this repo)
+ numpy==1.18.4
+ tensorboardX==1.8
+ cv2==4.2.0


### Datasets and Data Preparation

Please download the following datasets:

+ PASCAL-5i is based on the [**PASCAL VOC 2012**](http://host.robots.ox.ac.uk/pascal/VOC/voc2012/) and [**SBD**](http://home.bharathh.info/pubs/codes/SBD/download.html) where the val images should be excluded from the list of training samples.

+ [**COCO 2014**](https://cocodataset.org/#download).

This code reads data from .txt files where each line contains the paths for image and the correcponding label respectively. Image and label paths are seperated by a space. Example is as follows:

    image_path_1 label_path_1
    image_path_2 label_path_2
    image_path_3 label_path_3
    ...
    image_path_n label_path_n

Then update the train/val/test list paths in the config files.

#### [Update] We have uploaded the lists we use in our paper.
+ The train/val lists for COCO contain 82081 and 40137 images respectively. They are the default train/val splits of COCO. 
+ The train/val lists for PASCAL5i contain 5953 and 1449 images respectively. The train list should be **voc_sbd_merge_noduplicate.txt** and the val list is the original val list of pascal voc (**val.txt**).

##### To get voc_sbd_merge_noduplicate.txt:
+ We first merge the original VOC (voc_original_train.txt) and SBD ([**sbd_data.txt**](http://home.bharathh.info/pubs/codes/SBD/train_noval.txt)) training data. 
+ [**Important**] sbd_data.txt does not overlap with the PASCALVOC 2012 validation data.
+ The merged list (voc_sbd_merge.txt) is then processed by the script (duplicate_removal.py) to remove the duplicate images and labels.

### Run Demo / Test with Pretrained Models
+ Please download the pretrained models.
+ We provide **8 pre-trained models**: 4 ResNet-50 based [**models**](https://mycuhk-my.sharepoint.com/:u:/g/personal/1155122171_link_cuhk_edu_hk/EW20i_eiTINDgJDqUqikNR4Bo-7kVFkLBkxGZ2_uorOJcw?e=4%3aSIRlwD&at=9) for PASCAL-5i and 4 VGG-16 based [**models**](https://mycuhk-my.sharepoint.com/:u:/g/personal/1155122171_link_cuhk_edu_hk/EYS498D4TOZMtIb3WbQDGSQBsqxJHLSiMEAa49Iym0NO0A?e=4%3apRTPnj&at=9) for COCO.
+ Update the config file by speficifying the target **split** and **path** (`weights`) for loading the checkpoint.
+ Execute `mkdir initmodel` at the root directory.
+ Download the ImageNet pretrained [**backbones**](https://mycuhk-my.sharepoint.com/:u:/g/personal/1155122171_link_cuhk_edu_hk/EQEY0JxITwVHisdVzusEqNUBNsf1CT8MsALdahUhaHrhlw?e=4%3a2o3XTL&at=9) and put them into the `initmodel` directory.
+ Then execute the command: 

    `sh test.sh {*dataset*} {*model_config*}`

Example: Test PFENet with ResNet50 on the split 0 of PASCAL-5i: 

    sh test.sh pascal split0_resnet50


### Train

Execute this command at the root directory: 

    sh train.sh {*dataset*} {*model_config*}


# Related Repositories

This project is built upon a very early version of **SemSeg**: https://github.com/hszhao/semseg. 

Other projects in few-shot segmentation:
+ OSLSM: https://github.com/lzzcd001/OSLSM
+ CANet: https://github.com/icoz69/CaNet
+ PANet: https://github.com/kaixin96/PANet
+ FSS-1000: https://github.com/HKUSTCV/FSS-1000
+ AMP: https://github.com/MSiam/AdaptiveMaskedProxies
+ On the Texture Bias for FS Seg: https://github.com/rezazad68/fewshot-segmentation
+ SG-One: https://github.com/xiaomengyc/SG-One
+ FS Seg Propogation with Guided Networks: https://github.com/shelhamer/revolver


Many thanks to their greak work!

# Citation

If you find this project useful, please consider citing:
```
@article{tian2020pfenet,
  title={Prior Guided Feature Enrichment Network for Few-Shot Segmentation},
  author={Tian, Zhuotao and Zhao, Hengshuang and Shu, Michelle and Yang, Zhicheng and Li, Ruiyu and Jia, Jiaya},
  journal={TPAMI},
  year={2020}
}
```
