# Open Source Tools for Robot Learning Research

**Comprehensive Survey of Tools, Libraries, and Frameworks**
**Last Updated**: 2025-11-13
**Target Research**: HiLoop (Hierarchical Diffusion with World Models)

---

## 📚 Contents

1. **[Simulation Environments](01_simulation_environments.md)** - Physics simulators (MuJoCo, Isaac Gym, PyBullet)
2. **[Robot Learning Frameworks](02_robot_learning_frameworks.md)** - Benchmarks (CALVIN, RoboSuite, Meta-World)
3. **[Diffusion & Flow Libraries](03_diffusion_flow_libraries.md)** - Generative models (Diffusers, TorchCFM)
4. **[Datasets & Benchmarks](04_datasets_benchmarks.md)** - Data (RT-X, RoboMimic, D4RL)
5. **[Equivariant & World Models](05_equivariant_world_models.md)** - SE(3) libraries, world model frameworks
6. **[Visualization & Debugging](06_visualization_debugging.md)** - Tracking (W&B), rendering (Open3D)

---

## 🚀 Quick Start: Essential Stack for HiLoop

### Minimal Installation (Get Started in 10 Minutes)

```bash
# Core simulation
pip install mujoco
pip install robosuite

# Diffusion models
pip install diffusers accelerate

# Robot learning
git clone https://github.com/mees/calvin.git
cd calvin && pip install -e .

# Experiment tracking
pip install wandb

# Visualization
pip install imageio imageio-ffmpeg matplotlib seaborn

# Done! You're ready to prototype HiLoop
```

---

## 🎯 Recommended Tools by Research Component

### For HiLoop Development:

| Component | Primary Tool | Alternative | Why |
|-----------|-------------|-------------|-----|
| **Simulator** | MuJoCo | Isaac Gym | Fast, standard, well-documented |
| **Benchmark** | CALVIN | RoboSuite | Long-horizon tasks (HiLoop strength) |
| **Diffusion** | Diffusers | TorchCFM | Mature, well-tested, good schedulers |
| **World Model** | DreamerV3 | Custom RSSM | State-of-the-art architecture |
| **Tracking** | W&B | TensorBoard | Best UI, free for academics |
| **3D Viz** | Open3D | PyVista | Fast, point cloud focus |
| **Dataset** | RoboMimic | RT-X | Clean, curated, easy start |

---

## 📊 Tool Categories Overview

### 🎮 Simulation (6 tools reviewed)
- **Best Overall**: MuJoCo (fast, accurate, standard)
- **For Scale**: Isaac Gym (10K parallel envs, GPU-accelerated)
- **For Prototyping**: PyBullet (easy, free always)
- **For Contact**: SAPIEN (manipulation-focused)

### 🤖 Frameworks (10 tools reviewed)
- **Best Benchmark**: CALVIN (long-horizon, language)
- **For Development**: RoboSuite (fast iteration)
- **For Multi-task**: Meta-World (50 tasks)
- **For Reference**: Diffusion Policy (official code)

### 🌊 Diffusion/Flow (7 libraries reviewed)
- **Best Diffusion**: Diffusers (HuggingFace, 23K stars)
- **For Flow Matching**: TorchCFM (fast, 5-10x speedup)
- **For Continuous-Time**: Torchdiffeq (Neural ODEs)
- **For Optimization**: k-diffusion (fast samplers)

### 📊 Datasets (10 datasets reviewed)
- **Largest**: RT-X (1M episodes, 22 robots)
- **Cleanest**: RoboMimic (curated, high-quality)
- **For Offline RL**: D4RL (standard benchmark)
- **Real-World**: BridgeData V2 (60K real demos)

### 🔄 Equivariant/World Models (10 libraries reviewed)
- **For SE(3)**: e3nn (general, rigorous)
- **For Vision**: escnn (efficient 3D conv)
- **For World Models**: DreamerV3 (state-of-the-art)
- **For Reference**: EquiBot (equivariant diffusion)

