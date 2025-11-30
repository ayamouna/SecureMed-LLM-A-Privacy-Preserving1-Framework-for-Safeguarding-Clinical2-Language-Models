SecureMed-LLM: A Privacy-Preserving Framework for Safeguarding Clinical Language Models

This repository provides the full implementation of SecureMed-LLM, a secure medical AI pipeline designed to generate chest X-ray clinical reports while ensuring privacy, robustness, and safety.
System Architecture (6-Level Secure Pipeline)

SecureMed-LLM consists of a six-level security pipeline designed to protect patient data, ensure robust processing, and deliver safe clinical reports:

Level 1 — PHI Anonymization
Removes patient identifiers from text and images (Presidio + Med-Guard).

Level 2 — Secure Transmission (TLS 1.3)
Protects data transfer using modern cryptographic protocols.

Level 3 — LLM Processing
Generates clinical Findings and Impressions using the robust fine-tuned LLM.

Level 4 — IDS-LLM Validation
Ensures clinical safety using rule-based checks, parameter constraints, and anomaly detection.

Level 5 — ECIES Encryption
Encrypts the output report before delivery to prevent tampering or interception.

Level 6 — Secure Delivery
Sends the encrypted report to authorized clinicians only.

The system integrates:

Differential Privacy (DP-SGD)

Adversarial Fine-Tuning (FGSM, PGD, DeepFool)

PHI Anonymization for images and text

Encrypted Inference using ECIES

IDS-LLM Validation for safe clinical outputs

This project accompanies the master thesis:
“SecureMed-LLM: A Privacy-Preserving Framework for Safeguarding Clinical Language Models.”
The graphical abstract provides an overview of the complete SecureMed-LLM framework. It illustrates:

Local anonymization of patient images using Med-Guard

Secure data transmission before model processing

Robust LLM fine-tuning using adversarial training (FGSM, PGD, DeepFool) and Differential Privacy

IDS-LLM validation module that blocks unsafe or clinically inconsistent reports

ECIES encryption to protect the generated report

Key performance results, including BLEU improvements, privacy leakage reduction, and robustness gains

This visual summarizes the full privacy-preserving and safety-aware pipeline from input chest X-ray to the final secure clinical report.

⭐ Key Features

✔️ Adversarially robust report generation

✔️ Differential Privacy with ε = 3.0

✔️ PHI removal with Med-Guard + Presidio

✔️ Fully encrypted inference pipeline

✔️ IDS-LLM validation (rule-based + clinical + anomaly detection)

✔️ Secure multi-level architecture

📊 Results Summary

MIA Attack Reduction: 89% → 55% with DP

Prompt Injection Defense: 37.5% → 78.3%

Adversarial Robust BLEU: 0.29 → 0.68 after fine-tuning
Dataset

We used an enhanced version of the publicly available OPEN-I Chest X-ray dataset, downloaded from Kaggle.

Train: 93,347 pairs

Validation: 1,885 pairs

Test: 1,541 images

Each study includes a chest X-ray and a radiology report (Findings + Impression).

📥 Download Link:
https://www.kaggle.com/datasets/financekim/curated-cxr-report-generation-dataset/data

Validation Pass Rate: 91.8%
