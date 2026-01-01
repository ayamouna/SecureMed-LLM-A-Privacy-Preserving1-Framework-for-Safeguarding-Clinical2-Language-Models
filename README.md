# SecureMed-LLM: A Privacy-Preserving Framework for Safeguarding Clinical Language Models

This repository provides the full implementation of **SecureMed-LLM**, a secure medical AI pipeline designed to generate chest X-ray clinical reports while ensuring **privacy**, **robustness**, and **clinical safety**.

This project accompanies the master thesis:  
*"SecureMed-LLM: A Privacy-Preserving Framework for Safeguarding Clinical Language Models."*

---

## System Architecture (6-Level Secure Pipeline)

1. **PHI Anonymization**: Removes patient identifiers from text and images (Presidio + Med-Guard).  
2. **Secure Transmission (TLS 1.3)**: Protects data transfer using modern cryptographic protocols.  
3. **LLM Processing**: Generates clinical Findings and Impressions using the robust fine-tuned LLM.  
4. **IDS-LLM Validation**: Ensures clinical safety using rule-based checks, parameter constraints, and anomaly detection.  
5. **ECIES Encryption**: Encrypts the output report before delivery to prevent tampering.  
6. **Secure Delivery**: Sends the encrypted report to authorized clinicians only.  

The system integrates:  
- Differential Privacy (DP-SGD)  
- Adversarial Fine-Tuning (FGSM, PGD, DeepFool)  
- PHI Anonymization for images and text  
- Encrypted inference using ECIES  
- IDS-LLM Validation for safe clinical outputs  

---

## Graphical Abstract

The graphical abstract illustrates the complete pipeline:  
- Local anonymization of patient data  
- Secure transmission  
- Robust LLM fine-tuning with adversarial training and Differential Privacy  
- IDS-LLM validation blocking unsafe or inconsistent reports  
- ECIES encryption to protect the generated report  
- Secure delivery to clinicians  

---

## Key Features

- Adversarially robust report generation  
- Differential Privacy (ε = 3.0, configurable)  
- PHI removal with Med-Guard + Presidio  
- Fully encrypted inference pipeline  
- IDS-LLM validation (rule-based + clinical + anomaly detection)  
- Secure multi-level architecture  

---

## Results Summary

| Metric | Before | After |
|--------|-------|------|
| Membership Inference Attack | 89% | 55% |
| Prompt Injection Defense | 37.5% | 78.3% |
| Adversarial Robust BLEU | 0.29 | 0.68 |
| Validation Pass Rate | - | 91.8% |

---

## Dataset

We used an enhanced version of the publicly available **OPEN-I Chest X-ray dataset**, obtained from Kaggle:

- **Train:** 93,347 image–report pairs  
- **Validation:** 1,885 pairs  
- **Test:** 1,541 images  

Each study includes a chest X-ray and a radiology report (Findings + Impression).

📥 **Download Link:**  
[OPEN-I Kaggle Dataset](https://www.kaggle.com/datasets/financekim/curated-cxr-report-generation-dataset/data)

---

## Installation

```bash
# Clone repository
git clone https://github.com/ayamouna/SecureMed-LLM-A-Privacy-Preserving1-Framework-for-Safeguarding-Clinical2-Language-Models.git
cd SecureMed-LLM-A-Privacy-Preserving1-Framework-for-Safeguarding-Clinical2-Language-Models
```
## Create virtual environment
python -m venv venv
source venv/bin/activate   # Linux / macOS
venv\Scripts\activate      # Windows
Usage

After installation, you can run scripts for:

Data Preprocessing & PHI Anonymization

python medguard_text_anonymizer.py
python medguard_image_anonymizer.py


LLM Fine-Tuning & Adversarial Training

python finetune_llm_offline.py
python dp_training.py
python adversarial_training.py


IDS-LLM Validation

python ids_validation.py
python visualize_ids_performance.py


ECIES Encryption / Secure Delivery

python encrypt_report.py
python decrypt_report.py

Computational Resources

Due to large LLMs, GPU-enabled or cloud-based environments are recommended:

Google Colab, AWS, Azure, or local GPU

CPU-only is limited to preprocessing or small-scale testing

# Install dependencies
pip install -r requirements.txt
