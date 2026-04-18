# RobustLLM: Robustness Assessment in Industrial Cyber-Physical Systems (CPS)

![Research Intensity](https://img.shields.io/badge/Research-Intensity-blue.svg)
![Python](https://img.shields.io/badge/Python-3.10+-yellow.svg)
![AI-Stability](https://img.shields.io/badge/Model-Llama--3.1--8B-green.svg)

## 📋 Overview
This repository contains a technical research artifact investigating the reliability of **Large Language Models (LLMs)** within high-stakes industrial environments. As factories transition to **Industry 4.0**, utilizing LLMs for predictive maintenance presents a critical challenge: **Input Perturbation.**

In this study, we subject the `Llama-3.1-8B-instant` model to a strictly deterministic gradient of stochastic sensor noise ($0.0\sigma$ to $1.2\sigma$) to identify mathematical "Collapse Boundaries." We compare raw inference accuracy against a denoised "Hybrid" pipeline using **Neuro-Symbolic architecture.**

---

## 📑 Research Artifacts
To ensure academic rigor, this research is available in several high-fidelity formats:

*   **📄 Final Research Brief:** [Technical Report (Google Docs)](https://docs.google.com/document/d/e/2PACX-1vSfi8u0vRqHtWb4Hr91xzOwsGzusmMSW0_MhI67FI6V2D-_jEVwUqbqUOWhJTr6jfK6VrdllT2KSIsC/pub)
*   **💻 Interactive Environment:** [Open in Google Colab](https://colab.research.google.com/#fileId=https%3A//storage.googleapis.com/kaggle-colab-exported-notebooks/ranimbouraoui3/quantify-llm-sensitivity-to-sensor-perturbation.fb568685-13d5-4e8e-8ae1-3447f9fc3474.ipynb%3FX-Goog-Algorithm%3DGOOG4-RSA-SHA256%26X-Goog-Credential%3Dgcp-kaggle-com%2540kaggle-161607.iam.gserviceaccount.com/20260417/auto/storage/goog4_request%26X-Goog-Date%3D20260417T230406Z%26X-Goog-Expires%3D259200%26X-Goog-SignedHeaders%3Dhost%26X-Goog-Signature%3D2fd2e0facb8ceb43eb9c56552dd392a89b1a1b7cda7d76aca163e51265f5267bd026fc8f6fe52e368c03b2dbc6616be07b787c22f9a5a59833b24e336dd007c95ef4e752dd37f8cf74295164e0774579a8b6a78ff2c4d2d570408d6e0679a34cfafc4c76f450baecffe6ce38a45b73bcdbe179897ececd4256c819af2c39f5e21eddc6e5af637aa2bf9569867bdd28a674968ec5552bab04dc03bda8297ee49a92a8d655785f614b1f8d1142ba69fb4cc50fd646360dafb8bb72e9aa5bfed71b5c1d836e7b0bec350bcbcbebafc65d5ea82776c76a403189293ba857902fab8077b88e52ed7c3ac3bbc10758ee413331a3b6acb00248f4a9a3b697acc021888c)
*   **📊 Dataset Source:** [AI4I 2020 Predictive Maintenance (UCI)](https://www.kaggle.com/datasets/stephanmatzka/predictive-maintenance-dataset-ai4i-2020)
*   **🛠 Inference Engine:** Groq API (High-speed LPU architecture)

---

## 🛠 Methodology & Technical Design
The experiment follows a standardized research protocol:

1.  **Stochastic Injection**: Systematic injection of Gaussian noise into binary machine-failure sensor operational features.
2.  **Pipeline Comparison**:
    *   **Baseline Pipeline**: Direct zero-shot inference on numerical sensor streams.
    *   **Filtered Pipeline**: Implementation of a **Moving Average bottleneck** to quantify SNR (Signal-to-Noise Ratio) stabilization effects.
3.  **Deterministic Calibration**: Used `temperature: 0.0` and fixed `NumPy random seed: 42` to ensure total scientific reproducibility across independent runs.

---

## 📊 Findings & Data Analysis
*   **Volatile Inference**: Empirical data reveals that between $0.0\sigma$ and $0.8\sigma$, LLM reasoning behaves non-monotonically, highly sensitive to micro-perturbations.
*   **Operational Collapse**: Identified a critical boundary at **1.2σ**, established as the current "Hard Reliability Limit" for zero-shot numerical parsing.
*   **Stability Persistence**: The deterministic results prove that LLMs function as pattern matchers rather than logical threshold reasoners in the context of Industrial CPS.

---

## 🚀 Configuration & Setup
This project utilizes the **Groq API** for high-speed inference. To ensure security, the API key is handled via environment secrets.

### **Option 1: Google Colab (Recommended)**
1.  Click the **🔑 (Secrets)** icon on the left sidebar.
2.  Add a secret named `API_key` and paste your Groq API token.
3.  Toggle **"Notebook access"** to ON.

### **Option 2: Kaggle**
1.  Go to `Add-ons` -> `Secrets`.
2.  Create a secret labeled `API_key`.
3.  Ensure **Internet** is enabled in the sidebar settings before running.

---

## 💻 Tech Stack
- **Data Engineering:** Python, Pandas, NumPy
- **Visual Analytics:** Seaborn, Matplotlib
- **AI Infrastructure:** Groq Cloud LPU, Meta Llama-3.1-8B

---

## 📜 References
- *Matzka, S. (2020). AI4I 2020 Predictive Maintenance Dataset.*
- *Meta AI (2024). Llama-3.1 Technical Report.*
- *Groq Cloud LPU (2025). Operational Latency & Inference Profiles.*
