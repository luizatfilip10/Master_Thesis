# Master Thesis Repository

This repository contains the data samples, annotation guidelines, prompt-development files, model outputs, notebooks, and evaluation results used for a master's thesis on LLM-based annotation of argumentation and narrative discourse.

The project investigates how large language models can be used to identify argumentative components and narrative spans in two different discourse types: TED Talk transcripts and short folktale-like stories from the STORAL dataset.

## Project overview

The thesis compares human annotation with LLM-generated annotation across two main tasks:

1. **Argumentation annotation**
   - TED Talks: explicit argumentative components
   - STORAL stories: implicit argumentative components inferred from narrative context

2. **Narrative annotation**
   - TED Talks: narrative spans classified according to rhetorical function

The workflow includes dataset sampling, human annotation guideline design, prompt optimization, final LLM evaluation, agreement analysis, semantic-similarity evaluation, and qualitative error analysis.

## Annotation layers

### TED argumentation layer

TED Talk transcripts are annotated for explicit argumentative components:

- `MC-EXP`: explicit major claim
- `C-EXP`: explicit claim
- `P-EXP`: explicit premise

### TED narrative layer

Narrative spans in TED Talks are classified according to their rhetorical function in the broader discourse. The labels include:

- `Exordium`
- `Narratio`
- `Propositio`
- `Confirmatio`
- `Peroratio`
- `Other`

### STORAL implicit argumentation layer

STORAL stories are annotated for implicit argumentative components. The supporting span is copied from the story, while the argumentative meaning is written as an explicit formulation:

- `MC-IMP`: implicit major claim
- `C-IMP`: implicit claim
- `P-IMP`: implicit premise

## Datasets

| Dataset | Description | Final sample |
|---|---|---:|
| TED | TED Talk transcripts sampled from a larger CSV dataset (Corral Jr. Miguel, 2020) | 20 transcripts |
| STORAL | Short stories sampled from merged train, validation, and test splits (Guan et al., 2022) | 20 stories |

The final annotation corpus contains 40 texts in total: 20 TED Talk transcripts and 20 STORAL stories.

## Sampling procedure

For both datasets, text length was used as the basis for sampling. Texts were considered eligible if their character length fell within one standard deviation of the mean length for that dataset. From the eligible subset, 20 texts were randomly sampled using random seed `42`.

| Dataset | Total loaded/merged rows | Mean length | Standard deviation | Eligible rows | Sample size | Random seed |
|---|---:|---:|---:|---:|---:|---:|
| TED | 4005 | 10032.02 characters | 5490.74 characters | 2578 | 20 | 42 |
| STORAL | 1779 | 1387.17 characters | 1024.98 characters | 1353 | 20 | 42 |

## Folder descriptions

| Folder | Description |
|---|---|
| `Annotation_Guidelines` | Contains the annotation guidelines used for the argumentation and narrative annotation layers. |
| `TED_dataset` | Contains the sampled TED Talk transcripts used in the final annotation corpus, including CSV files and individual text files. |
| `STORAL_dataset` | Contains the sampled STORAL stories used in the final annotation corpus, including CSV files and individual text files. |
| `Prompt_Optimization_ARG` | Contains files from the argumentation prompt-development phase for TED Talks, including test inputs, reference annotations, model outputs, and evaluation materials. |
| `Prompt_Optimization_NARR` | Contains files from the narrative prompt-development phase for TED Talks, including test inputs, reference annotations, model outputs, and evaluation materials. |
| `Prompt_Optimization_STORAL` | Contains files from the STORAL implicit-argumentation prompt-development phase. |
| `Final_ARG_Prompting` | Contains the final argumentation-prompt evaluation files for TED Talks. |
| `Final_NARR_Prompting` | Contains the final narrative-prompt evaluation files for TED Talks. |
| `Final_STORAL_Prompting` | Contains the final implicit-argumentation prompt evaluation files for STORAL stories. |
| `Notebooks` | Contains Jupyter notebooks used for sampling, prompting, result processing, agreement analysis, and evaluation. |
| `Results` | Contains final result tables, including Gamma agreement results, TED F1 scores, STORAL semantic-similarity results, and qualitative error-analysis summaries. |
| `Paper` | Contains final research paper on the study. |

## Evaluation

| Evaluation method | Purpose |
|---|---|
| Gamma agreement analysis | Used for span-based agreement between human annotators and between human annotations and model annotations. |
| F1-based evaluation | Used for TED model outputs across relaxed F1, overlap F1, character-offset F1, and sentence-level F1. |
| Semantic similarity evaluation | Used for STORAL implicit argumentation by comparing explicit formulations with SBERT and BERTScore-style similarity metrics. |
| Qualitative error analysis | Used to identify recurring model errors, including missed annotations, extra annotations, boundary errors, and label/function confusions. |

## How to use this repository

| Step | Action |
|---:|---|
| 1 | Start with `Annotation_Guidelines/` to understand the annotation scheme. |
| 2 | Inspect `TED_dataset/` and `STORAL_dataset/` to see the final sampled texts. |
| 3 | Use the `Prompt_Optimization_*` folders to review the prompt-development phase. |
| 4 | Use the `Final_*_Prompting/` folders to inspect final model inputs, outputs, and reference annotations. |
| 5 | Use `Notebooks/` to reproduce or inspect the evaluation workflow. |
| 6 | Use `Results/` for the final CSV result tables used in the thesis. |

## Notes on reproducibility

The notebooks are organized by evaluation stage rather than as a single end-to-end script. Some notebooks may require adjusting local paths depending on where the repository is cloned. The results CSV files are included so that the main reported results can be inspected without rerunning every experiment.

## Data and licensing notes

This repository contains sampled and derived research data used for a master's thesis. Before reusing or redistributing the data, check the licensing and citation requirements of the original TED and STORAL sources.

## Thesis context

This repository supports a master's thesis on computational annotation of argumentation and narrative discourse using Large Language Models. The main goal is to examine how well LLMs can reproduce human span annotations and explicit formulations across different discourse types and annotation layers.

## Repository structure

```text
Master_Thesis/
├── Annotation_Guidelines/
├── TED_dataset/
├── STORAL_dataset/
├── Prompt_Optimization_ARG/
├── Prompt_Optimization_NARR/
├── Prompt_Optimization_STORAL/
├── Final_ARG_Prompting/
├── Final_NARR_Prompting/
├── Final_STORAL_Prompting/
├── Notebooks/
├── Results/
└── README.md
```

Author: Luiza-Teodora Filip (s5183685)
