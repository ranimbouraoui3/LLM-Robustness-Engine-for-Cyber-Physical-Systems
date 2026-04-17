# RobustLLM: Robustness Assessment in Industrial Cyber-Physical Systems (CPS)

![Research Intensity](https://img.shields.io/badge/Research-Intensity-blue.svg)
![Python](https://img.shields.io/badge/Python-3.10+-yellow.svg)
![AI-Stability](https://img.shields.io/badge/Model-Llama--3.1--8B-green.svg)

## 📋 Overview
This repository contains a technical research artifact investigating the reliability of **Large Language Models (LLMs)** within high-stakes industrial environments. As factories transition to **Industry 4.0**, utilizing LLMs for predictive maintenance presents a critical challenge: **Input Perturbation.**

In this study, we subject the `Llama-3.1-8B-instant` model to a gradient of stochastic sensor noise ($0.0\sigma$ to $1.2\sigma$) to identify mathematical "Collapse Boundaries." We compare raw inference accuracy against a denoised "Hybrid" pipeline using **Neuro-Symbolic architecture.**

---

## 📑 Research Artifacts
*   **Final Report:** [Full Technical Research Brief (Google Docs)](https://docs.google.com/document/d/e/2PACX-1vSfi8u0vRqHtWb4Hr91xzOwsGzusmMSW0_MhI67FI6V2D-_jEVwUqbqUOWhJTr6jfK6VrdllT2KSIsC/pub)
*   **Artifact Type:** Experimental Pipeline & Robustness Analysis
*   **Inference Engine:** Groq API (High-speed LPU architecture)

---

## 🛠 Methodology & Technical Design
The experiment utilizes the **AI4I 2020 Predictive Maintenance Dataset** and follows a strictly deterministic methodology:

1.  **Stochastic Injection**: Injected synthetic Gaussian noise into operational features (Torque, Rotational Speed, Temperature).
2.  **Pipeline Comparison**:
    *   **Baseline Pipeline**: Zero-shot inference on raw un-processed sensor streams.
    *   **Filtered Pipeline**: Implementation of a **Moving Average bottleneck** to evaluate SNR (Signal-to-Noise Ratio) stabilization.
3.  **Parameter Locking**: Used `temperature: 0.0` and fixed `NumPy seeds` to ensure experimental reproducibility.

---

## 📊 Core Findings
*   **The Volatility Zone**: Empirical evidence suggests LLMs behave as stochastic reasoners between $0.0\sigma$ and $0.8\sigma$, oscillating between false positives and logic flips.
*   **Operational Boundary**: Identified a critical boundary at **1.2σ**, where signal integrity collapses, triggering total inference failure.
*   **Hybrid Gain**: Denoising pre-processing stabilizes baseline accurate detection but requires careful signal alignment to avoid over-smoothing relevant failure anomalies.

---

## 💻 Tech Stack
*   **Languages**: Python
*   **Data Science**: Pandas, NumPy, Seaborn, Matplotlib
*   **AI Infrastructure**: Groq REST API, Llama-3.1 (8B instant)
*   **Cloud Hosting**: Kaggle Notebooks

---

## 🚀 How to Reproduce
1.  **API Integration**:
    *   Go to `Add-ons` -> `Secrets`.
    *   Add key: `API_key`
    *   Value: `[Your Groq API Key]`
2.  **Environment Settings**:
    *   Ensure **Internet** is enabled in the Kaggle settings sidebar.
3.  **Run the script**:
    *   Execute the cells to generate the comparative tri-panel visualization.

---

## 🔭 Future Research
My ongoing investigation focuses on the development of **Deterministic Guardrails** to filter verbalized non-binary responses and the utilization of **Few-Shot Calibration** to enhance numerical inference accuracy without dedicated fine-tuning.

---

**References**
- *Matzka, S. (2020). AI4I 2020 Predictive Maintenance Dataset.*
- *Meta AI (2024). Llama-3.1 Technical Report.*
- *Groq Cloud LPU (2025). Model Latency & Inference Profiles.*
