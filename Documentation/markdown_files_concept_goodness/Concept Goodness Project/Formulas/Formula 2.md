#  Length and Frequency
# umls-concept-goodness

## The wild idea to combine factor_1 and frequency of occurence into goodness

### Original Formula
The original formula for "Goodness" was:

$$
\text{Goodness} = 1 - \left( \frac{\text{Refined Word Count}}{\text{Longest Term Length}} \right)
$$

This formula measures the brevity of a term relative to the longest term in the dataset.

### Integrating PubMed Frequency
To incorporate the frequency of appearance in PubMed, you can modify the "Goodness" formula by including a factor that inversely scales with this frequency. Let's call the frequency of a term in PubMed \( f \), where \( f \) is normalized between 0 and 1 (with 0 being rare and 1 being common). One way to integrate this could be:

$$
\text{New Goodness} = \left( 1 - \left( \frac{\text{Refined Word Count}}{\text{Longest Term Length}} \right) \right) \times (1 - f)
$$

Here, \( (1 - f) \) will reduce the "Goodness" of more commonly occurring terms, enhancing the value of rarer terms.

### Implementation Example
To implement this formula, you need to:
1. **Calculate or retrieve \( f \), the frequency of each term in PubMed**. This could be a value between 0 and 1 based on the proportion of PubMed articles in which the term appears.
2. **Normalize this frequency if not already normalized**. If \( f \) isn't given as a normalized value, calculate it by dividing the frequency of each term by the frequency of the most common term.
3. **Integrate \( f \) into the "Goodness" calculation**.

Here’s a conceptual Python snippet assuming you have `df_digit_filter` with a column `PubMed_Frequency` that holds the raw frequency counts:
```python
import pandas as pd

# Sample data setup
df_digit_filter = pd.DataFrame({
    'Term': ['term1', 'term2', 'term3', 'term4'],
    'Refined_Word_Count': [2, 3, 4, 5],
    'PubMed_Frequency': [100, 150, 50, 300]  # Example frequency counts
})

# Normalize PubMed frequency
max_frequency = df_digit_filter['PubMed_Frequency'].max()
df_digit_filter['Normalized_Frequency'] = df_digit_filter['PubMed_Frequency'] / max_frequency

# Calculate longest term length
longest_term_length = df_digit_filter['Refined_Word_Count'].max()

# Calculate new goodness score
df_digit_filter['Goodness'] = (1 - (df_digit_filter['Refined_Word_Count'] / longest_term_length)) * (1 - df_digit_filter['Normalized_Frequency'])

# View the dataframe
print(df_digit_filter)
```


## Understanding "Goodness"

### 1. Brevity (Length of Term)
The formula incorporates the length of the term relative to the longest term in the dataset. Shorter terms are generally preferred because they are often more direct and less complex. This aspect of the formula is:

$$
1 - \left(\frac{\text{Refined Word Count}}{\text{Longest Term Length}}\right)
$$

- If a term is as short as possible, this component of the formula approaches 1.
- If a term is as long as the longest term, this component approaches 0.

### 2. Rarity (Frequency of Appearance in PubMed)
The formula adjusts the goodness based on how frequently the term appears in PubMed. Less frequent terms are given a higher value by the factor:

$$
1 - f
$$

where \( f \) is the normalized frequency:
- Rare terms (lower \( f \)) lead to a higher value of \(1 - f\), increasing the "Goodness".
- Common terms (higher \( f \)) lead to a lower value of \(1 - f\), reducing the "Goodness".

## Final "Goodness" Interpretation
- **Higher "Goodness" Score**: Indicates that a term is both relatively short and relatively rare in the literature. Such terms are likely to be more specific and unique, which might make them valuable additions to an ontology because they can provide precise and distinct knowledge that is not overly generalized.

- **Lower "Goodness" Score**: Suggests that a term either is too common (appears frequently in PubMed) or is relatively long (possibly overly verbose or complex), making it less ideal for ontology inclusion. Such terms might not enhance the ontology's precision or might already be well-represented in existing literature.

## Practical Application in Ontologies
In the context of building or enhancing an ontology:
- **Terms with High "Goodness"**:
  - Are likely to enhance the ontology’s descriptive power without adding redundancy.
  - Can help in covering niche or specific areas that are not already overcrowded with common terminology.

- **Terms with Low "Goodness"**:
  - Might not be necessary to include if they represent well-known, frequently discussed concepts unless their inclusion brings a new perspective or connection that is valuable.

## Example Use Case
Consider you are enhancing an ontology about medical conditions. A rare term like "Neurofibromatosis" might have a high "Goodness" score due to its specificity and relatively low occurrence in general literature, making it a strong candidate for inclusion. In contrast, a common term like "Hypertension" might have a lower "Goodness" score due to its high frequency in literature, suggesting careful consideration of what its inclusion would add to the ontology.


