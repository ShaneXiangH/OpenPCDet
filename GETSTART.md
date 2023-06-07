
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

[VoxelNeXt](https://github.com/open-mmlab/OpenPCDet/blob/master/tools/cfgs/kitti_models/pv_rcnn.yaml):
```
python train.py --cfg_file /storage/drive_2/xinhao/OpenPCDet/tools/cfgs/kitti_models/pv_rcnn.yaml --ckpt_save_interval 5
```

### Testing and Inference

[PV-RCNN](https://github.com/open-mmlab/OpenPCDet/blob/master/tools/cfgs/kitti_models/pv_rcnn.yaml):
```
python test.py --cfg_file /storage/drive_2/xinhao/OpenPCDet/tools/cfgs/kitti_models/pv_rcnn.yaml --batch_size 1 --ckpt ${CKPT}
```
