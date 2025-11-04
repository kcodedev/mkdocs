# Semi-Supervised Learning

Semi-supervised learning combines both labeled and unlabeled data to improve learning performance. It leverages the abundance of unlabeled data along with limited labeled examples.

### Characteristics

- **Training Data**: Mix of labeled and unlabeled data
- **Goal**: Improve performance using additional unlabeled data
- **Approach**: Use unlabeled data to learn better representations

### Common Approaches

- **Self-Training**: Use model predictions on unlabeled data as pseudo-labels
- **Co-Training**: Train multiple models on different views of data
- **Graph-Based Methods**: Propagate labels through data similarity graphs
- **Generative Models**: Learn data distribution from unlabeled data

### Applications

- Text classification with limited labeled documents
- Image recognition with few labeled images
- Speech recognition
- Bioinformatics