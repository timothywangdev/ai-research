# Diffusion and Flow Matching Libraries

**Last Updated**: 2025-11-13
**Category**: Generative modeling libraries for diffusion and flow matching

---

## 🌊 Diffusion Model Libraries

### 1. Diffusers (Hugging Face)

**Developer**: Hugging Face
**License**: Apache 2.0
**GitHub**: https://github.com/huggingface/diffusers
**Stars**: ~23K

**Description**:
- State-of-the-art diffusion models library
- Easy-to-use API (like Transformers library)
- Pre-trained models for images, audio, video

**Key Features**:
- Multiple diffusion variants (DDPM, DDIM, PNDM, etc.)
- Schedulers (noise schedules, sampling strategies)
- Pre-trained models (Stable Diffusion, etc.)
- Pipeline abstractions
- Training utilities

**Pros**:
- Industry-standard (most popular)
- Excellent documentation
- Active development
- Large community
- Easy to extend

**Cons**:
- Focused on images/video (not robotics-specific)
- Some overhead (abstraction layers)

**Relevance to Our Research**: ⭐⭐⭐⭐⭐
- **Best starting point** for diffusion implementation
- Well-tested schedulers
- Training utilities
- **Use for**: HiLoop diffusion policy implementation

**Getting Started**:
```python
pip install diffusers

from diffusers import DDPMScheduler, UNet2DModel

# Define model
model = UNet2DModel(
    sample_size=64,
    in_channels=3,
    out_channels=3,
    layers_per_block=2,
    block_out_channels=(64, 128, 256),
)

# Scheduler
scheduler = DDPMScheduler(num_train_timesteps=1000)

# Training loop
noise = torch.randn_like(x)
timesteps = torch.randint(0, scheduler.num_train_timesteps, (batch_size,))
noisy_x = scheduler.add_noise(x, noise, timesteps)
pred_noise = model(noisy_x, timesteps).sample
loss = F.mse_loss(pred_noise, noise)
```

**Key Schedulers for Robotics**:
- DDPM: Original (slow but accurate)
- DDIM: Faster sampling (10-50 steps vs 1000)
- DPM-Solver: Even faster (5-20 steps)

---

### 2. Torchdiffeq (Neural ODEs)

**Developer**: RTQichen (Chen et al., NeurIPS 2018)
**License**: MIT
**GitHub**: https://github.com/rtqichen/torchdiffeq
**Stars**: ~5K

**Description**:
- Differential equation solvers in PyTorch
- Foundation for continuous normalizing flows
- Neural ODE implementation

**Key Features**:
- ODE solvers (Dopri5, Euler, RK4, etc.)
- Adjoint method (memory-efficient backprop)
- Adaptive step size
- Event handling

**Pros**:
- Clean API
- Memory-efficient
- Well-tested solvers

**Cons**:
- Lower-level (need to build on top)
- Slower than discrete methods

