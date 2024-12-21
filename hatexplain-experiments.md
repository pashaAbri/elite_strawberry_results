# Experiment 3: Binary Classification with Confidence Scoring

## Experiment Design

To evaluate LLM performance on binary classification of problematic content (hate speech/offensive language) with
confidence scoring and optional explanations.

### Prompt

```text
You will classify numbered text items for problematic content. Each text is in a code block. Return classifications through the classify_texts function.    
    The function expects:
    1. "classifications" array: 1 for problematic content (hate speech/offensive language), 0 for non-problematic
    2. "confidence_scores" array: confidence level between 0 and 1 for each classification
    3. Optional "explanations" array with brief justifications

    Confidence Score Guidelines:
    - 0.9-1.0: Very high confidence (clear, unambiguous cases)
    - 0.7-0.9: High confidence (strong indicators present)
    - 0.5-0.7: Moderate confidence (some indicators but with ambiguity)
    - 0.3-0.5: Low confidence (unclear cases)
    - 0.0-0.3: Very low confidence (highly ambiguous cases)

    Classification Guidelines:
    - Evaluate each text independently
    - Look for explicit hate speech or clear offensive language
    - When in doubt, classify as non-problematic (0)
    - Double-check your classifications before submitting, especially for later items
    - Maintain consistent classification criteria throughout all texts
    - Assign lower confidence scores when context is ambiguous

    Example Input:
    Text 1:
    ```
    ["<user>", "i", "agree", "it", "is", "a", "very", "high", "chance", "this", "is", "a", "white", "person", "saying", "it"]
    ```

    Text 2:
    ```
    ["leftists", "are", "bad", "at", "marxmanship", "anders", "breivik", "required", "<number>", "shots", "to", "kill", "<number>"]
    ```

    Text 3:
    ```
    ["they", "are", "acting", "like", "animals", "in", "this", "situation"]
    ```

    Expected Output:
    {
        "classifications": [0, 1, 0],
        "confidence_scores": [0.85, 0.95, 0.45],
        "explanations": [
            "No problematic content, high confidence due to neutral language",
            "Contains explicit hate speech and reference to violence, very high confidence",
            "Potentially dehumanizing language but highly context-dependent, low confidence due to ambiguity"
        ]
    }

    Before returning: Verify all classifications and confidence scores are consistent, paying special attention to the last 25% of texts. Apply the same standards used in early texts to later ones.

    Provide only the function call response, maintaining text order.
```

### Models Evaluated + Results

#### 1. OpenAI GPT-4-mini

| Threshold | Accuracy | Precision | Recall | F1 Score |
|-----------|----------|-----------|--------|----------|
| 0.100     | 0.628    | 0.614     | 0.987  | 0.757    |
| 0.200     | 0.686    | 0.660     | 0.960  | 0.782    |
| 0.250     | 0.693    | 0.669     | 0.949  | 0.784    |
| 0.300     | 0.697    | 0.673     | 0.944  | 0.786    |
| 0.350     | 0.701    | 0.704     | 0.848  | 0.769    |
| 0.400     | 0.658    | 0.710     | 0.709  | 0.709    |
| 0.500     | 0.636    | 0.744     | 0.580  | 0.652    |
| 0.600     | 0.619    | 0.770     | 0.503  | 0.609    |
| 0.700     | 0.574    | 0.782     | 0.382  | 0.513    |
| 0.800     | 0.542    | 0.844     | 0.272  | 0.411    |
| 0.900     | 0.455    | 0.932     | 0.079  | 0.145    |
| 1.000     | 0.412    | 0.000     | 0.000  | 0.000    |

#### 2. Anthropic Claude-3-Sonnet (20240620)

| Threshold | Accuracy | Precision | Recall | F1 Score |
|-----------|----------|-----------|--------|----------|
| 0.100     | 0.637    | 0.620     | 0.992  | 0.763    |
| 0.200     | 0.696    | 0.667     | 0.966  | 0.789    |
| 0.250     | 0.709    | 0.680     | 0.955  | 0.794    |
| 0.300     | 0.719    | 0.691     | 0.946  | 0.798    |
| 0.350     | 0.732    | 0.715     | 0.906  | 0.799    |
| 0.400     | 0.694    | 0.722     | 0.780  | 0.750    |
| 0.500     | 0.640    | 0.762     | 0.564  | 0.648    |
| 0.600     | 0.617    | 0.802     | 0.462  | 0.587    |
| 0.700     | 0.559    | 0.836     | 0.311  | 0.454    |
| 0.800     | 0.491    | 0.883     | 0.156  | 0.265    |
| 0.900     | 0.454    | 0.927     | 0.078  | 0.144    |
| 1.000     | 0.412    | 0.000     | 0.000  | 0.000    |

#### 3. Meta LLama 3.1 70B (using togetherai endpoint)

| Threshold | Accuracy | Precision | Recall | F1 Score |
|-----------|----------|-----------|--------|----------|
| 0.100     | 0.615    | 0.605     | 0.993  | 0.752    |
| 0.200     | 0.646    | 0.628     | 0.978  | 0.765    |
| 0.250     | 0.659    | 0.638     | 0.970  | 0.770    |
| 0.300     | 0.679    | 0.656     | 0.957  | 0.778    |
| 0.350     | 0.694    | 0.681     | 0.904  | 0.777    |
| 0.400     | 0.682    | 0.682     | 0.861  | 0.761    |
| 0.500     | 0.666    | 0.722     | 0.702  | 0.712    |
| 0.600     | 0.597    | 0.760     | 0.460  | 0.573    |
| 0.700     | 0.551    | 0.835     | 0.295  | 0.436    |
| 0.800     | 0.483    | 0.864     | 0.144  | 0.247    |
| 0.900     | 0.468    | 0.889     | 0.109  | 0.194    |
| 1.000     | 0.412    | 0.000     | 0.000  | 0.000    |
