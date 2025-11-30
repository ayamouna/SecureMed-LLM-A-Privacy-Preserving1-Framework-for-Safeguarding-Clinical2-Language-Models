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

Validation Pass Rate: 91.8%
