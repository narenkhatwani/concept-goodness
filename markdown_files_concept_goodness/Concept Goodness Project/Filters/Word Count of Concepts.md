In this section, we describe the process for calculating the word count for UMLS concepts. The word count is a fundamental parameter in evaluating the concept goodness and can provide insights into the brevity and clarity of terms.

## Step 1: Extract Terms from MRCONSO.TXT

1. **Download and Open MRCONSO.TXT:**
   - Ensure you have the `MRCONSO.TXT` file, which contains UMLS terms.
   - Open the file using Notepad++ or load it into a data processing tool (e.g., Python, R, Excel).

2. **Identify Relevant Columns:**
   - The primary columns of interest are the Concept Unique Identifier (CUI) and the term (text string).
   - Filter for English terms if not already done.

Next -> [[Frequency of Occurence in PubMED]]