# Spine-Segmentation-and-Vertebrae-Localization-using-YOLOv8



This notebook provides a comprehensive guide to training an instance segmentation model on the CSI 2014 spine CT dataset using Ultralytics YOLOv8 and achieving strong performance.

## Introduction

Instance segmentation combines object detection with semantic segmentation to detect and segment individual objects in an image. It has applications in medical imaging for tasks like organ and lesion segmentation.

The CSI 2014 dataset contains CT scans of the full spine region with pixel-level annotation masks for each vertebra. This challenging medical imaging data can be used to develop and evaluate instance segmentation models. 

YOLOv8 is a real-time object detection and segmentation framework. Its speed, accuracy and support for transfer learning make it well-suited for specialized datasets like CSI 2014.

## CSI 2014 Dataset

The dataset consists of:

- 20 training CT scans
- 4 test CT scans
- Axial slice thickness of 3mm
- Annotations for 24 vertebrae per patient scan
- Pixel-level masks for each individual vertebra

The data captures the full spine with multiple slices per patient. The thin slice thickness provides high resolution for segmentation.

## YOLOv8 Architecture

YOLOv8 uses a transformer backbone with a Spatial Pyramid Pooling Feature (SPPF) head for object detection. For segmentation it adds a Segment head with upsampling layers and masking components.

The YOLOv8 Small (v8s) model used has ~12M parameters. It uses a simplified CSP-M backbone with 2 extra corrective ArcSoft heads for accuracy.

Some key improvements over YOLOv7:

- Dynamic input resolution
- Anchor-free detection
- Mask scoring for segmentation
- Better regularization methods

## Training Setup

- **Framework**: Ultralytics YOLOv8 PyTorch 
- **Model**: YOLOv8 Small (v8s)
- **Input Size**: 640 x 640
- **Epochs**: 50
- **Batch Size**: 16
- **Augmentation**: Mosaic, HSV colorspace
- **Hardware**: GPU (Nvidia Tesla T4)

## Training Process

- Upload CSI images and annotations to Roboflow 
- Export dataset in YOLO format
- Load pretrained YOLOv8 COCO model 
- Train for 50 epochs with mosaic augmentation
- Evaluate model on validation set
- Perform inference on test images

The COCO pretrained base provides good initialization for transfer learning on the CSI dataset.

## Results

The YOLOv8 model achieves strong instance segmentation performance:

- **Validation mAP50**: 0.96
- **Validation Mask mAP50**: 0.968

This shows accurate detection and segmentation of individual vertebrae from the CT scans.

Below are some sample predictions:

![image](https://github.com/KMH15/Spine-Segmentation-and-Vertebrae-Localization-using-YOLOv8/assets/76402601/65dd311c-9764-4454-98a4-306c3b62255c)




## Conclusion

The notebook demonstrates how to effectively train YOLOv8 for instance segmentation on medical imaging data like CSI 2014 spine CT scans. The model attains high accuracy in detecting and segmenting individual vertebrae. The approach can be extended to similar instance segmentation problems across healthcare.

## References

- [CSI 2014 Dataset Paper](https://link.springer.com/chapter/10.1007/978-3-319-10404-1_35)  
- [YOLOv8 Paper](https://arxiv.org/abs/2207.02696)
- [Roboflow Notebooks](https://notebooks.roboflow.com)

Let me know if you would like me to add or expand any sections further.