### 📈 Visualization (12 tools reviewed)
- **Tracking**: W&B (best UI, collaborative)
- **Video**: Imageio (simple, effective)
- **3D**: Open3D (point clouds, fast)
- **Profiling**: PyTorch Profiler (find bottlenecks)

---

## 🏆 Top 10 Most Important Tools

### Must-Have (Install These First):
1. **MuJoCo** - Simulation foundation
2. **Diffusers** - Diffusion models
3. **CALVIN** - Benchmark evaluation
4. **W&B** - Experiment tracking
5. **RoboMimic** - Clean datasets

### Highly Recommended:
6. **TorchCFM** - Flow matching (faster than diffusion)
7. **e3nn** - SE(3) equivariance (data efficiency)
8. **DreamerV3** - World model architecture
9. **Open3D** - 3D visualization
10. **Imageio** - Video logging

---

## 📖 Decision Trees

### "Which Simulator Should I Use?"

```
Start here: Do you need massive parallelization?
├─ YES: Isaac Gym (10K+ parallel environments)
└─ NO: Is contact dynamics critical?
    ├─ YES: SAPIEN or MuJoCo (high-quality contact)
    └─ NO: Is it your first time?
        ├─ YES: RoboSuite on MuJoCo (batteries included)
        └─ NO: MuJoCo (standard, flexible)
```

### "Which Benchmark Should I Evaluate On?"

```
What's your focus?
├─ Long-horizon, hierarchy: CALVIN ✅ (HiLoop's strength)
├─ Multi-task learning: Meta-World (50 tasks)
├─ Imitation learning: RoboMimic (clean demos)
├─ Offline RL: D4RL (standard offline benchmark)
└─ Large-scale: RLBench (100 tasks)
```

### "Diffusion or Flow Matching?"

```
What's your priority?
├─ Stability, maturity: Diffusion (Diffusers) ✅
├─ Speed (5-10x faster): Flow Matching (TorchCFM) ✅
├─ Continuous-time: Torchdiffeq + Flow Matching
└─ Just starting: Diffusers (better docs)

Recommendation: Start with Diffusion, switch to Flow if speed bottleneck
```

### "How to Track Experiments?"

```
What's your setup?
├─ Team collaboration: W&B ✅ (best UI, sharing)
├─ Privacy-critical: TensorBoard (local-only)
├─ Production deployment: MLflow (full ML lifecycle)
└─ Just learning: TensorBoard (free, simple)
```

---

## 🔧 Complete Installation Script

### All-in-One Setup for HiLoop Research:

```bash
#!/bin/bash
# HiLoop Development Environment Setup

echo "🚀 Installing HiLoop research stack..."

# 1. Core dependencies
pip install torch torchvision torchaudio --index-url https://download.pytorch.org/whl/cu118

# 2. Simulation
pip install mujoco
pip install robosuite
pip install gymnasium-robotics

# 3. Diffusion & Flow
pip install diffusers accelerate transformers
pip install torchcfm
pip install torchdiffeq

# 4. Equivariance & World Models
pip install e3nn escnn

# 5. Benchmarks & Datasets
git clone https://github.com/mees/calvin.git && cd calvin && pip install -e . && cd ..
pip install metaworld
pip install d4rl

# 6. Experiment Tracking
pip install wandb

# 7. Visualization
pip install matplotlib seaborn plotly
pip install imageio imageio-ffmpeg
pip install opencv-python
pip install open3d

# 8. Utilities
pip install einops  # Tensor operations
pip install hydra-core  # Config management
pip install tqdm  # Progress bars
pip install tensorboard  # Backup tracking

# 9. Data handling
pip install h5py  # For RoboMimic datasets
pip install zarr  # For large-scale data

# Optional: Large-scale (requires NVIDIA GPU)
# pip install nvidia-pyindex
# pip install isaacgym  # Follow official install instructions

echo "✅ Installation complete!"
echo "🎯 Ready to start HiLoop development"
```

---

## 📦 Containerized Setup (Docker)

### Dockerfile for Reproducible Environment:

