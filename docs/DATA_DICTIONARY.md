# Data Dictionary

## `results_all_runs.csv`

One row per architecture and random seed, extracted from rendered run-level tables in the supplied notebooks.

- `model`: model/architecture label.
- `seed`: random seed.
- `test_accuracy`: top-1 test accuracy as a fraction (e.g. 0.91 = 91%).
- `test_precision_macro`, `test_recall_macro`, `test_macro_f1`: macro-averaged classification metrics as fractions.
- `parameters`: number of trainable parameters.
- `model_size_mb`: reported model size in MB.
- `flops_g`: reported FLOPs in billions.
- `total_training_time_sec`: reported total training duration in seconds.
- `avg_epoch_time_sec`: reported average epoch duration in seconds.
- `inference_latency_ms`: reported latency per image in milliseconds.
- `inference_throughput_img_sec`: reported throughput in images/second.
- `peak_gpu_memory_mb`: peak GPU memory where visible in the notebook output.
- `source_notebook`: source notebook filename from which the displayed result was extracted.

Some model-specific columns may be blank if the notebook's saved display truncated that field. Blank values mean unavailable in the rendered output, not zero.

## `results_summary.csv`

Long-format summary with `model`, `metric`, `mean`, `std_sample`, and `n`. Mean and sample standard deviation are calculated from the visible run-level values in `results_all_runs.csv`; `n` is the number of non-missing observations used for that metric.

## `learning_logs_extracted.csv`

Epoch-level train/validation losses and accuracies recovered from saved notebook output lines. It may not contain every epoch if the notebook output stream was truncated.

## `generalization_gaps.csv`

Final-epoch train-validation accuracy and loss differences computed from the recoverable log rows. These are diagnostic derived values, not a replacement for the original full evaluation logs.
