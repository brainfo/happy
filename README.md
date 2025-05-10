# Histology Analysis Pipeline.py (HAPPY) <img src="readme_images/HAPPYPlacenta.png" width="100" align="right" />

## Fork

a fork for packaging and easy inference usage (on torch 2.6.0+cu12).

This fork won't touch any training pipeline.


### Fork To do

- [x] chunck all sql insert command to get around too many records issue (too many nuclei or cell prediction to be saved, especially)
- [x] convert the graph_model.pt to be state_dict only. for the loading using newer versions of torch. (I am on torch 2.6.0+cu124)
    - [x] the conversion was done with cpu only torch 2.0.1 and with (only) the happy.models.clustergcn. see https://github.com/brainfo/full2weights

### Installation

```bash
sudo apt install libvips
```

Recommend using uv to install.

```bash
uv pip install git+https://github.com/brainfo/happy.git
```

### Inferences

1. cell inference
```bash
python $happy_prefix/cell_inference.py --project-name placenta --organ-name placenta --nuc-model-id 1 --cell-model-id 2 --slide-id 1 --cell-batch-size 800 --nuc-batch-size 16 > cell_inference.stdout 2>&1
```

2. Use the converted state dict model for graph inference, for the run id correctly with cell predictions saved in the database
```bash
python $happy_prefix/graph_inference.py --project-name placenta --organ-name placenta --pre-trained-path $happy_prefix/projects/placenta/trained_models/graph_converted_state_dict.pth --run-id 3 > graph_inference.stdout 2>&1
```

## On the original version

With this env:
```bash
requires-python = "==3.10.16"
dependencies = [
    "torch==2.0.1",
    "torch-geometric==2.3.1",
    "torch-scatter",
    "torch-sparse",
    "torch-cluster",
    "torch-spline-conv"
]
[tool.uv]
package = false
```

```bash
git clone https://github.com/Nellaker-group/happy.git
cd happy
uv pip install -e .
```

will work