**Relevance to Our Research**: ⭐⭐⭐⭐
- For continuous-time policies
- Flow matching implementation
- World model dynamics (continuous)
- **Use for**: Flow matching (#3 idea), continuous-time WM

**Getting Started**:
```python
pip install torchdiffeq

from torchdiffeq import odeint

# Define dynamics
def dynamics(t, y):
    return -y  # Simple ODE: dy/dt = -y

# Solve
t = torch.linspace(0, 1, 100)
y0 = torch.tensor([1.0])
solution = odeint(dynamics, y0, t)
```

---

### 3. Torchsde (Stochastic Differential Equations)

**Developer**: Google Research (Patrick Kidger)
**License**: Apache 2.0
**GitHub**: https://github.com/google-research/torchsde
**Stars**: ~1.5K

**Description**:
- Stochastic differential equation solvers
- Score-based generative models
- SDE formulation of diffusion

**Key Features**:
- SDE solvers (Euler-Maruyama, Milstein, etc.)
- Brownian motion handling
- Adjoint method for SDEs
- Score matching utilities

**Pros**:
- SDE framework (more general than ODEs)
- Good for score-based models
- Principled stochasticity

**Cons**:
- More complex than ODE
- Slower inference

**Relevance to Our Research**: ⭐⭐⭐
- For stochastic world models
- Score-based diffusion (alternative formulation)
- **Use for**: Advanced diffusion variants

---

## 🔄 Flow Matching Libraries

### 4. TorchCFM (Conditional Flow Matching)

**Developer**: Atanackovic et al. (Facebook AI)
**License**: MIT
**GitHub**: https://github.com/atong01/conditional-flow-matching
**Stars**: ~800

**Description**:
- Official conditional flow matching implementation
- Fast and efficient
- Multiple flow matching variants

**Key Features**:
- Optimal transport conditional flow matching (OT-CFM)
- Straight paths (rectified flows)
- Training utilities
- Sampling algorithms

**Pros**:
- State-of-the-art flow matching
- Fast training (vs diffusion)
- Clean implementation

**Cons**:
- Newer (less battle-tested than diffusers)
- Smaller community

**Relevance to Our Research**: ⭐⭐⭐⭐⭐
- **Critical for Flow Matching idea (#3)**
- 5-10x faster than diffusion
- **Use for**: Flow matching hierarchical policies

**Getting Started**:
```python
pip install torchcfm

from torchcfm import ConditionalFlowMatcher

# Define flow matcher
cfm = ConditionalFlowMatcher(sigma=0.0)  # Deterministic (OT-CFM)

# Training
x0 = data  # Source
x1 = target  # Target
t = torch.rand(batch_size, 1)
xt, ut = cfm.sample_location_and_conditional_flow(x0, x1, t)

# Model predicts velocity
vt = model(xt, t)
loss = F.mse_loss(vt, ut)
```

**Flow Matching Variants**:
- OT-CFM: Optimal transport (straight paths)
- Rectified Flow: Simpler training
- Stochastic Interpolants: Generalization

---

### 5. FlowMat (Custom Implementation)

**Note**: Many flow matching implementations are custom per paper

**Key Papers with Code**:
- **Flow Matching for Generative Modeling** (Lipman et al., ICLR 2023)
  - GitHub: https://github.com/facebookresearch/flow_matching
- **Riemannian Flow Matching** (Chen et al., ICLR 2024)
  - GitHub: https://github.com/facebookresearch/riemannian-fm
- **SE(3) Flow Matching** (for proteins)
  - GitHub: https://github.com/microsoft/protein-frame-flow

**Relevance**: ⭐⭐⭐⭐
- Study implementations
- Adapt for robotics
- **Use for**: SE(3)-equivariant flow matching

---

## 🎯 Score-Based Models

### 6. Score-SDE

**Developer**: Yang Song (Stanford/OpenAI)
**License**: Apache 2.0
**GitHub**: https://github.com/yang-song/score_sde_pytorch
**Stars**: ~2K

**Description**:
- Score-based generative models via SDEs
- Unified framework for diffusion
- State-of-the-art image generation (2021)

**Key Features**:
- Multiple SDE formulations (VP, VE, subVP)
- Predictor-corrector sampling
- Likelihood computation
- Training on various datasets

**Pros**:
- Theoretically principled
- Flexible framework
- Good documentation

**Cons**:
- Image-focused (not robotics)
- Complex (steep learning curve)

**Relevance to Our Research**: ⭐⭐⭐
- Theoretical understanding
- Advanced diffusion techniques
- **Use for**: If need advanced diffusion features

---

## 🛠️ Utility Libraries

### 7. k-diffusion

**Developer**: Katherine Crowson
**License**: MIT
**GitHub**: https://github.com/crowsonkb/k-diffusion
**Stars**: ~1.5K

**Description**:
- Diffusion model toolkit
- Karras et al. noise schedules
- Sampling improvements

**Key Features**:
- Advanced schedulers
- DPM-Solver, DPM-Solver++
- Heun sampler
- Classifier-free guidance

**Pros**:
- Fast samplers
- Good noise schedules
- Production-ready

**Cons**:
- Less documentation
- Focused on images

**Relevance to Our Research**: ⭐⭐⭐
- Fast sampling (important for robotics)
- **Use for**: Optimize diffusion sampling speed

---

## 📊 Comparison Table

| Library | Type | Speed | Ease of Use | Robotics Focus | Stars | Best For |
|---------|------|-------|-------------|----------------|-------|----------|
| **Diffusers** | Diffusion | ⭐⭐⭐ | ⭐⭐⭐⭐⭐ | ⭐⭐ | 23K | General diffusion |
| **TorchCFM** | Flow | ⭐⭐⭐⭐⭐ | ⭐⭐⭐⭐ | ⭐⭐⭐ | 800 | Flow matching |
| **Torchdiffeq** | ODE | ⭐⭐⭐⭐ | ⭐⭐⭐⭐ | ⭐⭐⭐ | 5K | Continuous-time |
| **Torchsde** | SDE | ⭐⭐⭐ | ⭐⭐⭐ | ⭐⭐ | 1.5K | Stochastic models |
| **Score-SDE** | SDE | ⭐⭐⭐ | ⭐⭐ | ⭐⭐ | 2K | Theory/advanced |
| **k-diffusion** | Diffusion | ⭐⭐⭐⭐ | ⭐⭐⭐ | ⭐⭐ | 1.5K | Fast sampling |

---

## 🎯 Recommendations for Our Research

### For HiLoop Diffusion Policy: **Diffusers**
- ✅ Most mature, well-documented
- ✅ Good schedulers (DDIM, DPM-Solver)
- ✅ Easy to customize
- ✅ Training utilities
- **Use for**: HiLoop waypoint + execution policies

### For Flow Matching (#3 Idea): **TorchCFM**
- ✅ State-of-the-art flow matching
- ✅ 5-10x faster than diffusion
- ✅ Clean API
- **Use for**: Flow matching hierarchical policies

### For Continuous-Time: **Torchdiffeq**
- ✅ Neural ODE foundation
- ✅ Clean, efficient
- **Use for**: Continuous-time world model, flow matching

### For Optimization: **k-diffusion**
- ✅ Fast samplers (DPM-Solver++)
- **Use for**: Optimize inference speed (if diffusion too slow)

---

## 🚀 Implementation Recommendations

### HiLoop Stack:

**Waypoint Generation** (High-level):
```python
from diffusers import DDIMScheduler, UNet1DModel

# 1D UNet for action sequences
waypoint_model = UNet1DModel(...)
waypoint_scheduler = DDIMScheduler(num_train_timesteps=100)
```

**Execution Policy** (Low-level):
```python
# Same architecture, different training data
execution_model = UNet1DModel(...)
execution_scheduler = DDIMScheduler(num_train_timesteps=50)
```

**Alternative: Flow Matching**
```python
from torchcfm import ConditionalFlowMatcher

waypoint_cfm = ConditionalFlowMatcher(sigma=0.0)
# 5-10x faster sampling → better for online refinement
```

---

## 📚 Learning Resources

### Diffusion Models:
- **Tutorial**: Hugging Face Diffusion Course
  - https://github.com/huggingface/diffusion-models-class
- **Paper**: "Denoising Diffusion Probabilistic Models" (Ho et al., NeurIPS 2020)
- **Blog**: Lil'Log - "What are Diffusion Models?"
  - https://lilianweng.github.io/posts/2021-07-11-diffusion-models/

### Flow Matching:
- **Paper**: "Flow Matching for Generative Modeling" (Lipman et al., ICLR 2023)
- **Tutorial**: TorchCFM documentation
  - https://atong01.github.io/conditional-flow-matching/
- **Blog**: "Flow Matching Guide" (Kilcher)

### Neural ODEs:
- **Paper**: "Neural Ordinary Differential Equations" (Chen et al., NeurIPS 2018)
- **Tutorial**: Torchdiffeq examples
  - https://github.com/rtqichen/torchdiffeq/tree/master/examples

---

## 🔧 Installation Commands

```bash
# Core libraries
pip install diffusers
pip install accelerate  # For fast training
pip install transformers  # For conditional inputs

# Flow matching
pip install torchcfm

# Neural ODEs/SDEs
pip install torchdiffeq
pip install torchsde

# Utilities
pip install einops  # Tensor operations
pip install wandb  # Experiment tracking

# Optional: Advanced samplers
pip install k-diffusion
```

---

**Next**: Datasets and benchmarks
