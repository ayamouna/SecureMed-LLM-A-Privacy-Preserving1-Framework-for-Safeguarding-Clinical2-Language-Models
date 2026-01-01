# SecureMed-LLM: A Privacy-Preserving Framework for Safeguarding Clinical Language Models

**SecureMed-LLM** is a secure medical AI framework designed to generate **chest X-ray clinical reports** while ensuring **patient privacy**, **adversarial robustness**, and **clinical safety**.

This repository accompanies the master thesis:  
*"SecureMed-LLM: A Privacy-Preserving Framework for Safeguarding Clinical Language Models."*

---

## Table of Contents
1. [About the Project](#about-the-project)
2. [Why SecureMed-LLM is Useful](#why-securemed-llm-is-useful)
3. [System Architecture](#system-architecture-6-level-secure-pipeline)
4. [Models Used](#models-used)
5. [Key Features](#key-features)
6. [Dataset](#dataset)
7. [Results Summary](#results-summary)
8. [Methodology & Workflow](#methodology--workflow)
9. [Installation](#installation)
10. [Usage](#usage)
11. [Computational Resources](#computational-resources)
12. [Contributing](#contributing)
13. [License](#license)

---

## About the Project

SecureMed-LLM provides a **fully secure and privacy-preserving pipeline** for clinical report generation from chest X-ray images. It combines:

- Differential Privacy (DP-SGD)  
- Adversarial Fine-Tuning (FGSM, PGD, DeepFool)  
- PHI anonymization for text and images  
- IDS-LLM validation for clinical safety  
- ECIES encryption for secure report delivery  

---

## Why SecureMed-LLM is Useful

- Protects sensitive patient data during AI-driven clinical report generation.  
- Reduces risk of adversarial attacks and prompt injections.  
- Ensures generated reports are **clinically valid and safe**.  
- Provides a reproducible, GPU-compatible research framework for medical AI.

---

## System Architecture (6-Level Secure Pipeline)

1. **PHI Anonymization**  
   Removes personally identifiable information from medical text and images using **Med-Guard** and **Presidio**.

2. **Secure Transmission (TLS 1.3)**  
   Encrypts data transfer between systems using modern cryptography.

3. **LLM Processing**  
   Generates clinical **Findings** and **Impressions** using a fine-tuned **T5 model**.

4. **IDS-LLM Validation**  
   Ensures safety through rule-based checks, medical constraints, and anomaly detection.

5. **Report Encryption (ECIES)**  
   Encrypts reports before delivery to prevent tampering.

6. **Secure Delivery**  
   Sends encrypted reports exclusively to authorized clinicians.

---

## Models Used

- **BioMedCLIP**  
  - Purpose: Chest X-ray image encoding and vision-text feature alignment  
  - [HuggingFace Link](https://huggingface.co/microsoft/BiomedCLIP-PubMedBERT_256-vit_base_patch16_224)

- **T5-base**  
  - Purpose: Generation of Findings and Impressions sections  
  - [HuggingFace Link](https://huggingface.co/google/t5/t5-base)

---

## Key Features

- Adversarially robust report generation (**FGSM, PGD, DeepFool**)  
- Differential Privacy (**DP-SGD**, ε configurable)  
- PHI anonymization for text and images  
- Encrypted inference pipeline (**ECIES**)  
- IDS-LLM validation for clinical safety  
- Multi-level secure architecture  

---

## Dataset

- Enhanced **OPEN-I Chest X-ray dataset** (from Kaggle)  
  - **Train:** 93,347 image–report pairs  
  - **Validation:** 1,885 pairs  
  - **Test:** 1,541 images  
- Each study includes a chest X-ray and associated report (Findings + Impression)  
[Dataset Link](https://www.kaggle.com/datasets/financekim/curated-cxr-report-generation-dataset/data)

---

## Results Summary

| Metric | Before | After |
|--------|-------|------|
| Membership Inference Attack | 89% | 55% |
| Prompt Injection Defense | 37.5% | 78.3% |
| Adversarial Robust BLEU | 0.29 | 0.68 |
| Validation Pass Rate | - | 91.8% |

---

## Methodology & Workflow

1. **Environment Setup**  
   - Create Python virtual environment and install dependencies.

2. **Data Preparation and Anonymization**  
   - Text anonymization with **Med-Guard** and **Presidio**  
   - Image anonymization to remove identifying metadata

3. **Differential Privacy & Noise Injection**  
   - Training with **DP-SGD** to ensure privacy–utility trade-offs

4. **LLM Fine-Tuning**  
   - Visual features extracted using **BioMedCLIP**  
   - **T5-base** fine-tuned on anonymized reports  
   - Adversarial training with ~5% adversarial samples (**FGSM, PGD, DeepFool**)

5. **Model Selection**  
   - Based on robustness, BLEU score, and privacy leakage metrics

6. **Secure Deployment**  
   - Clinician submits a chest X-ray  
   - SecureMed-LLM generates report  
   - IDS-LLM validates report  
   - Report encrypted with clinician’s public key  
   - Clinician decrypts report using private key

---

## Installation

```bash
# Clone repository
git clone https://github.com/ayamouna/SecureMed-LLM-A-Privacy-Preserving1-Framework-for-Safeguarding-Clinical2-Language-Models.git
cd SecureMed-LLM-A-Privacy-Preserving1-Framework-for-Safeguarding-Clinical2-Language-Models
```
# Create virtual environment
python -m venv venv
source venv/bin/activate   # Linux / macOS
venv\Scripts\activate      # Windows


### Install dependencies
pip install -r requirements.txt

### Usage
Data Preprocessing & PHI Anonymization
python medguard_text_anonymizer.py
python medguard_image_anonymizer.py

### LLM Fine-Tuning & Adversarial Training
python finetune_llm_offline.py
python dp_training.py
python adversarial_training.py

### IDS-LLM Validation
python ids_validation.py
python visualize_ids_performance.py

### ECIES Encryption / Secure Delivery
python encrypt_report.py
python decrypt_report.py

### Computational Resources

GPU-enabled or cloud-based environments recommended (Google Colab, AWS, Azure)

CPU-only is suitable for preprocessing or small-scale testing

Some components (e.g., large-scale LLM fine-tuning) require GPUs due to computational constraints
