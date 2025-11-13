# Robot Learning Datasets and Benchmarks

**Last Updated**: 2025-11-13
**Category**: Large-scale datasets, benchmarks, and evaluation platforms

---

## 📊 Large-Scale Robot Datasets

### 1. Open X-Embodiment (RT-X)

**Developer**: Google DeepMind + 20+ institutions
**License**: Various (mostly permissive)
**Website**: https://robotics-transformer-x.github.io/
**Paper**: "Open X-Embodiment: Robotic Learning Datasets and RT-X Models" (2023)

**Description**:
- Largest multi-robot dataset
- 1M+ trajectories from 22 robot embodiments
- 527 skills across 160,226 tasks
- Goal: Cross-embodiment generalization

**Statistics**:
- Size: ~1 million episodes
- Robots: 22 different (Franka, UR5, Sawyer, etc.)
- Tasks: Pick-place, pushing, drawer opening, cleaning, etc.
- Observation: RGB images + proprioception
- Format: RLDS (tfds)

**Datasets Included**:
- BridgeData V2
- RT-1 Robotics
- Language-Table
- Austin Buds Dataset
- BC-Z
- And 15+ more

**Pros**:
- Massive scale (1M episodes)
- Diverse embodiments
- Language annotations
- Pre-trained models (RT-1, RT-2, RT-X)

**Cons**:
- TensorFlow format (not PyTorch-native)
- Large download size (~multiple TB)
- Quality varies across subsets
- Preprocessing needed

**Relevance to Our Research**: ⭐⭐⭐⭐⭐
- **Foundation model pre-training**: World model, policies
- Cross-embodiment transfer
- Language grounding
- **Use for**: Large-scale pre-training (if compute available)

**Access**:
```python
# Via RLDS
pip install rlds tensorflow_datasets

import tensorflow_datasets as tfds

dataset = tfds.load('fractal20220817_data', split='train')
for episode in dataset:
    for step in episode['steps']:
        obs = step['observation']
        action = step['action']
```

---

### 2. RoboMimic Datasets

**Developer**: Stanford IRIS Lab
**License**: MIT
**GitHub**: https://github.com/ARISE-Initiative/robomimic
**Website**: https://robomimic.github.io/

**Description**:
- Curated imitation learning datasets
- High-quality human demonstrations
- Multiple benchmark tasks
- Standard evaluation

**Datasets**:
- **Lift** (PH-Low): Lift object, proficient-human, low-dimensional obs
- **Can** (PH-Image): Pick can and place, image observations
- **Square** (MH): Insert peg, multi-human quality
- **Transport**: Bimanual manipulation

**Quality Levels**:
- Proficient-Human (PH): Expert demos
- Multi-Human (MH): Mixed quality
- Machine-Generated (MG): Learned policy rollouts

**Observation Types**:
- Low-dimensional: Robot state + object poses
- Image: RGB cameras (multiple views)
- Depth: Depth images

**Pros**:
- High-quality demonstrations
- Standard benchmark (many papers use)
- Clean data (processed)
- PyTorch-friendly (HDF5 format)

**Cons**:
- Limited scale (~200-1000 demos per task)
- Fixed tasks (4 main tasks)
- Simulated only

**Relevance to Our Research**: ⭐⭐⭐⭐⭐
- **Standard imitation learning benchmark**
- Clean, curated data
- Good for ablations
- **Use for**: Baseline comparisons, initial experiments

**Access**:
```bash
# Download datasets
cd robomimic
python robomimic/scripts/download_datasets.py --tasks lift can square

# Use in code
from robomimic.utils.file_utils import policy_from_checkpoint
dataset = h5py.File('datasets/lift/ph/low_dim.hdf5', 'r')
```

---

### 3. D4RL (Datasets for Deep Data-Driven RL)

**Developer**: UC Berkeley (Fu et al.)
**License**: MIT
**GitHub**: https://github.com/Farama-Foundation/D4RL
**Paper**: "D4RL: Datasets for Deep Data-Driven Reinforcement Learning" (2020)

**Description**:
- Offline RL benchmark
- Multiple domains (manipulation, locomotion, navigation)
- Various data quality levels

**Manipulation Tasks**:
- Adroit Hand: Pen, Hammer, Door, Relocate
- FrankaKitchen: Kitchen manipulation (7 tasks)

