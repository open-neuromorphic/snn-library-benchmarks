# SNN library benchmarking

In data-generation.ipynb we benchmark forward and backward calls of different libraries. 

# Installation
Start with creating a new Conda environment. Use Python 3.10 in order to use torch.compile (3.11 not supported in Aug 2023)
```
conda create -n frameworks python=3.10 pip
conda activate frameworks
```
Then install PyTorch (adjust for your CUDA version). Instructions available [here](https://pytorch.org/get-started/locally/)
```
conda install pytorch torchvision torchaudio pytorch-cuda=11.7 -c pytorch -c nvidia
```
Install the benchmarked frameworks from PyPI
```
pip install -r requirements.txt
```
At the time of testing (02/08/2023), SpikingJelly v0.0...14 contains a [bug](https://github.com/fangwei123456/spikingjelly/issues/401) in the latest CuPy implementation, so you'll have to install from source. Hopefully they'll release v0.....15 soon.
https://github.com/fangwei123456/spikingjelly

You'll also need to [install CuPy](https://docs.cupy.dev/en/stable/install.html) to enable it as a backend.

In addition I installed Lava-dl via Conda after the pip install
```
conda install lava-dl -c conda-forge
```

# Docker
The following commands will build the docker image, generate the figures and copy them to this folder.
`./bench.sh` takes the batch size as its first argument.

```
./build.sh
./bench.sh 32
```

# Acknowledgements
* Gregor Lenz wrote the initial version, benchmarking latency for forward and backward passes in Norse, Sinabs, snnTorch, EXODUS, Lava and SpikingJelly. 
* Sumit Shreshta improved benchmarking of Lava
* Kade Heckel added Spyx benchmarks
* Cameron Barker containerized all the benchmarks and added memory benchmarks
