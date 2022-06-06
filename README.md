# GRCNN-PyTorch

## Overview

This repository contains an op-for-op PyTorch reimplementation
of [Gated Recurrent Convolution Neural Network for OCR](https://dl.acm.org/doi/pdf/10.5555/3294771.3294803).

## Table of contents

- [GRCNN-PyTorch](#grcnn-pytorch)
    - [Overview](#overview)
    - [Table of contents](#table-of-contents)
    - [Download weights](#download-weights)
    - [Download datasets](#download-datasets)
    - [How Test and Train](#how-test-and-train)
        - [Test](#test)
        - [Train GRCNN model](#train-grcnn-model)
        - [Resume train GRCNN model](#resume-train-grcnn-model)
    - [Result](#result)
    - [Contributing](#contributing)
    - [Credit](#credit)
        - [An End-to-End Trainable Neural Network for Image-based Sequence Recognition and Its Application to Scene Text Recognition](#an-end-to-end-trainable-neural-network-for-image-based-sequence-recognition-and-its-application-to-scene-text-recognition)

## Download weights

- [Google Driver](https://drive.google.com/drive/folders/17ju2HN7Y6pyPK2CC_AqnAfTOe9_3hCQ8?usp=sharing)
- [Baidu Driver](https://pan.baidu.com/s/1yNs4rqIb004-NKEdKBJtYg?pwd=llot)

## Download datasets

Contains ICDAR2013~2019, MJSynth, SynthText, SynthAdd, Verisimilar Synthesis, UnrealText and more, etc.

- [Google Driver](https://drive.google.com/drive/folders/1CwkA0gKd4bnj66W0l6CB14sx-aAe3WOE?usp=sharing)
- [Baidu Driver](https://pan.baidu.com/s/1v31aBT5phe5Ci6N0Wsn3xQ?pwd=llot)

Please refer to `README.md` in the `data` directory for the method of making a dataset.

## How Test and Train

Both training and testing only need to modify the `config.py` file.

### Test

- line 40: `mode` change to `test`.
- line 80: `model_path` change to `results/pretrained_models/GRCNN-MJSynth-e9341ede.pth.tar`.

### Train GRCNN model

- line 40: `mode` change to `train`.
- line 42: `exp_name` change to `GRCNN_MJSynth`.

### Resume train GRCNN model

- line 40: `mode` change to `train`.
- line 42: `exp_name` change to `GRCNN_MJSynth`.
- line 56: `resume` change to `samples/GRCNN_MJSynth/epoch_xxx.pth.tar`.

## Result

Source of original paper
results: [https://dl.acm.org/doi/pdf/10.5555/3294771.3294803](https://dl.acm.org/doi/pdf/10.5555/3294771.3294803)

In the following table, `-` indicates show no test.

|    Model    | IIIT5K(None) | SVT(None) | IC03(None) |
|:-----------:|:------------:|:---------:|:----------:|
| CRNN(paper) |     80.8     |   81.5    |    91.2    |
| CRNN(repo)  |   **81.5**   | **80.1**  |   **-**    |

```bash
# Download `CRNN-Synth90k-e9341ede.pth.tar` weights to `./results/pretrained_models`
# More detail see `README.md<Download weights>`
python predict.py --image_path ./figures/Available.png --weights_path ./results/pretrained_models/CRNN-MJSynth-e9341ede.pth.tar
```

Input: <span align="center"><img src="figures/Available.png"/></span>

Output:

```text
Build CRNN model successfully.
Load CRNN model weights `./results/pretrained_models/CRNN-MJSynth-e9341ede.pth.tar` successfully.
``./figures/Available.png` -> `available`
```

## Contributing

If you find a bug, create a GitHub issue, or even better, submit a pull request. Similarly, if you have questions,
simply post them as GitHub issues.

I look forward to seeing what the community does with these models!

## Credit

### Gated Recurrent Convolution Neural Network for OCR

_Jianfeng Wang, Xiaolin Hu_ <br>

**Abstract** <br>
Optical Character Recognition (OCR) aims to recognize text in natural images.
Inspired by a recently proposed model for general image classification, Recurrent
Convolution Neural Network (RCNN), we propose a new architecture named
Gated RCNN (GRCNN) for solving this problem. Its critical component, Gated
Recurrent Convolution Layer (GRCL), is constructed by adding a gate to the
Recurrent Convolution Layer (RCL), the critical component of RCNN. The gate
controls the context modulation in RCL and balances the feed-forward information
and the recurrent information. In addition, an efficient Bidirectional Long ShortTerm Memory (BLSTM) is built for
sequence modeling. The GRCNN is combined
with BLSTM to recognize text in natural images. The entire GRCNN-BLSTM
model can be trained end-to-end. Experiments show that the proposed model
outperforms existing methods on several benchmark datasets including the IIIT-5K,
Street View Text (SVT) and ICDAR

[[Paper]](https://dl.acm.org/doi/pdf/10.5555/3294771.3294803) [[Code(Lua)]](https://github.com/Jianf-Wang/GRCNN-for-OCR)

```bibtex
@inproceedings{jianfeng2017deep,
 author    = {Wang, Jianfeng and Hu, Xiaolin},
 title     = {Gated Recurrent Convolution Neural Network for OCR},
 booktitle = {Advances in Neural Information Processing Systems},
 year      = {2017}
}
```

