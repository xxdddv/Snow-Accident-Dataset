# Real-snow accident adaptation and evaluation supplement

Frozen version: 146 distinct native image files, one accident-region class (class 0), 80 training / 14 development / 52 test images. The test cohort contains 26 conservative incident/source groups. Native published photographs and original video frames are included; geometric augmentations and simulated weather are not counted as new originals.

## Results

| Scope | Cryo AP50 (%) | Cryo AP50:95 (%) | YOLOv8n AP50 (%) | YOLOv8n AP50:95 (%) |
|---|---:|---:|---:|---:|
| Full 52-image cohort | 70.315 | 38.508 | 59.292 | 31.205 |
| Added 6 images | 99.500 | 64.354 | 99.500 | 73.396 |
| New-case 4 images | 99.500 | 75.536 | 99.500 | 91.410 |
| Two known-case additional views | 99.500 | 30.134 | 99.500 | 39.962 |

The overall AP50:95 difference is +7.303 percentage points for Cryo; the newly added subgroup favors YOLOv8n. All outcomes are retained. The cohort contains previously observed cases and is not a 52-case new blind benchmark. It evaluates models adapted on the 80-image real-domain training split, not untouched original-paper models. Original-paper checkpoint initialization histories are not fully established.

## Download and reproduce

Download [`real-snow-146-fixed80-test52-v2.zip`](https://github.com/xxdddv/Snow-Accident-Dataset/releases/tag/real-snow-146-v2) and verify `SHA256SUMS.txt`. It contains all 146 images and YOLO labels, source and split manifests, the two frozen best checkpoints, prediction-time protocols, all scope metrics and predictions, original training records, frozen custom Ultralytics source, and `evaluate_fixed.py`.

Extract into one directory. Use the recorded Python 3.10 / PyTorch 1.13.1+cu116 environment and compatible torchvision, and run `python evaluate_fixed.py` there. This executes fixed-weight evaluation without training. The bundled custom source is required for Cryo modules. Inspect the included environment and protocol files for the complete setup. Historical audit files retain their original machine paths; the dataset YAML and execution entry use portable relative paths.

The authors reported that they reviewed the existing 146-image version. The original provenance and annotation audit records are preserved rather than retrospectively rewritten.

## Attribution and rights

This supplement is separate from the repository's original controlled-weather dataset. Original photographs, video frames, code and other third-party material retain their individual upstream terms; the repository-wide data license must not be interpreted as relicensing all third-party originals. `sources_and_attribution.csv` preserves source links, credited authors and recorded licenses. Consult the full manifests and upstream sources for applicable conditions and underlying third-party video rights. Custom Ultralytics source retains its upstream AGPL notices.

This package reports one-class accident-region detection, not a calibrated accident-risk score or real-road population false-alarm rate. The small evaluation cohort and prior observation limit generalization claims.
