# Handwritten Digit Generator using DCGAN

A Deep Convolutional Generative Adversarial Network (DCGAN) built from scratch using TensorFlow/Keras to generate realistic handwritten digits trained on the MNIST dataset.

---

## Table of Contents

1. Project Overview  
2. Problem Statement  
3. Objectives  
4. Dataset Description  
5. Background: GAN and DCGAN  
6. System Architecture  
7. Model Architecture  
8. Training Strategy  
9. Results  
10. Evaluation  
11. Limitations  
12. Future Improvements  
13. Project Structure  
14. Technologies Used  
15. Conclusion  
16. References  

---

## 1. Project Overview

Generative models represent a major advancement in deep learning. Unlike traditional supervised learning models that classify or predict outputs, generative models learn the underlying data distribution and create new samples that resemble the training data.

This project implements a Deep Convolutional Generative Adversarial Network (DCGAN) to synthesize realistic handwritten digits similar to those in the MNIST dataset. The model learns digit patterns and generates entirely new images from random noise vectors.

---

## 2. Problem Statement

The objective of this project is to determine whether a neural network can learn the distribution of handwritten digits and generate realistic synthetic images that resemble human handwriting.

The system must:

- Learn features of handwritten digits without labels.
- Train a generator network to produce synthetic images.
- Train a discriminator network to distinguish real from fake images.
- Achieve stable adversarial training.

---

## 3. Objectives

- Design Generator and Discriminator architectures from scratch.
- Use LeakyReLU activation for stable gradient propagation.
- Apply Batch Normalization to improve training stability.
- Train on 60,000+ MNIST training samples.
- Implement adversarial training using Binary Cross-Entropy loss.
- Save checkpoints for reproducibility.
- Visualize generated images during training.

---

## 4. Dataset Description

The project uses the MNIST dataset, a benchmark dataset in computer vision and deep learning research.

Dataset Details:

- Total images: 70,000
- Training samples: 60,000
- Test samples: 10,000
- Image size: 28 × 28 pixels
- Color mode: Grayscale
- Classes: Digits 0–9

Since GANs operate in an unsupervised setting, digit labels are not used during training.

---

## 5. Background: GAN and DCGAN

### Generative Adversarial Networks (GAN)

GANs were introduced by Ian Goodfellow in 2014. A GAN consists of two neural networks trained simultaneously:

Generator (G):
- Takes a random noise vector as input.
- Produces synthetic images.

Discriminator (D):
- Receives both real and generated images.
- Classifies them as real or fake.

The objective function is defined as a minimax game:

min_G max_D V(D, G)

The generator tries to fool the discriminator, while the discriminator tries to correctly classify images.

---

### Deep Convolutional GAN (DCGAN)

DCGAN improves standard GANs by incorporating convolutional neural networks.

Key characteristics:

- Uses convolutional layers instead of fully connected layers.
- Eliminates pooling layers and uses strided convolutions.
- Applies Batch Normalization.
- Uses LeakyReLU activation.
- Uses Tanh activation in the generator output layer.

DCGAN significantly improves image quality and training stability.

---

## 6. System Architecture

Random Noise Vector (100-dimensional latent space)  
        ↓  
Generator Network  
        ↓  
Generated Image (28 × 28)  
        ↓  
Discriminator Network  
        ↓  
Real / Fake Output  

---

## 7. Model Architecture

### Generator Architecture

- Input: 100-dimensional noise vector
- Dense layer to expand feature representation
- Batch Normalization
- LeakyReLU activation
- Reshape to 7 × 7 × 256 feature map
- Transposed convolution layers for upsampling
- Final activation: Tanh
- Output: 28 × 28 × 1 generated image

---

### Discriminator Architecture

- Input: 28 × 28 × 1 image
- Convolution layers with stride 2
- LeakyReLU activation
- Dropout for regularization
- Flatten layer
- Dense output layer
- Binary classification (Real or Fake)

---

## 8. Training Strategy

The model is trained using adversarial learning.

Training Process:

1. Sample random noise vectors.
2. Generate fake images using the generator.
3. Feed real images to the discriminator.
4. Feed fake images to the discriminator.
5. Compute discriminator loss.
6. Compute generator loss.
7. Update both networks using backpropagation.

Hyperparameters:

- Optimizer: Adam
- Loss function: Binary Cross-Entropy
- Latent dimension: 100
- Batch size: 128
- Epochs: 50

---

## 9. Results

After multiple training epochs:

- Generated digits progressively become sharper.
- Noise is significantly reduced.
- The generator learns stroke patterns and digit structure.
- Outputs visually resemble handwritten digits from the dataset.

The adversarial training process enables the model to generate realistic synthetic digits from pure random noise.

---

## 10. Evaluation

GANs do not use traditional accuracy metrics.

Evaluation techniques include:

- Visual inspection of generated samples
- Fréchet Inception Distance (FID)
- Inception Score
- Precision and Recall for generative models

In this project, visual monitoring was used to assess generator performance.

---

## 11. Limitations

- Training instability is common in GANs.
- Risk of mode collapse.
- Limited to grayscale digit generation.
- No conditional control over digit classes.
- Limited training epochs.

---

## 12. Future Improvements

- Train for more epochs.
- Implement Conditional GAN (cGAN).
- Use Wasserstein GAN with Gradient Penalty (WGAN-GP).
- Compute FID score for quantitative evaluation.
- Extend to Fashion-MNIST or CIFAR datasets.
- Deploy as a web-based application.

---

## 13. Project Structure

dcgan-mnist/  
│  
├── models/  
├── checkpoints/  
├── outputs/  
├── train.py  
├── generator.py  
├── discriminator.py  
├── requirements.txt  
└── README.md  

---

## 14. Technologies Used

- Python  
- TensorFlow  
- Keras  
- NumPy  
- Matplotlib  

---

## 15. Conclusion

This project demonstrates the capability of adversarial learning in generative modeling. The DCGAN successfully learns the distribution of handwritten digits and generates realistic synthetic images from random noise.

The project highlights how convolutional architectures significantly improve GAN performance and image quality.

---

## 16. References

- Goodfellow et al., 2014 – Generative Adversarial Networks  
- Radford et al., 2015 – Unsupervised Representation Learning with Deep Convolutional GANs  
- MNIST Dataset Documentation