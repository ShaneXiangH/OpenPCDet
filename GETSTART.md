
### [Data-Preparation](https://github.com/open-mmlab/OpenPCDet/blob/master/docs/GETTING_STARTED.md)

* To test all the saved checkpoints of a specific training setting and draw the performance curve on the Tensorboard:
```
add the --eval_all argument:
```

* Should firstly `cd tools`

### Training

[PV-RCNN](https://github.com/open-mmlab/OpenPCDet/blob/master/tools/cfgs/kitti_models/pv_rcnn.yaml):
```
python train.py --cfg_file /storage/drive_2/xinhao/OpenPCDet/tools/cfgs/kitti_models/pv_rcnn.yaml --ckpt_save_interval 5
```

[VoxelNeXt](https://github.com/open-mmlab/OpenPCDet/blob/master/tools/cfgs/waymo_models/voxelnext_ioubranch_large.yaml) on KITTI:
```
python train.py --cfg_file /storage/drive_2/xinhao/OpenPCDet/tools/cfgs/kitti_models/voxelnext_ioubranch_large.yaml --ckpt_save_interval 5
```

### Testing and Inference

[PV-RCNN](https://github.com/open-mmlab/OpenPCDet/blob/master/tools/cfgs/kitti_models/pv_rcnn.yaml):
```
python test.py --cfg_file /storage/drive_2/xinhao/OpenPCDet/tools/cfgs/kitti_models/pv_rcnn.yaml --batch_size 1 --ckpt ${CKPT}
```

### Some common issues

* When change a .yaml setting from WOD to kitti:
1. Change `CLASS_NAMES` and any related names such as `CLASS_NAMES_EACH_HEAD` to `['Car', 'Pedestrian', 'Cyclist']`
2. Change `EVAL_METRIC` to `kitti`
3. Suggested to just copy all items in `DATA_CONFIG` from a KITTI .yaml settings into this new .yaml file


* If encounter: `KeyError: 'road_plane'`
1. Set to `USE_ROAD_PLANE: False`