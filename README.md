# Fork of [derronqi/yolov7-face](https://github.com/derronqi/yolov7-face)

Differences between original repository and fork:

* Compatibility with PyTorch >=2.0. (🔥)
* Original pretrained models and converted ONNX models from GitHub [releases page](https://github.com/clibdev/yolov7-face/releases). (🔥)
* The [wider_val.txt](data/widerface/val/wider_val.txt) file for WIDERFace evaluation.
* The following deprecations has been fixed:
  * UserWarning: torch.meshgrid: in an upcoming release, it will be required to pass the indexing argument. 

# Installation

```shell
pip install -r requirements.txt
```

# Pretrained models

| Method        | Test Size | Easy | Medium | Hard | FLOPs (B) @640 | Link                                                                                                                                                                                      |
|---------------|-----------|------|--------|------|----------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| yolov7-lite-t | 640       | 88.7 | 85.2   | 71.5 | 0.8            | [PyTorch](https://github.com/clibdev/yolov7-face/releases/latest/download/yolov7-lite-t.pt), [ONNX](https://github.com/clibdev/yolov7-face/releases/latest/download/yolov7-lite-t.onnx)   |
| yolov7-lite-s | 640       | 92.7 | 89.9   | 78.5 | 3.0            | [PyTorch](https://github.com/clibdev/yolov7-face/releases/latest/download/yolov7-lite-s.pt), [ONNX](https://github.com/clibdev/yolov7-face/releases/latest/download/yolov7-lite-s.onnx)   |
| yolov7-tiny   | 640       | 94.7 | 92.6   | 82.1 | 13.2           | [PyTorch](https://github.com/clibdev/yolov7-face/releases/latest/download/yolov7-tiny.pt), [ONNX](https://github.com/clibdev/yolov7-face/releases/latest/download/yolov7-tiny.onnx)       |
| yolov7s       | 640       | 94.8 | 93.1   | 85.2 | 16.8           | [PyTorch](https://github.com/clibdev/yolov7-face/releases/latest/download/yolov7s-face.pt), [ONNX](https://github.com/clibdev/yolov7-face/releases/latest/download/yolov7s-face.onnx)     |
| yolov7        | 640       | 96.9 | 95.5   | 88.0 | 103.4          | [PyTorch](https://github.com/clibdev/yolov7-face/releases/latest/download/yolov7-face.pt), [ONNX](https://github.com/clibdev/yolov7-face/releases/latest/download/yolov7-face.onnx)       |
| yolov7+TTA    | 640       | 97.2 | 95.8   | 87.7 | 103.4          | [PyTorch](https://github.com/clibdev/yolov7-face/releases/latest/download/yolov7-face.pt)                                                                                                 |
| yolov7-w6     | 960       | 96.4 | 95.0   | 88.3 | 89.0           | [PyTorch](https://github.com/clibdev/yolov7-face/releases/latest/download/yolov7-w6-face.pt), [ONNX](https://github.com/clibdev/yolov7-face/releases/latest/download/yolov7-w6-face.onnx) |
| yolov7-w6+TTA | 1280      | 96.9 | 95.8   | 90.4 | 89.0           | [PyTorch](https://github.com/clibdev/yolov7-face/releases/latest/download/yolov7-w6-face.pt)                                                                                              |

# Inference

```shell
python detect.py --weights yolov7s-face.pt --source data/images/22_Picnic_Picnic_22_10.jpg
```

# Export to ONNX format

```shell
pip install onnx
```
```shell
python models/export.py --weights yolov7s-face.pt --grid
```
