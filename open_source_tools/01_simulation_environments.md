# Simulation Environments for Robot Learning

**Last Updated**: 2025-11-13
**Category**: Physics simulators and robot simulation platforms

---

## 🎮 Major Physics Simulators

### 1. MuJoCo (Multi-Joint dynamics with Contact)

**Developer**: DeepMind (originally Roboti LLC)
**License**: Apache 2.0 (free since 2021)
**GitHub**: https://github.com/deepmind/mujoco
**Stars**: ~7.5K

**Description**:
- Industry-standard physics simulator for robotics and reinforcement learning
- Fast, accurate contact dynamics
- Used in hundreds of research papers

**Key Features**:
- High-performance physics (contact, friction, constraints)
- XML-based model specification (MJCF format)
- Python bindings (mujoco-py, dm_control)
- Built-in visualization
- Supports: Manipulation, locomotion, grasping

**Pros**:
- Fast and accurate
- Well-documented
- Large community (DeepMind support)
- Free since 2021 (was $500/year)

**Cons**:
- Learning curve (XML specification)
- Limited photorealistic rendering (functional, not pretty)
- Harder to customize physics (closed-source core)

**Relevance to Our Research**: ⭐⭐⭐⭐⭐
- Standard for RL/manipulation research
- Fast enough for large-scale pre-training
- Good contact dynamics (important for insertion tasks)
- **Use for**: HiLoop pre-training, ablation studies

**Getting Started**:
```python
pip install mujoco
import mujoco
import mujoco.viewer

# Load model
model = mujoco.MjModel.from_xml_path('robot.xml')
data = mujoco.MjData(model)

# Simulate
while True:
    mujoco.mj_step(model, data)
    viewer.sync()
```

---

### 2. PyBullet

**Developer**: Erwin Coumans (Google Brain)
**License**: Zlib (permissive)
**GitHub**: https://github.com/bulletphysics/bullet3
**Stars**: ~11.5K

**Description**:
- Python bindings for Bullet physics engine
- Popular for robotics research (free alternative to MuJoCo pre-2021)
- Many robot models available (URDF support)

**Key Features**:
- Real-time physics simulation
- Built-in GUI
- VR support
- Extensive robot model library (Franka, UR5, etc.)
- Direct contact with Bullet C++ backend

**Pros**:
- Completely free (always)
- Easy to use (Python API)
- Good URDF support
- Large model zoo

**Cons**:
- Slower than MuJoCo (for RL)
- Less accurate contact dynamics
- Community smaller than MuJoCo (now)

**Relevance to Our Research**: ⭐⭐⭐⭐
- Good for prototyping
- Fallback if MuJoCo issues
- Useful for sim-to-sim transfer experiments (train MuJoCo, test PyBullet)

**Getting Started**:
```python
pip install pybullet
import pybullet as p
import pybullet_data

p.connect(p.GUI)
p.setAdditionalSearchPath(pybullet_data.getDataPath())
robot = p.loadURDF("franka_panda/panda.urdf")
```

---

### 3. NVIDIA Isaac Sim / Isaac Gym

**Developer**: NVIDIA
**License**: Proprietary (free for research/education)
**Website**: https://developer.nvidia.com/isaac-sim
**GitHub (Gym)**: https://github.com/NVIDIA-Omniverse/IsaacGymEnvs

**Description**:
- **Isaac Sim**: Photorealistic simulation built on Omniverse
- **Isaac Gym**: GPU-accelerated RL training (thousands of parallel envs)
- State-of-the-art performance for large-scale RL

**Key Features**:
- Photorealistic rendering (ray tracing)
- GPU-accelerated physics (PhysX 5)
- Massive parallelization (10K+ envs on single GPU)
- ROS/ROS2 integration
- Domain randomization built-in

**Pros**:
- Fastest for RL (GPU parallelization)
- Photorealistic (good for sim-to-real vision)
- NVIDIA support
- Growing ecosystem

**Cons**:
- Requires NVIDIA GPU (RTX recommended)
- Steeper learning curve
- Larger installation size (~20GB)
- Less portable (GPU-dependent)

**Relevance to Our Research**: ⭐⭐⭐⭐⭐
- Best for large-scale pre-training (world models, policies)
- Photorealistic rendering (sim-to-real vision)
- Domain randomization (robust policies)
- **Use for**: Massive-scale world model pre-training

**Getting Started**:
```python
# Isaac Gym example
from isaacgym import gymapi
gym = gymapi.acquire_gym()
sim = gym.create_sim(0, 0, gymapi.SIM_PHYSX, params)
```

---

### 4. SAPIEN

**Developer**: UCSD / Stanford
**License**: MIT
**GitHub**: https://github.com/haosulab/SAPIEN
**Stars**: ~400

**Description**:
- Modern simulator focused on manipulation
- Articulated object simulation
- Good contact dynamics

**Key Features**:
- Python API (easy to use)
- Realistic contact/friction
- Built-in rendering (Vulkan)
- PartNet-Mobility dataset integration
- Actor-based architecture

**Pros**:
- Designed for manipulation (not locomotion)
- Good documentation
- Active development
- Free and open-source

