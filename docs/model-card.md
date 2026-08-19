# Model card

## Summary

N.O. H.A.R.M.S. is a retrospective academic prototype for classifying a fixed set of room activities from pose-derived temporal input. Its recovered configuration specifies a 17-keypoint pose representation and a SlowOnly 3D ResNet-50 recognizer trained with MMAction2-compatible components.

## Intended use

Research and prototyping of human-activity recognition methods in appropriately authorized settings. Outputs may support a trained human's review workflow; they are not a clinical conclusion or automated alerting authority.

## Out-of-scope uses

- Diagnosis, treatment recommendation, or clinical triage
- Unconsented monitoring or workplace surveillance
- Identification of people, emotion inference, or assessment of mental state
- Deployment without privacy review, human oversight, and monitoring for error and bias

## Inputs and outputs

| Item | Description |
| --- | --- |
| Input | Pose/keypoint annotation sequences derived from restricted video |
| Output | One of 10 defined activity labels |
| Decision maker | A human reviewer; no autonomous clinical action |

## Performance and limitations

No recoverable metric log, confusion matrix, held-out evaluation record, or dataset split manifest was supplied. Do not infer accuracy from the checkpoint filename. Performance can be sensitive to camera placement, lighting, occlusion, population shift, annotation quality, pose-detector errors, class imbalance, and differences between staged and real care environments.

## Privacy, fairness, and safety

Pose-derived data can still be sensitive. A renewed implementation needs authorized data access, minimization of retained imagery, access controls, documented consent/notice practices, error analysis across relevant groups and environments, and a procedure for human review of uncertain or high-impact cases.

