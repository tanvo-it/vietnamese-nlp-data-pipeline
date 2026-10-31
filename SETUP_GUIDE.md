# Setup and Installation Guide

## 🚀 Quick Start

### Option 1: Google Colab (Recommended)
The easiest way to run these notebooks is using Google Colab with free GPU access.

1. **Open in Colab**
   - Go to [Google Colab](https://colab.research.google.com/)
   - Upload the notebook files or connect to GitHub
   - Enable GPU: Runtime → Change runtime type → GPU

2. **Install Dependencies**
   ```python
   !pip install -q transformers datasets torch accelerate evaluate rouge-score sacrebleu scikit-learn pandas numpy matplotlib seaborn google-generativeai sentencepiece protobuf
   ```

### Option 2: Local Installation

#### Prerequisites
- Python 3.8 or higher
- CUDA-compatible GPU (optional but recommended)
- 16GB+ RAM recommended
- 10GB+ free disk space

#### Step-by-Step Installation

1. **Clone Repository**
   ```bash
   git clone https://github.com/tanvo-it/Transformer_in_NLP.git
   cd Transformer_in_NLP
   ```

2. **Create Virtual Environment**
   ```bash
   # Using conda (recommended)
   conda create -n transformer-nlp python=3.9
   conda activate transformer-nlp
   
   # Or using venv
   python -m venv transformer-nlp
   source transformer-nlp/bin/activate  # Linux/Mac
   # transformer-nlp\Scripts\activate  # Windows
   ```

3. **Install Dependencies**
   ```bash
   pip install -r requirements.txt
   ```

4. **Verify Installation**
   ```python
   import torch
   import transformers
   print(f"PyTorch version: {torch.__version__}")
   print(f"Transformers version: {transformers.__version__}")
   print(f"CUDA available: {torch.cuda.is_available()}")
   ```

## 🔧 Configuration

### GPU Setup
```python
# Check GPU availability
import torch
device = torch.device('cuda' if torch.cuda.is_available() else 'cpu')
print(f"Using device: {device}")

if torch.cuda.is_available():
    print(f"GPU: {torch.cuda.get_device_name(0)}")
    print(f"Memory: {torch.cuda.get_device_properties(0).total_memory / 1e9:.2f} GB")
```

### Memory Optimization
For systems with limited GPU memory:

```python
# Enable gradient checkpointing
training_args = TrainingArguments(
    gradient_checkpointing=True,
    dataloader_pin_memory=False,
    per_device_train_batch_size=2,  # Reduce batch size
    gradient_accumulation_steps=8,  # Simulate larger batches
)
```

### Hugging Face Setup
```python
# Optional: Login to Hugging Face for private models
from huggingface_hub import login
login()  # Enter your token when prompted
```

## 📊 Dataset Access

The Vietnamese Medical Q&A dataset is publicly available:
```python
from datasets import load_dataset
dataset = load_dataset('hungnm/vietnamese-medical-qa')
```

## 🐛 Troubleshooting

### Common Issues

#### 1. CUDA Out of Memory
```python
# Solutions:
# - Reduce batch size
# - Enable gradient checkpointing
# - Use gradient accumulation
# - Clear cache between runs
torch.cuda.empty_cache()
```

#### 2. Tokenizer Issues
```python
# For Vietnamese text processing
tokenizer = AutoTokenizer.from_pretrained(
    "Qwen/Qwen2-0.5B",
    trust_remote_code=True,
    use_fast=True
)
```

#### 3. Package Conflicts
```bash
# Clean installation
pip uninstall torch transformers
pip install torch transformers --no-cache-dir
```

#### 4. Slow Training
```python
# Enable mixed precision training
from transformers import TrainingArguments
training_args = TrainingArguments(
    fp16=True,  # Enable mixed precision
    dataloader_num_workers=4,  # Parallel data loading
)
```

### Performance Optimization

#### CPU Optimization
```python
import torch
torch.set_num_threads(4)  # Adjust based on your CPU cores
```

#### Memory Management
```python
# Monitor memory usage
import psutil
import GPUtil

def print_memory_usage():
    # CPU Memory
    memory = psutil.virtual_memory()
    print(f"CPU Memory: {memory.percent}% used")
    
    # GPU Memory
    if torch.cuda.is_available():
        gpu = GPUtil.getGPUs()[0]
        print(f"GPU Memory: {gpu.memoryUtil*100:.1f}% used")
```

## 📝 Running the Notebooks

### Execution Order
1. **Start with any architecture** - all notebooks are independent
2. **Recommended sequence for learning**:
   - `Encoder_Only.ipynb` - Simplest architecture
   - `Decoder_Only.ipynb` - Most common in modern LLMs
   - `Encoder_Decoder.ipynb` - Most complex but powerful

### Expected Runtime
- **Encoder-Only**: ~2-3 hours with GPU
- **Decoder-Only**: ~3-4 hours with GPU  
- **Encoder-Decoder**: ~4-5 hours with GPU

### Monitoring Training
```python
# Add to training loop for monitoring
import matplotlib.pyplot as plt

def plot_training_progress(trainer):
    logs = trainer.state.log_history
    train_loss = [log['train_loss'] for log in logs if 'train_loss' in log]
    eval_loss = [log['eval_loss'] for log in logs if 'eval_loss' in log]
    
    plt.figure(figsize=(10, 6))
    plt.plot(train_loss, label='Training Loss')
    plt.plot(eval_loss, label='Validation Loss')
    plt.legend()
    plt.show()
```

## 🔐 Security Considerations

### API Keys
If using external APIs (like Google Gemini):
```python
import os
from google.colab import userdata

# In Colab
api_key = userdata.get('GEMINI_API_KEY')

# Locally
api_key = os.getenv('GEMINI_API_KEY')
```

### Data Privacy
- Medical data is sensitive - ensure compliance with regulations
- Consider data anonymization for public sharing
- Use secure environments for production deployments

## 📞 Support

### Getting Help
1. **Check Issues**: Look at existing GitHub issues
2. **Documentation**: Review Hugging Face documentation
3. **Community**: Ask on Hugging Face forums or Stack Overflow

### Reporting Issues
When reporting issues, include:
- Python version
- Package versions (`pip list`)
- Error messages
- System specifications
- Minimal reproducible example

---

*Happy coding! 🚀*