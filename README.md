# CNN Architecture Benchmark — Results Repository

This repository contains **results and supporting research artifacts only** for the study:

> *A Controlled Multi-Dimensional Empirical Study of CNN Architectural Evolution: Accuracy, Generalization, Computational Complexity, Memory, and Inference Efficiency*

It intentionally does **not** include the complete training source code or the original Colab notebooks.

## Architectures evaluated

- LeNet-5
- AlexNet
- VGG-16
- GoogLeNet (Inception)
- ResNet-18

## Repository layout

```text
cnn-architecture-benchmark/
├── README.md
├── .gitignore
├── results/
│   ├── results_all_runs.csv
│   ├── results_summary.csv
│   ├── learning_logs_extracted.csv
│   ├── generalization_gaps.csv
│   ├── lenet_alexnet_classification_reports.csv
│   ├── googlenet_resnet18_classification_reports.csv
│   └── vgg16_per_class_report.csv
├── figures/
│   └── exported PNG figures from the executed notebooks
├── configs/
│   └── benchmark_config.yaml
└── docs/
    ├── DATA_DICTIONARY.md
    └── ARTIFACT_PROVENANCE.md
```

## Experimental protocol

The notebooks describe CIFAR-10 experiments using a fixed 45,000/5,000/10,000 train/validation/test split, 20 epochs, batch size 128, SGD with learning rate 0.1 and momentum 0.9, weight decay 0.0005, cosine annealing, and seeds 42, 43, and 44. Training augmentation includes random crop with padding and random horizontal flip; normalization uses CIFAR-10 channel statistics.

The LeNet-5/AlexNet and VGG-16 notebooks report PyTorch 2.11.0 with torchvision 0.26.0 on a Tesla T4. The GoogLeNet/ResNet-18 notebook reports PyTorch 2.10.0 with torchvision 0.25.0 on a Tesla T4. Exact CUDA/runtime versions are recorded in `configs/benchmark_config.yaml`. These differences should be considered when comparing runtime measurements.

## Results overview

The executed notebook outputs report ResNet-18 as the highest-accuracy successfully converged model in this benchmark. LeNet-5 is much smaller and has low measured inference latency. GoogLeNet has a relatively small parameter count but higher measured FLOPs and inference latency. VGG-16 remains near the 10-class chance baseline in the supplied run and is treated as a non-convergence diagnostic, not as evidence of its intrinsic capability.

See `results/results_summary.csv` for metric means and sample standard deviations where the run-level output data was available.

## Data and interpretation notes

- CSV files were extracted from the saved outputs of the supplied executed notebooks. No training was re-run to create this bundle.
- Some notebook outputs display truncated tables. Where a field was not present in the saved rendered output, it is left blank rather than inferred.
- `learning_logs_extracted.csv` contains epoch-level log lines that could be recovered from saved notebook output streams.
- `generalization_gaps.csv` is calculated from the final epoch logs recovered from those outputs. It should be interpreted as an output-derived diagnostic.
- Figures are exported from embedded notebook output images. Their names are descriptive labels based on the notebook cell that produced them.
- CIFAR-10 is not redistributed.
- Model checkpoints and the full source notebooks are not included.

## Reproducibility limitations

This is a results/artifacts repository, not a self-contained executable reproduction package. The source notebooks and training implementation are intentionally excluded. Runtime measurements are sensitive to hardware, library versions, and implementation details. VGG-16 did not converge under the supplied training recipe and should not be ranked as a successfully trained model.

## Citation

Please cite the accompanying paper when using or discussing these results. Add the final bibliographic citation here once publication details are available.

**Paper title:** *A Controlled Multi-Dimensional Empirical Study of CNN Architectural Evolution: Accuracy, Generalization, Computational Complexity, Memory, and Inference Efficiency*

**Repository URL:** Add the GitHub URL after publishing.
