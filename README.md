# ERGeoBench

Official repository for **ERGeoBench: A Comprehensive Benchmark for Embodied Reasoning and Geo-localization in Multimodal Large Language Models**.

ERGeoBench is a benchmark for evaluating whether multimodal large language models (MLLMs) can perform **vision-driven embodied geo-localization**. Unlike conventional geo-localization benchmarks that rely on a single image or a full panorama, ERGeoBench evaluates models under progressively interactive settings, including **Single-view**, **Panorama-view**, and **Embodied-view**. In the embodied setting, an agent actively controls yaw, pitch, and zoom to gather visual evidence and refine its location hypothesis over multiple steps.

> Code, prompts, evaluation scripts, annotation files, and panorama identifiers will be released here.

---

## Project Page

Project page: <https://kaiXuewen.github.io/ERGeoBench/>

Code repository: <https://github.com/kaiXuewen/ERGeoBench>

---

## News

- **2026-XX-XX**: Repository created. Full release coming soon.
- **2026-XX-XX**: Paper accepted to ICML 2026.
- **Coming soon**: Code, metadata, prompts, and evaluation scripts.

---

## Overview

ERGeoBench is designed to evaluate the following question:

> Can multimodal large language models actively explore a visual environment and progressively infer their geographic location?

The benchmark contains globally distributed street-view panoramas and evaluates models across four capability dimensions:

1. **Foundational Perception**  
   Fine-grained recognition of geographically informative visual cues, including architecture, signage, vegetation, terrain, and infrastructure.

2. **Spatial Awareness**  
   Understanding of viewpoint, direction, depth, relative position, and cross-view consistency.

3. **Commonsense Reasoning**  
   Inferring likely geographic, cultural, environmental, and functional context from visual evidence.

4. **Geo-localization**  
   Predicting country, city, street or area, and GPS coordinates.

ERGeoBench is intended as a diagnostic benchmark for studying location-aware multimodal agents, active perception, and interpretable geo-localization.

---

## Evaluation Settings

ERGeoBench evaluates models under three progressively interactive visual settings.

### Single-view

The model receives one fixed perspective view and must infer the location from limited visual evidence.

### Panorama-view

The model receives the full panoramic observation. This setting provides broad visual coverage but does not require sequential exploration.

### Embodied-view

The model acts as an embodied agent. At each step, it observes the current view, updates its hypothesis, and decides the next action through yaw, pitch, and zoom control.

The embodied setting evaluates whether a model can:

- actively select informative viewpoints,
- inspect fine-grained visual evidence,
- integrate evidence across multiple observations,
- maintain cross-view spatial consistency,
- update its location hypothesis over time.

---

## Release Plan

We plan to release the following components:

- [ ] Evaluation scripts for Single-view, Panorama-view, and Embodied-view settings
- [ ] Prompt templates for all settings
- [ ] Benchmark metadata and annotation files
- [ ] Street View panorama identifiers
- [ ] Model prediction files
- [ ] Metric computation scripts
- [ ] Data loading and preprocessing utilities
- [ ] Documentation for reproducing benchmark results
- [ ] Example inference scripts

---

## Data Release Policy

To support reproducibility while respecting data redistribution constraints, we will release **panorama identifiers and metadata** rather than redistributing raw Street View images.

The released metadata may include:

- sample ID,
- panorama ID,
- country label,
- city label,
- split information,
- task annotations,
- evaluation labels.

Users should retrieve corresponding visual observations through the official data access interfaces and follow the applicable terms of use of the original data providers.

A tentative metadata format is shown below:

```csv
sample_id,pano_id,country,city,split
000001,PLACEHOLDER_PANO_ID,Japan,Tokyo,test
000002,PLACEHOLDER_PANO_ID,France,Paris,test
```

The final metadata format will be released together with the evaluation scripts.

---

## Repository Structure

