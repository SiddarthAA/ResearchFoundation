satmae-india-pipeline/
│
├── README.md                       # Project overview, setup instructions, pipeline description
├── requirements.txt               # Python dependencies
├── setup.sh / environment.yml     # Conda or shell-based environment setup
├── .gitignore
│
├── config/                         # Configuration files for each module
│   ├── config.yaml
│   ├── satmae.yaml
│   ├── agents.yaml
│   └── llm_orchestration.yaml
│
├── data/                           # All data-related scripts and files
│   ├── raw/                        # Raw datasets (Bhuvan, Sentinel, FloodNet, etc.)
│   ├── processed/                  # Preprocessed and standardized inputs
│   ├── utils/                      # Patchifier, normalization, metadata extractors
│   └── download_scripts/          # APIs/scrapers for dataset downloads
│
├── foundation/                     # SatMAE model backbone
│   ├── model/                      # SatMAE and ViT encoder code
│   ├── fine_tune.py                # Fine-tuning on Indian imagery
│   ├── extract_embeddings.py       # Generate patch/CLS tokens for downstream agents
│   └── train_satmae_helpers.py
│
├── agents/                         # Task-specific model heads
│   ├── segmentation/
│   │   ├── train_seg.py
│   │   ├── model.py                # SegFormer/UPerNet
│   │   └── infer_seg.py
│   ├── classification/
│   │   ├── train_cls.py
│   │   └── model.py
│   ├── captioning/
│   │   ├── train_caption.py
│   │   └── model.py                # BLIP-2 interface
│   └── change_detection/
│       ├── train_change.py
│       └── model.py                # ChangeFormer wrapper
│
├── orchestration/                  # Multi-agent orchestrator + LLM interface
│   ├── controller.py               # Controls task-agent assignment
│   ├── prompt_templates.py
│   ├── llm_wrapper.py              # Gemini / GPT / LLaMA interfaces
│   └── multi_agent_manager.py
│
├── interface/                      # APIs and web-based dashboards
│   ├── api.py                      # REST API using FastAPI/Flask
│   ├── streamlit_app.py            # UI interface for demo
│   ├── batch_inference.py
│   └── map_visualizer.py           # Mapbox / Kepler visual output
│
├── notebooks/                      # Jupyter notebooks for exploration & visualization
│   ├── EDA_indian_data.ipynb
│   ├── visualize_embeddings.ipynb
│   └── results_demo.ipynb
│
├── logs/                           # Training logs and evaluation reports
│   ├── training_logs/
│   └── eval_reports/
│
└── docs/                           # Documentation and research references
    ├── architecture_diagram.png
    ├── design.md
    └── research_notes.md
