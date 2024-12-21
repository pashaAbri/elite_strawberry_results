# Lit Review

## Index

Three-class Classification

1. [HateXplain (2020)](#hatexplain-original-paper---2020)
    - note: only Three-class Classification
    - [Results Summary](#results-summary)
    - [Model Architecture](#model-architecture)
    - [Evaluation Metrics](#evaluation-metrics)
2. [Masked Rationale Prediction (2022)](#masked-rationale-prediction-mrp---2022)
    - note: only Three-class Classification
    - [Results Summary](#results-summary-1)
    - [Model Architecture](#model-architecture-1)
3. [Breaking Free Transformer Models (2024)](#breaking-free-transformer-models---2024)
    - Context attribution approach
    - [Zero-Shot Classification Results](#zero-shot-classification-results)
    - [Text Classification Results](#text-classification-results)
        - Three-class Results
        - Binary Results
    - [Model Architecture](#model-architecture-2)
        - Context Attribution Layer
        - Base Models
        - Training Approach

Binary Classification

## HateXplain (original paper) - 2020

### Results Summary

| Model            | Accuracy | Macro F1 | AUROC |
|------------------|----------|----------|-------|
| CNN-GRU          | 0.627    | 0.606    | 0.793 |
| BiRNN            | 0.595    | 0.575    | 0.767 |
| BiRNN-Attn       | 0.621    | 0.614    | 0.795 |
| BiRNN-HateXplain | 0.629    | 0.629    | 0.805 |
| BERT             | 0.690    | 0.674    | 0.843 |
| BERT-HateXplain  | 0.698    | 0.687    | 0.851 |

### Model Architecture

Base Models

- CNN-GRU: Convolutional Neural Network with Gated Recurrent Unit
- BiRNN: Bidirectional Recurrent Neural Network
- BiRNN-Attn: BiRNN with Attention Mechanism
- BERT: Pretrained BERT base model

Enhanced Models (with rationale supervision)

- BiRNN-HateXplain: BiRNN with supervised attention using annotated rationales
- BERT-HateXplain: BERT with supervised attention using annotated rationales

### Evaluation Metrics

The paper evaluates models across three key dimensions:

1. Performance Metrics
    - Accuracy
    - Macro F1-score
    - AUROC (Area Under the Receiver Operating Characteristic curve) score

** AUROC is a metric that evaluates model performance across different classification thresholds

2. Bias Metrics
    - Subgroup AUC: Model performance on specific community subgroups
    - BPSN AUC: Background Positive, Subgroup Negative - measures false positives
    - BNSP AUC: Background Negative, Subgroup Positive - measures false negatives
    - GMB AUC: Generalized Mean of Bias - aggregate bias metric

3. Explainability Metrics
    - Plausibility:
        - IOU F1 Score
        - Token F1 Score
        - AUPRC Score
    - Faithfulness:
        - Comprehensiveness
        - Sufficiency

## Masked Rationale Prediction (MRP) - 2022

Key Innovation: The paper introduces Masked Rationale Prediction (MRP) as an intermediate task, which helps models learn
contextual reasoning similar to human annotators rather than relying on specific trigger words.

### Results Summary

| Model           | Accuracy | Macro F1 | AUROC |
|-----------------|----------|----------|-------|
| BERT            | 69.0     | 67.4     | 84.3  |
| BERT-HateXplain | 69.8     | 68.7     | 85.1  |
| BERT-MLM        | 70.0     | 67.5     | 85.4  |
| BERT-RP         | 70.7     | 69.3     | 85.3  |
| BERT-MRP        | 70.4     | 69.9     | 86.2  |

### Model Architecture

The paper introduces a two-stage training approach:

1. **Pre-finetuning Stage (MRP):**

- Model learns to predict masked rationale labels by considering surrounding context
- Uses both sentence tokens and rationale embeddings as input
- Rationale embeddings are partially masked during training

2. **Hate Speech Detection Stage:**

- Model is initialized with parameters from MRP stage
- Fine-tuned specifically for hate speech classification
- Does not use rationale labels during inference

Key Variants:

- BERT-MRP: Uses 50% masked rationales during pre-training
- BERT-RP: Uses 100% masked rationales (equivalent to pure token classification)
- BERT-MLM: Traditional masked language modeling pre-training

## Breaking Free Transformer Models - 2024

Key Innovation: Introduces concept space operators that project embeddings into task-specific latent spaces, improving
generalizability without fine-tuning the base models.

### Zero-Shot Classification Results

Train on IMDB, Test on HateXplain (Binary Classification):

| Model       | Accuracy | F1 Macro | Recall | Intra-Space weight |
|-------------|----------|----------|--------|--------------------|
| DistilBERT  | 0.6013   | 0.4450   | 0.0869 | N/A                |
| Space Model | 0.5821   | 0.5187   | 0.2698 | 0.001              |
| Space Model | 0.5977   | 0.5040   | 0.2007 | 0                  |

Note: Maps sentiment polarity to hate speech labels:

- Negative sentiment → Hate/Offensive (0)
- Positive sentiment → Normal (1)

### Text Classification Results

Three-class Classification Results

| Model              | Accuracy | F1 Macro | Precision | Recall |
|--------------------|----------|----------|-----------|--------|
| Space Model (BERT) | 0.5296   | 0.4304   | 0.5431    | 0.5296 |
| BERT               | 0.4485   | 0.3314   | 0.4471    | 0.4485 |

Binary Classification Results

| Model               | Accuracy | F1 Macro | Precision | Recall |
|---------------------|----------|----------|-----------|--------|
| Space-model (XLNet) | 0.8798   | 0.8797   | 0.8764    | 0.8824 |
| XLNet-base-cased    | 0.8160   | 0.8156   | 0.8421    | 0.7750 |
| Space-model (BERT)  | 0.8110   | 0.8108   | 0.8227    | 0.7899 |
| BERT-base-cased     | 0.6588   | 0.6555   | 0.6919    | 0.5649 |

### Model Architecture

The paper introduces "Space Model" architecture with several key components:

1. **Context Attribution Layer**

- Projects contextual embeddings into concept spaces
- Uses **_tanh_** activation for similarity measure
- Regularizes through Intra-Space loss

2. **Base Models Used**

- BERT base-cased
- XLNet base-cased
- DistilBERT

3. **Training Stages**

- No fine-tuning of the base model
- Only trains the context attribution operators
- Uses novel loss functions for concept space optimization

- Training Parameters
    - Maximum sequence length: 256-512
    - Batch size: Variable (4-32)
    - Learning rate: 2e-4 (basic), 1e-5 (state-of-the-art)