```dockerfile
FROM nvidia/cuda:11.8.0-cudnn8-devel-ubuntu22.04

# Install Python
RUN apt-get update && apt-get install -y \
    python3.10 python3-pip git wget \
    libgl1-mesa-glx libglib2.0-0 \
    && rm -rf /var/lib/apt/lists/*

# Install MuJoCo
RUN mkdir -p /root/.mujoco && \
    cd /root/.mujoco && \
    wget https://github.com/deepmind/mujoco/releases/download/2.3.7/mujoco-2.3.7-linux-x86_64.tar.gz && \
    tar -xzf mujoco-2.3.7-linux-x86_64.tar.gz

ENV LD_LIBRARY_PATH=/root/.mujoco/mujoco-2.3.7/lib:$LD_LIBRARY_PATH

# Install Python packages
COPY requirements.txt /tmp/
RUN pip3 install -r /tmp/requirements.txt

# Set working directory
WORKDIR /workspace

CMD ["/bin/bash"]
```

---

## 🎓 Learning Path

### If You're New to Robot Learning:

**Week 1: Basics**
1. Install MuJoCo + RoboSuite
2. Run example environments
3. Collect demonstrations (keyboard control)

**Week 2: Imitation Learning**
4. Train behavior cloning baseline (simple MLP)
5. Visualize results (W&B)
6. Study Diffusion Policy code

**Week 3: Diffusion Models**
7. Read Diffusion Policy paper
8. Implement simple diffusion policy (Diffusers)
9. Train on RoboMimic Lift task

**Week 4: Hierarchy**
10. Read HiLoop-related papers (ChainedDiffuser, Subgoal Diffuser)
11. Implement waypoint generation (high-level)
12. Add execution policy (low-level)

**Week 5: World Models**
13. Study DreamerV3 architecture
14. Implement simple dynamics predictor
15. Integrate with hierarchical policy

**Week 6+: HiLoop**
16. Combine all components
17. Evaluate on CALVIN
18. Iterate and improve

---

## 📚 Essential Papers for Each Tool Category

### Simulation:
- MuJoCo: "MuJoCo: A physics engine for model-based control" (Todorov et al., IROS 2012)

### Diffusion Models:
- "Denoising Diffusion Probabilistic Models" (Ho et al., NeurIPS 2020)
- "Diffusion Policy" (Chi et al., RSS 2023)

### Flow Matching:
- "Flow Matching for Generative Modeling" (Lipman et al., ICLR 2023)

### World Models:
- "World Models" (Ha & Schmidhuber, 2018)
- "Mastering Atari with Discrete World Models" (Hafner et al., 2021)

### Equivariance:
- "E(3)-Equivariant Graph Neural Networks" (Satorras et al., ICML 2021)
- "EquiBot" (Xie et al., CoRL 2024)

---

## 🔗 Quick Links

### Official Websites:
- MuJoCo: https://mujoco.org/
- CALVIN: https://github.com/mees/calvin
- Diffusers: https://huggingface.co/docs/diffusers/
- W&B: https://wandb.ai/
- Open3D: http://www.open3d.org/

### Community:
- Robotics Discord: https://discord.gg/robotics
- /r/MachineLearning: https://reddit.com/r/MachineLearning
- Papers with Code: https://paperswithcode.com/area/robots

### Getting Help:
- GitHub Issues (各repo)
- Stack Overflow (tag: robotics, pytorch, mujoco)
- Twitter/X: Follow @_diffsim, @hardmaru, @jannerm_

---

## 🐛 Common Issues & Solutions

### Problem: MuJoCo not rendering
```bash
# Solution: Install missing graphics libraries
sudo apt-get install libgl1-mesa-glx libgl1-mesa-dev
export MUJOCO_GL=egl  # or osmesa
```

### Problem: CUDA out of memory
```python
# Solution: Reduce batch size, enable gradient checkpointing
import torch
torch.cuda.empty_cache()

# Use gradient checkpointing (Diffusers)
model.enable_gradient_checkpointing()
```

