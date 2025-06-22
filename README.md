# AI-Driven Ligand Design for Alzheimer’s Disease Targeted Exosome Delivery

## Project Overview

This project was developed for the **ChemLLMathon Hackathon** and aims to accelerate the **design of ligands** for **Alzheimer's-targeted exosome delivery** using fine-tuned large language models. By predicting key molecular properties and generating novel ligands, the system supports more effective drug delivery mechanisms to the brain.

---

## Problem Statement

Traditional Alzheimer’s therapies suffer from:

* Poor blood-brain barrier (BBB) penetration.
* Lack of targeting specificity.
* Inefficient or ineffective treatments.

**Exosomes** offer promise in targeted drug delivery, but ligand design remains a major bottleneck. This project applies AI to design ligands that:

* Bind selectively to AD biomarkers (Amyloid-β, tau).
* Penetrate the BBB effectively.
* Maintain stability in physiological conditions.

---

## Solution Architecture

**Input**:

* SMILES strings for molecules.
* Associated LogP and LogS property values.

**Output**:

* Fine-tuned ChemBERTa models predicting LogP and LogS.
* ChemGPT-generated SMILES with target LogP/LogS properties.

### Models Used:

* **ChemBERTa** for property prediction.
* **ChemGPT** for molecule generation.

---

## Technical Implementation

### 1. ChemBERTa Fine-Tuning

* Separate models for LogP and LogS prediction.
* Used Hugging Face tokenization.
* Trained with **AdamW** optimizer and dynamic LR scheduler.
* Cross-entropy loss for regression.

**Challenges**: Class imbalance impacted accuracy.

**Solution**: Weighted sampling and synthetic augmentation.

* RMSE improved from >1.5 to <1.0 for underrepresented property ranges.

### 2. ChemGPT Training

* Trained to generate valid SMILES sequences.
* 96% validity achieved.

**Enhancement**: Classified dataset into "desired" and "other" groups for better generative targeting.

---

## Dependencies

* Python
* PyTorch
* Hugging Face Transformers
* RDKit
* Scikit-learn
* Pandas, NumPy, Matplotlib

---

## Repository and Deployment

**GitHub Repo**: [ChemLLMathon\_fine\_tuning\_ChemBerta](https://github.com/HajerAbbas/ChemLLMathon_fine_tuning_ChemBerta)

**Environment**: Google Colab (T4 GPU)

**Deployment Potential**: Docker, AWS/GCP for scalable inference.

---

## Usage

### Property Prediction:

```python
from your_model_package import predict_logp, predict_logs
predict_logp("CCO")  # Predict LogP from SMILES
```

### Molecule Generation:

```python
from your_model_package import generate_smiles
generate_smiles(target_logp=2.5, target_logs=-1.0)
```

Future work includes building a web UI using React.

---

## Future Directions

* Larger and more diverse datasets.
* Web-based visualization and input.
* Enhanced model generalizability and interpretability.

---

## Contributors

* **Rodynah Alabdulhadi**: Presentation
* **Afnan Ajeebi**: AD-related data planning
* **Huda Alghamdi**: Molecular structure generation
* **Hajer Abbas**: Programming and AI model development
* **Fajer Hamzah**: Biochemical structure generation
* **Zainab S. Alghamdi**: Mentor (Chemical/Biomedical)
* **Salwa J. Kamal**: Mentor (Chemical)

---

## License

This project is open source and shared under an appropriate open-source license in line with ChemLLMathon policies.

---

## Contact

For questions or collaboration:

* [hajerabbas2024@gmail.com](mailto:hajerabbas2024@gmail.com)
