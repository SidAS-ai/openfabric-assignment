# openfabric-assignment
# Text to 3D AI Generation Pipeline

## Overview

This project implements an end-to-end creative AI pipeline that takes a simple text prompt and transforms it into a 3D model through a series of AI-powered steps:

1. **Text Enhancement**: Transforms basic text prompts into rich, detailed descriptions optimized for image generation
2. **Text-to-Image Generation**: Creates high-quality images based on the enhanced prompts
3. **Image-to-3D Conversion**: Transforms 2D images into fully-realized 3D models
4. **Memory Storage**: Maintains a database of all creations for easy retrieval and reference

The pipeline leverages HuggingFace's hosted language models for prompt enhancement and Openfabric's specialized AI services for image and 3D model generation.

## Features

- 🧠 **AI-Powered Prompt Enhancement**: Automatically enriches your basic ideas with detailed descriptions
- 🖼️ **High-Quality Image Generation**: Creates detailed images with control over style, composition, and more
- 🏺 **Automated 3D Model Creation**: Converts images to 3D models in GLB format
- 🔍 **Creation Memory**: Stores all your creations with searchable metadata
- 🖥️ **Intuitive UI**: Simple Gradio interface for easy interaction
- 🔄 **Configurable Models**: Switch between different HuggingFace models for varied results

## Installation

### Prerequisites

- Python 3.8 or higher
- CUDA-compatible GPU recommended for faster processing
- HuggingFace API token
- Openfabric API key

### Setup

1. Clone this repository:
   ```bash
   git clone https://github.com/your-username/text-to-3d-pipeline.git
   cd text-to-3d-pipeline
   ```

2. Install dependencies:
   ```bash
   pip install -r requirements.txt
   ```

3. Set up environment variables (or you'll be prompted when running the program):
   ```bash
   export HF_TOKEN="your_huggingface_token"
   export OPENFABRIC_API_KEY="your_openfabric_api_key"
   ```

## Usage

### Running the Pipeline

```bash
python main.py
```

This will:
1. Initialize the pipeline components
2. Run a test generation with a sample prompt
3. Launch the Gradio web interface

### Using the Gradio Interface

The interface has three main tabs:

#### Create Tab
- Enter your creative prompt in the text area
- Click "Generate" to start the creation process
- View the generated image and download the 3D model

#### Memory Tab
- Search your previous creations by keywords
- Review details of past generations

#### Settings Tab
- Select different HuggingFace models for prompt enhancement

### Direct API Usage

You can integrate the pipeline into your own applications:

```python
from creative_pipeline import CreativePipeline

# Initialize the pipeline
pipeline = CreativePipeline()

# Generate from a prompt
result = pipeline.create_from_prompt("A glowing dragon standing on a cliff at sunset")

# Access the results
image_path = result["image_path"]
model_path = result["model_path"]
enhanced_prompt = result["enhanced_prompt"]

# Search previous creations
past_creations = pipeline.search_memory("dragon")
```

## Architecture

### Components

1. **HuggingFaceLLM**: Handles prompt enhancement using advanced language models
   - Supports various models like Llama 3 8B, Mistral, Gemma, and OpenHermes
   - Formats system and user prompts for optimal text enhancement

2. **OpenfabricConnector**: Interfaces with Openfabric's AI services
   - Text-to-Image generation with customizable parameters
   - Image-to-3D model conversion

3. **MemoryManager**: Manages the SQLite database of creations
   - Stores all details including original prompts, enhanced descriptions, and file paths
   - Provides searching and retrieval functionality

4. **CreativePipeline**: Orchestrates the entire workflow
   - Manages the sequential process from text to 3D
   - Handles error states and provides detailed results

### Directory Structure

```
text-to-3d-pipeline/
├── main.py                   # Main application entry point
├── outputs/                  # Generated output files
│   ├── images/               # Generated images
│   └── models/               # Generated 3D models
├── memory/                   # Database storage
│   └── creative_memory.db    # SQLite database
├── requirements.txt          # Dependencies
└── README.md                 # This file
```

## Configuration Options

### HuggingFace Models

The pipeline supports multiple language models for prompt enhancement:

- meta-llama/Llama-3-8b-instruct (default)
- mistralai/Mistral-7B-Instruct-v0.2
- google/gemma-7b-it
- teknium/OpenHermes-2.5-Mistral-7B

### Image Generation Parameters

Customize image generation with these parameters:

- Width and height (default: 768x768)
- Number of inference steps (default: 50)
- Guidance scale (default: 7.5)
- Negative prompts for improved quality

## Requirements

- torch
- huggingface_hub
- openfabric_pysdk
- Pillow
- gradio
- sqlite3
- requests

## OUTPUT OF THE CODE
![image](https://github.com/user-attachments/assets/f16fee72-e06c-473c-867b-a6b941709dbf)


## Limitations

- Image generation quality depends on the prompt and Openfabric's models
- 3D model generation works best with clear, well-defined objects
- Processing time varies based on server load and complexity of the request
- GPU acceleration recommended for optimal performance

## Contributing

Contributions are welcome! Please feel free to submit a Pull Request.

1. Fork the repository
2. Create your feature branch (`git checkout -b feature/amazing-feature`)
3. Commit your changes (`git commit -m 'Add some amazing feature'`)
4. Push to the branch (`git push origin feature/amazing-feature`)
5. Open a Pull Request

## License

This project is licensed under the MIT License - see the LICENSE file for details.

## Acknowledgments

- [HuggingFace](https://huggingface.co/) for providing powerful language models
- [Openfabric](https://www.openfabric.ai/) for image and 3D generation capabilities
- [Gradio](https://gradio.app/) for the web interface framework
