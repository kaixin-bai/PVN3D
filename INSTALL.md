# PVN3D安装记录

## conan激活cuda和cudnn
eval $(arpm_env cuda/10.0.130@ar/stable cudnn/7.6.0@ar/stable)

## 创建conda虚拟环境
conda create -n pvn3d python=3.6

## 安装特定版本的pytorch
conda install pytorch==1.0.1 torchvision==0.2.2 cudatoolkit=10.0 -c pytorch

## build pn++
cd /data/hdd1/kb/agile/pvn3d_test/PVN3D

python3 setup.py build_ext

## 下载linemod数据集的checkpoints
https://hkustconnect-my.sharepoint.com/personal/yhebk_connect_ust_hk/_layouts/15/onedrive.aspx?id=%2Fpersonal%2Fyhebk_connect_ust_hk%2FDocuments%2Fpublically shared 共享文件夹%2FPVN3D_pretrained_model%2FLineMOD&originalPath=aHR0cHM6Ly9oa3VzdGNvbm5lY3QtbXkuc2hhcmVwb2ludC5jb20vOmY6L2cvcGVyc29uYWwveWhlYmtfY29ubmVjdF91c3RfaGsvRWhheTVwUHRsLUJHbnZBRWNsWEJSdThCRXBaZUh1Rzl4LWFOX2RqQXR0NXJQQT9ydGltZT1kX21Rc2EwSDJFZw

# 测试
open3d的10版本如果先import torch再import open3d会有问题：

double free or corruption (out)

Aborted (core dumped)

如果是9版本问题是：

free(): invalid pointer

Aborted (core dumped)

解决方法：先import open3d
