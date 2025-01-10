# elite_strawberry_results

# HateXplain Dataset Analysis

## Results Summary

### Binary (2-Class) Evaluation

| Model                                             | Accuracy | Precision | Recall | F1 Score |
|---------------------------------------------------|----------|-----------|--------|----------|
| Space Model (BERT)                                | 0.8110   | 0.8227    | 0.7899 | 0.8108   |
| Space Model (XLNet)                               | 0.8798   | 0.8764    | 0.8824 | 0.8797   |
| Exp3 Zero Shot - 0.35 threshold - Claude-3-Sonnet | 0.732    | 0.715     | 0.906  | 0.799    |
| Exp3 Zero Shot - 0.35 threshold - GPT-4-mini      | 0.701    | 0.704     | 0.848  | 0.769    |
| Exp3 Zero Shot - 0.35 threshold - LLama 3.1 70B   | 0.694    | 0.681     | 0.904  | 0.777    |

### Binary (3-Class) Evaluation

| Paper                | Model              | Accuracy | Macro F1 | AUROC | Precision | Recall |
|----------------------|--------------------|----------|----------|-------|-----------|--------|
| HateXplain (2020)    | BERT-HateXplain    | 0.698    | 0.687    | 0.851 | -         | -      |
| MRP (2022)           | BERT-MRP           | 0.704    | 0.699    | 0.862 | -         | -      |
| Breaking Free (2024) | Space Model (BERT) | 0.5296   | 0.4304   | -     | 0.5431    | 0.5296 |
| Breaking Free (2024) | BERT               | 0.4485   | 0.3314   | -     | 0.4471    | 0.4485 |

| Experiment           | Model                                            | Accuracy | Macro F1 | AUROC  | Notes              |
|----------------------|--------------------------------------------------|----------|----------|--------|--------------------|
| Exp 9                | Llama 8.1 8B - base                              | 0.332    | 0.35     | -      |                    |
| Exp 9                | Llama 8.1 8B - fine tuned                        | 0.700    | 0.68     | -      |                    |
| Exp 9.1              | Llama 8.1 8B Instruct - base                     | 0.426    | 0.44     | -      |                    |
| Exp 9.1              | Llama 8.1 8B Instruct - fine tuned               | 0.704    | 0.69     | -      | 1 epoch            |
| Exp 9.2              | Llama 8.1 8B Instruct - base                     | 0.436    | 0.45     | -      |                    |
| Exp 9.2              | Llama 8.1 8B Instruct - fine tuned               | 0.708    | 0.69     | -      | 3 epochs           |
| Exp 10               | Llama 8.1 8B Instruct - base                     | 0.493    | 0.48     | -      |                    |
| Exp 10               | Llama 8.1 8B Instruct - fine tuned               | 0.634    | 0.61     | -      |                    |
| Exp 11.1             | Llama 8.1 8B Instruct - fine tuned               | 0.398    | 0.33     | -      | with probabilities |
| Exp 11.2             | Llama 8.1 8B Instruct - fine tuned               | 0.475    | 0.44     | -      | with probabilities |
| Exp 12               | Llama 8.1 8B - SequenceClassification - base     | 0.3136   | 0.5101   | 0.8796 |                    |
| Exp 12.1             | Llama 8.1 8B - SequenceClassification - finetune | 0.5913   | 0.5101   | 0.8241 |                    |
| Exp 12.2             | Llama 8.1 8B - SequenceClassification - finetune | 0.4831   | 0.3588   | 0.7523 |                    |
| Exp 13               | BERT - base                                      | 0.3136   | 0.1894   | 0.5257 |                    |
| Exp 13.1             | BERT - EnsembleSpaceModel                        | 0.4878   | 0.3729   | 0.6891 | 5 epochs           |
| Exp 13.2             | BERT - EnsembleSpaceModel                        | 0.4706   | 0.3747   | 0.6861 | 20 epochs          |
| Exp 13.3             | XLNET - base                                     | 0.3141   | 0.3092   | 0.4897 |                    |
| Exp 13.3             | XLNET - EnsembleSpaceModel                       | 0.5138   | 0.4722   | 0.6834 |                    |

## Dataset Overview

