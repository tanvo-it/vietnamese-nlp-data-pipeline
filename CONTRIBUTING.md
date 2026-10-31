# Contributing to Transformer Architectures in NLP

Thank you for your interest in contributing to this project! This document provides guidelines for contributing to the Vietnamese Medical Q&A transformer implementations.

## 🤝 How to Contribute

### Types of Contributions

We welcome several types of contributions:

1. **Bug Reports** - Found an issue? Let us know!
2. **Feature Requests** - Have an idea for improvement?
3. **Code Contributions** - Fix bugs or add new features
4. **Documentation** - Improve explanations and guides
5. **Performance Optimizations** - Make the code faster or more efficient
6. **New Architectures** - Implement additional transformer variants

### Getting Started

1. **Fork the Repository**
   ```bash
   git clone https://github.com/tanvo-it/Transformer_in_NLP.git
   cd Transformer_in_NLP
   ```

2. **Create a Branch**
   ```bash
   git checkout -b feature/your-feature-name
   # or
   git checkout -b fix/your-bug-fix
   ```

3. **Set Up Development Environment**
   ```bash
   pip install -r requirements.txt
   pip install -r requirements-dev.txt  # If available
   ```

## 📝 Contribution Guidelines

### Code Style

- **Python**: Follow PEP 8 style guidelines
- **Notebooks**: Keep cells organized and well-documented
- **Comments**: Write clear, concise comments
- **Docstrings**: Use Google-style docstrings

```python
def preprocess_medical_text(text: str, remove_stopwords: bool = True) -> str:
    """
    Preprocess Vietnamese medical text for model input.
    
    Args:
        text: Raw Vietnamese medical text
        remove_stopwords: Whether to remove Vietnamese stopwords
        
    Returns:
        Preprocessed text ready for tokenization
        
    Example:
        >>> preprocess_medical_text("Bác sĩ ơi, tôi bị đau đầu")
        "bác sĩ đau đầu"
    """
```

### Commit Messages

Use clear, descriptive commit messages:

```bash
# Good
git commit -m "Add ROUGE evaluation metrics to encoder-decoder model"
git commit -m "Fix tokenization issue with Vietnamese diacritics"
git commit -m "Update README with performance benchmarks"

# Avoid
git commit -m "fix bug"
git commit -m "update"
```

### Pull Request Process

1. **Update Documentation** - Ensure README and docs reflect your changes
2. **Add Tests** - Include tests for new functionality
3. **Check Performance** - Verify your changes don't degrade performance
4. **Update Requirements** - Add any new dependencies to requirements.txt

### Pull Request Template

```markdown
## Description
Brief description of changes

## Type of Change
- [ ] Bug fix
- [ ] New feature
- [ ] Documentation update
- [ ] Performance improvement
- [ ] Other (please describe)

## Testing
- [ ] Tested on Google Colab
- [ ] Tested locally
- [ ] Added unit tests
- [ ] Verified on Vietnamese medical dataset

## Checklist
- [ ] Code follows style guidelines
- [ ] Self-review completed
- [ ] Documentation updated
- [ ] No breaking changes
```

## 🐛 Reporting Issues

### Bug Reports

When reporting bugs, please include:

1. **Environment Information**
   ```python
   import torch, transformers, sys
   print(f"Python: {sys.version}")
   print(f"PyTorch: {torch.__version__}")
   print(f"Transformers: {transformers.__version__}")
   print(f"CUDA: {torch.cuda.is_available()}")
   ```

2. **Steps to Reproduce**
   - Exact steps that led to the issue
   - Expected vs actual behavior
   - Error messages and stack traces

3. **Minimal Example**
   ```python
   # Provide minimal code that reproduces the issue
   from transformers import AutoTokenizer
   tokenizer = AutoTokenizer.from_pretrained("Qwen/Qwen2-0.5B")
   # ... rest of minimal example
   ```

### Feature Requests

For feature requests, please describe:
- **Use Case**: Why is this feature needed?
- **Proposed Solution**: How should it work?
- **Alternatives**: What alternatives have you considered?
- **Additional Context**: Any other relevant information

## 🔬 Development Guidelines

### Adding New Architectures

When adding new transformer architectures:

1. **Create New Notebook** - Follow existing naming convention
2. **Document Architecture** - Add detailed explanation in ARCHITECTURE_GUIDE.md
3. **Benchmark Performance** - Compare against existing implementations
4. **Update README** - Add to architecture comparison table

### Medical Domain Considerations

- **Accuracy**: Medical information must be accurate
- **Safety**: Implement safeguards against harmful advice
- **Privacy**: Ensure patient data privacy
- **Bias**: Test for and mitigate medical biases

### Performance Standards

- **Memory Efficiency**: Code should run on standard GPUs (T4, V100)
- **Training Time**: Reasonable training times for educational purposes
- **Inference Speed**: Optimize for real-time applications
- **Reproducibility**: Results should be reproducible

## 🧪 Testing

### Running Tests

```bash
# Run all tests
python -m pytest tests/

# Run specific test file
python -m pytest tests/test_tokenization.py

# Run with coverage
python -m pytest --cov=src tests/
```

### Test Categories

1. **Unit Tests** - Test individual functions
2. **Integration Tests** - Test model training/inference
3. **Performance Tests** - Benchmark speed and memory
4. **Medical Accuracy Tests** - Validate medical content

## 📚 Documentation

### Documentation Standards

- **Clear Explanations** - Assume readers are learning
- **Code Examples** - Include working code snippets
- **Visual Aids** - Add diagrams where helpful
- **References** - Cite relevant papers and resources

### Building Documentation

```bash
# Generate documentation (if using Sphinx)
cd docs/
make html

# Or for simple markdown
# Just edit .md files directly
```

## 🌟 Recognition

Contributors will be recognized in:
- README.md contributors section
- Release notes for significant contributions
- Special thanks for major improvements

## 📞 Getting Help

- **GitHub Issues** - For bugs and feature requests
- **Discussions** - For questions and general discussion
- **Email** - For private matters: [your-email@domain.com]

## 📋 Code of Conduct

### Our Standards

- **Respectful Communication** - Be kind and professional
- **Inclusive Environment** - Welcome all backgrounds and skill levels
- **Constructive Feedback** - Focus on improving the project
- **Medical Ethics** - Maintain high standards for medical content

### Enforcement

Violations of the code of conduct should be reported to the project maintainers. All reports will be handled confidentially.

---

Thank you for contributing to advancing NLP research and Vietnamese medical AI! 🚀