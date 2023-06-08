
### [Data-Preparation](https://github.com/open-mmlab/OpenPCDet/blob/master/docs/GETTING_STARTED.md)

* To test all the saved checkpoints of a specific training setting and draw the performance curve on the Tensorboard:
```
add the --eval_all argument, instead of  ---ckpt ${CKPT}
```

* Should firstly `cd tools`

### Training (including --eval_all inference)

[PV-RCNN](https://github.com/open-mmlab/OpenPCDet/blob/master/tools/cfgs/kitti_models/pv_rcnn.yaml):
```
python train.py --cfg_file cfgs/kitti_models/pv_rcnn.yaml --ckpt_save_interval 5 --extra_tag default
```

[VoxelNeXt](https://github.com/open-mmlab/OpenPCDet/blob/master/tools/cfgs/waymo_models/voxelnext_ioubranch_large.yaml) on KITTI:
```
python train.py --cfg_file cfgs/kitti_models/voxelnext_ioubranch_large.yaml --ckpt_save_interval 5 --extra_tag default
``` 


### Testing and Inference

[PV-RCNN](https://github.com/open-mmlab/OpenPCDet/blob/master/tools/cfgs/kitti_models/pv_rcnn.yaml):
```
python test.py --cfg_file cfgs/kitti_models/pv_rcnn.yaml --batch_size 1 --ckpt ../output/kitti_models/pv_rcnn/default/ckpt/latest_model.pth --extra_tag default
```
[VoxelNeXt](https://github.com/open-mmlab/OpenPCDet/blob/master/tools/cfgs/waymo_models/voxelnext_ioubranch_large.yaml) on KITTI:
```
python test.py --cfg_file cfgs/kitti_models/voxelnext_ioubranch_large.yaml --batch_size 1 --ckpt ../output/kitti_models/voxelnext_ioubranch_large/default/ckpt/latest_model.pth --extra_tag default
``` 

### Some common issues

* When change a .yaml setting from WOD to kitti:
1. Change `CLASS_NAMES` and any related names such as `CLASS_NAMES_EACH_HEAD` to `['Car', 'Pedestrian', 'Cyclist']`
2. Change `EVAL_METRIC` to `kitti`
3. Suggested to just copy all items in `DATA_CONFIG` from a KITTI .yaml settings into this new .yaml file


* If encounter: `KeyError: 'road_plane'`
1. Set to `USE_ROAD_PLANE: False`