# Equivariant Learning and World Model Libraries

**Last Updated**: 2025-11-13
**Category**: SE(3) equivariance, geometric deep learning, world models

---

## 🔄 Equivariant Learning Libraries

### 1. e3nn (Euclidean Neural Networks)

**Developer**: Mario Geiger, Tess Smidt, et al.
**License**: MIT
**GitHub**: https://github.com/e3nn/e3nn
**Stars**: ~900

**Description**:
- General-purpose E(3)-equivariant neural networks
- PyTorch-based
- Used in molecular modeling, point clouds, robotics

**Key Features**:
- SO(3), E(3), SE(3) equivariance
- Spherical harmonics
- Tensor products
- Irreducible representations (irreps)
- Point convolutions

**Pros**:
- Most general E(3) library
- Mathematically rigorous
- Active development
- Good documentation

**Cons**:
- Steep learning curve (group theory knowledge)
- Slower than specialized libraries
- Complex API

**Relevance to Our Research**: ⭐⭐⭐⭐⭐
- **Critical for SE(3)-equivariant policies**
- Equivariant Hierarchical idea (#2)
- 3-5x data efficiency
- **Use for**: Implement SE(3)-equivariant waypoint generation

**Getting Started**:
```python
pip install e3nn

import torch
from e3nn import o3
from e3nn.nn import FullyConnectedNet

# Define irreps (representations)
irreps_in = o3.Irreps("1x1e + 2x1o")  # 1 even scalar, 2 odd vectors
irreps_out = o3.Irreps("1x1e")

# Create equivariant network
net = FullyConnectedNet(
    irreps_in=irreps_in,
    irreps_out=irreps_out,
    irreps_hidden=[o3.Irreps("64x0e + 32x1e")],
)

# Forward pass (equivariant to rotations)
x = torch.randn(10, irreps_in.dim)
out = net(x)
```

**Key Concepts**:
- **Irreps**: Irreducible representations (how data transforms under rotations)
- **0e**: Scalar (invariant)
- **1o**: Vector (rotates)
- **Tensor Products**: Combine features equivariantly

---

### 2. escnn (Equivariant Steerable CNNs)

**Developer**: Gabriele Cesa, Maurice Weiler
**License**: BSD-3-Clause
**GitHub**: https://github.com/QUVA-Lab/escnn
**Stars**: ~500

**Description**:
- E(n)-equivariant CNNs
- 2D and 3D support
- Efficient implementation

**Key Features**:
- Group-equivariant convolutions
- SO(2), SO(3), E(2), E(3) support
- Steerable filters
- ResNet-style architectures

**Pros**:
- Efficient (optimized kernels)
- CNN-like API (familiar)
- Good for vision tasks

**Cons**:
- Less general than e3nn
- Focused on CNNs (not general graphs)

**Relevance to Our Research**: ⭐⭐⭐⭐
- Equivariant vision encoders
- 3D convolutions (point clouds)
- **Use for**: SE(3)-equivariant visual features

**Getting Started**:
```python
pip install escnn

from escnn import gspaces
from escnn import nn

# Define group (SO(3) for 3D rotations)
g = gspaces.rot3dOnR3()

# Equivariant conv layer
in_type = nn.FieldType(g, [g.trivial_repr] * 3)  # 3 scalar channels
out_type = nn.FieldType(g, [g.regular_repr] * 16)  # 16 feature channels

conv = nn.R3Conv(in_type, out_type, kernel_size=5)
```

---

### 3. Equiformer (Transformers + Equivariance)

**Developer**: Yi-Lun Liao et al. (MIT)
**License**: MIT
**GitHub**: https://github.com/atomicarchitects/equiformer
**Stars**: ~300

**Description**:
- Equivariant Transformers
- SO(3)/SE(3) equivariance + attention
- State-of-the-art on molecular property prediction

**Key Features**:
- SE(3)-equivariant attention
- Based on e3nn
- Scalable (Transformer architecture)
- High accuracy

**Pros**:
- Combines Transformers with equivariance
- State-of-the-art performance
- Scalable

**Cons**:
- Complex (Transformer + group theory)
- Molecular domain focus

**Relevance to Our Research**: ⭐⭐⭐⭐
- Equivariant Transformers (good for sequence modeling)
- Could use for equivariant policy architectures
- **Use for**: Advanced equivariant architectures

---

### 4. Geometric Deep Learning Libraries (General)

**PyTorch Geometric** (PyG)
- **GitHub**: https://github.com/pyg-team/pytorch_geometric
- **Stars**: ~20K
- **Use**: Graph neural networks (GNNs)
- **Relevance**: ⭐⭐⭐
  - Point cloud processing
  - Scene graphs
  - Not inherently equivariant (but supports)

**DGL (Deep Graph Library)**
- **GitHub**: https://github.com/dmlc/dgl
- **Stars**: ~13K
- **Use**: Graph learning
- **Relevance**: ⭐⭐⭐
  - Alternative to PyG
  - Good for large graphs

---

## 🌍 World Model Libraries

### 5. DreamerV3 (Official)

**Developer**: Danijar Hafner (Google DeepMind)
**License**: MIT
**GitHub**: https://github.com/danijar/dreamerv3
**Stars**: ~1K

**Description**:
- State-of-the-art model-based RL
- Learns world model from pixels
- Plans in latent space

**Key Features**:
- World model: RSSM (Recurrent State-Space Model)
- Actor-critic in latent space
- Works on diverse tasks (Atari, DMC, Minecraft)
- Single set of hyperparameters

**Pros**:
- State-of-the-art world model
- Production-ready (JAX implementation)
- Proven on many domains

**Cons**:
- JAX (not PyTorch)
- Complex codebase
- Optimized for RL (not imitation learning)

**Relevance to Our Research**: ⭐⭐⭐⭐⭐
- **World model architecture reference**
- RSSM could adapt for HiLoop
- **Use for**: World model implementation inspiration

**Getting Started**:
```python
git clone https://github.com/danijar/dreamerv3.git
# JAX-based, see repo for installation

# Key components:
# - world_model.py: Dynamics model
# - agent.py: Actor-critic
# - train.py: Training loop
```

---

### 6. WorldModels (Ha & Schmidhuber)

**Developer**: David Ha (Google Brain)
**License**: MIT
**GitHub**: https://github.com/hardmaru/WorldModelsExperiments
**Stars**: ~1K

**Description**:
- Original World Models paper implementation
- VAE + RNN dynamics
- Classic work (2018)

**Components**:
- Vision: VAE (encode observations)
- Memory: MDN-RNN (predict next latent)
- Controller: Small policy in latent space

**Pros**:
- Simple, interpretable
- Foundational work

**Cons**:
- Outdated (2018)
- Less performant than DreamerV3

**Relevance to Our Research**: ⭐⭐⭐
- Historical reference
- Simpler than Dreamer (easier to understand)
- **Use for**: Learning world model basics

---

### 7. MuZero (DeepMind)

**Developer**: DeepMind
**License**: Apache 2.0
**GitHub**: https://github.com/werner-duvaud/muzero-general
**Stars**: ~2K (unofficial implementation)

**Description**:
- Model-based RL without model of environment
- Learns value-equivalent model
- State-of-the-art in games (Go, Chess, Atari)

**Key Features**:
- Representation, dynamics, prediction networks
- MCTS planning
- Self-supervised learning

**Pros**:
- Very powerful
- No explicit environment model needed

**Cons**:
- Complex
- Optimized for games (not manipulation)

**Relevance to Our Research**: ⭐⭐⭐
- Advanced world model techniques
- Could inspire value-equivalent WM
- **Use for**: If need advanced WM features

---

### 8. IRIS (Implicit Recurrent State Space Model)

**Developer**: Jürgen Schmidhuber group
**License**: MIT
**GitHub**: https://github.com/eloialonso/iris
**Stars**: ~200

**Description**:
- Discrete world model
- Transformer-based
- State-of-the-art on Atari

**Key Features**:
- Discrete latent space (like VQ-VAE)
- Transformer dynamics
- Efficient training

**Pros**:
- Modern architecture (Transformers)
- Good performance

**Cons**:
- Newer (less battle-tested)
- Atari-focused

**Relevance to Our Research**: ⭐⭐⭐
- Modern WM architecture
- Could adapt for manipulation
- **Use for**: Alternative to RSSM

---

## 🧰 Utility Libraries

### 9. Geometric Algebra Transformer (GATr)

**Developer**: David Ruhe et al.
**License**: MIT
**GitHub**: https://github.com/Qualcomm-AI-research/geometric-algebra-transformer
**Stars**: ~200

**Description**:
- E(3)-equivariant Transformers via geometric algebra
- Alternative to e3nn-based methods
- Efficient

**Pros**:
- Elegant formulation
- Efficient (vs e3nn)
- Transformer-based

**Cons**:
- Newer (less mature)
- Geometric algebra learning curve

**Relevance to Our Research**: ⭐⭐⭐
- Cutting-edge equivariant architecture
- **Use for**: If need more efficient than e3nn

---

### 10. EquiBot (Equivariant Robot Policy)

**Developer**: Stanford (Xie et al.)
**License**: MIT
**GitHub**: https://github.com/UT-Austin-RPL/EquiBot
**Stars**: ~100

**Description**:
- Official EquiBot implementation
- SE(3)-equivariant diffusion policy
- Direct relevance to our work

**Key Features**:
- SE(3)-equivariant architecture
- Diffusion policy
- Manipulation tasks

**Pros**:
- Directly applicable (manipulation + equivariance)
- Shows 3-5x data efficiency

**Cons**:
- Research code (may need adaptation)
- Specific to their method

**Relevance to Our Research**: ⭐⭐⭐⭐⭐
- **Direct competitor/inspiration**
- Equivariant diffusion (our idea #2)
- **Use for**: Architecture reference, baseline comparison

---

## 📊 Comparison Table

| Library | Focus | Ease of Use | Performance | Maturity | Relevance |
|---------|-------|-------------|-------------|----------|-----------|
| **e3nn** | E(3) equivariance | ⭐⭐⭐ | ⭐⭐⭐⭐ | ⭐⭐⭐⭐⭐ | ⭐⭐⭐⭐⭐ |
| **escnn** | Equivariant CNNs | ⭐⭐⭐⭐ | ⭐⭐⭐⭐⭐ | ⭐⭐⭐⭐ | ⭐⭐⭐⭐ |
| **Equiformer** | Equi Transformers | ⭐⭐ | ⭐⭐⭐⭐⭐ | ⭐⭐⭐ | ⭐⭐⭐⭐ |
| **DreamerV3** | World models | ⭐⭐ | ⭐⭐⭐⭐⭐ | ⭐⭐⭐⭐⭐ | ⭐⭐⭐⭐⭐ |
| **EquiBot** | Equi manipulation | ⭐⭐⭐ | ⭐⭐⭐⭐ | ⭐⭐⭐ | ⭐⭐⭐⭐⭐ |

---

## 🎯 Recommendations for Our Research

### For SE(3)-Equivariance: **e3nn**
- ✅ Most general, well-supported
- ✅ Mathematical rigor
- **Use for**: Equivariant Hierarchical (#2)

### For Vision Equivariance: **escnn**
- ✅ Efficient 3D convolutions
- ✅ CNN-like API
- **Use for**: Equivariant visual encoders

### For World Models: **DreamerV3**
- ✅ State-of-the-art
- ✅ Proven architecture
- **Use for**: HiLoop world model

### For Reference: **EquiBot**
- ✅ Direct relevance (equivariant diffusion)
- ✅ Manipulation focus
- **Use for**: Architecture inspiration, baseline

---

## 🚀 Implementation Roadmap

### HiLoop with Equivariance (Optional Enhancement):

**Phase 1: Standard HiLoop**
- World model: Adapt DreamerV3 RSSM (no equivariance)
- Policies: Standard diffusion (Diffusers)

**Phase 2: Add SE(3) Equivariance**
- Replace vision encoder with escnn 3D conv
- Use e3nn for pose representations
- Equivariant world model predictions

**Phase 3: Equivariant Hierarchical** (Idea #2)
- Full SE(3)-equivariant pipeline
- Reference EquiBot architecture
- Combine hierarchy + equivariance

---

## 📚 Learning Resources

### E(3) Equivariance:
- **Tutorial**: e3nn documentation
  - https://docs.e3nn.org/
- **Paper**: "E(3)-equivariant Graph Neural Networks" (Satorras et al., ICML 2021)
- **Course**: Tess Smidt's Euclidean Neural Networks course
  - https://blondegeek.github.io/e3nn_tutorial/

### World Models:
- **Paper**: "World Models" (Ha & Schmidhuber, 2018)
- **Paper**: "Mastering Atari with Discrete World Models" (Hafner et al., 2021)
- **Paper**: "DreamerV3" (Hafner et al., 2023)
- **Blog**: David Ha's blog
  - https://worldmodels.github.io/

---

## 🔧 Installation

```bash
# Equivariant learning
pip install e3nn
pip install escnn

# World models
# DreamerV3 (JAX)
pip install jax jaxlib
git clone https://github.com/danijar/dreamerv3.git

# PyTorch alternatives (community implementations)
pip install dreamerv3-torch  # Unofficial PyTorch port

# Geometric deep learning
pip install torch-geometric
pip install torch-scatter torch-sparse

# EquiBot (clone and install)
git clone https://github.com/UT-Austin-RPL/EquiBot.git
cd EquiBot && pip install -e .
```

---

**Next**: Visualization and debugging tools
