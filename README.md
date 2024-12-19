# fxxking_mmlab

## MMdeploy

### Reqiurements:
```bash
mim list
```

```
>>> Package    Version    Source
>>> ---------  ---------  -----------------------------------------
>>> mmcv       2.0.1      https://github.com/open-mmlab/mmcv
>>> mmdet      3.2.0      https://github.com/open-mmlab/mmdetection
>>> mmengine   0.8.4      https://github.com/open-mmlab/mmengine
>>> mmpose     1.1.0      /home/hhd1/project/mmlab/mmpose
>>> mmyolo     0.6.0      https://github.com/open-mmlab/mmyolo
```

```bash
pip list
```

```
mmcv                   2.0.1
mmdet                  3.2.0
mmengine               0.8.4
mmpose                 1.1.0        / path to /mmlab/mmpose
mmyolo                 0.6.0
onnx                   1.12.0
onnxruntime            1.8.1
opencv-python          4.8.0.76
opencv-python-headless 4.9.0.80
opendatalab            0.0.10
openmim                0.3.9
openxlab               0.0.24
pandas                 2.0.3
Pillow                 9.3.0
pycocotools            2.0.7
numpy                  1.24.4
```

### Install:
```bash
conda create -n mmdeploy python=3.8 -y
conda activate mmdeploy

# torch and torchvision 三个版本三选一就行, according to https://pytorch.org/get-started/previous-versions/
pip install torch==1.13.1+cu116 torchvision==0.14.1+cu116 torchaudio==0.13.1 --extra-index-url https://download.pytorch.org/whl/cu116 # CUDA 11.6
pip install torch==1.13.1+cu117 torchvision==0.14.1+cu117 torchaudio==0.13.1 --extra-index-url https://download.pytorch.org/whl/cu117 # CUDA 11.7
pip install torch==1.13.1+cpu torchvision==0.14.1+cpu torchaudio==0.13.1 --extra-index-url https://download.pytorch.org/whl/cpu # CPU only
pip install -U openmim==0.3.9 # 如果在国内可以尝试镜像加速: pip install -U openmim==0.3.9 -i https://mirrors.aliyun.com/pypi/simple
mim install mmengine==0.8.4 # 如果在国内可以尝试镜像加速: mim install mmengine==0.8.4 -i https://mirrors.aliyun.com/pypi/simple
mim install mmcv==2.0.1 # 如果在国内可以尝试镜像加速: mim install mmcv==2.0.1 -i https://mirrors.aliyun.com/pypi/simple

# onnxruntime or onnxruntime-gpu 二选一
pip install onnxruntime==1.8.1
# if you cant find onnxruntime==1.8.1
# wget https://pypi.tuna.tsinghua.edu.cn/packages/b1/68/5a45e375e3a7b71edb8f48101dcc9f6339c3c2ccbbed6f2193b599c8f4be/onnxruntime-1.8.1-cp38-cp38-manylinux_2_17_x86_64.manylinux2014_x86_64.whl
# pip install ./onnxruntime-1.8.1-cp38-cp38-manylinux_2_17_x86_64.manylinux2014_x86_64.whl
pip install onnxruntime==1.8.1
# if you cant find onnxruntime-gpu==1.8.1
# wget https://pypi.tuna.tsinghua.edu.cn/packages/ae/53/d065090e5f0727bf892313f0fdd005eb0cc9942486cfec38f6ad6e03d8fc/onnxruntime_gpu-1.18.1-cp38-cp38-manylinux_2_27_x86_64.manylinux_2_28_x86_64.whl#sha256=96e665393934cd6a2d7f5c4a8449815fc88e6afaeafc0b1da795545fabc7624f
# pip install ./onnxruntime_gpu-1.18.1-cp38-cp38-manylinux_2_27_x86_64.manylinux_2_28_x86_64.whl

git clone -b main https://github.com/open-mmlab/mmdeploy.git
git clone -b 3.x https://github.com/open-mmlab/mmdetection.git
# 如果clone不下来直接去下载zip,实测3.2.0可用: https://github.com/open-mmlab/mmdetection/tree/v3.2.0, 点击`code`，-> `download ZIP` , about 14.7 MB
cd mmdetection
mim install -v -e .
```
