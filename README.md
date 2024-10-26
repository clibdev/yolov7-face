# Fork of [derronqi/yolov7-face](https://github.com/derronqi/yolov7-face)

Differences between original repository and fork:

* Compatibility with PyTorch >=2.5. (🔥)
* Original pretrained models and converted ONNX models from GitHub [releases page](https://github.com/clibdev/yolov7-face/releases). (🔥)
* The [wider_val.txt](data/widerface/val/wider_val.txt) file for WIDERFace evaluation.
* The following deprecations has been fixed:
  * UserWarning: torch.meshgrid: in an upcoming release, it will be required to pass the indexing argument.
  * DeprecationWarning: 'np.float' is a deprecated alias for builtin 'float'.
  * FutureWarning: You are using 'torch.load' with 'weights_only=False'.
  * FutureWarning: Cython directive 'language_level' not set.
  * Cython Warning: Using deprecated NumPy API.

# Installation

```shell
pip install -r requirements.txt
```

# Pretrained models

* Download links:

| Name               | Model Size (MB) | Link                                                                                                                                                                                                | SHA-256                                                                                                                              |
|--------------------|-----------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|--------------------------------------------------------------------------------------------------------------------------------------|
| YOLOv7-Lite-t-Face | 0.7<br>2.1      | [PyTorch](https://github.com/clibdev/yolov7-face/releases/latest/download/yolov7-lite-t-face.pt)<br>[ONNX](https://github.com/clibdev/yolov7-face/releases/latest/download/yolov7-lite-t-face.onnx) | 04ea1dedc42c336004a29a770da8cbc795e50b0d835366b611578fd7648a1f3a<br>448b3ad27119ca15f629d9e83fe4e8c71a783c0358a154f5f4f9197320a0c89d |
| YOLOv7-Lite-s-Face | 2.3<br>5.2      | [PyTorch](https://github.com/clibdev/yolov7-face/releases/latest/download/yolov7-lite-s-face.pt)<br>[ONNX](https://github.com/clibdev/yolov7-face/releases/latest/download/yolov7-lite-s-face.onnx) | 8ad12d062bf14ec27196aa159312c33347f5850cfc4bf6e977725404ac64f01d<br>0570fb8472d2eba1350612c0d4d691abe1337e3f173069438940dc3686f0e335 |
| YOLOv7-Tiny-Face   | 11.8<br>24.2    | [PyTorch](https://github.com/clibdev/yolov7-face/releases/latest/download/yolov7-tiny-face.pt)<br>[ONNX](https://github.com/clibdev/yolov7-face/releases/latest/download/yolov7-tiny-face.onnx)     | 91eab824696f6cfadbc60bee63e969d4b4ca0484bc4c1e57b4dbd73917990127<br>76c213da5cda623984ab8c0ca97cf30fec1f75ced7fff9a0e1a1afbda8efdbc0 |
| YOLOv7s-Face       | 8.5<br>17.4     | [PyTorch](https://github.com/clibdev/yolov7-face/releases/latest/download/yolov7s-face.pt)<br>[ONNX](https://github.com/clibdev/yolov7-face/releases/latest/download/yolov7s-face.onnx)             | 044a2194cbb646ff8c31cc4264a10e061dc269929ac7b881db292511fc43c2c9<br>e69b61c08ab856766c65605aabc7ed6620fcdc9ab9b5d1fb2c558ed429c8ff3b |
| YOLOv7-Face        | 70.2<br>140.6   | [PyTorch](https://github.com/clibdev/yolov7-face/releases/latest/download/yolov7-face.pt)<br>[ONNX](https://github.com/clibdev/yolov7-face/releases/latest/download/yolov7-face.onnx)               | 20dd9c9834b467be1b1302b089c3b97d2d0055bae99c97f69d1a5bb63323911b<br>2c588b1bad756c189257d6de813837b04931441c10dae789121e5e1f95da1f64 |
| YOLOv7-W6-Face     | 133.9<br>267.8  | [PyTorch](https://github.com/clibdev/yolov7-face/releases/latest/download/yolov7-w6-face.pt)<br>[ONNX](https://github.com/clibdev/yolov7-face/releases/latest/download/yolov7-w6-face.onnx)         | 61b6205a6e01632b0df2bb6775420d65657676fa528b817966fbb6519afdca4a<br>6263fd8022268a029573300e1de273db3b091b5b745520e88e735b2faa296c9a |

* Evaluation results on WIDERFace dataset:

| Name               | Image Size | Easy | Medium | Hard | FLOPs (B) @640 |
|--------------------|------------|------|--------|------|----------------|
| YOLOv7-Lite-t-Face | 640        | 88.7 | 85.2   | 71.5 | 0.8            |
| YOLOv7-Lite-s-Face | 640        | 92.7 | 89.9   | 78.5 | 3.0            |
| YOLOv7-Tiny-Face   | 640        | 94.7 | 92.6   | 82.1 | 13.2           |
| YOLOv7s-Face       | 640        | 94.8 | 93.1   | 85.2 | 16.8           |
| YOLOv7-Face        | 640        | 96.9 | 95.5   | 88.0 | 103.4          |
| YOLOv7-W6-Face     | 960        | 96.4 | 95.0   | 88.3 | 89.0           |

# Inference

```shell
python detect.py --weights yolov7s-face.pt --source data/images/22_Picnic_Picnic_22_10.jpg
```

# WIDERFace evaluation

* Download WIDERFace [validation dataset](https://drive.google.com/file/d/1GUCogbp16PMGa39thoMMeWxp7Rp5oM8Q/view).
* Move dataset to `data/widerface/val` directory.

```shell
python test_widerface.py --weights yolov7s-face.pt --dataset_folder data/widerface/val/images/
```
```shell
cd widerface_evaluate
```
```shell
python setup.py build_ext --inplace
```
```shell
python evaluation.py
```

# Export to ONNX format

```shell
pip install onnx
```
```shell
python models/export.py --weights yolov7s-face.pt --grid
```
