# SecureMed-LLM: A Privacy-Preserving Framework for Safeguarding Clinical Language Models

## Description
This repository provides the full implementation of SecureMed-LLM, a secure medical AI framework for chest X-ray clinical report generation. The system ensures privacy preservation, robustness against adversarial attacks, and secure delivery of clinical reports.

This code accompanies the master thesis:
"SecureMed-LLM: A Privacy-Preserving Framework for Safeguarding Clinical Language Models."

## System Architecture
SecureMed-LLM follows a six-level secure pipeline:

**Level 1 – PHI Anonymization**  
Removal of personally identifiable information from medical images and text using Med-Guard and Presidio.

**Level 2 – Secure Transmission**  
Secure data transfer using TLS 1.3.

**Level 3 – LLM Processing**  
Generation of Findings and Impressions using a fine-tuned large language model.

**Level 4 – IDS-LLM Validation**  
Validation of generated reports using rule-based constraints, clinical checks, and anomaly detection.

**Level 5 – Report Encryption**  
Encryption of generated reports using ECIES to prevent tampering or interception.

**Level 6 – Secure Delivery**  
Delivery of encrypted reports to authorized clinicians only.

## Key Features
- Adversarially robust report generation (FGSM, PGD, DeepFool)
- Differential Privacy training (DP-SGD, ε = 3.0)
- PHI anonymization for text and images
- Encrypted inference pipeline using ECIES
- IDS-LLM validation for clinical safety
- Multi-level secure architecture

## Dataset Information
The experiments use an enhanced version of the publicly available OPEN-I Chest X-ray dataset obtained from Kaggle.

- Training set: 93,347 image-report pairs
- Validation set: 1,885 pairs
- Test set: 1,541 images

Dataset link:
https://www.kaggle.com/datasets/financekim/curated-cxr-report-generation-dataset/data

## Code Information
The repository contains:
- Data preprocessing scripts
- Model training and adversarial fine-tuning scripts
- Privacy-preserving mechanisms
- IDS-LLM validation modules
- Evaluation and result analysis scripts

## Usage Instructions
1. Clone the repository:
```bash
git clone https://github.com/your-username/SecureMed-LLM.git
cd SecureMed-LLM