**Cons**:
- Smaller community than MuJoCo/PyBullet
- Less battle-tested
- Fewer pre-made environments

**Relevance to Our Research**: ⭐⭐⭐⭐
- Manipulation-focused (aligns with our work)
- Good contact dynamics
- **Use for**: Contact-rich task experiments

---

### 5. Drake

**Developer**: Toyota Research Institute / MIT
**License**: BSD-3-Clause
**GitHub**: https://github.com/RobotLocomotion/drake
**Stars**: ~2K

**Description**:
- Robotics toolbox with simulation, planning, control
- Strong mathematical foundations
- Used in industry (Toyota)

**Key Features**:
- Multi-body dynamics
- Optimization-based planning
- Contact modeling
- C++ and Python
- Model-based control tools

**Pros**:
- Principled contact handling
- Optimization tools (trajectory optimization)
- Industry-grade
- Well-documented

**Cons**:
- Steeper learning curve
- Not primarily RL-focused (more classical robotics)
- Slower iteration (C++ core)

**Relevance to Our Research**: ⭐⭐⭐
- Good for model-based control
- Contact modeling (if needed)
- Not primary choice for RL/learning

---

## 🌍 Embodied AI Environments

### 6. AI2-THOR

**Developer**: Allen Institute for AI
**License**: Apache 2.0
**GitHub**: https://github.com/allenai/ai2thor
**Stars**: ~1K

**Description**:
- Indoor scene simulator
- Mobile manipulation
- Vision-based tasks

**Key Features**:
- Photorealistic indoor scenes
- Object interactions
- Vision tasks (object detection, segmentation)
- Multi-agent support

**Relevance to Our Research**: ⭐⭐
- Not manipulation-focused (more navigation)
- Could use for multi-task learning

---

### 7. Habitat / Habitat 2.0

**Developer**: Meta AI (FAIR)
**License**: MIT
**GitHub**: https://github.com/facebookresearch/habitat-sim
**Stars**: ~2K

**Description**:
- Photorealistic 3D environments
- Embodied AI research
- Fast rendering

**Key Features**:
- High-quality graphics
- Fast (optimized C++)
- Large-scale datasets (Matterport3D, etc.)
- Rearrangement tasks

**Relevance to Our Research**: ⭐⭐⭐
- Good for vision-based manipulation
- Rearrangement tasks relevant
- Less focus on contact dynamics

---

## 📊 Comparison Table

| Simulator | Speed | Contact Quality | Rendering | Learning Curve | Best For | Stars |
|-----------|-------|----------------|-----------|----------------|----------|-------|
| **MuJoCo** | ⭐⭐⭐⭐⭐ | ⭐⭐⭐⭐⭐ | ⭐⭐⭐ | ⭐⭐⭐ | RL, Manipulation | 7.5K |
| **PyBullet** | ⭐⭐⭐⭐ | ⭐⭐⭐ | ⭐⭐⭐ | ⭐⭐⭐⭐⭐ | Prototyping | 11.5K |
| **Isaac Gym** | ⭐⭐⭐⭐⭐⭐ | ⭐⭐⭐⭐ | ⭐⭐⭐⭐⭐ | ⭐⭐ | Large-scale RL | N/A |
| **SAPIEN** | ⭐⭐⭐⭐ | ⭐⭐⭐⭐⭐ | ⭐⭐⭐⭐ | ⭐⭐⭐⭐ | Manipulation | 400 |
| **Drake** | ⭐⭐⭐ | ⭐⭐⭐⭐⭐ | ⭐⭐⭐ | ⭐⭐ | Model-based | 2K |

---

## 🎯 Recommendations for Our Research

### Primary: **MuJoCo**
- ✅ Standard in field (most papers use)
- ✅ Fast and accurate
- ✅ Good contact dynamics
- ✅ Well-supported
- **Use for**: HiLoop development, ablations, benchmarks

### Secondary: **Isaac Gym**
- ✅ Best for massive-scale pre-training
- ✅ GPU acceleration (10K+ parallel envs)
- ✅ Photorealistic rendering
- **Use for**: World model pre-training at scale

### Tertiary: **PyBullet**
- ✅ Fallback option
- ✅ Sim-to-sim transfer experiments
- ✅ Prototyping

### For Contact Tasks: **SAPIEN**
- ✅ Manipulation-focused
- ✅ Good contact dynamics
- **Use for**: Contact-rich task evaluation

---

## 📚 Resources

**MuJoCo**:
- Docs: https://mujoco.readthedocs.io/
- Tutorial: https://github.com/deepmind/mujoco/blob/main/python/tutorial.ipynb
- Models: https://github.com/deepmind/mujoco_menagerie

**Isaac Gym**:
- Docs: https://docs.omniverse.nvidia.com/isaacsim/
- Examples: https://github.com/NVIDIA-Omniverse/IsaacGymEnvs

**PyBullet**:
- Quickstart: https://docs.google.com/document/d/10sXEhzFRSnvFcl3XxNGhnD4N2SedqwdAvK3dsihxVUA

**SAPIEN**:
- Docs: https://sapien.ucsd.edu/docs/
- Tutorials: https://sapien.ucsd.edu/docs/tutorial/

---

**Next**: Robot learning frameworks and libraries
