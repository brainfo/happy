# Histology Analysis Pipeline.py (HAPPY) <img src="readme_images/HAPPYPlacenta.png" width="100" align="right" />

## Fork

a fork for packaging and easy inference usage.

This fork won't touch any training pipeline.

## Installation

Our codebase is writen in python=3.10 and has been tested on Ubuntu 20.04.2 (WSL2), 
MacOS 11.1, and CentOS 7.9.2009 using both an NVIDIA A100 GPU and a CPU

You will first need to install the vips C binaries. The libvips documentation lists
installation instructions [here](https://github.com/libvips/libvips/wiki) for different 
OSs. If you are using MacOS you may brew install with:

```bash
brew install vips --with-cfitsio --with-imagemagick --with-openexr --with-openslide --with-webp
```

If you are on Ubuntu you may apt get:

```bash
sudo apt install libvips
```

Recommend using uv to install.

```bash
uv pip install git+https://github.com/brainfo/happy.git
```

### On the original version

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


## Fork To do

- [x] chunck all sql insert command to get around too many records issue (too many nuclei or cell prediction to be saved, especially)
- [ ] convert the graph_model.pt to be state_dict only. for the loading using newer versions of torch. (I am on torch 2.6.1, cuda 12.8)
- [ ] otherwise, re-trian the graph model using torch 2.6.1, cuda 12.8
