# Provenance

This folder's contents were merged in from [ShivainKhera/uav-pipeline-structural-deformation-detection](https://github.com/ShivainKhera/uav-pipeline-structural-deformation-detection) — the ground-based proof-of-concept detection code, trained YOLOv8 weights, and training dataset referenced by the patent in this repo.

`README_source.md` is that repo's original README. The raw stock-image dataset-building scaffolding (unprocessed source images used to construct the training set) was left out of this merge as it is not needed to run or understand the detection code itself.

Key files:
- `Training_fine_tune/Model_training.py` — trains the YOLOv8s model on the thermal hotspot dataset.
- `Training_fine_tune/Run.py` — runs inference on a folder of images, outputs annotated images and per-image detection text logs.
- `Training_fine_tune/Run2.py` — runs inference on video.
- `Training_fine_tune/runs/detect/yolov8s_32x24_colored7/weights/best.pt` — the best trained model checkpoint.
- `Training_fine_tune/Training_dataset/` — the YOLOv8-format training/validation/test dataset (single class: `Hotspot`).
