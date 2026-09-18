# CIC-IDS2017 Network Traffic — Data Preparation

## Overview
This project focuses on cleaning and preparing network traffic data from the
CIC-IDS2017 dataset using Python and Pandas.

The project uses the Tuesday Working Hours dataset, containing benign traffic
along with FTP-Patator and SSH-Patator attack traffic.

## Objectives
- Understand the structure of network traffic data
- Clean inconsistent column names
- Handle missing values
- Handle infinite values
- Remove duplicate records
- Validate data types
- Validate traffic labels
- Analyze class distribution
- Document preprocessing decisions

## Dataset
**Dataset:** CIC-IDS2017  
**File:** `Tuesday-WorkingHours.pcap_ISCX.csv`  
**Source:** Canadian Institute for Cybersecurity, University of New Brunswick

Official dataset page:
https://www.unb.ca/cic/datasets/ids-2017.html

The original dataset is included in this repository.

## Tools & Technologies
- Python
- Pandas
- NumPy
- Matplotlib
- Google Colab
- GitHub

## Data Preparation
The following preprocessing steps were performed:
1. Inspected the dataset structure and data types.
2. Removed unnecessary whitespace from column names.
3. Identified and handled missing values.
4. Investigated and removed records containing undefined infinite values.
5. Removed duplicate records.
6. Validated numerical and categorical features.
7. Validated traffic labels.
8. Analyzed class distribution and identified class imbalance.

## Preprocessing Details
### Missing Values
201 missing values were found in `Flow Bytes/s`.

Investigation showed that these records had zero flow duration and zero
forward/backward packet bytes. The undefined rate values were represented as 0.

### Infinite Values
327 infinite values were found in `Flow Packets/s` and `Flow Bytes/s`,
affecting 264 records.

All affected records had zero flow duration. Since these rate calculations
were undefined, the 264 records were removed.

### Duplicate Records
24,019 duplicate records were identified and removed.

### Data Types
The dataset contains 78 numerical network-flow features and one categorical
target column, `Label`.

No unnecessary type conversions were applied.

### Traffic Labels
The dataset contains three traffic classes:
- BENIGN
- FTP-Patator
- SSH-Patator

## Results
| Metric | Result |
|---|---:|
| Original Records | 445,909 |
| Final Records | 421,626 |
| Columns | 79 |
| Numerical Features | 78 |
| Categorical Features | 1 |
| Missing Values | 0 |
| Infinite Values | 0 |
| Duplicate Records | 0 |
| Traffic Classes | 3 |

## Class Distribution
The cleaned dataset contains significantly more benign traffic than attack
traffic.

The original class distribution was preserved during data preparation.
Balancing techniques will be considered separately during the modeling stage.
