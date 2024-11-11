# Experiments - Classification Prompt

## Experiment 1: OpenAI Meta-Prompt

Prompt:
```text
Classify the given text for hate speech and offensive language.

Analyze the text thoroughly to determine if it falls under the categories of hate speech or offensive language. Consider context, intent, and commonly recognized harmful language. Use clear criteria to guide this determination.

# Steps

1. **Comprehend the Text:** Read and understand the content and context of the provided text.
2. **Identify Hate Speech:** Check for elements that promote hatred, violence, or discrimination against a group or individual based on race, gender, ethnicity, religion, or other protected characteristics.
3. **Identify Offensive Language:** Look for any language that is vulgar, derogatory, or likely to offend the general public with its tone or subject.
4. **Determine Neither:** Verify if the text does not contain either hate speech or offensive language.
5. **Conclude:** Based on the analysis, determine which category or categories are applicable to the text.

# Output Format

Respond with a JSON object containing three boolean fields: 
- `hate_speech`: true if the text contains hate speech, false otherwise.
- `offensive_language`: true if the text contains offensive language, false otherwise.
- `neither`: true if the text contains neither hate speech nor offensive language, false otherwise.

# Examples

**Example 1:**

- **Input:** "All [group] people are evil and should be banned."
- **Output:** 
  '''json
  {
    "hate_speech": true,
    "offensive_language": false,
    "neither": false
  }
  '''

**Example 2:**

- **Input:** "This person's behavior was annoying and unprofessional."
- **Output:** 
  '''json
  {
    "hate_speech": false,
    "offensive_language": false,
    "neither": true
  }
  ''

**Example 3:**

- **Input:** "That's the stupidest thing I've ever heard."
- **Output:**
  '''json
  {
    "hate_speech": false,
    "offensive_language": true,
    "neither": false
  }
  '''

# Notes

- Ensure the analysis is context-sensitive as language might vary in offensiveness based on cultural or situational factors.
- Some language may belong to more than one category; ensure the JSON output accurately represents this by setting multiple fields to true if necessary.
```
- Created using OpenAI's meta-prompt generator (O1 model training methodology)
- Uses JSON output format
- Includes detailed steps and examples
- Requires context-sensitive analysis
- LLM Caching: No
- Asked for Explanation: No
- Step-by-Step: Yes

## Experiment 2: Basic Prompt
Prompt:
```text
Classify the following text for hate speech and offensive language. Return your answer as three numbers in the format [x,x,x] where:
- First number: 1 if hate speech, 0 if not
- Second number: 1 if offensive language, 0 if not
- Third number: 1 if neither, 0 if not Only one number can be 1, the others must be 0.
```
- Simple array format [x,x,x]
- No additional context or guidance
- LLM Caching: No
- Asked for Explanation: No
- Step-by-Step: No

## Experiment 3: Basic + Definitions
Prompt:
```text
Classify the following text for hate speech and offensive language. Return your answer as three numbers in the format [x,x,x] where:
- First number: 1 if hate speech, 0 if not
- Second number: 1 if offensive language, 0 if not
- Third number: 1 if neither, 0 if not
Only one number can be 1, the others must be 0.

Definitions:
- Hate Speech: Content expressing hostility or promoting violence against protected groups (race, religion, ethnicity, gender, sexual orientation, disability)
- Offensive Language: Content containing profanity, insults, or crude language that may be inappropriate
- Neither: Content that contains neither hate speech nor offensive language
```
- Adds clear definitions for each category
- Explicitly defines protected groups
- LLM Caching: No
- Asked for Explanation: No
- Step-by-Step: No
- Definitions Provided: Yes

## Experiment 4: Basic + Explanation Requirement
Prompt:
```text
Classify the following text for hate speech and offensive language. Provide your classification as three numbers in the format [x,x,x] where:
- First number: 1 if hate speech, 0 if not
- Second number: 1 if offensive language, 0 if not
- Third number: 1 if neither, 0 if not
Only one number can be 1, the others must be 0.

After the classification, provide a brief explanation of why you made this classification in the format:
Classification: [x,x,x]
Explanation: your explanation here
```
- Requires explanation for classification
- Structured output format
- LLM Caching: No
- Asked for Explanation: Yes
- Step-by-Step: No

## Experiment 5: Basic + Step-by-Step Analysis
Prompt:
```text
Classify the following text for hate speech and offensive language by following these steps:

1. First, check if the text targets any protected characteristics (race, religion, ethnicity, gender, sexual orientation, disability)
2. If yes and it expresses hostility or promotes discrimination, classify as hate speech [1,0,0]
3. If no, check if the text contains profanity, insults, or crude language
4. If yes, classify as offensive language [0,1,0]
5. If neither, classify as neither [0,0,1]

Return your classification as three numbers in the format [x,x,x] where:
- First number: 1 if hate speech, 0 if not
- Second number: 1 if offensive language, 0 if not
- Third number: 1 if neither, 0 if not
Only one number can be 1, the others must be 0.

Show your analysis by completing these steps:
1. Protected characteristics check: (yes/no)
2. Hostility/discrimination check: (if applicable)
3. Profanity/crude language check: (yes/no)
4. Final classification: [x,x,x]
```
- Guided decision process
- Sequential analysis steps 
- Documented reasoning requirements
- LLM Caching: No
- Asked for Explanation: No
- Step-by-Step: Yes

## Experiment 6: Simple JSON Format
```
Classify the following text as either hate_speech, offensive_language, or neither. 
   ...:         Return your answer in JSON format with boolean values
```
- Simple JSON format
- Minimal instructions
- LLM Caching: No
- Asked for Explanation: No
- Step-by-Step: No
