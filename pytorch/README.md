# Invopoint
**Distribution training is not supportted yet because of mmdetection3d.**

## Download data

```bash
hdfs dfs -copyToLocal hdfs://harunava/home/byte_ailab_vc/user/chendengsheng/invopoint data
```
## Train

### ModelNet40

```bash
CUDA_VISIBLE_DEVICES=0 python function/train_modelnet.py --cfg cfgs/modelnet/invopoint.yaml --log_dir log_modelnet40_invopoint_train
```

### PartNet
```bash
CUDA_VISIBLE_DEVICES=1 python function/train_partnet.py --cfg cfgs/partnet/invopoint.yaml --log_dir log_partnet_invopoint_train
```

### ShapeNetPart
```bash
CUDA_VISIBLE_DEVICES=2 python function/train_shapenetpart.py --cfg cfgs/shapenetpart/invopoint.yaml --log_dir log_shapenetpart_invopoint_train
```

### S3DIS
```bash
CUDA_VISIBLE_DEVICES=3 python function/train_s3dis.py --cfg cfgs/s3dis/invopoint.yaml --log_dir log_s3dis_invopoint_train
```

## Evaluate

### ModelNet40
```bash
python function/evaluate_modelnet.py --cfg cfgs/modelnet/invopoint.yaml --load_path <checkpoint> --log_dir log_modelnet40_invopoint_eval
 ```

### PartNet
```bash
python function/evaluate_partnet.py --cfg cfgs/partnet/invopoint.yaml --load_path <checkpoint> --log_dir log_partnet_invopoint_eval
```

### ShapeNetPart
```bash
python function/evaluate_shapenetpart.py --cfg cfgs/shapenetpart/invopoint.yaml --load_path <checkpoint> --log_dir log_shapenetpart_invopoint_eval
```

### S3DIS
```bash
python function/evaluate_s3dis.py --cfg cfgs/s3dis/invopoint.yaml --load_path <checkpoint> --log_dir log_s3dis_invopoint_train
```


## Performance

## ModelNet40

|     Method     |  Acc  |
| :------------: | :---: |
| Point-wise MLP | 93.0  |
|  Pseudo Grid   | 93.1  |
| Adapt Weights  | 92.9  |
|    PosPool     | 93.0  |
|    PosPool*    | 93.3  |
|       -        |   -   |
|   invopoint    | 80.1  |

## S3DIS

|     Method     | mIoU  |
| :------------: | :---: |
| Point-wise MLP | 66.3  |
| Adapt Weights  | 64.5  |
|    PosPool*    | 65.5  |
|       -        |   -   |
|   invopoint    |   x   |

## PartNet

|     Method     | mIoU (val) | mIoU (test) |
| :------------: | :--------: | :---------: |
| Point-wise MLP |    49.1    |    82.5     |
|  Pseudo Grid   |    50.6    |    53.3     |
| Adapt Weights  |    50.5    |    52.9     |
|    PosPool     |    50.5    |    53.6     |
|    PosPool*    |    51.1    |    53.7     |
|       -        |     -      |      -      |
|   invopoint    |    45.4    |    34.2     |

## ShapeNetPart

|     Method     | mIoU  | msIoU |  Acc  |
| :------------: | :---: | :---: | :---: |
| Point-wise MLP | 85.7  | 84.1  | 94.5  |
|  Pseudo Grid   | 86.0  | 84.3  | 94.6  |
| Adapt Weights  | 85.9  | 84.5  | 94.6  |
|    PosPool     | 85.9  | 84.6  | 94.6  |
|    PosPool*    | 86.2  | 84.8  | 94.8  |
|       -        |   -   |   -   |   -   |
|   invopoint    | 81.5  | 78.3  | 91.6  |