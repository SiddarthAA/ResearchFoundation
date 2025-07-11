satmae-india-pipeline/<br>
│<br>
├── README.md                       # Project overview, setup instructions, pipeline description<br>
├── requirements.txt               # Python dependencies<br>
├── setup.sh / environment.yml     # Conda or shell-based environment setup<br>
├── .gitignore<br>
│<br>
├── config/                         # Configuration files for each module<br>
│   ├── config.yaml<br>
│   ├── satmae.yaml<br>
│   ├── agents.yaml<br>
│   └── llm_orchestration.yaml<br>
│<br>
├── data/                           # All data-related scripts and files<br>
│   ├── raw/                        # Raw datasets (Bhuvan, Sentinel, FloodNet, etc.)<br>
│   ├── processed/                  # Preprocessed and standardized inputs<br>
│   ├── utils/                      # Patchifier, normalization, metadata extractors<br>
│   └── download_scripts/          # APIs/scrapers for dataset downloads<br>
│<br>
├── foundation/                     # SatMAE model backbone<br>
│   ├── model/                      # SatMAE and ViT encoder code<br>
│   ├── fine_tune.py                # Fine-tuning on Indian imagery<br>
│   ├── extract_embeddings.py       # Generate patch/CLS tokens for downstream agents<br>
│   └── train_satmae_helpers.py<br>
│<br>
├── agents/                         # Task-specific model heads<br>
│   ├── segmentation/<br>
│   │   ├── train_seg.py<br>
│   │   ├── model.py                # SegFormer/UPerNet<br>
│   │   └── infer_seg.py<br>
│   ├── classification/<br>
│   │   ├── train_cls.py<br>
│   │   └── model.py<br>
│   ├── captioning/<br>
│   │   ├── train_caption.py<br>
│   │   └── model.py                # BLIP-2 interface<br>
│   └── change_detection/<br>
│       ├── train_change.py<br>
│       └── model.py                # ChangeFormer wrapper<br>
│<br>
├── orchestration/                  # Multi-agent orchestrator + LLM interface<br>
│   ├── controller.py               # Controls task-agent assignment<br>
│   ├── prompt_templates.py<br>
│   ├── llm_wrapper.py              # Gemini / GPT / LLaMA interfaces<br>
│   └── multi_agent_manager.py<br>
│<br>
├── interface/                      # APIs and web-based dashboards<br>
│   ├── api.py                      # REST API using FastAPI/Flask<br>
│   ├── streamlit_app.py            # UI interface for demo<br>
│   ├── batch_inference.py<br>
│   └── map_visualizer.py           # Mapbox / Kepler visual output<br>
│<br>
├── notebooks/                      # Jupyter notebooks for exploration & visualization<br>
│   ├── EDA_indian_data.ipynb<br>
│   ├── visualize_embeddings.ipynb<br>
│   └── results_demo.ipynb<br>
│<br>
├── logs/                           # Training logs and evaluation reports<br>
│   ├── training_logs/<br>
│   └── eval_reports/<br>
│<br>
└── docs/                           # Documentation and research references<br>
    ├── architecture_diagram.png<br>
    ├── design.md<br>
    └── research_notes.md<br>
