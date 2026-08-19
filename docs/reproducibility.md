# Reproducibility notes

## What was recovered

- An MMAction2-compatible SlowOnly ResNet-50 configuration.
- A ten-class action vocabulary.
- A checkpoint file named `best_acc_top1_epoch_89.pth`.
- A restricted 120-video training archive.
- A final report with historical evaluation results, but not the original metric logs.

## What is needed for a legitimate rerun

1. Obtain documented authorization for the source dataset and any derived pose annotations.
2. Recover or regenerate train/validation annotation files expected by the configuration:
   - `data/skeleton/custom_dataset_train.pkl`
   - `data/skeleton/custom_dataset_val.pkl`
3. Install an MMAction2 version compatible with the recovered configuration and its base runtime.
4. Place the configuration in the corresponding MMAction2 configuration tree, or update its `_base_` path deliberately.
5. Record package versions, GPU model, random seeds, splits, preprocessing settings, and evaluation metrics.

## Recovered training choices

The configuration samples 48-frame clips, applies pose heatmap generation, uses a 56 x 56 training crop and 64 x 64 validation resize, trains for 240 epochs, and evaluates top-1 accuracy. It uses SGD with momentum 0.9, weight decay 0.0001, a configured learning rate of 0.4, gradient clipping at norm 40, and cosine annealing.

## Recommended evaluation additions

Before reporting renewed results, add a split manifest, class counts, a confusion matrix, per-class precision/recall, confidence intervals where appropriate, camera/environment holdout tests, and an error review focused on occlusion and care-room variation.

## Historical versus renewed results

The team report documents 66.67% Top-1 and 83.33% Top-5 accuracy for the pose-based experiment, along with an 88% aggregate accuracy claim for the rule-based pipeline. Those figures describe the historical project evaluation; they must not be presented as results of a newly reproduced run unless the original split, inputs, environment, and logs are recovered or a new protocol is executed.
