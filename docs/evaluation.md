# Evaluation record

## Evidence boundary

This page summarizes results reported in the team final report. The original experiment logs, prediction files, split manifest, and exact software environment were not recovered, so the values below are historical evidence rather than live benchmark claims.

## Pose-based action recognition

The report describes a PoseC3D experiment implemented through MMAction2. Videos were converted to pose keypoints, and a pose-based model was trained to classify manually labeled actions. The evaluation used 30 unseen validation and test videos.

| Metric | Reported result |
| --- | ---: |
| Top-1 accuracy | 66.67% |
| Top-5 accuracy | 83.33% |

The report identifies low-resolution video, motion blur, occlusion, and inaccurate or missing keypoints as major sources of error. Similar actions, including picking up an object and opening a fridge, were reported as difficult to distinguish.

## Rule-based coarse activity recognition

The second pipeline ran YOLOv11 person detection on every frame, intersected the detected person with manually defined room activity zones, and used a temporal buffer to reduce transient false positives. Events were compared with manually annotated ground truth.

### Five-video event comparison

The report's tabulated five-video comparison used a 10-second event-matching window:

| Measure | Count or value |
| --- | ---: |
| Ground-truth actions | 35 |
| YOLO predictions | 39 |
| Correct predictions within window | 26 |
| False positives | 11 |
| Missed predictions | 9 |
| Precision | 0.70 |
| Recall | 0.74 |
| F1 score | 0.72 |

The report separately summarizes the rule-based method as 88% action-annotation accuracy with about 5 seconds of time error. The available material does not document the aggregation procedure behind that headline figure, so it is preserved as a reported aggregate rather than recomputed from the five-video table.

## Interpretation

The two paths answer different questions. The YOLOv11 pipeline was designed for coarse, location-dependent activities and for updating a client interface. The PoseC3D path aimed to generalize beyond fixed room zones using body-pose dynamics. Neither path is a clinical validation, and any future use requires a renewed protocol, authorized data access, and human oversight.

