# Invopoint

## Download data

```bash
hdfs dfs -copyToLocal hdfs://harunava/home/byte_ailab_vc/user/chendengsheng/invopoint data
```

## ModelNet40

```bash
CUDA_VISIBLE_DEVICES=0 python -m torch.distributed.launch --master_port 3994 --nproc_per_node 1 \
    function/train_modelnet_dist.py --cfg cfgs/modelnet/invopoint.yaml --log_dir log_modelnet40_invopoint
```

#### PartNet
```bash
CUDA_VISIBLE_DEVICES=1 python -m torch.distributed.launch --master_port 3995 --nproc_per_node 1 \
    function/train_partnet_dist.py --cfg cfgs/partnet/invopoint.yaml --log_dir log_partnet_invopoint
```

#### ShapeNetPart
```bash
CUDA_VISIBLE_DEVICES=2 python -m torch.distributed.launch --master_port 3996 --nproc_per_node 1 \
    function/train_shapenetpart_dist.py --cfg cfgs/shapenetpart/invopoint.yaml --log_dir log_shapenetpart_invopoint
```

#### S3DIS
```bash
CUDA_VISIBLE_DEVICES=3 python -m torch.distributed.launch --master_port 3997 --nproc_per_node 1 \
    function/train_s3dis_dist.py --cfg cfgs/s3dis/invopoint.yaml --log_dir log_s3dis_invopoint
```

### Evaluating
For evaluation, we recommend using 1 gpu for more precise result.
#### ModelNet40
```bash
python -m torch.distributed.launch --master_port <port_num> --nproc_per_node 1 \
    function/evaluate_modelnet_dist.py --cfg <config file> --load_path <checkpoint> [--log_dir <log directory>]
 ```
- `<port_num>` is the port number used for distributed evaluation, you can choose like 12347.
- `<config file>` is the yaml file that determines most experiment settings. Most config file are in the `cfgs` directory.
- `<checkpoint>` is the model checkpoint used for evaluating.
- `<log directory>` is the directory that the log file, checkpoints will be saved, default is `log_eval`.

#### PartNet
```bash
python -m torch.distributed.launch --master_port <port_num> --nproc_per_node 1 \
    function/evaluate_partnet_dist.py --cfg <config file> --load_path <checkpoint> [--log_dir <log directory>]
```

#### ShapeNetPart
```bash
python -m torch.distributed.launch --master_port <port_num> --nproc_per_node 1 \
    function/evaluate_shapenetpart_dist.py --cfg <config file> --load_path <checkpoint> [--log_dir <log directory>]
```

#### S3DIS
```bash
python -m torch.distributed.launch --master_port <port_num> --nproc_per_node 1 \
    function/evaluate_s3dis_dist.py --cfg <config file> --load_path <checkpoint> [--log_dir <log directory>]
```
