# Speech-to-Text and Question Generation

A comprehensive workflow for converting speech audio to text and generating questions using fine-tuned Whisper models. This project processes audio files collected during ANNAM outreach programs to extract and analyze speech content.

## Overview

This repository contains tools and scripts for:
- **Speech-to-Text (STT)**: Converting audio files to transcribed text using OpenAI's Whisper model
- **Question Generation**: Generating questions from transcribed content
- **Fine-tuning**: Optimizing Whisper models for specific languages and domains (e.g., Punjabi)

The project specifically focuses on processing audio data from ANNAM (outreach initiatives) programs and includes fine-tuning capabilities using LoRA (Low-Rank Adaptation) for efficient model optimization.

## Features

- **Whisper-based STT**: State-of-the-art speech recognition using OpenAI's Whisper model
- **LoRA Fine-tuning**: Efficient parameter-efficient fine-tuning using Low-Rank Adaptation
- **Punjabi Language Support**: Pre-configured for Punjabi language transcription
- **Batch Processing**: Process multiple audio files efficiently
- **Dataset Integration**: Works with Hugging Face datasets for easy data management
- **Quantization Support**: 8-bit quantization support for memory-efficient processing

## Project Structure

```
Speech-to-Text-and-Question-Generation/
├── Pipelines/
│   ├── Noise_Suppression_Diarization_Splitting_Local_Whisper_LoRA/
│   │   ├── noise_suppression_diarization_splitting_local_whisper_transcription.ipynb # Local GPU Whisper-LoRA + Gemini Insights Pipeline
│   │   └── README.md                                                                 # Documentation for the Local pipeline
│   └── Noise_Suppression_Diarization_Splitting_Gemini_API/
│       ├── noise_suppression_diarization_splitting_gemini_api_transcription.ipynb    # Gemini API Transcription Pipeline
│       └── README.md                                                                 # Documentation for the Gemini API pipeline
├── Fine Tuning Script/
│   └── Whisper_small_LORA_finetune.ipynb               # Fine-tuning notebook with LoRA
├── Helper Notebook/                                    # Development helper scripts
├── Noise Suppression And Diarization/                 # Noise suppression & Diarization experiments
├── LICENSE                                             # MIT License
├── README.md                                          # This file
└── .git/                                               # Version control
```

## Transcription & Analysis Pipelines

This repository contains two production-grade workflows for speaker diarization, audio splitting, and transcription:

### 1. Local Whisper-LoRA Pipeline
* **Path**: [Pipelines/Noise_Suppression_Diarization_Splitting_Local_Whisper_LoRA/noise_suppression_diarization_splitting_local_whisper_transcription.ipynb](Pipelines/Noise_Suppression_Diarization_Splitting_Local_Whisper_LoRA/noise_suppression_diarization_splitting_local_whisper_transcription.ipynb)
* **Description**: Performs noise suppression, Pyannote diarization, audio splitting/speaker isolation, and runs a **local Whisper-large-v3-turbo** model wrapped with custom Punjabi/Gurmukhi LoRA adapters on a local GPU. It then queries the Gemini API for Devanagari transliteration and insights.
* **Best For**: High-fidelity Gurmukhi transcription without sending raw segment audio to APIs (ideal for local/GPU environments).
* **Documentation**: See the detailed [Pipelines/Noise_Suppression_Diarization_Splitting_Local_Whisper_LoRA/README.md](Pipelines/Noise_Suppression_Diarization_Splitting_Local_Whisper_LoRA/README.md).

### 2. Gemini API-based Pipeline
* **Path**: [Pipelines/Noise_Suppression_Diarization_Splitting_Gemini_API/noise_suppression_diarization_splitting_gemini_api_transcription.ipynb](Pipelines/Noise_Suppression_Diarization_Splitting_Gemini_API/noise_suppression_diarization_splitting_gemini_api_transcription.ipynb)
* **Description**: Performs noise suppression, Pyannote diarization, and audio splitting, but delegates speech transcription directly to the **Gemini API** (`gemini-2.5-flash-lite`) by sending audio segments in-memory.
* **Best For**: Lightweight execution environments without local GPU memory capacity for heavy Whisper models.
* **Documentation**: See the detailed [Pipelines/Noise_Suppression_Diarization_Splitting_Gemini_API/README.md](Pipelines/Noise_Suppression_Diarization_Splitting_Gemini_API/README.md).

## Installation

### Prerequisites

- Python 3.8+
- pip or conda package manager
- CUDA 11.0+ (for GPU acceleration, optional but recommended)

### Setup

1. **Clone the repository**:
   ```bash
   git clone <repository-url>
   cd Speech-to-Text-and-Question-Generation
   ```

2. **Install dependencies**:
   ```bash
   pip install transformers datasets peft accelerate bitsandbytes evaluate jiwer trl
   ```

3. **Optional - For Jupyter notebook use**:
   ```bash
   pip install jupyter
   ```

## Usage

### Fine-tuning Whisper Model

Open and run the fine-tuning notebook:

```bash
jupyter notebook "Fine Tuning Script/Whisper_small_LORA_finetune.ipynb"
```

**Key steps in the notebook**:
1. Install required dependencies
2. Load the Punjabi STT dataset from Hugging Face
3. Prepare and preprocess audio data (resample to 16kHz)
4. Configure Whisper feature extractor and tokenizer
5. Apply LoRA adaptation for efficient fine-tuning
6. Train the model on your data
7. Evaluate and save the fine-tuned model

**Configuration**:
- **Model**: `openai/whisper-small`
- **Language**: Punjabi
- **Task**: Transcription
- **Optimization**: LoRA (Parameter-efficient fine-tuning)
- **Quantization**: 8-bit (optional)

### Dataset

The notebook uses the Punjabi STT dataset available on Hugging Face:
- Dataset: `abhi8799/Punjabi-STT-Small-8H`
- Audio format: WAV/MP3
- Sampling rate: 16kHz
- Language: Punjabi

## Key Libraries

- **transformers**: Hugging Face transformers library for Whisper models
- **datasets**: Hugging Face datasets for data loading and preprocessing
- **peft**: Parameter-Efficient Fine-Tuning (LoRA support)
- **accelerate**: Training acceleration
- **bitsandbytes**: 8-bit quantization support
- **jiwer**: Evaluation metrics (Word Error Rate)
- **trl**: Transformer Reinforcement Learning utilities

## Model Details

### Whisper
- **Base Model**: OpenAI's Whisper-small
- **Architecture**: Encoder-Decoder transformer
- **Multilingual**: Supports 99+ languages
- **Fine-tuning Approach**: LoRA adaptation for efficiency

### LoRA (Low-Rank Adaptation)
- Dramatically reduces trainable parameters
- Enables fine-tuning on consumer hardware
- Maintains model quality while reducing computational cost

## License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

## Acknowledgments

- **OpenAI**: For the Whisper speech recognition model
- **Hugging Face**: For the transformers library and model hub
- **ANNAM Initiative**: For providing the outreach audio data
- **IIT Ropar**: Academic support and resources

## Contributing

Contributions are welcome! Please feel free to:
1. Fork the repository
2. Create a feature branch
3. Make your changes
4. Submit a pull request

## Support

For issues, questions, or suggestions, please open an issue on the repository.

---

**Last Updated**: June 2026
**Version**: 1.0.0 
