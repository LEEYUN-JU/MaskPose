# MaskPose

### Paper
Rom-Pose is pose estimation model based on simple baseline and ASBU
Use restored mask image for increasing accuracy of human pose estimation

Enviroment
---
Python 3.9.7
CUDA 11.1 relese
NVIDIA GPU A5000 used

### Download backbone code from URL
https://github.com/microsoft/human-pose-estimation.pytorch - for pose estimation model
https://github.com/ducminhkhoi/Amodal-Instance-Seg-ASBU.git - for ASBU model

Installation 
---
1. Follow the Baseline code installation.
2. Change Joints Dataset.py file
3. Change lib/core/function.py
4. Change lib/core/inference.py

Dataset
---
### Download COCO dataset from URL
https://cocodataset.org/#download

```bash
${POSE_ROOT}
|-- data
`-- |-- mpii
    `-- |-- annot
        |   |-- gt_valid.mat
        |   |-- test.json
        |   |-- train.json
        |   |-- trainval.json
        |   `-- valid.json
        `-- images
            |-- 000001163.jpg
            |-- 000003072.jpg
```

Mask image dataset using by data/makedataset.py

How to use
---
Set all the models need.
Make Whole COCO dataset which consist of answer mask dataset.
Train the ASBU model.
Train the HPE model with ASBU model's output.
Combine together to test.

/CUDA_VISIBLE_DEVICES=0,1,2,3 python pose_estimation/train.py --cfg experiments/coco/resnet152/256x192_d256x3_adam_lr1e-3.yaml
