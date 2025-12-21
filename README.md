# SecureMed-LLM: A Privacy-Preserving Framework for Safeguarding Clinical Language Models

## Description
This repository provides the full implementation of **SecureMed-LLM**, a secure medical AI framework designed to generate chest X-ray clinical reports while ensuring **privacy preservation**, **robustness against adversarial attacks**, and **secure delivery** of clinical outputs.

The framework integrates privacy-preserving learning, adversarial robustness, clinical safety validation, and cryptographic protection into a unified multi-level secure pipeline.

This code accompanies the master thesis:  
**“SecureMed-LLM: A Privacy-Preserving Framework for Safeguarding Clinical Language Models.”**

---

## System Architecture (6-Level Secure Pipeline)
SecureMed-LLM follows a six-level security pipeline designed to protect patient data, ensure robust processing, and deliver safe clinical reports:

**Level 1 — PHI Anonymization**  
Removes personally identifiable information from medical images and text using **Med-Guard** and **Presidio**.

**Level 2 — Secure Transmission (TLS 1.3)**  
Protects data transfer using modern cryptographic protocols.

**Level 3 — LLM Processing**  
Generates clinical **Findings** and **Impressions** using a robust fine-tuned large language model.

**Level 4 — IDS-LLM Validation**  
Ensures clinical safety using rule-based checks, parameter constraints, and anomaly detection.

**Level 5 — Report Encryption (ECIES)**  
Encrypts the generated clinical report before delivery to prevent tampering or interception.

**Level 6 — Secure Delivery**  
Sends the encrypted report exclusively to authorized clinicians.

---

## Models Used

### BioMedCLIP
BioMedCLIP is used as the vision–language backbone for medical image understanding and multimodal alignment.

- Model: **BioMedCLIP**
- Purpose: Chest X-ray image encoding and visual–textual feature alignment
- Source: [BioMedCLIP on HuggingFace](https://huggingface.co/microsoft/BiomedCLIP-PubMedBERT_256-vit_base_patch16_224)
- Pretrained weights provided by the original authors

### T5 Language Model
A **T5-based language model** is used for clinical report generation.

- Model family: **T5**
- Version: **T5-base**
- Purpose: Generation of Findings and Impression sections
- Source: [T5-base on HuggingFace](https://huggingface.co/google-t5/t5-base)
- Fine-tuned on medical report data

---

## Key Features
- Adversarially robust report generation (FGSM, PGD, DeepFool)  
- Differential Privacy training using DP-SGD (ε = 3.0)  
- PHI anonymization for both images and text  
- Encrypted inference pipeline using ECIES  
- IDS-LLM validation for clinical safety  
- Secure multi-level system architecture  

---

## Graphical Abstract
The graphical abstract provides an overview of the complete SecureMed-LLM framework and illustrates:

- Local anonymization of patient images using Med-Guard  
- Secure data transmission prior to model processing  
- Robust LLM fine-tuning with adversarial training and Differential Privacy  
- IDS-LLM validation blocking unsafe or clinically inconsistent reports  
- ECIES encryption protecting the generated report  
- Key performance improvements in robustness and privacy  

This visual summarizes the full privacy-preserving and safety-aware pipeline from chest X-ray input to the final secure clinical report.

---

## Results Summary
- **Membership Inference Attack reduction:** 89% → 55% with Differential Privacy  
- **Prompt injection defense accuracy:** 37.5% → 78.3%  
- **Adversarial robust BLEU score:** 0.29 → 0.68 after fine-tuning  
- **Validation pass rate:** 91.8%  

---

## Dataset Information
The experiments use an enhanced version of the publicly available **OPEN-I Chest X-ray dataset**, obtained from Kaggle.

- Training set: 93,347 image–report pairs  
- Validation set: 1,885 pairs  
- Test set: 1,541 images  

Each study includes a chest X-ray image and an associated radiology report (Findings + Impression).

Dataset link:  
https://www.kaggle.com/datasets/financekim/curated-cxr-report-generation-dataset/data

---

## Code Information
The repository contains:

- Data preprocessing scripts  
- Model training and adversarial fine-tuning scripts  
- Privacy-preserving and anonymization modules  
- IDS-LLM validation components
- IDS-LLM Validation Module

This module validates generated clinical reports in SecureMed-LLM using:

Rule-based checks for forbidden terms and contradictions.

Clinical term verification to ensure medical accuracy.

Anomaly detection using Isolation Forest on sentence embeddings.

Computes IDS decisions, confusion matrix, and performance metrics.

Produces a visualization of pass rates for each validation module. 
- Evaluation and result analysis scripts
- ECIES Encryption Module
This module provides end-to-end encryption for clinical reports in SecureMed-LLM using ECIES (X25519 + AES-GCM). It allows:

Encrypting a report with the doctor’s public key.

Decrypting the report with the doctor’s private key.

Secure delivery of regenerated reports while maintaining patient privacy.

Dependencies: cryptography Python package

---

## Computational Resources
Due to the computational requirements of large language models (LLMs), it is recommended to run training and large-scale experiments using cloud-based or GPU-enabled environments:

- Training and fine-tuning were conducted using GPU resources.  
- Cloud platforms such as Google Colab, AWS, Azure, or similar environments are suitable.  
- Local execution without a GPU may be limited to preprocessing, evaluation, or small-scale testing.  

**Note:** Pretrained model weights are used where available to reduce computational cost.

---

## Installation

Clone the repository:

```bash
git clone https://github.com/ayamouna/SecureMed-LLM-A-Privacy-Preserving1-Framework-for-Safeguarding-Clinical2-Language-Models.git
cd SecureMed-LLM-A-Privacy-Preserving1-Framework-for-Safeguarding-Clinical2-Language-Models
