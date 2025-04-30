```markdown
# Contranpe: A Novel Convolutional Transformer for EEG Decoding

## Overview
Contranpe is a cutting-edge deep learning architecture designed for classifying motor imagery electroencephalogram (EEG) signals. By integrating the strengths of Convolutional Neural Networks (CNNs) and Transformers, Contranpe effectively captures both local and global features from EEG data, achieving superior performance in brain-computer interface (BCI) applications. The model introduces innovative components, including Multi-Head Latent Attention (MLA) and Mixture of Experts (MoE), to enhance feature representation and classification accuracy.

This repository contains the implementation of Contranpe, tested on the BCI Competition IV Dataset 2a, where it achieved an average classification accuracy of 79.59%, outperforming established baselines like FBCSP, ConvNet, and EEGNet.

## Features
- **Hybrid Architecture**: Combines CNNs for local feature extraction with Transformers for global temporal dependency modeling.
- **Multi-Head Latent Attention (MLA)**: A novel attention mechanism that projects features into a low-dimensional latent space, improving computational efficiency and robustness to noisy EEG signals.
- **Mixture of Experts (MoE)**: Enhances classification by dynamically allocating specialized expert networks, improving accuracy and generalization.
- **Data Preprocessing**: Includes bandpass filtering (4-40 Hz) and Z-score normalization to enhance signal quality.
- **Data Augmentation**: Employs time-segment splicing to increase training data diversity and mitigate overfitting.


Additionally, set up CUDA for GPU acceleration if available.

## Dataset
The model is evaluated on the [BCI Competition IV Dataset 2a](http://www.bbci.de/competition/iv/), which includes EEG data from 9 subjects performing four motor imagery tasks (left hand, right hand, feet, and tongue). The dataset consists of 22 channels sampled at 250 Hz, with 288 trials per session per subject.


## Model Architecture
Contranpe consists of three main modules:
1. **Convolutional Module**:
   - Extracts local temporal and spatial features using 1D temporal and spatial convolutions.
   - Includes batch normalization, ELU activation, and average pooling to reduce noise and dimensionality.
2. **Transformer Module**:
   - Utilizes MLA to capture long-term temporal dependencies.
   - Incorporates positional encoding to preserve temporal information.
3. **Classification Module**:
   - Employs MoE with 8 expert networks for dynamic and robust classification.
   - Outputs probabilities for four motor imagery classes.

## Results
Contranpe was evaluated on the BCI Competition IV Dataset 2a, achieving:
- **Average Accuracy**: 79.59% across 9 subjects.
- **Comparison with Baselines**:
  - FBCSP: 67.75%
  - ConvNet: 72.53%
  - EEGNet: 74.50%
  - C2CM: 74.46%
  - DRDA: 74.74%

Ablation studies confirmed the contributions of MLA and MoE:
- Replacing MLA with standard Multi-Head Attention reduced accuracy by 2.54%.
- Replacing MoE with a fully connected layer reduced accuracy by 3.32%.
- Removing both MLA and MoE led to a 5.77% accuracy drop.

## Future Work
- Extend Contranpe to other EEG paradigms (e.g., ERP analysis, emotion recognition).
- Incorporate domain adaptation for cross-subject generalization.
- Optimize computational efficiency for deployment on resource-constrained devices.
- Explore advanced signal processing techniques (e.g., wavelet transforms) to further enhance robustness.

## Acknowledgments
- Thanks to Prof. Wang Ting for guidance and support.
- Gratitude to the BCI Competition IV organizers for providing the dataset.
- Inspired by advancements in deep learning for EEG decoding.
