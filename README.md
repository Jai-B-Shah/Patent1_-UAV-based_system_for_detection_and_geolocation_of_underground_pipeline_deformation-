# UAV-based System for Detection and Geolocation of Underground Pipeline Structural Deformation

**Patent Published: IN202641062273 A1 (May 2026)**

This project is a UAV-mounted thermal imaging system that detects structural deformation and leaks in underground pipelines and pinpoints their exact location in the field. A drone fitted with a thermal camera flies over a pipeline route, captures temperature-pattern images of the ground, and an onboard edge computer analyzes those images in real time to flag abnormal heat signatures, typical of a leak or a deformed section, while tagging each detection with its GPS coordinates and timestamp. This removes the need for manual ground surveys over long and often inaccessible pipeline corridors, and gives maintenance teams a precise, traceable record of where a problem was found and when.

A ground-based proof-of-concept of the detection pipeline (camera capture, GPS/time logging, and the trained detection model) was built and tested ahead of the UAV integration described in the patent filing.

## Skills & Tools Demonstrated

- Embedded/edge computing on a Raspberry Pi 5
- Thermal imaging with the MLX90640 thermal camera sensor
- GPS-based geotagging (NEO-6M GPS module) and real-time timestamping
- Machine learning image analysis: CNN-based classification fused with YOLOv8 object detection
- Model training and fine-tuning (Ultralytics YOLOv8s) on a custom thermal hotspot dataset
- Python for hardware interfacing, inference pipelines, and data logging
- Patent drafting and IP documentation (India patent filing via VIT)
- System-level design integrating sensors, edge compute, and ML inference into one pipeline

## What Was Built

- A UAV-mounted thermal imaging and edge-computing pipeline design, covered by the patent filing, for detecting and geolocating underground pipeline deformation
- A ground-based proof-of-concept detection system: MLX90640 thermal camera + Raspberry Pi 5 + NEO-6M GPS module, wired and tested on real hardware (see `Hardware/`)
- A custom-trained YOLOv8s model (single class: "Hotspot") that detects thermal anomalies in captured frames and reports a confidence score and bounding box per detection
- A GPS and timestamp logging layer that geotags every captured frame and every detection, so each flagged anomaly carries an exact location and time
- A full data flow: thermal capture -> edge-device calibration and ROI extraction -> CNN classification -> YOLO-based detection, confidence scoring, and GPS/timestamp fusion -> output for a monitoring dashboard/alert
- A formal patent application (IN202641062273 A1), filed through Vellore Institute of Technology, describing the complete UAV-based system

## Results

- The custom YOLOv8s "Hotspot" detector was trained for 100 epochs on the thermal dataset; at the final epoch it reached a precision of ~0.37, recall of ~0.43, and mAP50 of ~0.29 on the validation set. These are early-stage proof-of-concept numbers from a small custom dataset, not a production-tuned model.
- The pipeline was demonstrated end-to-end on real hardware: live GPS coordinates and timestamps were successfully attached to each captured frame and to each detected hotspot (see `Diagrams/Terminal_output_gps_and_timestamp.jpeg` and `Diagrams/Output_image.jpeg`).
- The invention was formally filed and published as an Indian patent application: IN202641062273 A1 (May 2026).

## Repository Structure

- `Patent/` — the official published patent document (IN202641062273 A1) and the VIT Invention Disclosure Form (IDF-B) filed ahead of the patent application, documenting the working principle, prior-art analysis, and experimental validation
- `Hardware/` — photo of the assembled ground-based hardware prototype (Raspberry Pi 5, MLX90640 thermal camera, NEO-6M GPS module)
- `Diagrams/` — system architecture diagram, data flow chart, sample thermal detection output, GPS/timestamp terminal log, and detection confidence output
- `Code/uav-pipeline-detection-code/` — the ground-based proof-of-concept detection code, training scripts, trained YOLOv8 weights, and training dataset (see `Code/uav-pipeline-detection-code/PROVENANCE.md` for its origin and file-by-file breakdown)

## Author & Acknowledgments

This project is the subject of a jointly filed Indian patent application. Inventors:

- **Tanmaya Kumar Das**
- **Shivain Khera**
- **Jai B Shah**

Applicant: **Vellore Institute of Technology (VIT)**

This repository is maintained by Jai B Shah and documents the shared invention and the proof-of-concept work built toward it.
