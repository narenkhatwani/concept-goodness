# Frequency of Occurrence

In this section, we outline the process for calculating the frequency of occurrence of UMLS concepts in relevant databases. This parameter helps in understanding the prevalence and importance of each term within a specified context.

## Step 1: Identify Relevant Databases

1. **Select Databases:**
   - Determine which databases are relevant for your project. Common choices include PubMed, MEDLINE, and other specialized medical or scientific databases.

2. **Obtain Access:**
   - Ensure you have access to the chosen databases. This may require institutional access, subscriptions, or specific API keys.

## Step 2: Extract Term Frequencies

1. **Query the Database:**
   - Formulate queries to search for the occurrence of each UMLS term within the selected database.
   - Use appropriate search parameters and filters to ensure accuracy.

2. **Count Occurrences:**
   - For each term, count the number of times it appears in the database. This may involve parsing search results or using API-provided statistics.

## Step 3: Compile Frequency Data

1. **Create a Frequency Table:**
   - Compile the frequency data into a structured format, such as a table or spreadsheet.
   - Ensure each entry includes the term, its CUI, and the frequency of occurrence.

### Example Table Structure

| CUI       | Term                          | Frequency of Occurrence |
|-----------|-------------------------------|-------------------------|
| C0000039  | Dipalmitoylphosphatidylcholine| 45                      |
| C0000040  | Acetaminophen                 | 1200                    |
| C0000045  | Aspirin                       | 850                     |


Next ->[[German Equivalence]]