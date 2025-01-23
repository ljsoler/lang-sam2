# This implementation extends [lang-sam library](https://github.com/paulguerrero/lang-sam) combining GroundingDINO with the new SAM2.

# Language Segment-Anything

Language Segment-Anything 2 is an open-source project that combines the power of instance segmentation and text prompts to generate masks for specific objects in images. Built on the recently released Meta model, segment-anything, and the GroundingDINO detection model, it's an easy-to-use and effective tool for object detection and image segmentation.

## Features

- Zero-shot text-to-bbox approach for object detection.
- Zero-shot text-to-mask approach for semantic segmentation
- GroundingDINO detection model integration together with Segment Anything (SAM) 2.
- Easy deployment using the Lightning AI app platform.
- Customizable text prompts for precise object segmentation.

## Getting Started

### Prerequisites

- Python 3.9 or higher
- torch >= 2.5.1
- torchvision

### Installation

```
pip install torch torchvision
pip install -U git+https://github.com/ljsoler/lang-sam2.git
```

Or
Clone the repository and install the required packages:

```
git clone https://github.com/ljsoler/lang-sam2.git && cd lang-sam2
pip install torch torchvision
pip install -e .
```
Or use Conda
Create a Conda environment from the `environment.yml` file:
```
conda env create -f environment.yml
# Activate the new environment:
conda activate lang-sam2
```


### Usage

To run the Lightning AI APP, please refer to lang-segment-anything (https://github.com/luca-medeiros/lang-segment-anything) for more information:

`lightning run app app.py`

Use as a library:

```python
from PIL import Image
from lang_sam import LangSAM2

model = LangSAM()
image_pil = Image.open("./assets/car.jpeg").convert("RGB")
text_prompt = "wheel"
masks, boxes, phrases, logits = model.predict(image_pil, text_prompt)
```

Use with custom checkpoint:

First download a model checkpoint. 

```python
from PIL import Image
from lang_sam import LangSAM

model = LangSAM("<model_type>", "<path/to/checkpoint>")
image_pil = Image.open("./assets/car.jpeg").convert("RGB")
text_prompt = "wheel"
masks, boxes, phrases, logits = model.predict(image_pil, text_prompt)
```

## Acknowledgments

This project is based on the following repositories:

- [GroundingDINO](https://github.com/IDEA-Research/GroundingDINO)
- [Segment-Anything2](https://github.com/facebookresearch/sam2)
- [Lightning AI](https://github.com/Lightning-AI/lightning)
- [lang-sam](https://github.com/paulguerrero/lang-sam)

## License

This project is licensed under the Apache 2.0 License
