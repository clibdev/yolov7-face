# Fork of [derronqi/yolov7-face](https://github.com/derronqi/yolov7-face)

Differences between original repository and fork:

* Compatibility with PyTorch >=2.4. (🔥)
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

| Name               | Model Size (MB) | Link                                                                                                                                                                                              | SHA-256 |
|--------------------|-----------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|---------|
| YOLOv7-Lite-t-Face | <br>            | [PyTorch](https://github.com/clibdev/yolov7-face/releases/latest/download/yolov7-lite-t-face.pt), [ONNX](https://github.com/clibdev/yolov7-face/releases/latest/download/yolov7-lite-t-face.onnx) | <br>    |
| YOLOv7-Lite-s-Face | <br>            | [PyTorch](https://github.com/clibdev/yolov7-face/releases/latest/download/yolov7-lite-s-face.pt), [ONNX](https://github.com/clibdev/yolov7-face/releases/latest/download/yolov7-lite-s-face.onnx) | <br>    |
| YOLOv7-Tiny-Face   | <br>            | [PyTorch](https://github.com/clibdev/yolov7-face/releases/latest/download/yolov7-tiny-face.pt), [ONNX](https://github.com/clibdev/yolov7-face/releases/latest/download/yolov7-tiny-face.onnx)     | <br>    |
| YOLOv7s-Face       | <br>            | [PyTorch](https://github.com/clibdev/yolov7-face/releases/latest/download/yolov7s-face.pt), [ONNX](https://github.com/clibdev/yolov7-face/releases/latest/download/yolov7s-face.onnx)             | <br>    |
| YOLOv7-Face        | <br>            | [PyTorch](https://github.com/clibdev/yolov7-face/releases/latest/download/yolov7-face.pt), [ONNX](https://github.com/clibdev/yolov7-face/releases/latest/download/yolov7-face.onnx)               | <br>    |
| YOLOv7-W6-Face     | <br>            | [PyTorch](https://github.com/clibdev/yolov7-face/releases/latest/download/yolov7-w6-face.pt), [ONNX](https://github.com/clibdev/yolov7-face/releases/latest/download/yolov7-w6-face.onnx)         | <br>    |

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
