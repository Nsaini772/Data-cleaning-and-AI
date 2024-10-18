The program to clean the DNA genome data used for training and testing the AI model.


## Overview

This repository contains a Python script designed for processing genomic data. The script performs the following main tasks:

1. **Cleaning Accessible Sequence Data**: It reads a text file containing DNA sequences, calculates the average length of these sequences, and outputs truncated sequences to a new file.
2. **Identifying Negative Intervals**: It reads a BED file of accessible chromatin regions, identifies gaps between these regions, and writes the negative intervals to a new BED file.
3. **Refining Negative Data**: Using the average sequence length from the first part, it further processes another set of sequences, writing the results to a separate output file.

## Input Files

### 1. Accessible Sequence File (`PP1.txt`)
- **Format**: Plain text file where each sequence is represented on a new line. Lines starting with `>` are headers and are ignored.
- **Example Content**:
    ```
    >chr1 1000	5000 ATCGTACG
    >chr1 5600	7600 GCTAGCTA
    >chr1 8000	11000 ACGTGCTC
    ```

### 2. Chromatin Region File (`ENCFF852UQF.bed`)
- **Format**: BED file format, with tab-separated columns representing chromosome, start position, and end position of accessible regions.
- **Example Content**:
    ```
    >chr1	1000	5000
    >chr1	6000	8000
    >chr2	2000	3000
    ```

### 3. Non-Accessible Sequence File (`PN1.txt`)
- **Format**: Similar to the accessible sequence file (`PP1.txt`), this plain text file contains sequences on separate lines, ignoring lines that start with `>`. Get this fromt eh intervals of accessible file.
- **Example Content**:
    ```
    >chr1 5001	5599 ATCGTACG
    >chr1 7599	7999 GCTAGCTG
    ```

## Output Files

### 1. Positive Sequences File (`positive.txt`)
- **Format**: Plain text file containing truncated sequences along with their line numbers.
- **Example Output**:
    ```
    1: ATCG
    2: GCTA
    ```

### 2. Negative Intervals File (`negative.bed`)
- **Format**: BED file format that lists gaps between accessible regions as negative intervals.
- **Example Output**:
    ```
    >chr1	5001	5999
    >chr2	3001	3999
    ```

### 3. Refined Negative Output File (`output_negative_ext.txt`)
- **Format**: Plain text file that contains truncated sequences from the non-accessible sequence data, formatted with line numbers.
- **Example Output**:
    ```
    1: TGCAT
    2: ACGTA
    ```

## How to Run

1. Clone the repository to your local machine.
2. Update the file paths in the script to point to your input files.
3. Run the script using the command:
   ```
   python your_script.py
   ```
4. The output files will be generated in the specified paths.


