# AttnGAN-Inspired Text-to-Image Synthesis for Fine-Grained Bird Species Generation

A university assignment that compares two text-to-image GANs on bird images from CUB-200-2011:

- **Baseline:** a simple text embedding and a ConvTranspose generator
- **Improved, AttnGAN-style:** an LSTM text encoder with word-level attention and an upsample + convolution generator

The notebook in this repository has been run end to end in Google Colab. Its outputs (training logs, loss curves, generated images and the comparison metrics) are saved in the notebook.

## What the notebook does

| Step | Details |
|---|---|
| Data | Downloads CUB-200-2011 from Kaggle (it tries a few datasets in order; the saved run used `veeralakrishna/200-bird-species-with-11788-images`) and builds a subset of **10 classes × 20 images = 200 images**, resized to **64×64** |
| Captions | Generates descriptive captions for each image from templates (size, colour, pattern, beak, perch, background), then builds a 95-token vocabulary |
| Baseline model | Embedding text encoder (28,672 params), ConvTranspose generator (4.6M), discriminator (2.8M) |
| Improved model | Bidirectional LSTM text encoder (1.3M params), generator with word-level attention and upsample + conv blocks (4.6M), discriminator (2.9M) |
| Training | Both models for **60 epochs**, batch size 16, Adam (generator 2e-4, discriminator 1e-4), cosine LR schedule, BCE-with-logits loss, label smoothing 0.1 on real labels |
| Evaluation | Generates images from text captions and compares the two models side by side |

## Results from the saved run

The notebook compares 64 generated images per model on two simple image statistics. These aren't standard GAN metrics like FID or Inception Score.

| Metric | Definition | Baseline | AttnGAN-style |
|---|---|---:|---:|
| Pixel diversity | Std of pixel values across generated images | 0.4937 | 0.2470 |
| Sharpness proxy | Mean absolute image gradient | 0.2204 | 0.1055 |

These come from a single 60-epoch run on 200 images. The loss curves, generated samples and comparison grid are saved as images in the notebook outputs.

## Files

| File | Description |
|---|---|
| `AttnGAN_Bird_Text_to_Image (1).ipynb` | Colab notebook with the full pipeline and its saved outputs |
| `AttnGAN_Scientific_Paper.docx` | Paper draft describing the project |
| `LICENSE` | License file |

## Run it

1. Open `AttnGAN_Bird_Text_to_Image (1).ipynb` in [Google Colab](https://colab.research.google.com/) (File → Upload notebook).
2. Set the runtime to GPU (Runtime → Change runtime type). The saved run used a T4.
3. Have your Kaggle API token (`kaggle.json`, from Kaggle → Account → Create API Token) ready. The notebook asks you to upload it, then downloads the dataset.
4. Run the cells in order. The notebook writes its checkpoints and output images to `/content/`.

## Tech

PyTorch · torchvision · NumPy · Matplotlib · Pillow · Kaggle API
