# SecureMed-LLM: A Privacy-Preserving Framework for Safeguarding Clinical Language Models
Description

This repository provides the full implementation of SecureMed-LLM, a secure medical AI framework designed to generate chest X-ray clinical reports while ensuring privacy preservation, robustness against adversarial attacks, and secure delivery of clinical outputs.

The framework integrates privacy-preserving learning, adversarial robustness, clinical safety validation, and cryptographic protection into a unified multi-level secure pipeline.

This code accompanies the master thesis:
“SecureMed-LLM: A Privacy-Preserving Framework for Safeguarding Clinical Language Models.”

System Architecture (6-Level Secure Pipeline)

SecureMed-LLM follows a six-level security pipeline designed to protect patient data, ensure robust processing, and deliver safe clinical reports:

Level 1 — PHI Anonymization
Removes personally identifiable information from medical images and text using Med-Guard and Presidio.

Level 2 — Secure Transmission (TLS 1.3)
Protects data transfer using modern cryptographic protocols.

Level 3 — LLM Processing
Generates clinical Findings and Impressions using a robust fine-tuned large language model.

Level 4 — IDS-LLM Validation
Ensures clinical safety using rule-based checks, medical constraints, and anomaly detection.

Level 5 — Report Encryption (ECIES)
Encrypts the generated clinical report before delivery to prevent tampering or interception.

Level 6 — Secure Delivery
Delivers encrypted reports exclusively to authorized clinicians.

Models Used
BioMedCLIP

BioMedCLIP is used as the vision–language backbone for medical image understanding and multimodal alignment.

Model: BioMedCLIP

Purpose: Chest X-ray image encoding and visual–textual feature alignment

Source: https://huggingface.co/microsoft/BiomedCLIP-PubMedBERT_256-vit_base_patch16_224

Pretrained weights provided by the original authors

T5 Language Model

A T5-based language model is used for clinical report generation.

Model family: T5

Version: T5-base

Purpose: Generation of Findings and Impression sections

Source: https://huggingface.co/google-t5/t5-base

Fine-tuned on anonymized medical report data

Key Features

Adversarially robust report generation (FGSM, PGD, DeepFool)

Differential Privacy training using DP-SGD (ε configurable)

PHI anonymization for both text and images

Encrypted inference pipeline using ECIES

IDS-LLM validation for clinical safety

Multi-level secure system architecture

Graphical Abstract

The graphical abstract illustrates the complete SecureMed-LLM pipeline, including:

Local anonymization of patient images and text

Secure data transmission

Robust LLM fine-tuning with adversarial training and Differential Privacy

IDS-LLM validation blocking unsafe or inconsistent reports

ECIES encryption protecting the generated report

Secure delivery to clinicians

Results Summary

Membership Inference Attack reduction: 89% → 55% with Differential Privacy

Prompt injection defense accuracy: 37.5% → 78.3%

Adversarial robust BLEU score: 0.29 → 0.68 after fine-tuning

Validation pass rate: 91.8%

Dataset Information

The experiments use an enhanced version of the publicly available OPEN-I Chest X-ray dataset, obtained from Kaggle.

Training set: 93,347 image–report pairs

Validation set: 1,885 pairs

Test set: 1,541 images

Each study includes a chest X-ray image and an associated radiology report (Findings + Impression).

Dataset link:
https://www.kaggle.com/datasets/financekim/curated-cxr-report-generation-dataset/data

Code Information

The repository contains:

Data preprocessing scripts

Model training and adversarial fine-tuning scripts

Privacy-preserving and anonymization modules

IDS-LLM validation components

ECIES-based encryption modules

Evaluation and result analysis scripts

Methodology and Workflow

SecureMed-LLM follows a staged experimental workflow:

Environment Setup
A Python virtual environment is created and dependencies are installed.

Data Preparation and Anonymization

Text anonymization using Med-Guard and Presidio

Image anonymization to remove identifying metadata and features

Differential Privacy and Noise Injection
Training is performed using DP-SGD with multiple ε values to evaluate privacy–utility trade-offs.

LLM Fine-Tuning

BioMedCLIP extracts visual features

T5-base is fine-tuned on anonymized reports

Adversarial training (FGSM, PGD, DeepFool) is applied

Approximately 5% adversarial samples are injected during fine-tuning

Model Selection
The best model is selected based on:

Robustness

BLEU score

Privacy leakage metrics

Secure Deployment

Clinician submits a chest X-ray

SecureMed-LLM generates a report

IDS-LLM validates the report

The report is encrypted with the clinician’s public key

The clinician decrypts it using their private key

Computational Resources

Due to the computational requirements of large language models (LLMs), GPU-enabled or cloud-based environments are recommended.

Training and fine-tuning were conducted using GPU resources

Suitable platforms include Google Colab, AWS, Azure, or similar services

Local execution without a GPU is suitable only for preprocessing or evaluation
## Installation

Clone the repository:
```bash
git clone https://github.com/ayamouna/SecureMed-LLM-A-Privacy-Preserving1-Framework-for-Safeguarding-Clinical2-Language-Models.git
cd SecureMed-LLM-A-Privacy-Preserving1-Framework-for-Safeguarding-Clinical2-Language-Models
Install dependencies:

pip install -r requirements.txt
