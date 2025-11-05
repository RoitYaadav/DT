#Off-Road Human Intrusion Detection Dataset
Abstract
This repository introduces a novel RGB and thermal image dataset focused on human intrusion detection in challenging off-road environments. Data is collected using multiple synchronized RGB cameras and a thermal camera mounted on autonomous ground vehicles (AGVs), capturing diverse terrains, lighting conditions, and a range of human activities—including walking, running, crouch-walking, crawling, and fence crossing. Benchmark results for several state-of-the-art object detection algorithms are provided, highlighting strengths and limitations in complex, unstructured settings. The dataset aids research on image-only human detection for safe AGV operation, especially in low-light and cluttered scenes.

Table of Contents
Abstract

Dataset Overview

Sensor Platform and Data Collection

Annotation Schema

Benchmark and Results

Getting Started

Repository Structure

Contributing

License

Acknowledgements

Dataset Overview
Over 32,000 labeled RGB images and 24,000 labeled thermal images (out of 150,000+ collected) from off-road, forested locations.

Data captured using three 3MP RGB cameras (front, rear, roof center) and a LWIR thermal camera, all mounted on a Mahindra Thar 4×4 AGV.

Includes morning, noon, night, and transitional lighting/thermal recordings.

Human actions: walking, running, crouch-walking, crawling, climbing, standing, lying (simulating realistic intrusions).

Figure Placeholder:
Insert sample labeled image here (Figure 3 from paper)
``

Sensor Platform and Data Collection
AGV equipped with synchronized RGB and thermal sensors. See architecture diagram.

Sensors:

RGB Cameras: e-con Systems, 3MP, 10 FPS, 120° (front/rear)/70° (roof center) FOV, JPEG, undistorted.

Thermal Camera: LWIR, 10 FPS, grayscale/8-bit color-mapped, ideal for nighttime.

Data captured at Garuda Flight of Freedom, Karnataka, India.

Figure Placeholder:
Insert system architecture diagram (Figure 1 from paper)
``
<img width="1325" height="793" alt="DataSet_Image" src="https://github.com/user-attachments/assets/e15aba1e-9c8b-408b-a9df-32cd308704a5" />


Figure Placeholder:
Insert front and roof-mounted sensor rig image (Figure 2 from paper)
``

Annotation Schema
Labels follow CVAT/COCO format, with humans marked if ≥75% are visible. Each includes:

Action, accessories, gender, age group, distance category (Near, Middle, Far), occlusion status.

Frame tags: time of day, camera view, number of humans, empty frame flag.

Annotation distribution balanced by action, lighting, distance, accessories, and demographics.

Table Placeholder:
Insert RGB and thermal image specs and dataset stats (Table I from paper)

text
| Specification / Statistic | RGB Cameras       | Thermal Camera         |
|--------------------------|-------------------|-----------------------|
| Resolution               | 3 MP              | LWIR (IR grayscale / 8-bit color) |
| Field of View (FOV)      | 120° / 70°        | 70°                   |
| Frame Rate               | 10 FPS            | 10 FPS                |
| Image Format             | JPEG              | Grayscale             |
| Mounting Position        | Front, Rear, Roof | Roof center           |
| Synchronization          | GNSS-based PTP    | GNSS-based PTP        |
| Primary Use Case         | Daytime           | Night, low-visibility |
| Total Images Collected   | 100,000+          | 50,000+               |
| Labeled Images           | 32,000            | 24,000                |
| Labeled Human Objects    | 91,300            | 67,400                |
| Distinct Human Actions   | See paper         | See paper             |
Benchmark and Results
Seven state-of-the-art object detectors evaluated:

YOLOv5, YOLOv8, Faster R-CNN, DETR, RT-DETR, DINOv2, Grounding DINO.

Transformer-based models outperform CNN-based, especially in off-road/low-light conditions. RGB yields higher detection rates than thermal; thermal is vital for poor visibility.

Metrics: Precision, recall, mean Average Precision at IoU=0.5 (mAP@0.5), mAP@0.5:0.95, tested on 2,000-image subset.

Table Placeholder:
Insert RGB-based detection results (Table II from paper)

text
| Model           | Precision | Recall | mAP@0.5 | mAP@0.5:0.95 |
|-----------------|-----------|--------|---------|--------------|
| YOLOv5          | 72.8      | 47.8   | 54.8    | 29.1         |
| YOLOv8          | 84.7      | 54.3   | 66.3    | 52.8         |
| Faster R-CNN    | 38.0      | 46.0   | 73.0    | 39.0         |
| DETR (R50)      | 68.3      | 71.0   | 72.4    | 42.1         |
| RT-DETR (R50)   | 71.3      | 69.3   | 76.2    | 45.9         |
| DINOv2 (Swin-B) | 86.1      | 81.3   | 85.2    | 53.5         |
| Grounding DINO  | 83.4      | 78.7   | 82.0    | 51.6         |
Table Placeholder:
Insert thermal-based detection results (Table III from paper)

text
| Model           | Precision | Recall | mAP@0.5 | mAP@0.5:0.95 |
|-----------------|-----------|--------|---------|--------------|
| YOLOv5          | 62.4      | 39.6   | 45.2    | 21.4         |
| YOLOv8          | 72.1      | 46.0   | 54.0    | 39.6         |
| Faster R-CNN    | 30.5      | 36.2   | 61.0    | 32.4         |
| DETR (R50)      | 60.2      | 64.1   | 65.5    | 37.0         |
| RT-DETR (R50)   | 63.8      | 60.3   | 69.1    | 40.3         |
| DINOv2 (Swin-B) | 75.0      | 70.2   | 77.1    | 47.8         |
| Grounding DINO  | 71.5      | 67.0   | 74.0    | 45.2         |
Getting Started
Download the dataset:
Download Off-Road Human Intrusion Detection Dataset (Google Drive)

Clone this repository:

bash
git clone https://github.com/yourusername/Offroad-Human-Intrusion-Detection.git
Follow data/ directory instructions for folder organization after download.

Scripts for training and evaluation are in models/ and evaluation/.

Repository Structure
text
├── data/          # Dataset download links and folder structure
├── models/        # Detection models and training scripts
├── evaluation/    # Evaluation and benchmarking code
├── annotations/   # COCO-format annotations, sample images
├── docs/          # Documentation, figures, sample images
├── LICENSE
└── README.md
Contributing
We welcome issues, pull requests, and suggestions. See [CONTRIBUTING.md] or contact maintainers for collaboration.

License
Released under [YOUR LICENSE HERE]. See LICENSE for details.

Acknowledgements
Research team: [Your Lab/Institution].

Data and annotation: [Authors/Contributors].

Supported by [Funding Source].