```text
ERGeoBench/
├── README.md
├── LICENSE
├── requirements.txt
├── data/
│   ├── pano_ids.csv
│   ├── metadata.json
│   └── annotations/
├── prompts/
├── scripts/
├── evaluation/
├── model_outputs/
├── docs/
└── assets/
```

---

## Installation

The code will be released soon. The expected installation process will be:

```bash
git clone https://github.com/kaiXuewen/ERGeoBench.git
cd ERGeoBench
conda create -n ergeobench python=3.10
conda activate ergeobench
pip install -r requirements.txt
```

---

## Quick Start

The evaluation scripts are under preparation. The expected usage will be:

```bash
# Single-view evaluation
python scripts/run_single_view.py \
    --metadata data/metadata.json \
    --prompt prompts/single_view_prompt.txt \
    --output model_outputs/single_view_predictions.json

# Panorama-view evaluation
python scripts/run_panorama_view.py \
    --metadata data/metadata.json \
    --prompt prompts/panorama_view_prompt.txt \
    --output model_outputs/panorama_view_predictions.json

# Embodied-view evaluation
python scripts/run_embodied_view.py \
    --metadata data/metadata.json \
    --prompt prompts/embodied_view_prompt.txt \
    --max_steps 15 \
    --output model_outputs/embodied_view_predictions.json
```

---

## Evaluation Metrics

ERGeoBench evaluates geo-localization using the **Geo-Localization Score (GLS)**, which combines semantic accuracy and geographic distance error.

The evaluation may include:

- country accuracy,
- city accuracy,
- street or area accuracy,
- Acc.@1km,
- Acc.@25km,
- Acc.@200km,
- Acc.@750km,
- Acc.@2500km,
- average localization error,
- median localization error,
- GLS.

Example usage:

```bash
python evaluation/evaluate_geoloc.py \
    --prediction model_outputs/embodied_view_predictions.json \
    --ground_truth data/annotations/geolocalization.json
```

---

## Prompt Template

The embodied prompt follows a closed-loop reasoning structure:

```text
Structured observation
    -> Evidence evaluation
        -> Hypothesis update
            -> Next-action planning
```

The prompt requires the model to:

- organize visual evidence into five categories,
- identify reliable and unreliable clues,
- maintain an explicit location hypothesis,
- explain uncertainty,
- choose verification-oriented actions,
- output a structured JSON response.

The full prompt template will be released in `prompts/`.

---

## Citation

If you find ERGeoBench useful, please cite our paper:

```bibtex
@inproceedings{xue2026ergeobench,
  title     = {ERGeoBench: A Comprehensive Benchmark for Embodied Reasoning and Geo-localization in Multimodal Large Language Models},
  author    = {Xue, Kaiwen and Wei, Tao and Ou, Zhonghong and Zhang, Guoxin and Lu, Kaoyan and Feng, Yu and Zhu, Yifan and Luo, Haoran},
  booktitle = {Proceedings of the International Conference on Machine Learning},
  year      = {2026}
}
```

The final BibTeX entry will be updated after the official proceedings metadata becomes available.

---

## License

The license for code, annotations, and metadata will be specified before the official release.

Tentatively:

- Code: Apache-2.0 or MIT License
- Metadata and annotations: CC BY-NC 4.0 or a similar non-commercial research license
- Raw imagery: not redistributed

Please check the final license files before using the released resources.

---

## Disclaimer

This repository is intended for academic research on multimodal reasoning, embodied perception, and geo-localization. Users are responsible for complying with the terms of use of any third-party data providers and APIs used to retrieve visual observations.

ERGeoBench does not redistribute raw Street View imagery. The benchmark release is designed to provide reproducible metadata, annotations, prompts, and evaluation code.

---

## Contact

For questions, please contact:

```text
Kaiwen Xue
Beijing University of Posts and Telecommunications
Email: YOUR_EMAIL
```

You can also open an issue in this repository after the official release.

---

## Acknowledgements

We thank all collaborators and reviewers for their constructive feedback on ERGeoBench. More details will be added in the final release.
