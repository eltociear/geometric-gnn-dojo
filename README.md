# ⚔️ Geometric GNN Dojo

*Geometric GNN Dojo* is a pedagogical resource for beginners and experts to explore the design space of **Graph Neural Networks for geometric graphs**.

## Architectures

The `/src` directory provides unified implementations of several popular geometric GNN architectures:
- Invariant GNNs: [SchNet](https://arxiv.org/abs/1706.08566), [DimeNet](https://arxiv.org/abs/2003.03123)
- Equivariant GNNs using cartesian vectors: [E(n) Equivariant GNN](https://proceedings.mlr.press/v139/satorras21a.html), [GVP-GNN](https://arxiv.org/abs/2009.01411)
- Equivariant GNNs using spherical tensors: [Tensor Field Network](https://arxiv.org/abs/1802.08219), [MACE](http://arxiv.org/abs/2206.07697)

<figure><center><img src="experiments/fig/axes-of-expressivity.png" width="70%"></center></figure>

## Experiments

The `/experiments` directory contains notebooks with synthetic experiments to highlight practical challenges in building powerful geometric GNNs:
- `kchains.ipynb`: Distinguishing k-chains, which test a model's ability to **propagate geometric information** non-locally and demonstrate oversquashing with increased depth.
- `rotsym.ipynb`: Rotationally symmetric structures, which test a layer's ability to **identify neighbourhood orientation** and highlight the utility of higher order tensors in equivariant GNNs.
- `incompleteness.ipynb`: Counterexamples from [Pozdnyakov et al.](https://journals.aps.org/prl/abstract/10.1103/PhysRevLett.125.166001), which test a layer's ability to create **distinguishing fingerprints for local neighbourhoods** and highlight the need for higher order scalarisation.



## Installation

```bash
# Create new conda environment
conda create -n pyg python=3.8

# Install PyTorch (Check CUDA version!)
conda install pytorch==1.12.1 torchvision==0.13.1 torchaudio==0.12.1 cudatoolkit=11.3 -c pytorch

# Install PyG
conda install pyg -c pyg -c conda-forge

# Install other dependencies
pip3 install e3nn==0.4.4
conda install matplotlib pandas networkx
pip3 install ipdb ase
conda install jupyterlab -c conda-forge
```



## Directory Structure and Usage

```
.
├── README.md
| 
├── experiments                         # Synthetic experiments
│   ├── incompleteness.ipynb            # Experiment on counterexamples from Pozdnyakov et al.
│   ├── kchains.ipynb                   # Experiment on k-chains
│   └── rotsym.ipynb                    # Experiment on rotationally symmetric structures
| 
└── src                                 # Geometric GNN models library
    ├── models.py                       # Models built using layers
    ├── gvp_layers.py                   # Layers for GVP-GNN
    ├── egnn_layers.py                  # Layers for E(n) Equivariant GNN
    ├── tfn_layers.py                   # Layers for Tensor Field Networks
    ├── modules                         # Layers for MACE
    └── utils                           # Helper functions for training, plotting, etc.
```
