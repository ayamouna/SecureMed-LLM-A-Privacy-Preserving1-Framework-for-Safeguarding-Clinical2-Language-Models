# SecureMed-LLM-A-Privacy-Preserving-Framework-for-Safeguarding-Clinical-Language-Models
This repository provides the full implementation of a secure medical LLM pipeline, including Differential Privacy (DP-SGD), adversarial fine-tuning (FGSM, PGD, DeepFool), PHI anonymization for images and text, encrypted inference using ECIES, and an IDS-LLM validation layer for safety and consistency checking.
WHAT AD ALSO # SecureMed-LLM-A-Privacy-Preserving1-Framework-for-Safeguarding-Clinical2-Language-Models
This repository provides the full implementation of a secure medical LLM pipeline, including Differential Privacy (DP-SGD), adversarial fine-tuning (FGSM, PGD, DeepFool), PHI anonymization for images and text, encrypted inference using ECIES, and an IDS-LLM validation layer for safety and consistency checking.
# SecureMed-LLM: Privacy-Preserving Clinical LLM

SecureMed-LLM is a safeguarded large language model for generating chest X-ray clinical reports. It integrates:

- **Adversarial Robustness**: Fine-tuning with FGSM, PGD, and DeepFool attacks.
- **Differential Privacy**: DP-SGD with ε = 3.0 for optimal privacy-utility balance.
- **PHI Anonymization**: Microsoft Presidio + Med-Guard for patient data protection.
- **Encrypted Inference**: ECIES encryption for secure report delivery.
- **IDS-LLM Validation**: Rule-based, clinical parameters, and anomaly detection to ensure safe outputs.

## Results
- **Membership Inference Attack Reduction**: 89% → 55% with DP.
- **Prompt Injection Defense**: Accuracy increased from 37.5% → 78.3%.
- **Robust BLEU Scores under Adversarial Attacks**: 0.29–0.68 post fine-tuning.
- **Validation Pass Rate**: 91.8% across all modules.

## Repository Structure
SecureMed-LLM/
## Dataset

The project uses an enhanced version of the publicly available **OPEN-I Chest X-ray dataset**, obtained from Kaggle. 

- **Training:** 93,347 image–report pairs  
- **Validation:** 1,885 pairs  
- **Testing:** 1,541 images  

Each study includes a chest X-ray image and a corresponding textual radiology report describing **Findings** (anatomical/pathological observations) and **Impression** (clinical interpretation).

**Data Folder Structure**:

├── scripts/               
│   ├── train_securemed.py # Fine-tuning LLM with DP + adversarial training
│   ├── evaluate.py        # Evaluate model performance (BLEU, SSIM, PSNR)
│   ├── inference.py       # Generate clinical reports from X-ray images
│   └── README.md          # Explain purpose of each script
├── models/                
│   ├── securemed_checkpoint.pt # Fine-tuned model checkpoint
│   └── README.md               # Info about model versions and usage
├── utils/                 
│   ├── data_processing.py # Anonymization, image preprocessing, text cleaning
│   ├── adversarial.py     # FGSM, PGD, DeepFool attack functions
│   ├── privacy.py         # DP-SGD and Laplace noise functions
│   └── README.md          # How to use utility functions
├── notebooks/             
│   ├── experiments.ipynb  # Visualization, experiments, BLEU/SSIM plots
│   └── README.md          # Explanation of each notebook
├── assets/                
│   ├── figures/           # Diagrams, charts from paper
│   └── README.md          # Description of each figure/chart
├── README.md              # Main project overview, instructions, references
├── requirements.txt       # Python dependencies
├── LICENSE                # License file (e.g., MIT)
└── .gitignore             # Files/folders to ignore in Git
