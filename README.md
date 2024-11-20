# elite_strawberry_results

# Hate Speech Classification Results

This repository contains experimental results and analysis from comparing multiple Large Language Models (LLMs) on hate speech classification tasks using the [Davidson et al. (2017) dataset](https://github.com/t-davidson/hate-speech-and-offensive-language).

## Dataset Overview

The Davidson dataset classifies tweets into three categories:
- Hate Speech (0)
- Offensive Language (1)
- Neither (2)

Each tweet was labeled by multiple annotators, with the final classification determined by majority vote.

## Repository Structure

```
├── experiments.md                              # Detailed documentation of each experiment
├── davidson-dataset-distribution.md            # Distribution Results - Classification Distribution Comparison
├── confusion_matrices/                         # Visualization of model performance
│   ├── Anthropic - 3-5-sonnet-20240620.png     # Results from using Anthropic Model
│   ├── Open AI - gpt_4o_mini.png               # Results from using OpenAI Model
│   ├── Ollama - llama3.2latest.png             # Results from using Llama Model
│   └── ...
└── README.md
```

## Models Evaluated

The experiments compare three different LLM approaches:
- OpenAI GPT Models
- Anthropic Claude Models
- Ollama Llama 3.2 3B Model

## Experiment Framework

Each experiment tests different prompting strategies and configurations:
- Prompt engineering variations
- Use of examples and definitions
- Step-by-step reasoning requests
- Batch processing configurations
- Caching strategies

Key metrics tracked:
- Classification accuracy
- Model agreement with original labels
- Error patterns and bias analysis
- Processing efficiency

## Citation

If you use these results in your research, please cite:
```
Davidson, T., Warmsley, D., Macy, M. & Weber, I. (2017). 
"Automated Hate Speech Detection and the Problem of Offensive Language." 
ICWSM.
```