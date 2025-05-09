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

### Troubleshooting

Installing javabridge can sometimes be a little tricky on MacOS. If you get a 
'jvm not found' or 'jni.h not found' style error then you need to locate your 
java installation and export it. For example, if you installed java with homebrew you 
can:

```bash
export JAVA_HOME=/usr/local/opt/openjdk
```

If you then get a error with 'module = PyImport_ImportModuleLevelObject' you can 
install this fork of javabridge which fixes it:

```bash
pip install git+https://github.com/LeeKamentsky/python-javabridge.git#egg=javabridge
```


## Fork To do

- [x] chunck all sql insert command to get around too many records issue (too many nuclei or cell prediction to be saved, especially)
- [ ] convert the graph_model.pt to be state_dict only. for the loading using newer versions of torch. (I am on torch 2.6.1, cuda 12.8)
- [ ] otherwise, re-trian the graph model using torch 2.6.1, cuda 12.8