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
