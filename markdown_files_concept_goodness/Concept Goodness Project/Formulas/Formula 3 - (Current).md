# Weighted Average
# Concept Goodness Score Calculation

## Example Data

| CUI  | STR                       |
| ---- | ------------------------- |
| C001 | Acinetobacter Infections  |
| C002 | Franceschetti syndrome    |
| C003 | Extra Vascular Lung Water |
| C004 | Branching Enzyme          |
| C005 | MPTP                      |
## Step 1 : Word Count and Frequency of occurence 

This is the UMLS concepts with just the Word_Count and their Frequency of Occurence in PubMed Abstracts.

| CUI  | STR                       | Word_Count | Frequency_of_Occurrence |
| ---- | ------------------------- | ---------- | ----------------------- |
| C001 | Acinetobacter Infections  | 2          | 12767                   |
| C002 | Franceschetti syndrome    | 2          | 2886                    |
| C003 | Extra Vascular Lung Water | 4          | 2577                    |
| C004 | Branching Enzyme          | 2          | 2498                    |
| C005 | MPTP                      | 1          | 10388                   |
## Step 2 : German Equivalent of the Concepts

Finding the German_STR equivalent of the concepts:
#### Why ?

> If a two word phrase is ONE word in German, it is probably a good concept. Because German constructs loooong words from multiple nouns. - Dr Geller

| CUI  | STR                       | Word_Count | Frequency_of_Occurrence | German_STR                   | German_Equivalent_Rating |
| ---- | ------------------------- | ---------- | ----------------------- | ---------------------------- | ------------------------ |
| C001 | Acinetobacter Infections  | 2          | 12767                   | Acinetobacter-Infektionen    |                          |
| C002 | Franceschetti syndrome    | 2          | 2886                    | Franceschetti-Klein-Syndrom  |                          |
| C003 | Extra Vascular Lung Water | 4          | 2577                    | Extravaskuläres Lungenwasser |                          |
| C004 | Branching Enzyme          | 2          | 2498                    | Verzweigungsenzym            |                          |
| C005 | MPTP                      | 1          | 10388                   | MPTP                         |                          |

A problem I have here is **How do we assign scores to these terms ?**
 1. Assigning Scores Based on Criteria
- **Chemical names that are the same**: Score = 0.1
- **Two-word English terms with one German equivalent and other the same**: Score = 0.8 
- **Multi-word English terms with a single-word German equivalent**: Score = 0.9
- **General case**: Score = 0.5

**Scores for German Equivalence**:

- `Acinetobacter Infections` (Two-word similar structure): Score = 
- `Franceschetti syndrome` (Three word German equivalent): Score = 
- `Extra Vascular Lung Water` (Multi-word, two-word German equivalent): Score = 
- `Branching Enzyme` (Single German word): Score = 
- `MPTP` (same german equivalent): Score = 

## Step 3 :Existence in a Medical Dictionary (Merriam Webster API)

Considering a boolean value 0 - does not exist and 1 - exists in the Medical Dictionary, this makes the organic chemistry terms redundant and some other generic terms which don't have too much importance.

| CUI  | STR                       | Word_Count | Frequency_of_Occurrence | German_STR                   | German_Equivalent_Rating | Existence_in_dictionary |
| ---- | ------------------------- | ---------- | ----------------------- | ---------------------------- | ------------------------ | ----------------------- |
| C001 | Acinetobacter Infections  | 2          | 12767                   | Acinetobacter-Infektionen    |                          | 0                       |
| C002 | Franceschetti syndrome    | 2          | 2886                    | Franceschetti-Klein-Syndrom  |                          | 0                       |
| C003 | Extra Vascular Lung Water | 4          | 2577                    | Extravaskuläres Lungenwasser |                          | 0                       |
| C004 | Branching Enzyme          | 2          | 2498                    | Verzweigungsenzym            |                          | 0                       |
| C005 | MPTP                      | 1          | 10388                   | MPTP                         |                          | 1                       |

>**Should I consider anything else here ?**
## Step 4 :Normalization of the parameter values
### Frequency of Occurence and Word Count
Normalize the `Frequency of Occurrence` and `Word Count` to bring them to a common scale (0 to 1).

**Frequency of Occurrence**:

The widely used Normalization Formula
$$
[ \text{Normalized Frequency} = \frac{\text{Value} - \text{Min}}{\text{Max} - \text{Min}} ]
$$

**Word Count**:
What we initially agreed upon (w.r.t Longest Term Length)
$$
1 - \left( \frac{\text{Refined Word Count}}{\text{Longest Term Length}} \right)
$$
The widely used Normalization Formula
$$[ \text{Normalized Word Count} = \frac{\text{Value} - \text{Min}}{\text{Max} - \text{Min}} ]

$$
**German Equivalent Score**

**Existence in the medical dictionary score**



## Final Goodness Score
The formula for the Goodness Score (GS) is:

$$
GS = \frac{(Br \cdot w_1) + (FO \cdot w_2) + (GLM \cdot w_3) + (DP \cdot w_4)}{w_1 + w_2 + w_3 + w_4}

$$
Where:
- \(Br\): **Brevity**
- \(FO\): **Frequency of Occurrence**
- \(GLM\): **German Language Match**
- \(DP\): **Dictionary Presence**

- **Weights assigned to each factor =** 
$$w_1, w_2, w_3, w_4$$

# Next Step 

[[Human and Physician Survey (Iteration 1)]] 