# GenAI-VAE: Exploring Latent Spaces with Variational Autoencoders

Official implementation for the IEEE paper **"Exploring Latent Spaces for Generating Challenging Datasets using Variational Autoencoders"**, part of the **NAGMDRS GenAI-VAE** project.

This project presents a novel methodology for producing **challenging datasets** by systematically manipulating the **latent space** of a Variational Autoencoder (VAE). By applying controlled perturbations to latent vectors of a model trained on MNIST, we generate progressively complex data samples to enhance **robustness** and **generalization** in machine learning models.

---

## 📄 Abstract
Variational Autoencoders (VAEs) excel at generating synthetic data via compact latent representations.  
Our approach manipulates latent dimensions in a trained VAE to generate more complex datasets than the original, demonstrating its utility in preparing models for real-world scenarios.  
Experiments on **MNIST** show that controlled perturbations yield synthetic samples with increased difficulty, ideal for stress-testing and improving ML models.

---

## 📚 Paper Details
- **Title:** Exploring Latent Spaces for Generating Challenging Datasets using Variational Autoencoders  
- **Authors:** Akshay Gupta Narsina, Daksh Begani, Vandana Bhattacharjee  
- **Conference:** 2025 IEEE International Conference on Interdisciplinary Approaches in Technology and Management for Social Innovation (IATMSI)  
- **DOI:** [10.1109/IATMSI64286.2025.10985261](https://doi.org/10.1109/IATMSI64286.2025.10985261)  
- **Paper Link:** *(View on IEEE Xplore)*  

---

## 🔬 Methodology

### Model Architecture
- **Encoder:** Maps an input image to latent mean (μ) and log variance (log σ²).  
- **Reparameterization Trick:** `z = μ + ε * σ`, where `ε` ~ N(0, I).  
- **Decoder:** Reconstructs the image from `z`.  

### Loss Function
- **Reconstruction Loss:** Binary Cross-Entropy (BCE) between input and reconstruction.  
- **KL Divergence:** Regularizes latent distribution toward standard normal.

### Latent Space Perturbation
After training, we:
1. Extract latent vectors for MNIST images.
2. Apply controlled perturbations to selected latent dimensions.
3. Decode perturbed vectors to generate **more complex synthetic samples**.

---

## 📊 Results & Visualizations
Provided in **`VAE_MNIST.ipynb`**:
- **Latent Space Plots (2D & 3D)** — Shows digit clustering in latent space.
- **Image Generation** — Synthesized digits with increasing complexity via perturbations.

Example:

```
# Generate perturbed images
z_mean, z_log_var, _ = encoder.predict(x_test)
z = z_mean + np.random.normal(size=z_mean.shape) * 0.5  # perturbation
generated_images = decoder.predict(z)
```

---

## 🚀 Usage
1. Open **`VAE_MNIST.ipynb`** in Jupyter Lab / VS Code.
2. Run cells to:
   - Load & preprocess MNIST.
   - Build encoder, decoder, and VAE.
   - Train for desired epochs.
   - Visualize latent space & generated samples.

Quick start:
```
git clone https://github.com/yourusername/GenAI-VAE.git
cd GenAI-VAE
jupyter notebook VAE_MNIST.ipynb
```

---

## 🤝 Contributing
Pull requests and issue reports are welcome. Suggestions for improving the architecture, perturbation strategies, or dataset variety are encouraged.

---

## 📄 Citation
```bibtex
@INPROCEEDINGS{10985261,
  author={Narsina, Akshay Gupta and Begani, Daksh and Bhattacharjee, Vandana},
  booktitle={2025 IEEE International Conference on Interdisciplinary Approaches in Technology and Management for Social Innovation (IATMSI)}, 
  title={Exploring Latent Spaces for Generating Challenging Datasets using Variational Autoencoders}, 
  year={2025},
  volume={3},
  number={},
  pages={1-5},
  keywords={Training;Deep learning;Technological innovation;Perturbation methods;Autoencoders;Synthetic data;Latent space;MNIST},
  doi={10.1109/IATMSI64286.2025.10985261}
}
```

---

## 📜 License
MIT License © 2025 Akshay Gupta Narsina
