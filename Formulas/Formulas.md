# Concept Goodness Evaluation Formulas

In this document, we outline the formulas used to evaluate the concept goodness for UMLS terms based on various parameters. This process will help in assigning a value to each concept, ensuring a comprehensive and quantitative analysis.
## Parameters

1. **Refined Word Count (RWC)**
    - The word count after applying any refinement criteria.
    - Formula: \( RWC = \text{Count of refined words in the term} \)

2. **Frequency of Occurrence (FO)**
    - The frequency with which a term appears in PubMed or other relevant databases.
    - Formula: \( FO = \text{Count of occurrences in the database} \)

3. **Dictionary Presence (DP)**
    - A binary indicator of whether the term is found in a standard dictionary.
    - Formula: \( DP = 1 \text{ if the term is in the dictionary, else } 0 \)

4. **German Language Combinability (GLC)**
    - A score indicating how well the term combines with German language constructs.
    - Formula: \( GLC = \text{Score based on German language combinability} \)

## List of formulas:
- [[Formula 1]]
- [[Formula 2]]
- [[Formula 3 - (Current)]]