### Problem: CALVIN environment not loading
```bash
# Solution: Check data path
cd calvin
./download_data.sh  # Download required assets
```

### Problem: W&B login issues
```bash
# Solution: Set API key manually
export WANDB_API_KEY=your_key_here
# Or use: wandb login
```

---

## 📈 Performance Optimization Tips

### For Training Speed:
1. **Use mixed precision**: `accelerate` library
2. **Gradient checkpointing**: Save memory
3. **DataLoader workers**: `num_workers=4-8`
4. **Compile models**: `torch.compile()` (PyTorch 2.0+)

### For Inference Speed:
1. **Flow matching**: 5-10x faster than diffusion
2. **Fewer denoising steps**: DDIM (50 steps) vs DDPM (1000 steps)
3. **Model distillation**: Smaller models
4. **TorchScript/ONNX**: Optimize for deployment

### For Memory:
1. **Gradient accumulation**: Simulate larger batches
2. **16-bit precision**: `torch.float16`
3. **Offload to CPU**: `accelerate` library
4. **Efficient attention**: Flash Attention 2

---

## 🎯 Tool Recommendations by Experience Level

### Beginner (First Robot Learning Project):
- Simulator: **RoboSuite** (batteries included)
- Model: **Diffusion Policy** (official code, good tutorial)
- Tracking: **TensorBoard** (simple, local)
- Dataset: **RoboMimic Lift** (small, clean)

### Intermediate (Some RL/ML Experience):
- Simulator: **MuJoCo** (standard, flexible)
- Model: **Diffusers** (customizable)
- Tracking: **W&B** (professional, collaborative)
- Benchmark: **CALVIN** (realistic complexity)

### Advanced (Research Contributions):
- Simulator: **Isaac Gym** (massive scale) or **SAPIEN** (contact)
- Model: **Custom** (implement novel ideas)
- Equivariance: **e3nn** (if applicable)
- Dataset: **RT-X** (large-scale pre-training)

---

## 🔮 Future Trends (What to Watch)

### Emerging Tools:
1. **JAX-based simulators**: MJX (MuJoCo in JAX), faster
2. **Unified robotics APIs**: Universal robot interfaces
3. **Cloud robotics platforms**: Remote evaluation
4. **Foundation model APIs**: Control FMs (when available)

### Technologies to Learn:
1. **JAX**: Growing in ML research (Flax, Haiku)
2. **Ray**: Distributed training, hyperparameter tuning
3. **Hydra**: Configuration management
4. **Modal**: Cloud deployment made easy

---

## 📝 Citation

If you find this tool survey helpful:

```bibtex
@misc{robot_learning_tools_2024,
  title={Open Source Tools for Robot Learning Research: A Comprehensive Survey},
  author={AI Research Team},
  year={2024},
  note={Survey of 60+ tools across 6 categories}
}
```

---

## 🤝 Contributing

Found a missing tool or outdated information?
- Open an issue or PR in the repository
- Email: [your contact]
- Tools must be: Open-source, actively maintained, relevant to robot learning

---

## 📅 Update Schedule

This document is updated:
- **Monthly**: New tool releases, major updates
- **Quarterly**: Comprehensive review, deprecations
- **As needed**: Critical bug fixes, security updates

**Last major update**: 2025-11-13
**Next scheduled update**: 2025-12-13

---

## ✅ Checklist: Ready for HiLoop Development?

- [ ] MuJoCo installed and running
- [ ] RoboSuite environments working
- [ ] CALVIN benchmark set up
- [ ] Diffusers library installed
- [ ] W&B account created (or TensorBoard ready)
- [ ] Imageio working (can save videos)
- [ ] Open3D installed (for 3D viz)
- [ ] Studied Diffusion Policy code
- [ ] Read HiLoop-related papers
- [ ] GPU available (recommended: RTX 3090/4090 or A100)

**All checked?** You're ready to build HiLoop! 🚀

---

**Total Tools Surveyed**: 60+
**Categories**: 6
**Code Examples**: 50+
**Installation Scripts**: 3

**Happy building! 🤖✨**
