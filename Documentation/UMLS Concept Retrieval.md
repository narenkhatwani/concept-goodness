# UMLS Concept Retrieval

## Step 1: Obtain a UMLS License

1. Visit the [UMLS License page](https://www.nlm.nih.gov/research/umls/licensedcontent/umlsknowledgesources.html).
2. Follow the instructions to apply for a license. Note that it's not difficult if you are in the USA.

## Step 2: Download MRCONSO.RRF

1. Download the file `MRCONSO.RRF` from the [UMLS Knowledge Sources](https://www.nlm.nih.gov/research/umls/licensedcontent/umlsknowledgesources.html).
2. Rename the file to `MRCONSO.TXT`.

> **Note:** The file is extremely large, containing approximately 13 million lines. It is recommended to use Notepad++ for editing as no other free editor can handle this file size.

## Step 3: Filter for English Terms

1. Open the `MRCONSO.TXT` file in Notepad++.
2. Delete all the lines that do not contain `|ENG|`.

## Step 4: Remove Unnecessary Columns

1. Identify the columns:
    - The first column is the CUI (Concept Unique Identifier).
    - The column containing the text string (term) is located after several other columns.
2. Delete all columns between the CUI and the text string, retaining only the CUI and the text string.

## Step 5: Remove Columns After the Text String

1. Delete all columns following the text string, leaving only the CUI and the text string.

## Step 6: Handling Multiple Names for the Same Concept

- Each row with the same CUI describes the same concept with a different name. For example, many chemical names may correspond to the same CUI.
- Ensure that each unique CUI is preserved along with its associated terms.

This process will help in retrieving UMLS concepts for your concept goodness project by filtering and cleaning the dataset effectively.

Next -> [[Semantic Type Filtering]]