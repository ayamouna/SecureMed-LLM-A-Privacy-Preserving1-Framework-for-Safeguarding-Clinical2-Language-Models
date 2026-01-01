# SecureMed-LLM: A Privacy-Preserving Framework for Safeguarding Clinical Language Models

This repository provides the full implementation of **SecureMed-LLM**, a secure medical AI framework designed to generate chest X-ray clinical reports while ensuring **privacy preservation**, **adversarial robustness**, and **clinical safety**.

This work accompanies the master thesis:  
*"SecureMed-LLM: A Privacy-Preserving Framework for Safeguarding Clinical Language Models."*

---

## System Architecture (6-Level Secure Pipeline)

SecureMed-LLM follows a six-level security pipeline designed to protect patient data, ensure robust processing, and deliver safe clinical reports:

1. **PHI Anonymization**  
   Removes personally identifiable information from medical text and images using **Med-Guard** and **Presidio**.

2. **Secure Transmission (TLS 1.3)**  
   Protects data transfer using modern cryptographic protocols.

3. **LLM Processing**  
   Generates clinical **Findings** and **Impressions** using a robust fine-tuned **T5 model**.

4. **IDS-LLM Validation**  
   Ensures clinical safety through rule-based checks, medical constraints, and anomaly detection.

5. **Report Encryption (ECIES)**  
   Encrypts generated reports to prevent tampering or interception.

6. **Secure Delivery**  
   Sends encrypted reports exclusively to authorized clinicians.

The system integrates:  
- Differential Privacy training (**DP-SGD**)  
- Adversarial Fine-Tuning (**FGSM, PGD, DeepFool**)  
- PHI Anonymization for text and images  
- Encrypted inference using **ECIES**  
- IDS-LLM validation for safe clinical outputs

---

## Models Used

- **BioMedCLIP**  
  Vision–language backbone for medical image understanding and multimodal alignment.  
  **Purpose:** Chest X-ray image encoding and visual–textual feature alignment  
  [HuggingFace Link](https://huggingface.co/microsoft/BiomedCLIP-PubMedBERT_256-vit_base_patch16_224)

- **T5-base**  
  Language model for clinical report generation (Findings + Impressions).  
  **Purpose:** Generation of radiology reports  
  [HuggingFace Link](https://huggingface.co/google/t5/t5-base)

---

## Key Features

- Adversarially robust report generation (**FGSM, PGD, DeepFool**)  
- Differential Privacy (**DP-SGD**, ε configurable)  
- PHI anonymization for both text and images  
- Encrypted inference pipeline using **ECIES**  
- IDS-LLM validation for clinical safety  
- Multi-level secure architecture

---

## Dataset

- Enhanced version of **OPEN-I Chest X-ray dataset**, from Kaggle:  
  - **Training:** 93,347 image–report pairs  
  - **Validation:** 1,885 pairs  
  - **Test:** 1,541 images  
- Each study includes a chest X-ray image and associated radiology report (Findings + Impression)  
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
   - Create a Python virtual environment and install dependencies.

2. **Data Preparation and Anonymization**  
   - Text anonymization with **Med-Guard** and **Presidio**  
   - Image anonymization to remove identifying metadata

3. **Differential Privacy and Noise Injection**  
   - Training with **DP-SGD** to evaluate privacy–utility trade-offs

4. **LLM Fine-Tuning**  
   - **BioMedCLIP** extracts visual features from chest X-rays  
   - **T5-base** fine-tuned on anonymized reports  
   - Adversarial training applied (**FGSM, PGD, DeepFool**) with ~5% adversarial samples

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

### Clone repository
```bash
git clone https://github.com/ayamouna/SecureMed-LLM-A-Privacy-Preserving1-Framework-for-Safeguarding-Clinical2-Language-Models.git
cd SecureMed-LLM-A-Privacy-Preserving1-Framework-for-Safeguarding-Clinical2-Language-Models
```
### Create virtual environment
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
