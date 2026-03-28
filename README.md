# Adaptive-Image-Transformer (AIT)

<p align="left">
<a href="https://openaccess.thecvf.com/content/CVPR2021/papers/Chen_Adaptive_Image_Transformer_for_One-Shot_Object_Detection_CVPR_2021_paper.pdf">
  <img src="https://img.shields.io/static/v1?label=Paper&message=Link&color=red" height="20.5">
</a>

This repository provides the official implementation of the key modules introduced in "**Adaptive Image Transformer for One-Shot Object Detection** (CVPR 2021)."

**TL;DR:** AIT uses an encoder-decoder architecture for adaptive proposal-query alignment, along with selective channel attention (SCA) that amplifies or suppresses contributions across heads

<a href="https://homepage.iis.sinica.edu.tw/~liutyng/" target="_blank" rel="noreferrer"> <img src="https://i.imgur.com/3W9vtBl.png" alt="Logo" width="20" height="20"/></a> By Ding-Jie Chen, He-Yen Hsieh, and Tyng-Luh Liu

###### tags: `transformer`, `encoder-decoder`, `attention`, `object detection`

---

<table width="100%" border=1 frame=void rules=cols>
  <tr>
  <td style="border-left-style:none; border-right-style:none;">
    <b>Table of Contents</b><br><br>
    <a href="#1">1. Stepup</a><br>
    <a href="#1.1">1.1 Create Conda Environment</a><br>
    <a href="#1.2">1.2 Installation</a><br>
    <a href="#2">2. Prerequisites</a><br>
    <a href="#3">3. Run Adaptive Image Transformer</a><br>
    <a href="#4">4. Citation</a><br>
    <a href="#5">5. Acknowledgements</a><br>
  </tr>
</table>


## 🔥 Updates

- Accepted to CVPR 2021

## 🛠️ <a name="1"></a> 1. Setup

The project is tested on Python 3.10 and NVIDIA CUDA GPUs

### <a name="1.1"></a> 1.1 Create Conda Environment

```bash=
conda create -n AIT python=3.10 -y
conda activate AIT
```

### <a name="1.2"></a> 1.2 Installation

- Command Line for Installing PyTorch 2.6
```bash=
pip install torch==2.6.0 torchvision==0.21.0 torchaudio==2.6.0 --index-url https://download.pytorch.org/whl/cu124
```

## <a name="2"></a> 2. Prerequisites
- <a href="https://releases.ubuntu.com/18.04/" target="_blank" rel="noreferrer"> <img src="https://raw.githubusercontent.com/devicons/devicon/master/icons/linux/linux-original.svg" alt="linux" width="30" height="30"/> </a> Operating system
    - Ubuntu 22.04.5 LTS
- <a href="https://developer.nvidia.com/cuda-toolkit" target="_blank" rel="noreferrer"> <img src="https://upload.wikimedia.org/wikipedia/sco/2/21/Nvidia_logo.svg" alt="pytorch" width="30" height="30"/> </a> Graphics card
    - GPU: NVIDIA GeForce RTX 3090 or NVIDIA GeForce RTX 4090
- <a href="https://pytorch.org/get-started/previous-versions/" target="_blank" rel="noreferrer"> <img src="https://www.vectorlogo.zone/logos/pytorch/pytorch-icon.svg" alt="pytorch" width="30" height="30"/> </a> Framework and environment
    - pytorch: 2.6.0
    - cuda: 12.4
- <a href="https://docs.conda.io/en/latest/miniconda.html" target="_blank" rel="noreferrer"> <img src="https://raw.githubusercontent.com/devicons/devicon/master/icons/python/python-original.svg" alt="python" width="30" height="30"/> </a> Programming language
    - python: 3.10
 
### Project structure
```shell
$ tree ait
ait/
└── transformer
    ├── Layers.py    # Encoder and Decoder layers
    ├── Models.py    # Adaptive Image Transformer (AIT) implementation
    ├── Modules.py   # Scaled dot product attention
    └── SubLayers.py # Selective Channel Attention (SCA) module
```   

## 🚀 <a name="3"></a> 3. Run Adaptive Image Transformer

```bash=
python adaptive_image_transformer.py
```

For example, 128 proposals from Faster R-CNN and a batch size of 4. The proposal input is shaped as `batch_size × num_proposals` along the first dimension, and the AIT module outputs refined proposal features. You'll see that the output shows:
```bash=
--------------------------------------------------
Input shape:
        Proposal: 512 x 1024 x 7 x 7
          Query : 4 x 1024 x 8 x 8

Output shape:
        Reconstruted Proposal: 512 x 1024 x 8 x 8
```


## 🔖 <a name="4"></a> 4. Citation

If you find this work helpful for your research, please cite the following paper:

```bibtex
@inproceedings{ChenHL21,
  author    = {Ding-Jie Chen and He-Yen Hsieh and Tyng-Luh Liu},
  title     = {Adaptive Image Transformer for One-Shot Object Detection},
  booktitle = {CVPR},
  pages     = {12247--12256},
  publisher = {Computer Vision Foundation / {IEEE}},
  year      = {2021}
}
```

## 🙌 <a name="5"></a> 5. Acknowledgements
This repository is part of the official [AIT](https://github.com/CAIVIAC/AIT) project.
We also thank the authors of [faster-rcnn](https://github.com/jwyang/faster-rcnn.pytorch) and [CoAE](https://github.com/timy90022/One-Shot-Object-Detection) for their excellent work and implementations!
