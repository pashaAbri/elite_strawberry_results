## Missing Data Analysis

### Label Distribution

The 923 missing entries are distributed as follows:

- Undecided: 919 entries (99.57%)
- Offensive: 2 entries (0.22%)
- Hate speech: 2 entries (0.22%)

### Characteristics of Missing Data

1. **Predominant Label**: The vast majority (99.57%) of missing entries are labeled as "undecided", indicating low
   annotator agreement.

2. **Rationale Statistics**:
    - Average rationales per post: 0.01
    - Maximum rationales: 3
    - Minimum rationales: 0
    - This indicates that most missing entries lack rationale annotations.

3. **Source Distribution**: The missing entries come from both platforms:
    - Gab (e.g., '14971751_gab')
    - Twitter (e.g., '1179080731642990592_twitter')

## Explanation for Filtering

The data appears to have been filtered based on primarily two factors:

1. **Annotation Agreement**: Posts marked as "undecided" (919 out of 923) were removed from the final splits. This
   suggests a quality control measure where posts with low annotator agreement were excluded.

2. **Rationale Coverage**: The extremely low average of rationales (0.01 per post) indicates that these entries lack the
   explanatory annotations that are crucial for the dataset's purpose of explainable hate speech detection.

## Impact on Research

The filtering of these entries appears to be a deliberate choice to ensure dataset quality by:

- Removing entries where annotators couldn't reach consensus
- Excluding entries that lack proper rationale annotations
- Ensuring the remaining data is suitable for training explainable models

This filtering aligns with the dataset's goal of providing high-quality, explainable annotations for hate speech
detection.