The [HateXplain dataset](https://paperswithcode.com/dataset/hatexplain) is a collection of annotated texts from Twitter
and Gab for hate speech detection. This original paper was accepted
at [AAAI 2021](https://ojs.aaai.org/index.php/AAAI/article/view/17745). This document explains the dataset composition
and preliminary analysis.

### Dataset Statistics

- Full dataset size: 20,148 entries
- Final splits size: 19,225 entries
- Missing entries: 923 entries (see [hatexplain-missing.md](hatexplain-missing.md) for details)

### Dataset Distribution

The 19,225 "valid" entries are distributed as follows:

- normal: 7,814 entries (40.64%)
- hatespeech: 5,933 entries (30.86%)
- offensive: 5,478 entries (28.49%)

### Lit Review Summary (Comprehensive Results Comparison)

Please see [hatexplain-lit-review](hatexplain-lit-review.md) for full details.

### Three-Class Classification Results

| Paper                | Model              | Accuracy | Macro F1 | AUROC | Precision | Recall |
|----------------------|--------------------|----------|----------|-------|-----------|--------|
| HateXplain (2020)    | CNN-GRU            | 0.627    | 0.606    | 0.793 | -         | -      |
| HateXplain (2020)    | BiRNN              | 0.595    | 0.575    | 0.767 | -         | -      |
| HateXplain (2020)    | BiRNN-Attn         | 0.621    | 0.614    | 0.795 | -         | -      |
| HateXplain (2020)    | BiRNN-HateXplain   | 0.629    | 0.629    | 0.805 | -         | -      |
| HateXplain (2020)    | BERT               | 0.690    | 0.674    | 0.843 | -         | -      |
| HateXplain (2020)    | BERT-HateXplain    | 0.698    | 0.687    | 0.851 | -         | -      |
| MRP (2022)           | BERT               | 0.690    | 0.674    | 0.843 | -         | -      |
| MRP (2022)           | BERT-HateXplain    | 0.698    | 0.687    | 0.851 | -         | -      |
| MRP (2022)           | BERT-MLM           | 0.700    | 0.675    | 0.854 | -         | -      |
| MRP (2022)           | BERT-RP            | 0.707    | 0.693    | 0.853 | -         | -      |
| MRP (2022)           | BERT-MRP           | 0.704    | 0.699    | 0.862 | -         | -      |
| Breaking Free (2024) | Space Model (BERT) | 0.5296   | 0.4304   | -     | 0.5431    | 0.5296 |
| Breaking Free (2024) | BERT               | 0.4485   | 0.3314   | -     | 0.4471    | 0.4485 |

### Binary Classification Results

| Paper                | Model               | Accuracy | Macro F1 | Precision | Recall |
|----------------------|---------------------|----------|----------|-----------|--------|
| Breaking Free (2024) | Space-model (XLNet) | 0.8798   | 0.8797   | 0.8764    | 0.8824 |
| Breaking Free (2024) | XLNet-base-cased    | 0.8160   | 0.8156   | 0.8421    | 0.7750 |
| Breaking Free (2024) | Space-model (BERT)  | 0.8110   | 0.8108   | 0.8227    | 0.7899 |
| Breaking Free (2024) | BERT-base-cased     | 0.6588   | 0.6555   | 0.6919    | 0.5649 |

### Zero-Shot Classification Results (Train on IMDB, Test on HateXplain)

| Paper                | Model                 | Accuracy | F1 Macro | Recall | Intra-Space weight |
|----------------------|-----------------------|----------|----------|--------|--------------------|
| Breaking Free (2024) | DistilBERT            | 0.6013   | 0.4450   | 0.0869 | N/A                |
| Breaking Free (2024) | Space Model (w=0.001) | 0.5821   | 0.5187   | 0.2698 | 0.001              |
| Breaking Free (2024) | Space Model (w=0)     | 0.5977   | 0.5040   | 0.2007 | 0                  |

Notes:

1. "-" indicates metric not reported in original paper
2. Results grouped by classification type and experimental setup
3. Some models appear in multiple papers with same architecture but different training approaches
4. Zero-shot results map sentiment polarity to hate speech labels (Negative → Hate/Offensive (0), Positive → Normal (1))

### Annotation Details

The HateXplain dataset employs a robust multi-annotator system to ensure reliable content classification:

- Each entry is independently labeled by **_three_** annotators
- Annotators provide:
    - Classification label (normal, offensive, or hate speech)
    - Target categories for problematic content
    - Rationales explaining their decisions
- Final classifications are aggregated from individual annotations
- Annotator agreement levels are tracked and considered in analysis

## Experimental Framework

The analysis framework is designed to evaluate multiple Large Language Models (LLMs) on problematic content (hate speech
and offensive) detection:

### Models Tested

- OpenAI GPT-4-mini
- Anthropic Claude-3-Sonnet (20240620)
- Meta LLama 3.1 70B

### Experiment Configuration + Results

Each experiment tracks multiple parameters:

- Prompt design and instruction sets
- Batch processing configurations
- Use of annotator rationales
- Inclusion of target categories
- Consideration of annotator agreement levels

## Results

Please see [hatexplain-experiments.md](hatexplain-experiments.md) for full details.


