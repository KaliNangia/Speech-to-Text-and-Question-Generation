# Repository Folder Structure

```text
Speech-to-Text-and-Question-Generation/
├── Atomic Notebooks/              # Modular, step-by-step notebooks (Steps 01 to 06) for debugging specific pipeline stages
│   ├── 01_Audio_Ingestion_and_Standardization.ipynb
│   ├── 02_Noise_Suppression.ipynb
│   ├── 03_Speaker_Diarization.ipynb
│   ├── 04_Timeline_Refinement_and_Serialization.ipynb
│   ├── 05_Audio_Splitting_and_Speaker_Isolation.ipynb
│   ├── 06_Whisper_Lora_Transcription_and_Gemini_Insights.ipynb
│   └── README.md
├── Fine Tuning Script/            # Scripts for Whisper model fine-tuning (Kaggle/local)
│   ├── Whisper_small_LORA_finetune.ipynb
│   ├── whisper-finetune-kaggle.ipynb
│   ├── whisper-finetune-large.ipynb
│   └── whisper-finetune-turbo.ipynb
├── Helper Notebook/               # Alternate model variations and helper scripts
│   ├── Kaggle_whisper_medium_finetune.ipynb
│   ├── Kaggle_whisper_turbo_finetune.ipynb
│   ├── whisper-finetune-Fixed.ipynb
│   ├── whisper-medium-updated (1).ipynb
│   └── whisper-turbo-latest (1).ipynb
├── Notebooks (Diff Models)/       # Alternate inference backends (Gemini and Gemma models)
│   ├── Gemini/
│   │   └── Gurmukhi-Devanagari Dual-Script Transcription Workflow.ipynb
│   └── Gemma/
│       ├── Gemma_4_12B_Multimodal_ASR.ipynb
│       └── Whisper_and_Gemma_4_12B_ASR_Pipeline.ipynb
├── Pipelines/                     # Combined end-to-end processing workflows
│   ├── Diarization Implementation NoteBook/
│   │   ├── Using PyAnnote/
│   │   ├── architecture.md
│   │   └── diarization_progress_report.md
│   ├── Noise Suppression And Diarization/
│   │   ├── Cleaned_Audio/
│   │   ├── Diarization_Outputs/
│   │   ├── colab_instructions.md
│   │   ├── noise-supp&diar.ipynb
│   │   └── pipeline_visualization.md
│   ├── Noise_Suppression_Diarization_Splitting_Gemini_API/
│   │   ├── noise_suppression_diarization_splitting_gemini_api_transcription.ipynb
│   │   └── README.md
│   ├── Noise_Suppression_Diarization_Splitting_Local_Whisper_LoRA/
│   │   ├── noise_suppression_diarization_splitting_local_whisper_transcription.ipynb
│   │   └── README.md
│   └── Noisesuppression/
│       └── Noise_suppression.ipynb
├── REPORTS/                       # Fine-tuned model evaluations and word error rates (WER)
│   └── FINE TUNED MODELS/
│       ├── Testing_finetuned_models.ipynb
│       ├── WER_Finetuned_Models_Report.md
│       └── [individual transcripts comparisons txt files]
├── Transcript Results/            # Sample outputs and transcription results by model
│   ├── Using Gemini Models/
│   ├── whisper-medium/
│   └── whisper-turbo/
├── README.md                      # Primary project readme
├── STT Architecture.png           # Pipeline architecture visual diagram
├── Contributions_Log.md           # Progress logs and updates
└── LICENSE                        # Repository license details
```
