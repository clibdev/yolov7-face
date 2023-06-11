# Fork of [derronqi/yolov7-face](https://github.com/derronqi/yolov7-face)

Differences between original repository and fork:

* Compatibility with PyTorch >=2.0. (🔥)
* Original pretrained models from GitHub [releases page](https://github.com/clibdev/yolov7-face/releases). (🔥)
* The following deprecations has been fixed:
  * UserWarning: torch.meshgrid: in an upcoming release, it will be required to pass the indexing argument. 

# Installation

```shell
pip install -r requirements.txt
```

# Pretrained models

| Method        | Test Size | Easy | Medium | Hard | FLOPs (B) @640 | Link                                                                                         |
|---------------|-----------|------|--------|------|----------------|----------------------------------------------------------------------------------------------|
| yolov7-lite-t | 640       | 88.7 | 85.2   | 71.5 | 0.8            | [PyTorch](https://github.com/clibdev/yolov7-face/releases/latest/download/yolov7-lite-t.pt)  |
| yolov7-lite-s | 640       | 92.7 | 89.9   | 78.5 | 3.0            | [PyTorch](https://github.com/clibdev/yolov7-face/releases/latest/download/yolov7-lite-s.pt)  |
| yolov7-tiny   | 640       | 94.7 | 92.6   | 82.1 | 13.2           | [PyTorch](https://github.com/clibdev/yolov7-face/releases/latest/download/yolov7-tiny.pt)    |
| yolov7s       | 640       | 94.8 | 93.1   | 85.2 | 16.8           | [PyTorch](https://github.com/clibdev/yolov7-face/releases/latest/download/yolov7s-face.pt)   |
| yolov7        | 640       | 96.9 | 95.5   | 88.0 | 103.4          | [PyTorch](https://github.com/clibdev/yolov7-face/releases/latest/download/yolov7-face.pt)    |
| yolov7+TTA    | 640       | 97.2 | 95.8   | 87.7 | 103.4          | [PyTorch](https://github.com/clibdev/yolov7-face/releases/latest/download/yolov7-face.pt)    |
| yolov7-w6     | 960       | 96.4 | 95.0   | 88.3 | 89.0           | [PyTorch](https://github.com/clibdev/yolov7-face/releases/latest/download/yolov7-w6-face.pt) |
| yolov7-w6+TTA | 1280      | 96.9 | 95.8   | 90.4 | 89.0           | [PyTorch](https://github.com/clibdev/yolov7-face/releases/latest/download/yolov7-w6-face.pt) |

# Inference

```shell
python detect.py --weights yolov7s-face.pt --source data/images/22_Picnic_Picnic_22_10.jpg
```

# Export to ONNX format

```shell
pip install onnx
```
```shell
python models/export.py --weights yolov7s-face.pt
```
