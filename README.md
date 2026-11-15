# AttnGAN-Inspired Text-to-Image Synthesis for Fine-Grained Bird Species Generation (archived)

This repository is archived. The maintained version of the project is
**[Rewanooo22/attngan-bird-text-to-image](https://github.com/Rewanooo22/attngan-bird-text-to-image)**,
which contains the notebook, the paper draft and full documentation.

## Contents

| File | Description |
|---|---|
| `AttnGAN_Bird_Text_to_Image (1).ipynb` | Google Colab notebook with its outputs: a baseline text-conditioned GAN and an AttnGAN-inspired model (BiLSTM text encoder, word-level attention, upsample + conv generator) trained on a 200-image, 10-class CUB-200-2011 subset at 64x64 with template captions, 60 epochs each |
| `AttnGAN_Scientific_Paper.docx` | Paper draft describing the project |
| `LICENSE` | MIT License |

The executed notebook in this repository is the source of the run outputs (training losses and proxy metrics) referenced in the maintained repository's README. Note that the paper draft's reported improvements do not match those executed outputs; see the maintained README for details.

## License

Released under the [MIT License](LICENSE).
