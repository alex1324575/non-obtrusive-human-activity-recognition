# Data governance and publication boundaries

## Publication policy for this repository

The repository excludes all raw video, derived pose annotations, training checkpoints, and prediction examples. It publishes only configuration and documentation that can describe the work without redistributing sensitive source material.

## Why this boundary matters

Healthcare-adjacent video can contain identifiable people, room layouts, clinical context, and sensitive behavior even if faces are blurred or the downstream model uses pose data. A claim that a system is non-obtrusive does not remove privacy, consent, institutional review, or data-license obligations.

## Before any future release

- Verify the dataset license and the research project's authorization scope.
- Confirm whether model weights and skeleton annotations are redistributable derivative artifacts.
- Remove identifiers and conduct a privacy review of sample media and logs.
- Obtain team and institutional permission for any poster, report, or branded material.
- Publish a data statement, access procedure, and contact route rather than the dataset itself.

