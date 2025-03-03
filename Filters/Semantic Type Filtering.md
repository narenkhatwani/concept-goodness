# Semantic Type Filtering

In this section, we outline the process for filtering UMLS concepts based on their semantic types. Semantic types provide a way to categorize and understand the nature of each concept within the UMLS framework.

## Step 1: Identify Relevant Semantic Types

1. **Review the List of Semantic Types:**
   - Obtain the list of all semantic types from the UMLS Metathesaurus documentation.
   - Select the semantic types relevant to your project. For example, you might be interested in filtering for medical conditions, chemicals, or anatomical structures.

2. **Example Semantic Types:**
   - **T047:** Disease or Syndrome
   - **T121:** Pharmacologic Substance
   - **T109:** Organic Chemical

## Step 2: Extract Semantic Type Information

1. **Download MRSTY.RRF:**
   - This file contains the mapping of CUIs to their semantic types.
   - Download it from the [UMLS Knowledge Sources](https://www.nlm.nih.gov/research/umls/licensedcontent/umlsknowledgesources.html).

2. **Open MRSTY.RRF:**
   - Use Notepad++ or a similar editor to open the file.
   - Each line contains a CUI followed by its associated semantic type(s).

## Step 3: Filter Concepts by Semantic Type

1. **Load MRCONSO.TXT and MRSTY.RRF:**
   - Load both files into your preferred data processing tool (e.g., Python, R, Excel).

2. **Merge Files on CUI:**
   - Join `MRCONSO.TXT` with `MRSTY.RRF` on the CUI column to associate each concept with its semantic type(s).

3. **Apply Semantic Type Filter:**
   - Filter the merged dataset to retain only the concepts with the desired semantic types.


| **Semantic Type Name**               | **Abbreviation** | **TUI** |         |
| ------------------------------------ | ---------------- | ------- | ------- |
| **Activities & Behaviors**           |                  |         |         |
| Activity                             | ACTI             | T052    |         |
| Behavior                             | BHVR             | T053    |         |
| Individual Behavior                  | INBE             | T055    |         |
| Social Behavior                      | SOBS             | T054    |         |
| **Anatomy**                          |                  |         |         |
| Body Location or Region              | BLOR             | T029    |         |
| Body Part, Organ, or Organ Component | BPOR             | T023    |         |
| Body Space or Junction               | BSJ              | T030    |         |
| Body Substance                       | BDSU             | T031    |         |
| Cell                                 | CEL              | T025    |         |
| Cell Component                       | CLC              | T026    |         |
| Tissue                               | TISU             | T024    |         |
| **Chemicals & Drugs**                |                  |         |         |
| Antibiotic                           | ANT              | T195    | Removed |
| Biologically Active Substance        | BACS             | T123    | Removed |
| Chemical                             | CHEM             | T103    | Removed |
| Clinical Drug                        | CLND             | T200    | Removed |
| Element, Ion, or Isotope             | EII              | T196    | Removed |
| Enzyme                               | ENZY             | T126    |         |
| Hormone                              | HORM             | T125    |         |
| Immunologic Factor                   | IMFT             | T129    |         |
| Organic Chemical                     | ORCH             | T109    | Removed |
| Pharmacologic Substance              | PHSC             | T121    | Removed |
| Receptor                             | RCPT             | T192    |         |
| Vitamin                              | VITA             | T127    |         |
| **Devices**                          |                  |         |         |
| Medical Device                       | DEVC             | T074    | Removed |
| Research Device                      | RESD             | T075    | Removed |
| **Disorders**                        |                  |         |         |
| Disease or Syndrome                  | DSYN             | T047    |         |
| Mental or Behavioral Dysfunction     | MENP             | T048    |         |
| Neoplastic Process                   | NEO              | T191    |         |
| Pathologic Function                  | PATF             | T046    |         |
| Sign or Symptom                      | SOSY             | T184    |         |
| **Geographic Areas**                 |                  |         |         |
| Geographic Area                      | GORA             | T083    |         |
| **Living Beings**                    |                  |         |         |
| Age Group                            | AGGP             | T100    |         |
| Amphibian                            | AMPH             | T011    | Removed |
| Animal                               | ANIM             | T008    | Removed |
| Bird                                 | BIRD             | T012    | Removed |
| Fish                                 | FISH             | T013    | Removed |
| Human                                | HUMN             | T016    |         |
| Mammal                               | MAMM             | T015    | Removed |
| Plant                                | PLNT             | T002    | Removed |
| Reptile                              | REPT             | T014    | Removed |
| **Objects**                          |                  |         |         |
| Manufactured Object                  | MNOB             | T073    |         |
| Physical Object                      | PHOB             | T072    |         |
| **Occupations**                      |                  |         |         |
| Biomedical Occupation or Discipline  | BMOD             | T091    |         |
| Occupation or Discipline             | OCCC             | T090    |         |
| **Phenomena**                        |                  |         |         |
| Biologic Function                    | BIF              | T038    |         |
| Environmental Effect of Humans       | EEHU             | T069    |         |
| Human-caused Phenomenon or Process   | HCPP             | T068    |         |
| Laboratory or Test Result            | LBTR             | T034    |         |
| Molecular Function                   | MOFT             | T044    |         |
| Natural Phenomenon or Process        | NPPT             | T070    |         |
| Physiologic Function                 | PHSF             | T039    |         |
| **Procedures**                       |                  |         |         |
| Diagnostic Procedure                 | DPCD             | T060    |         |
| Therapeutic or Preventive Procedure  | TOPP             | T061    |         |
| **Qualitative Concepts**             |                  |         |         |
| Functional Concept                   | FND              | T169    |         |
| Idea or Concept                      | CONC             | T078    |         |
| Quantitative Concept                 | QNCO             | T081    |         |
| **Relationships**                    |                  |         |         |
| Spatial Concept                      | SPCO             | T082    |         |
| Temporal Concept                     | TMCO             | T079    |         |
| **Structures**                       |                  |         |         |
| Chemical Viewed Structurally         | CHEM             | T104    | Removed |
| Element, Ion, or Isotope             | EII              | T196    |         |

Next -> [[Word Count of Concepts]]