# PFENet - IVUS

> This repository is a fork of [PFENet] with minimal changes to use their
architecture. All credit belongs to the authors of the original repository.
Please refer to their original [README](./PFENet.md) for more information.


## Usage 

This repository and the Notebooks expect 
### Prerequisites

- The [backbones] must be placed in an `initmodel/` folder (please refer to the
  original [README](./PFENet.md) ).
- A folder a folder `dataset/`  must exist, and contain the dataset
from [Standardized evaluation methodology and reference database for evaluating
IVUS image segmentation][1]. Please refer to the authors of their
original paper for the dataset.

- We provide [weights] pretrained using Dataset A from [1], designed to be used
  for one-shot predictions of the lumen of Dataset B from [1]. For other
  weigths please refer to the original [README](./PFENet.md).

### Predition 

In descriptions on how to use the model and predict IVUS imaging are
described in the notebooks [Understanding
PFENet](./Understanding%20PFENet.ipynb) and [Novel Data](./Novel%20Data.ipynb).


### Training

To train the model execute `sh test.sh ivus split0_resnet50`. Make sure to
modify `config/ivus/ivus_split0_resnet50.yaml` to use the correct parameters.
Fine-tuning is possible setting `weights` to the location of the pretrained
weights.


[weights]: https://ubarcelona-my.sharepoint.com/:u:/g/personal/icanalma7_alumnes_ub_edu/ETwsxPNy46VMqbowm8M4DvIB6jHbslfupCkIKJh9bEVDDg?e=faI4nh
[backbones]: https://mycuhk-my.sharepoint.com/:u:/g/personal/1155122171_link_cuhk_edu_hk/EQEY0JxITwVHisdVzusEqNUBNsf1CT8MsALdahUhaHrhlw?e=4%3a2o3XTL&at=9
[PFENet]: https://github.com/dvlab-research/PFENet
[1]:  http://dx.doi.org/10.1016/j.compmedimag.2013.07.001

