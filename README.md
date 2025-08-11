
# 🛰️ SatMAE-India: Foundation + Agentic Vision System for Satellite Imagery

A scalable, modular pipeline that fine-tunes a pretrained SatMAE model on Indian satellite imagery and routes its spatial representations to task-specific agents for downstream applications like segmentation, classification, captioning, and change detection. The framework also integrates an LLM layer to interpret and polish outputs.

---

## 📌 Overview

Satellite imagery is central to applications in disaster management, agriculture, climate monitoring, and defense. Despite India's rich satellite ecosystem (ISRO, Bhuvan, Resourcesat, etc.), there's a lack of domain-specific foundational models.

This project builds:
- A fine-tuned **foundation model (SatMAE)** trained on Indian satellite imagery.
- A **multi-agent system** that branches into downstream tasks using task-specific models.
- An optional **closed/open-source LLM layer** to summarize or polish results in human-readable form.

---

## 🧱 Architecture

```text
[ Indian Satellite Image ]
            ↓
    [ Fine-Tuned SatMAE Encoder ]
            ↓
   [ Patch + CLS Embeddings ]
            ↓
  ┌─────────────────────────────┐
  │    Multi-Agent Controller   │
  └─────────────────────────────┘
       ↓       ↓       ↓      ↓
   Segment   Class.   Change  Caption
   Agent     Agent    Agent   Agent
       ↓       ↓       ↓      ↓
    Masks   Labels   DiffMap  Caption
            ↓
  ┌─────────────────────────────┐
  │    Optional LLM Polishing   │
  └─────────────────────────────┘
            ↓
       Final Output
````

---

## 🔍 Core Components

### 🔹 Foundation Encoder: SatMAE

A self-supervised Vision Transformer (ViT) model trained using masked autoencoding on satellite data. We fine-tune it using Indian datasets (Cartosat, FloodNet, Sentinel-1/2), enabling general spatial representation learning.

### 🔹 Multi-Agent System

Task-specific models, each using embeddings from the foundation model:

* **Segmentation Agent**: SegFormer/UPerNet
* **Classification Agent**: ViT head or linear probe
* **Change Detection Agent**: ChangeFormer
* **Captioning Agent**: BLIP / BLIP-2

### 🔹 LLM Layer (Optional)

Gemini, GPT-4, or LLaMA-based interface to interpret, summarize, and present results in natural language (e.g., damage summaries, land use reports).

---

## 🛰️ Indian Datasets

| Dataset        | Source              | Use Case                        |
| -------------- | ------------------- | ------------------------------- |
| Bhuvan / NRSC  | ISRO                | Land cover, urban, agriculture  |
| FloodNet India | IIIT-H / NRSC       | Disaster segmentation           |
| Sentinel-1/2   | ESA (India subset)  | SAR/Optical, multi-temporal     |
| ICRISAT / RSAC | Crop classification | Agriculture, vegetation mapping |

---

## 🗂️ File Structure

```
satmae-india-pipeline/
├── foundation/          # SatMAE encoder, fine-tuning, embedding extraction
├── agents/              # Segmentation, classification, captioning, change detection
├── orchestration/       # Agent controller, prompt manager, LLM interfaces
├── interface/           # APIs and streamlit-based frontends
├── data/                # Raw/processed datasets, utils
├── notebooks/           # Visualization and experimentation
├── config/              # YAML configuration files
├── docs/                # Diagrams, research notes, references
├── requirements.txt     # Dependencies
├── environment.yml      # Conda environment setup
└── README.md            # You are here
```

---

## ⚙️ Setup Instructions

```bash
# Clone the repository
git clone https://github.com/your-org/satmae-india-pipeline.git
cd satmae-india-pipeline

# Create conda environment
conda env create -f environment.yml
conda activate satmae-india

# Run the UI or API
python interface/streamlit_app.py
# or
uvicorn interface.api:app --reload
```

---

## 🧠 Tasks & Models

| Task             | Agent Model       | Input              | Output             |
| ---------------- | ----------------- | ------------------ | ------------------ |
| Segmentation     | SegFormer/UPerNet | Patch Embeddings   | Semantic Masks     |
| Classification   | ViT Head          | CLS Token          | Land/Scene Labels  |
| Change Detection | ChangeFormer      | Embeddings (T1/T2) | Binary Change Mask |
| Captioning       | BLIP-2            | Patch + CLS Tokens | Scene Description  |

---

## 📚 References

* **SatMAE**: [https://arxiv.org/abs/2306.05460](https://arxiv.org/abs/2306.05460)
* **SegFormer**: [https://arxiv.org/abs/2105.15203](https://arxiv.org/abs/2105.15203)
* **BLIP-2**: [https://arxiv.org/abs/2301.12597](https://arxiv.org/abs/2301.12597)
* **ChangeFormer**: [https://arxiv.org/abs/2201.01293](https://arxiv.org/abs/2201.01293)

---

## 👥 Contributors

* Siddartha A Yogesha
* Anshika Gupta 
* Riya Lall

---

## 📫 Contact

For queries, suggestions, or collaboration:
📧 `team@spaceai.in`
Open an issue on GitHub to start a discussion.

---

> *This project is developed as part of the PESU Research Foundation!*


