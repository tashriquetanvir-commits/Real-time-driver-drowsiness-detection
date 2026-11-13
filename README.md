# Driver Drowsiness Detection with Computer Vision

A BRAC University CSE427 team project comparing three deep learning models for classifying cropped eye images as **open** or **closed**. Eye closure is one signal that could support a future driver monitoring system.

## Project files

| File | Contents |
| --- | --- |
| [Google Colab notebook](CSE427_driverdrowsiness_FINAL_YOLO12_EfficientNetB0_ViT%20%281%29.ipynb) | Dataset preparation, training, evaluation, and visualizations |
| [CSE427 project report](CSE427_project_Report.pdf) | Methodology, results, limitations, and future work |

## Data and approach

- The primary dataset contains 4,000 images, evenly split between open and closed eyes. The notebook uses stratified training, validation, and test splits.
- A separate external dataset of approximately 14,500 images is used for evaluation. The closed-eye category maps to **closed**, and forward, left, and right gaze map to **open**.
- **EfficientNetB0** uses transfer learning. The **Vision Transformer (ViT)** classifies images using patches and self-attention.
- **YOLO12** uses a generated bounding box covering each entire eye crop because the source images lack manually annotated boxes.

## Reported results

| Model | Metric | Internal test | External validation |
| --- | --- | ---: | ---: |
| EfficientNetB0 | Accuracy | 70% | 65% |
| Vision Transformer | Accuracy | 100% | 84% |
| YOLO12 | mAP@0.50 | 99.5% | 99.4% |

These figures come from Tables I and II of the report. ViT had the higher external accuracy of the two classifiers. YOLO12's mAP measures detection performance against the generated boxes and should be interpreted separately from classification accuracy.

## Run the notebook

1. Open the notebook in Google Colab and select a GPU runtime.
2. Place the primary and external dataset archives in Google Drive. Update `ZIP_PATH` and `EXTERNAL_ZIP_PATH` to match their locations. The archives are required and are distributed separately from this repository.
3. Run the notebook sections in order to prepare the datasets, train the models, and reproduce the evaluation. The notebook uses Ultralytics for YOLO12 and TensorFlow/Keras for EfficientNetB0 and ViT.

## Scope

The experiments evaluate individual cropped eye images. Continuous webcam processing, measuring how long eyes remain closed, and validating alerts under real driving conditions are future work.

## Team

Khondokar Waysal E Mustafa and Tashrique Tanvir, BRAC University.
