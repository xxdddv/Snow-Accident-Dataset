# Snow-Accident Dataset

Snow-Accident is a one-class object detection dataset for traffic accident perception under adverse ice-and-snow conditions. It is intended for research on robust object detection, adverse-weather perception, intelligent transportation, and YOLO-based accident-related object detection.

## Dataset Creator

**Guanyu Chen**  
Northeast Forestry University  
Email: 2265381150@qq.com

The Snow-Accident Dataset was created and publicly released by Guanyu Chen at Northeast Forestry University.

## Dataset Overview

- **Task:** One-class object detection
- **Annotation format:** YOLO
- **Number of classes:** 1
- **Class name:** `accident-related_object`
- **Training images:** 14,481
- **Validation images:** 1,809
- **Light ice-and-snow test images:** 604
- **Moderate ice-and-snow test images:** 604
- **Heavy ice-and-snow test images:** 2,416
- **Additional normal-weather test images:** 700
- **Total released images:** 20,614

The folder name `test_medium` corresponds to the moderate ice-and-snow degradation test set reported in the associated paper.

## Class Definition

### Class 0: `accident-related_object`

This class includes visible accident-related objects or regions such as:

- collided vehicles;
- overturned vehicles;
- visible collision-related regions;
- accident-related scattered debris.

Unannotated regions are treated as background.

## Directory Structure

```text
Snow-Accident-Dataset-v1.0/
├── README.md
├── dataset.yaml
├── LICENSE-DATA
├── CITATION.cff
├── images/
│   ├── train/
│   ├── val/
│   ├── test_light/
│   ├── test_medium/
│   ├── test_heavy/
│   └── test-normal/
└── labels/
    ├── train/
    ├── val/
    ├── test_light/
    ├── test_medium/
    ├── test_heavy/
    └── test-normal/
```

Each image has a YOLO label file with the same base name.

Example:

```text
images/test_heavy/heavy_000001.jpg
labels/test_heavy/heavy_000001.txt
```

## Annotation Format

Each line in a label file follows the standard YOLO format:

```text
class_id x_center y_center width height
```

All coordinates are normalized to the range `[0, 1]`.

Example:

```text
0 0.512341 0.476852 0.214739 0.163284
```

## Dataset Split Policy

The dataset is divided into training, validation, and test subsets at the video-sequence level. Consecutive frames from the same source sequence are not distributed across different subsets.

The controlled ice-and-snow degradation subsets are generated only from held-out test images. No degraded version of the same source sequence is included in the training or validation set.

## Download

The complete dataset is available from the GitHub Release page:

- **Repository:** https://github.com/xxdddv/Snow-Accident-Dataset
- **Latest release:** https://github.com/xxdddv/Snow-Accident-Dataset/releases/latest

The dataset is distributed as three independent ZIP archives:

```text
Snow-Accident-Dataset-v1.0-part01.zip
Snow-Accident-Dataset-v1.0-part02.zip
Snow-Accident-Dataset-v1.0-part03.zip
```

Please also download:

```text
PAIR_TO_PART_MAPPING.csv
README_DOWNLOAD.txt
```

### Extraction Instructions

1. Download all three ZIP archives.
2. Extract all three ZIP archives into the same destination directory.
3. Keep the original directory structure.
4. The complete dataset will be restored after all three archives are extracted.

Each image and its matching YOLO label are stored in the same ZIP archive.

## Using the Dataset with Ultralytics YOLO

Install Ultralytics:

```bash
pip install ultralytics
```

Train a detector:

```bash
yolo detect train data=dataset.yaml model=yolov8n.pt epochs=100 imgsz=640
```

Evaluate on the default heavy-degradation test set:

```bash
yolo detect val data=dataset.yaml model=path/to/best.pt split=test
```

To evaluate another subset, change the `test:` entry in `dataset.yaml`.

## Recommended Evaluation Metrics

- Precision
- Recall
- F1-Score
- mAP@0.5
- mAP@0.5:0.95
- FPS
- GFLOPs

## License

The dataset is released under the **Creative Commons Attribution-NonCommercial 4.0 International License (CC BY-NC 4.0)**.

Commercial use is not permitted. Users must provide appropriate attribution and cite the dataset when using it in academic work.

See `LICENSE-DATA` for details.

## Citation

Please cite the dataset and the associated paper when using this work.

```bibtex
@dataset{chen2026snowaccident,
  author    = {Guanyu Chen},
  title     = {Snow-Accident Dataset: Accident-Related Object Detection under Adverse Ice-and-Snow Conditions},
  year      = {2026},
  version   = {1.0.0},
  publisher = {GitHub},
  url       = {https://github.com/xxdddv/Snow-Accident-Dataset}
}
```

## Associated Paper

**Cryo-YOLO: Robust Traffic Accident Detection under Adverse Ice-and-Snow Conditions**

## Contact

**Guanyu Chen**  
Northeast Forestry University  
Email: 2265381150@qq.com
