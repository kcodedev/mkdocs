# Self-Supervised Learning

Self-supervised learning creates supervisory signals from the data itself, typically by predicting parts of the input from other parts. It's a form of unsupervised learning that generates its own labels.

### Characteristics

- **Training Data**: Unlabeled data
- **Goal**: Learn useful representations through pretext tasks
- **Approach**: Create labels from data structure

### Common Techniques

- **Contrastive Learning**: Learn representations by comparing similar/dissimilar samples
- **Masked Language Modeling**: Predict masked words in text
- **Image Inpainting**: Predict missing parts of images
- **Rotation Prediction**: Predict image rotations

### Applications

- Pre-training for downstream tasks
- Representation learning
- Transfer learning