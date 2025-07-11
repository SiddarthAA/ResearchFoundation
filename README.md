satmae-india-pipeline/
│
├── README.md                     ← Overview, instructions, architecture, credits
├── requirements.txt             ← Core dependencies (PyTorch, Transformers, etc.)
├── setup.sh / environment.yml   ← Conda or bash setup script
├── .gitignore
│
├── config/
│   ├── config.yaml              ← Central config: paths, model settings, etc.
│   ├── satmae.yaml
│   ├── agents.yaml
│   └── llm_orchestration.yaml
│
├── data/
│   ├── raw/                     ← Raw datasets (Bhuvan, Sentinel, etc.)
│   ├── processed/               ← Preprocessed, patchified, ready-to-train data
│   ├── utils/                   ← Preprocessing scripts, patchifier, normalization
│   └── download_scripts/        ← Sentinel API, Bhuvan scrapers
│
├── foundation/
│   ├── model/                   ← SatMAE encoder wrapper + ViT utilities
│   ├── fine_tune.py             ← Fine-tuning SatMAE on Indian datasets
│   ├── extract_embeddings.py    ← Outputs CLS/Patch tokens for agents
│   └── train_satmae_helpers.py
│
├── agents/
│   ├── segmentation/
│   │   ├── train_seg.py
│   │   ├── model.py             ← SegFormer/UPerNet
│   │   └── infer_seg.py
│   ├── classification/
│   │   ├── train_cls.py
│   │   └── model.py             ← MLP/VIT-based head
│   ├── captioning/
│   │   ├── train_caption.py
│   │   └── model.py             ← BLIP-2 wrapper
│   └── change_detection/
│       ├── train_change.py
│       └── model.py             ← ChangeFormer
│
├── orchestration/
│   ├── controller.py            ← Calls agents based on task prompt
│   ├── prompt_templates.py      ← LLM prompt templates
│   ├── llm_wrapper.py           ← Gemini / GPT / LLaMA interface
│   └── multi_agent_manager.py   ← Agent routing, aggregation logic
│
├── interface/
│   ├── api.py                   ← FastAPI / Flask REST endpoints
│   ├── streamlit_app.py         ← Optional: Web dashboard
│   ├── batch_inference.py
│   └── map_visualizer.py        ← (Optional) Kepler/Mapbox integration
│
├── notebooks/
│   ├── EDA_indian_data.ipynb    ← Exploratory data analysis
│   ├── visualize_embeddings.ipynb
│   └── results_demo.ipynb
│
├── logs/
│   ├── training_logs/
│   └── eval_reports/
│
└── docs/
    ├── architecture_diagram.png
    ├── design.md
    └── research_notes.md
