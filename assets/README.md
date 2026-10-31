# Assets Directory

This directory contains visual assets and diagrams for the project documentation.

## Contents

- `architecture_comparison.png` - Visual comparison of the three transformer architectures
- `performance_metrics.png` - Performance comparison charts
- `training_curves.png` - Training loss and validation curves
- `model_diagram.png` - Detailed model architecture diagrams

## Usage

These images are referenced in the main README.md and documentation files to provide visual explanations of the concepts and results.

To generate these visualizations, run the respective notebook cells that create matplotlib/seaborn plots and save them using:

```python
plt.savefig('assets/filename.png', dpi=300, bbox_inches='tight')
```