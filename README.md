SecureMed-LLM: A Privacy-Preserving Framework for Safeguarding Clinical Language Models

This repository provides the full implementation of SecureMed-LLM, a secure medical AI pipeline designed to generate chest X-ray clinical reports while ensuring privacy, robustness, and safety.
The system integrates:

Differential Privacy (DP-SGD)

Adversarial Fine-Tuning (FGSM, PGD, DeepFool)

PHI Anonymization for images and text

Encrypted Inference using ECIES

IDS-LLM Validation for safe clinical outputs

This project accompanies the master thesis:
“SecureMed-LLM: A Privacy-Preserving Framework for Safeguarding Clinical Language Models.”

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
