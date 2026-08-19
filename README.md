# N.O. H.A.R.M.S.

> **Non-Obtrusive Human Activity Recognition in Medical Settings** - a research prototype for recognizing patient-room activities from pose-derived video representations.

![Status](https://img.shields.io/badge/status-archived%20research%20prototype-64748b)
![Framework](https://img.shields.io/badge/framework-MMAction2-6B46C1)
![Model](https://img.shields.io/badge/model-SlowOnly%20ResNet--50-2563EB)
![Data](https://img.shields.io/badge/data-restricted%20access-DC2626)

## Overview

N.O. H.A.R.M.S. explored non-obtrusive human activity recognition for long-term-care settings. The project pipeline used pose detection to transform video into pose/keypoint representations, then used an MMAction2-compatible 3D action-recognition model to classify activities. The intended research direction was to support review of events such as falls, missed medication, and irregular movement - not to make clinical decisions autonomously.

The recovered artifacts include the action labels and a SlowOnly ResNet-50 training configuration. Raw videos, processed annotations, and model weights are intentionally excluded because they may be governed by the source dataset's access terms and could contain sensitive health-related imagery.

## Research scope

```mermaid
flowchart LR
    V[Restricted care-setting video] --> P[Pose detection]
    P --> S[Pose / keypoint annotations]
    S --> A[MMAction2 PoseDataset]
    A --> M[SlowOnly ResNet-50 Recognizer3D]
    M --> C[Activity class prediction]
    C --> R[Human review / research analysis]
```

The project description identifies YOLO-based pose detection and an MMAction2 PoseC3D-style action-recognition workflow. The recovered configuration uses `Recognizer3D` with a `ResNet3dSlowOnly` backbone and pose heatmap inputs.

## Recovered configuration

| Area | Recovered setting |
| --- | --- |
| Classes | 10 activity categories |
| Input | 17-keypoint pose representation |
| Temporal sampling | 48 frames per clip |
| Backbone | SlowOnly 3D ResNet-50 |
| Training | SGD, cosine learning-rate schedule, 240 epochs |
| Training batch size | 8 |
| Evaluation | Top-1 accuracy metric |
| Recovered checkpoint | `best_acc_top1_epoch_89.pth` was supplied, but is intentionally not published |

See [the recovered configuration](configs/slowonly_r50_8xb32-u48-240e_k400-keypoint.py) and [reproducibility notes](docs/reproducibility.md).

## Activity taxonomy

The recovered `labels.txt` defines the following classes:

| # | Activity |
| ---: | --- |
| 1 | Open fridge |
| 2 | Open bedside table drawer |
| 3 | Sit at table |
| 4 | Sit at desk |
| 5 | Lay on bed |
| 6 | Sit on couch |
| 7 | Open cupboard |
| 8 | Sit on bed |
| 9 | Pick up book |
| 10 | Room transitions |

## Repository layout

```text
configs/       Recovered MMAction2 training configuration
labels.txt     Recovered activity-label vocabulary
docs/          Model card, governance notes, and reproduction guidance
data/          Placeholder only - no dataset or annotations are versioned
models/        Placeholder only - no weights are versioned
```

## Responsible use

This repository is a retrospective academic artifact, not a clinical product. It must not be used for diagnosis, treatment, surveillance without consent, or automated patient-risk decisions. Any renewed work requires institutional approval, valid dataset authorization, de-identification review, bias and error analysis, and a human-in-the-loop escalation policy.

Read the [model card](docs/model-card.md) and [data-governance notes](docs/data-governance.md) before requesting data or reproducing a run.

## What is intentionally excluded

- Raw training video archive (120 videos, supplied separately)
- Processed skeleton annotations and train/validation split files
- Best checkpoint weights
- Patient-facing examples, predictions, and identifiable media
- Credentials, dataset-access instructions, or source-dataset redistribution material

## Known limitations

The recovered artifacts do not include a metric log, evaluation report, dataset split manifest, pose-extraction scripts, or exact environment lockfile. As a result, this repository does **not** report accuracy, clinical validity, or comparative benchmarks. A checkpoint filename indicates a best top-1 checkpoint at epoch 89, but does not establish the score without the original log.

## Citation and attribution

This project was associated with the University of California, Davis and used Dr. Weakley's ICARE dataset under the applicable project access arrangement. Do not redistribute the dataset or derived artifacts without permission from the data owner and the relevant institution.

