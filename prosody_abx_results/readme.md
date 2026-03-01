# Prosodic ABX – Experimental Results

This directory contains prosodic ABX results on natural corpura for the paper:

> **Prosodic ABX: A Language-Agnostic Training-Free Metric of Prosodic Contrast in Speech Representations**

## Experimental Setting

- Metric: Prosody ABX error rate
- Distance: Cosine-DTW (as implemented in `fastabx`)
- Evaluation: Natural minimal-pair corpora

Full methodological details are described in the paper.

## Corpora Description

The three datasets correspond to different lexical prosodic contrasts and are derived from different speech corpora.

### English Stress (`stress`)

The stress results are computed on a natural minimal-pair corpus recorded specifically for this project.

- Speakers: 10 English speakers
- Content: Verb–noun minimal pairs embedded in sentence context
- Contrast type: Lexical stress

Details of the recording design, metadata, and preprocessing are documented in:

- `natural_corpus/English_Stress/readme.md`

within this OSF project.

---

### Japanese Pitch Accent (`pitch_accent`)

The pitch accent results are computed on a natural minimal-pair corpus recorded for this project.

- Speakers: 10 native Japanese speakers
- Content: Minimal pairs differing in pitch accent pattern
- Contrast type: pitch accent

Recording protocol, alignment details, and annotation format are documented in:

- `natural_corpus/Japanese_Pitch_Accent/readme.md`

within this OSF project.

---

### Mandarin Tone (`tone`)

The Mandarin tone results are computed on the publicly available **MCAE-Monosyllable** dataset.

- Speakers: 6 professional Mandarin speakers
- Content: Monosyllables with four lexical tones from MCAE-Monosyllable
- Contrast type: Lexical tone

The original dataset contains 422 monosyllables.  
Using the criterion that each tone of a syllable must be produced by at least 3 speakers, we retained 385 syllables for this evaluation.

## Directory Structure

- `prosody_abx_results/`
  - `stress/`
  - `pitch_accent/`
  - `tone/`

Each subdirectory corresponds to one dataset evaluating a distinct lexical prosodic contrast:

- `stress`: lexical stress (English)
- `pitch_accent`: pitch accent (Japanese)
- `tone`: lexical tone (Mandarin Chinese)

---

## What Each Dataset Contains

Each dataset directory contains:

- `{dataset}/`
  - `model_summary.tsv`
  - `layerwise/`
    - `tsv/`
    - `plots/`


---

### 1. `model_summary.tsv`

A tab-separated file summarizing model-level performance.

Columns:

- `model`: representation name (lowercase)
- `best_layer`: layer index with lowest across-speaker error rate  
  - `-` indicates only one across-speaker result (e.g., MFCC/FBANK)
- `best_error`: lowest across-speaker ABX error rate

The file is sorted in ascending order of `best_error`.

All 19 representations are included in this summary.

Representation sources in this release:

- From `torchaudio` pipeline:
  - Acoustic baseline:
    - `MFCC`
    - `FBANK`
  - English pretrain:
    - `WAVLM_BASE`
    - `WAVLM_BASE_PLUS`
    - `WAVLM_LARGE`
    - `HUBERT_BASE`
    - `HUBERT_LARGE`
    - `WAV2VEC2_LARGE`
    - `WAV2VEC2_BASE`
- From Hugging Face models:
  - Multilingual pretrain:
    - `wav2vec2-large-xlsr-53` -> `facebook/wav2vec2-large-xlsr-53`
    - `mhubert-147` -> `utter-project/mHuBERT-147`
  - Chinese pretrain:
    - `chinese-wav2vec2-large` -> `TencentGameMate/chinese-wav2vec2-large`
    - `chinese-wav2vec2-base` -> `TencentGameMate/chinese-wav2vec2-base`
    - `chinese-hubert-large` -> `TencentGameMate/chinese-hubert-large`
    - `chinese-hubert-base` -> `TencentGameMate/chinese-hubert-base`
  - Japanese pretrain:
    - `japanese-wav2vec2-base` -> `reazon-research/japanese-wav2vec2-base`
    - `japanese-wav2vec2-large` -> `reazon-research/japanese-wav2vec2-large`
    - `japanese-hubert-base-k2` -> `reazon-research/japanese-hubert-base-k2`
    - `japanese-hubert-large` -> `yky-h/japanese-hubert-large`

---

### 2. `layerwise/tsv/`

Contains per-layer across-speaker ABX error rates for each multilayer representation.

Each file (`{model}.tsv`)

is converted directly from the corresponding `fastabx` result file.

---

### 3. `layerwise/plots/`

Contains per-model layerwise plots (`{model}_layerwise.pdf`).

Each figure shows:

- X-axis: layer index
- Y-axis: prosodic ABX error rate

---
