# ERGeoBench

Official repository for **ERGeoBench: A Comprehensive Benchmark for Embodied Reasoning and Geo-localization in Multimodal Large Language Models**.

This repository will release the code and metadata for ERGeoBench.

## Release Plan

We will provide:

- Evaluation scripts for Single-view, Panorama-view, and Embodied-view settings
- Prompt templates for embodied geo-localization
- Benchmark annotations and metadata
- Street View panorama identifiers for reproducing visual observations
- Model prediction files and evaluation utilities

## Data Release

To support reproducibility while respecting data redistribution constraints, we will release panorama identifiers and metadata rather than redistributing raw Street View images.

Users should retrieve the corresponding visual observations through the official data access interfaces according to the applicable terms of use.

## Repository Structure
ERGeoBench/
├── data/
│   ├── pano_ids.csv
│   ├── metadata.json
│   └── annotations/
├── prompts/
│   ├── single_view_prompt.txt
│   ├── panorama_view_prompt.txt
│   └── embodied_view_prompt.txt
├── scripts/
│   ├── run_single_view.py
│   ├── run_panorama_view.py
│   └── run_embodied_view.py
├── evaluation/
│   ├── compute_gls.py
│   ├── evaluate_geoloc.py
│   └── metrics.py
├── model_outputs/
└── docs/
Coming Soon
 Code release
 Panorama ID list
 Evaluation scripts
 Prompt templates
 Annotation files
 Model outputs
 Leaderboard
Citation

If you find this benchmark useful, please cite our paper:

@inproceedings{xue2026ergeobench,
  title     = {ERGeoBench: A Comprehensive Benchmark for Embodied Reasoning and Geo-localization in Multimodal Large Language Models},
  author    = {Xue, Kaiwen and others},
  booktitle = {International Conference on Machine Learning},
  year      = {2026}
}
