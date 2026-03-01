# Prosodic ABX Datasets and Results

This repository provides the natural minimal pair corpora and experimental results used in:

**Prosodic ABX: A Language-Agnostic Training-Free Metric of Prosodic Contrast in Speech Representations**

## Overview

- Evaluation metric: across-speaker Prosodic ABX error rate
- Languages/tasks:
  - English lexical stress
  - Japanese pitch accent
  - Mandarin lexical tone
- Representations evaluated: 19 (acoustic + SSL models)
- For the detailed Prosodic ABX methodology, please refer to the paper.

## Repository Contents

- `natural_corpus/`
  - `English_Stress/`: English lexical stress corpus 
  - `Japanese_Pitch_Accent/`: Japanese pitch-accent corpus 
- `prosody_abx_results/`
  - `stress/`: ABX results on English lexical stress
  - `pitch_accent/`: ABX results on Japanese pitch accent
  - `tone/`: ABX results on Mandarin lexical tone

## Documentation

- `natural_corpus/English_Stress/README.md`
- `natural_corpus/Japanese_Pitch_Accent/README.md`
- `prosody_abx_results/README.md`

## Dataset Snapshot

- `English_Stress`: 10 native speakers of American English, lexical stress contrasts in noun/verb sentence contexts
- `Japanese_Pitch_Accent`: 10 native Japanese (Kanto) speakers, 46 pitch-accent contrasts
- `Mandarin_Tone`: Mandarin tone evaluation based on MCAE-Monosyllable; 385 syllables retained after speaker-coverage filtering

## Model Coverage

The 19 representations include:

- Acoustic baselines: MFCC, FBANK
- S3M models (multilingual, English-pretrained, Chinese-pretrained, Japanese-pretrained)

Full model lists and per-model results are in:
- `prosody_abx_results/README.md`

## Results Included

For each task (`stress`, `pitch_accent`, `tone`), the released results include:

- `model_summary.tsv`: model-level summary with each representation's best layer and best ABX error
- `layerwise/tsv/`: per-layer ABX error values for multilayer representations
- `layerwise/plots/`: layerwise ABX curves in PDF format

Where to find details:

- Result file definitions, column meanings, and model source notes:
  - `prosody_abx_results/README.md`
- Corpus design, labels, and metadata definitions:
  - `natural_corpus/English_Stress/README.md`
  - `natural_corpus/Japanese_Pitch_Accent/README.md`
  - `prosody_abx_results/README.md` (For mandarin) 

## Citation

If you use this repository, please cite the corresponding paper.

`[Citation will be updated after review.]`
