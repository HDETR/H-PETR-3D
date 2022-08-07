# H-PETR-3D

##  Main Results

| Model    | Epoch     | mAP    | NDS    |config  | download |
|:--------:|:---------:|:---------:|:--------:|:--------:|:-------------:|
| PETRv2   | 24epoch   | 41.00% | 50.30% |[config](projects/configs/petrv2/petrv2_vovnet_gridmask_p4_800x320.py)                                  |[model](https://drive.google.com/file/d/1tv_D8Ahp9tz5n4pFp4a64k-IrUZPu5Im/view?usp=sharing)
| H-PETRv2 | 24epoch   | 41.93% | 51.23% |[config](projects/configs/petrv2/hybrid_petrv2_vovnet_gridmask_p4_800x320_lambda1_group4_t1800.py)      |[model](https://github.com/HDETR/H-PETR-3D/releases/download/v1.0.0/hybrid_petrv2_vovnet_gridmask_p4_800x320_lambda1_group4_t1800.pth)
| PETRv2   | 36epoch   | 41.07% | 50.68% |[config](projects/configs/petrv2/petrv2_vvovnet_gridmask_p4_800x320_ep36.py)                             |[model](https://github.com/HDETR/H-PETR-3D/releases/download/v1.0.0/petrv2_vovnet_gridmask_p4_800x320_ep36.pth)
| H-PETRv2 | 36epoch   | 42.59% | 52.38% |[config](projects/configs/petrv2/hybrid_petrv2_vovnet_gridmask_p4_800x320_lambda1_group4_t1800_ep36.py) |[model](https://github.com/HDETR/H-PETR-3D/releases/download/v1.0.0/hybrid_petrv2_vovnet_gridmask_p4_800x320_lambda1_group4_t1800_ep36.pth)

## Preparation
Please refer to [PETR](https://github.com/megvii-research/PETR) for environment and dataset preparation.

## Train
```bash
tools/dist_train.sh projects/configs/petrv2/hybrid_petrv2_vovnet_gridmask_p4_800x320_lambda1_group4_t1800.py 8 --work-dir work_dirs/hybrid_petrv2_vovnet_gridmask_p4_800x320_lambda1_group4_t1800/
```

## Evaluation
```bash
tools/dist_test.sh projects/configs/petrv2/hybrid_petrv2_vovnet_gridmask_p4_800x320_lambda1_group4_t1800.py work_dirs/hybrid_petrv2_vovnet_gridmask_p4_800x320_lambda1_group4_t1800/latest.pth 8 --eval bbox
```

## Modified files compared to vanilla PETRv2
### To support Hybrid-brach
* projects/mmdet3d_plugin/models/dense_heads/hybrid_petrv2_head.py
* projects/mmdet3d_plugin/models/dense_heads/__init__.py
* projects/mmdet3d_plugin/models/utils/petr_transformer.py
* projects/configs/petrv2/hybrid_petrv2_vovnet_gridmask_p4_800x320_lambda1_group4_t1800.py
* projects/configs/petrv2/hybrid_petrv2_vovnet_gridmask_p4_800x320_lambda1_group4_t1800_ep36.py

## Citation
```bibtex
@article{jia2022detrs,
  title={DETRs with Hybrid Matching},
  author={Jia, Ding and Yuan, Yuhui and He, Haodi and Wu, Xiaopei and Yu, Haojun and Lin, Weihong and Sun, Lei and Zhang, Chao and Hu, Han},
  journal={arXiv preprint arXiv:2207.13080},
  year={2022}
}
```