**Data Types**:
- Expert: High-quality demos
- Medium: Mixed quality
- Random: Random policy
- Medium-Replay: RL buffer data

**Pros**:
- Standard offline RL benchmark
- Multiple data quality levels
- Good for offline→online studies

**Cons**:
- Smaller scale than RT-X
- Fixed tasks
- Simulated only

**Relevance to Our Research**: ⭐⭐⭐⭐
- Offline RL baselines
- Data quality ablations
- **Use for**: Diffusion + RL hybrid (#4 idea)

---

### 4. BridgeData V2

**Developer**: UC Berkeley / Stanford
**License**: CC BY 4.0
**Website**: https://rail-berkeley.github.io/bridgedata/
**Paper**: "BridgeData V2" (2024)

**Description**:
- Real-world manipulation dataset
- Diverse tasks and objects
- Multi-environment

**Statistics**:
- 60,096 trajectories
- 24 environments
- 155 objects
- Language annotations

**Tasks**:
- Pick-and-place variations
- Pushing, opening, closing
- Rearrangement
- Tool use

**Pros**:
- Real robot data (not sim)
- Diverse scenes
- Language conditioning
- High-quality

**Cons**:
- Single robot (WidowX)
- Moderate scale (60K)

**Relevance to Our Research**: ⭐⭐⭐⭐
- Real-world data
- Language grounding
- **Use for**: Real robot fine-tuning (if WidowX-compatible)

---

## 🎯 Benchmark Environments

### 5. CALVIN (Covered in frameworks, but key benchmark)

**Statistics**:
- 34 tasks
- Language instructions
- Long-horizon (5+ subtasks)
- 4 training environments (ABCD)

**Relevance**: ⭐⭐⭐⭐⭐
- **Primary evaluation benchmark**
- Tests long-horizon, hierarchy
- Standard in recent papers

---

### 6. ManiskillChallenge

**Developer**: UC San Diego
**License**: MIT
**GitHub**: https://github.com/haosulab/ManiSkill
**Website**: https://sapien.ucsd.edu/challenges/maniskill/

**Description**:
- Annual manipulation challenge
- Diverse manipulation tasks
- Sim-to-real track

**Tasks (2024)**:
- Pick-and-place
- Assembly
- Soft-body manipulation
- Mobile manipulation

**Pros**:
- Competition format (motivating)
- Evaluation server
- Prizes (if participating)
- Growing community

**Cons**:
- Annual (not continuous)
- SAPIEN-specific

**Relevance to Our Research**: ⭐⭐⭐
- Good for competitions
- Visibility (if submit)

---

## 📹 Video Datasets (for Learning from Observation)

### 7. Ego4D

**Developer**: Meta AI + universities
**License**: Various
**Website**: https://ego4d-data.org/

**Description**:
- Egocentric video dataset
- 3,670 hours of video
- First-person manipulation

**Tasks**:
- Action recognition
- Object interaction
- Hands manipulation

**Relevance to Our Research**: ⭐⭐
- Video pre-training (if using video models)
- Action affordances from videos
- Not direct manipulation data

---

### 8. Epic-Kitchens

**Developer**: University of Bristol / University of Catania
**License**: Research use
**Website**: https://epic-kitchens.github.io/

**Description**:
- Kitchen activities dataset
- 100 hours of recording
- Fine-grained action labels

**Relevance to Our Research**: ⭐⭐
- Kitchen manipulation videos
- Could pre-train visual representations
- Not robot-specific

---

## 🔍 Specialized Datasets

### 9. ContactDB (Contact and Grasp Dataset)

**Developer**: Yale
**License**: CC BY-NC-SA 4.0
**Website**: https://contactdb.cc.gatech.edu/

**Description**:
- Contact data during grasping
- Pressure maps
- 3D hand poses
- 50 objects

**Pros**:
- Contact-focused (rare)
- High-quality contact sensing

**Cons**:
- Human grasps (not robot)
- Small scale (50 objects)

**Relevance to Our Research**: ⭐⭐⭐
- Contact dynamics (BREAKTHROUGH 08)
- Learn contact patterns
- **Use for**: Contact-aware model training (if applicable)

---

### 10. YCB Object and Model Set

**Developer**: Yale / Columbia / Berkeley
**License**: CC BY 4.0
**Website**: http://ycbobjects.org/

**Description**:
- Standard object set for benchmarking
- 77 objects (household items)
- 3D meshes, textures, point clouds

**Objects**:
- Food items, tools, kitchen, etc.
- Realistic models

**Pros**:
- Standard in field (many papers use)
- High-quality models
- Free

**Cons**:
- Objects only (not full dataset)
- Need to create tasks

**Relevance to Our Research**: ⭐⭐⭐⭐
- Standard objects for sim
- Add to RoboSuite/CALVIN
- **Use for**: Custom task creation

---

## 📊 Dataset Comparison

| Dataset | Scale | Real/Sim | Diversity | Language | Quality | Use Case |
|---------|-------|----------|-----------|----------|---------|----------|
| **RT-X** | 1M | Both | ⭐⭐⭐⭐⭐ | ✅ | ⭐⭐⭐ | Pre-training |
| **RoboMimic** | 1K | Sim | ⭐⭐ | ❌ | ⭐⭐⭐⭐⭐ | Benchmarks |
| **D4RL** | 10K | Sim | ⭐⭐⭐ | ❌ | ⭐⭐⭐ | Offline RL |
| **BridgeData V2** | 60K | Real | ⭐⭐⭐⭐ | ✅ | ⭐⭐⭐⭐ | Real robot |
| **CALVIN** | N/A | Sim | ⭐⭐⭐ | ✅ | ⭐⭐⭐⭐ | Long-horizon |

---

## 🎯 Recommendations for Our Research

### For Development: **RoboMimic**
- ✅ Clean, curated
- ✅ Standard benchmark
- ✅ Fast iteration
- **Use for**: Initial HiLoop experiments

### For Evaluation: **CALVIN**
- ✅ Long-horizon (HiLoop strength)
- ✅ Standard in recent papers
- **Use for**: Main evaluation

### For Pre-training: **RT-X** (if compute permits)
- ✅ Massive scale
- ✅ Diverse
- **Use for**: World model pre-training

### For Offline→Online: **D4RL**
- ✅ Standard offline RL benchmark
- **Use for**: Diffusion + RL experiments (#4)

---

## 📥 Data Access Summary

### Easy Access (Direct Download):
- RoboMimic: `robomimic/scripts/download_datasets.py`
- D4RL: `pip install d4rl; import d4rl`
- YCB: Direct download from website

### Requires Registration:
- RT-X: Google Cloud, requires agreement
- BridgeData V2: Form submission
- Ego4D: Application required

### Via Benchmark APIs:
- CALVIN: Included in environment
- Meta-World: Generated during use
- RLBench: Generated during use

---

## 🚀 Quick Start Data Pipeline

### For HiLoop Development:

**Phase 1: Prototyping (Small Data)**
```bash
# Download RoboMimic
git clone https://github.com/ARISE-Initiative/robomimic.git
cd robomimic
python scripts/download_datasets.py --tasks lift

# Use directly
from robomimic.utils.file_utils import get_dataset
dataset = get_dataset('datasets/lift/ph/low_dim.hdf5')
```

**Phase 2: Benchmark Evaluation**
```bash
# Setup CALVIN
git clone https://github.com/mees/calvin.git
cd calvin && pip install -e .

# Evaluate on CALVIN tasks
# (Data generated during environment use)
```

**Phase 3: Large-Scale Pre-training (Optional)**
```bash
# Request RT-X access
# Follow instructions at robotics-transformer-x.github.io

# Download subset (e.g., BridgeData V2 within RT-X)
# Use RLDS format
```

---

## 📚 Data Processing Resources

### Data Loaders:
- **RoboMimic**: Built-in HDF5 loader
- **RT-X**: RLDS/tfds (TensorFlow)
- **D4RL**: Gym-style interface

### Conversion Tools:
- **RLDS to PyTorch**: https://github.com/kpertsch/rlds_dataset_mod
- **HDF5 to PyTorch**: Custom loader (straightforward)

### Augmentation:
- **ImgAug**: https://github.com/aleju/imgaug
- **Albumentations**: https://github.com/albumentations-team/albumentations
- **RoboSuite built-in**: Domain randomization

---

**Next**: World model libraries and equivariant learning tools
