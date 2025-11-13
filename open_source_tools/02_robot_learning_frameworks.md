# Robot Learning Frameworks and Libraries

**Last Updated**: 2025-11-13
**Category**: End-to-end frameworks for robot learning

---

## 🤖 Comprehensive Frameworks

### 1. RoboSuite

**Developer**: Stanford SAIL
**License**: MIT
**GitHub**: https://github.com/ARISE-Initiative/robosuite
**Stars**: ~2K

**Description**:
- Modular manipulation simulation framework
- Built on MuJoCo
- Standardized benchmarks

**Key Features**:
- 8+ robot models (Franka, UR5, Sawyer, etc.)
- 20+ manipulation tasks (pick-place, assembly, etc.)
- Modular design (swap robots, grippers, controllers)
- Domain randomization built-in
- Observation modalities (RGB, depth, proprio, force)

**Example Tasks**:
- Lift, Stack, NutAssembly, Door, Wipe, PickPlace, etc.

**Pros**:
- Well-maintained (active development)
- Good documentation
- Standard benchmark (many papers use)
- Easy to extend (add custom tasks)

**Cons**:
- MuJoCo-only (can't use other simulators)
- Tasks moderate complexity (not CALVIN-level long-horizon)

**Relevance to Our Research**: ⭐⭐⭐⭐⭐
- Standard manipulation benchmark
- Easy to prototype HiLoop
- Good for ablations
- **Use for**: Initial experiments, benchmarking

**Getting Started**:
```python
pip install robosuite
import robosuite as suite

env = suite.make(
    env_name="Lift",
    robots="Panda",
    has_renderer=True,
    use_camera_obs=False,
)

obs = env.reset()
for i in range(1000):
    action = env.action_space.sample()
    obs, reward, done, info = env.step(action)
```

---

### 2. CALVIN (Composable Activities with Long-hori Zon)

**Developer**: University of Freiburg
**License**: MIT
**GitHub**: https://github.com/mees/calvin
**Stars**: ~900

**Description**:
- Language-conditioned long-horizon manipulation
- Benchmark for multi-task learning
- Focuses on generalization

**Key Features**:
- Long-horizon tasks (chaining 5+ subtasks)
- Language instructions
- 34 tasks in shared kitchen environment
- Evaluation: Chain success rate

**Tasks Examples**:
- "Open drawer, pick up block, place in drawer, close drawer, turn on light"
- Tests compositional generalization

**Pros**:
- Long-horizon (realistic complexity)
- Language grounding
- Standard benchmark (many recent papers)
- Realistic tasks

**Cons**:
- Single environment (kitchen only)
- Limited visual diversity
- Slower than RoboSuite (more complex)

**Relevance to Our Research**: ⭐⭐⭐⭐⭐
- **Perfect for HiLoop**: Long-horizon tasks need hierarchy
- Language conditioning
- Standard benchmark
- **Use for**: Main evaluation benchmark

**Getting Started**:
```python
# Installation
git clone https://github.com/mees/calvin.git
cd calvin
pip install -e .

# Load environment
from calvin_env.envs.play_table_env import PlayTableSimEnv
env = PlayTableSimEnv(obs_space="rgb_static", show_gui=True)
```

---

### 3. Gym-Robotics (Now Gymnasium-Robotics)

**Developer**: Farama Foundation (OpenAI fork)
**License**: MIT
**GitHub**: https://github.com/Farama-Foundation/Gymnasium-Robotics
**Stars**: ~300

**Description**:
- Standard RL environments for robotics
- Gymnasium interface (OpenAI Gym successor)
- MuJoCo-based

**Environments**:
- FetchReach, FetchPush, FetchSlide, FetchPickAndPlace
- HandReach, HandManipulateBlock, HandManipulateEgg, HandManipulatePen
- AdroitHand environments

**Pros**:
- Standard Gym API (familiar)
- Well-tested
- Good for RL baselines

**Cons**:
- Limited task diversity
- Simpler than RoboSuite/CALVIN

**Relevance to Our Research**: ⭐⭐⭐
- Good for baselines
- Standard interface
- Not primary benchmark (CALVIN better for hierarchy)

---

### 4. Meta-World

**Developer**: Berkeley / Stanford
**License**: MIT
**GitHub**: https://github.com/Farama-Foundation/Metaworld
**Stars**: ~1.2K

**Description**:
- Meta-learning benchmark
- 50 manipulation tasks
- Multi-task and meta-learning evaluation

**Key Features**:
- 50 distinct manipulation tasks
- Meta-learning splits (ML1, ML10, ML45, MT50)
- Standardized Sawyer robot
- Goal-reaching tasks

**Pros**:
- Large task diversity (50 tasks)
- Meta-learning focus
- Active community

**Cons**:
- Single robot (Sawyer)
- Task complexity moderate

**Relevance to Our Research**: ⭐⭐⭐⭐
- Multi-task evaluation
- Could test: Hierarchical transfer across tasks
- **Use for**: Multi-task experiments

**Getting Started**:
```python
pip install metaworld
import metaworld

ml10 = metaworld.ML10()  # 10 training + 5 testing tasks
env = ml10.train_classes['reach-v2']()
task = ml10.train_tasks[0]
env.set_task(task)
```

---

### 5. RLBench

**Developer**: Imperial College London
**License**: GPL-3.0
**GitHub**: https://github.com/stepjam/RLBench
**Stars**: ~900

**Description**:
- Large-scale manipulation benchmark
- 100 unique tasks
- Built on PyRep/CoppeliaSim

**Key Features**:
- 100 tasks (diverse, realistic)
- Vision-based control
- Demonstrations available
- Task variations (position, color, shape)

**Tasks**:
- From simple (reach, pick) to complex (assembly, tool use)

**Pros**:
- Large task diversity (100 tasks)
- Realistic complexity
- Good for generalization studies

**Cons**:
- CoppeliaSim (not MuJoCo) - separate simulation ecosystem
- Setup more complex
- Slower than MuJoCo-based

**Relevance to Our Research**: ⭐⭐⭐⭐
- Large-scale evaluation
- Task diversity
- **Use for**: Generalization experiments (if time permits)

---

## 🦾 Real Robot Frameworks

### 6. Polymetis

**Developer**: Meta AI (FAIR)
**License**: MIT
**GitHub**: https://github.com/facebookresearch/fairo/tree/main/polymetis
**Stars**: ~800 (fairo repo)

**Description**:
- Real-time robot control library
- Franka Panda support
- Python interface, C++ backend

**Key Features**:
- Low-latency control (1 kHz)
- Torch integration (run policies directly)
- Impedance control
- Easy sim-to-real (same API)

**Pros**:
- Production-ready
- Low latency
- Torch-native

**Cons**:
- Franka-focused (limited robot support)
- Requires real hardware

**Relevance to Our Research**: ⭐⭐⭐⭐
- If deploying on Franka Panda
- Sim-to-real transfer
- **Use for**: Real robot deployment (if available)

---

### 7. DM Robotics

**Developer**: DeepMind
**License**: Apache 2.0
**GitHub**: https://github.com/deepmind/dm_robotics
**Stars**: ~500

**Description**:
- DeepMind's robotics libraries
- MuJoCo integration
- Real robot controllers

**Components**:
- dm_robotics.transformations (SE(3) math)
- dm_robotics.moma (modular manipulation)
- dm_robotics.controllers (joint/Cartesian control)
- dm_robotics.agentflow (task graphs)

**Pros**:
- Production-grade (DeepMind uses)
- Good utilities (transformations, controllers)
- MuJoCo integration

**Cons**:
- Less documentation than others
- Focused on DeepMind's setup

**Relevance to Our Research**: ⭐⭐⭐
- Useful utilities (SE(3) transforms)
- Not primary framework

---

## 🎓 Research Code Releases

### 8. Diffusion Policy (Official)

**Developer**: Columbia / MIT (Chi et al.)
**License**: MIT
**GitHub**: https://github.com/real-stanford/diffusion_policy
**Stars**: ~1.5K

**Description**:
- Official implementation of Diffusion Policy (RSS 2023)
- End-to-end training code
- Pre-trained models

**Key Features**:
- Full training pipeline
- Multiple benchmarks (Push-T, Kitchen, RoboMimic)
- Data processing utilities
- Visualization tools

**Pros**:
- Official implementation (authoritative)
- Well-documented
- Good starting point for diffusion policies

**Cons**:
- Specific to their method (not general framework)
- Code complexity (research code)

**Relevance to Our Research**: ⭐⭐⭐⭐⭐
- **Critical reference**: Our baseline
- Study architecture, training details
- **Use for**: Diffusion policy baseline implementation

---

### 9. 3D Diffuser Actor

**Developer**: ETH Zurich (Ke et al.)
**License**: MIT
**GitHub**: https://github.com/nickgkan/3d_diffuser_actor
**Stars**: ~400

**Description**:
- 3D point cloud diffusion policy
- State-of-the-art on RLBench
- Vision-based manipulation

**Key Features**:
- 3D representations (point clouds)
- Diffusion on 3D action proposals
- Multi-task learning

**Relevance to Our Research**: ⭐⭐⭐⭐
- 3D representations (aligns with TREND 02)
- Good reference for 3D world models
- **Use for**: Compare 3D vs 2D representations

---

### 10. ACT (Action Chunking with Transformers)

**Developer**: Stanford / Toyota Research (Zhao et al.)
**License**: MIT
**GitHub**: https://github.com/tonyzhaozh/act
**Stars**: ~800

**Description**:
- Action chunking for imitation learning
- CVAE + Transformer
- Bimanual manipulation

**Key Features**:
- Predict action sequences (chunks)
- Temporal coherence
- Real robot demos (ALOHA platform)

**Relevance to Our Research**: ⭐⭐⭐⭐
- Baseline for hierarchical comparison
- Action chunking = simple hierarchy
- **Use for**: Ablation vs single-level methods

---

## 📊 Comparison Table

| Framework | Purpose | Simulator | Tasks | Difficulty | Activity | Stars |
|-----------|---------|-----------|-------|------------|----------|-------|
| **RoboSuite** | Benchmark | MuJoCo | 20+ | Medium | ⭐⭐⭐⭐⭐ | 2K |
| **CALVIN** | Long-horizon | MuJoCo | 34 | High | ⭐⭐⭐⭐⭐ | 900 |
| **Meta-World** | Meta-learning | MuJoCo | 50 | Medium | ⭐⭐⭐⭐ | 1.2K |
| **RLBench** | Large-scale | CoppeliaSim | 100 | High | ⭐⭐⭐⭐ | 900 |
| **Diffusion Policy** | Method impl. | Various | N/A | N/A | ⭐⭐⭐⭐ | 1.5K |

---

## 🎯 Recommendations for Our Research

### Primary Benchmark: **CALVIN**
- ✅ Long-horizon (HiLoop's strength)
- ✅ Language conditioning
- ✅ Standard in recent papers
- ✅ Tests hierarchy/composition
- **Use for**: Main evaluation

### Secondary Benchmark: **RoboSuite**
- ✅ Fast iteration
- ✅ Well-maintained
- ✅ Good for ablations
- **Use for**: Development, quick experiments

### Multi-Task: **Meta-World**
- ✅ 50 tasks (generalization)
- ✅ Meta-learning evaluation
- **Use for**: Transfer experiments

### Baseline: **Diffusion Policy Code**
- ✅ Official implementation
- ✅ Study for architecture details
- **Use for**: Reproduce baseline

---

## 🚀 Quick Start for HiLoop Development

### Recommended Stack:
1. **Simulator**: MuJoCo (free, fast, standard)
2. **Framework**: RoboSuite (quick prototyping)
3. **Benchmark**: CALVIN (final evaluation)
4. **Baseline**: Diffusion Policy code (reference)

### Installation:
```bash
# Core
pip install mujoco
pip install robosuite
pip install gymnasium-robotics

# CALVIN
git clone https://github.com/mees/calvin.git
cd calvin && pip install -e .

# Diffusion Policy (for reference)
git clone https://github.com/real-stanford/diffusion_policy.git
```

---

**Next**: Diffusion and flow matching libraries
