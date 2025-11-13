# Visualization and Debugging Tools

**Last Updated**: 2025-11-13
**Category**: Experiment tracking, visualization, debugging, video rendering

---

## 📊 Experiment Tracking

### 1. Weights & Biases (W&B)

**Developer**: Weights & Biases
**License**: Free for academics (cloud), Apache 2.0 (local)
**Website**: https://wandb.ai/
**GitHub**: https://github.com/wandb/wandb
**Stars**: ~8K

**Description**:
- Industry-standard experiment tracking
- Cloud-based (with local option)
- Beautiful visualizations

**Key Features**:
- Metric logging (scalars, images, videos)
- Hyperparameter tracking
- Model checkpointing
- Artifact management
- Team collaboration
- Sweeps (hyperparameter optimization)
- Reports (publication-quality)

**Pros**:
- Best-in-class UI
- Free for academics
- Great documentation
- Active community
- Integrations (PyTorch, TensorFlow, etc.)

**Cons**:
- Cloud-based (data leaves server)
- Can be slow with many runs
- Requires internet

**Relevance to Our Research**: ⭐⭐⭐⭐⭐
- **Essential for experiment tracking**
- Track HiLoop training (losses, success rates)
- Compare ablations
- **Use for**: All experiments

**Getting Started**:
```python
pip install wandb

import wandb

# Initialize run
wandb.init(project="hiloop", name="experiment_01")

# Log metrics
for epoch in range(100):
    loss = train_step()
    wandb.log({"loss": loss, "epoch": epoch})

# Log media
wandb.log({"trajectory": wandb.Video("rollout.mp4")})

# Log artifacts
wandb.save("model.pth")
```

---

### 2. TensorBoard

**Developer**: TensorFlow team (Google)
**License**: Apache 2.0
**GitHub**: https://github.com/tensorflow/tensorboard
**Stars**: ~6K

**Description**:
- Traditional experiment tracking
- Local-first
- Integrated with PyTorch, TensorFlow

**Key Features**:
- Scalar logging
- Histograms
- Images, audio, video
- Graph visualization
- Hyperparameter tuning (HParams)
- Profiling

**Pros**:
- Free, open-source
- Local (no cloud)
- Lightweight
- PyTorch-native (torch.utils.tensorboard)

**Cons**:
- Less polished UI than W&B
- Harder to compare many runs
- Limited team features

**Relevance to Our Research**: ⭐⭐⭐⭐
- Good alternative to W&B (if prefer local)
- **Use for**: Experiments if not using W&B

**Getting Started**:
```python
from torch.utils.tensorboard import SummaryWriter

writer = SummaryWriter('runs/experiment_01')

# Log scalars
writer.add_scalar('Loss/train', loss, epoch)

# Log images
writer.add_image('Observation', obs_image, epoch)

# Log videos
writer.add_video('Rollout', video_tensor, epoch, fps=30)

writer.close()

# View: tensorboard --logdir=runs
```

---

### 3. MLflow

**Developer**: Databricks
**License**: Apache 2.0
**GitHub**: https://github.com/mlflow/mlflow
**Stars**: ~17K

**Description**:
- End-to-end ML platform
- Experiment tracking + model registry + deployment
- Self-hosted

**Key Features**:
- Tracking (like W&B/TensorBoard)
- Model registry
- Projects (reproducibility)
- Models (deployment)

**Pros**:
- Open-source
- Self-hosted (full control)
- Model management features

**Cons**:
- More complex setup
- UI not as polished
- Overkill for pure research

**Relevance to Our Research**: ⭐⭐⭐
- Good for production (if deploying)
- Heavier than needed for research

---

## 🎥 Video Rendering and Recording

### 4. Imageio

**Developer**: Imageio developers
**License**: BSD-2-Clause
**GitHub**: https://github.com/imageio/imageio
**Stars**: ~1.4K

**Description**:
- Simple image/video I/O
- Read/write many formats
- FFmpeg backend

**Key Features**:
- Read images, videos
- Write GIFs, MP4, AVI
- Frame-by-frame access
- Simple API

**Pros**:
- Very easy to use
- No dependencies (except for video formats)
- Well-maintained

**Cons**:
- Basic features (no fancy editing)

**Relevance to Our Research**: ⭐⭐⭐⭐⭐
- **Essential for saving rollout videos**
- Log robot trajectories
- **Use for**: Video logging in experiments

**Getting Started**:
```python
pip install imageio imageio-ffmpeg

import imageio

# Save frames as video
frames = []  # List of numpy arrays (H, W, 3)
for step in rollout:
    frames.append(env.render())

imageio.mimsave('rollout.mp4', frames, fps=30)

# Save as GIF
imageio.mimsave('rollout.gif', frames, fps=10)
```

---

### 5. OpenCV (cv2)

**Developer**: OpenCV team
**License**: Apache 2.0
**Website**: https://opencv.org/
**Stars**: ~75K

**Description**:
- Computer vision library
- Image/video processing
- Includes rendering utilities

**Key Features**:
- Video reading/writing
- Image manipulation
- Drawing (overlays, text)
- Camera interfaces

**Pros**:
- Industry-standard
- Fast (C++ backend)
- Comprehensive

**Cons**:
- API can be clunky
- Documentation inconsistent

**Relevance to Our Research**: ⭐⭐⭐⭐
- Video processing
- Add overlays (waypoints, predictions)
- **Use for**: Visualization of waypoints on video

**Getting Started**:
```python
pip install opencv-python

import cv2

# Save video
fourcc = cv2.VideoWriter_fourcc(*'mp4v')
out = cv2.VideoWriter('rollout.mp4', fourcc, 30.0, (640, 480))

for frame in frames:
    # Add overlays
    cv2.circle(frame, waypoint_pos, radius=5, color=(0,255,0), thickness=-1)
    cv2.putText(frame, f"Step {i}", (10,30), cv2.FONT_HERSHEY_SIMPLEX, 1, (255,255,255))
    out.write(frame)

out.release()
```

---

## 🔍 Debugging and Profiling

### 6. PyTorch Profiler

**Developer**: PyTorch team
**License**: BSD-3-Clause
**Docs**: https://pytorch.org/tutorials/recipes/recipes/profiler_recipe.html

**Description**:
- Built-in profiler for PyTorch
- CPU/GPU timing
- Memory usage
- Bottleneck identification

**Key Features**:
- Time breakdown (operators)
- GPU utilization
- Memory profiling
- Chrome trace export

**Pros**:
- Built-in (no install)
- Detailed breakdown
- Integrates with TensorBoard

**Cons**:
- Can slow down training
- Complex output

**Relevance to Our Research**: ⭐⭐⭐⭐
- Identify bottlenecks (world model, diffusion)
- Optimize inference speed
- **Use for**: Performance optimization

**Getting Started**:
```python
from torch.profiler import profile, ProfilerActivity

with profile(activities=[ProfilerActivity.CPU, ProfilerActivity.CUDA]) as prof:
    for _ in range(10):
        output = model(input)
        loss = criterion(output, target)
        loss.backward()
        optimizer.step()

# Print results
print(prof.key_averages().table(sort_by="cuda_time_total"))

# Export to TensorBoard
prof.export_chrome_trace("trace.json")
```

---

### 7. Line Profiler

**Developer**: Community
**License**: BSD-3-Clause
**GitHub**: https://github.com/pyutils/line_profiler
**Stars**: ~2K

**Description**:
- Line-by-line profiling
- Find slow lines of code
- Python-level (not PyTorch-specific)

**Pros**:
- Very precise (line-level)
- Easy to use
- Minimal overhead

**Cons**:
- Python only (not GPU)

**Relevance to Our Research**: ⭐⭐⭐
- Debug slow Python code
- **Use for**: Data loading, preprocessing bottlenecks

**Getting Started**:
```python
pip install line_profiler

# Add @profile decorator
@profile
def train_step(batch):
    # ... training code
    pass

# Run: kernprof -l -v script.py
```

---

## 📈 Visualization Libraries

### 8. Matplotlib

**License**: PSF-based
**Website**: https://matplotlib.org/
**Stars**: ~19K

**Description**:
- Standard plotting library
- Publication-quality figures

**Relevance to Our Research**: ⭐⭐⭐⭐⭐
- **Essential for paper figures**
- Plot learning curves, ablations
- **Use for**: All plotting

---

### 9. Seaborn

**License**: BSD-3-Clause
**GitHub**: https://github.com/mwaskom/seaborn
**Stars**: ~12K

**Description**:
- Statistical visualization
- Built on matplotlib
- Beautiful default styles

**Relevance to Our Research**: ⭐⭐⭐⭐
- Nicer plots than matplotlib
- **Use for**: Paper-quality visualizations

---

### 10. Plotly

**License**: MIT
**GitHub**: https://github.com/plotly/plotly.py
**Stars**: ~15K

**Description**:
- Interactive plots
- Web-based visualizations
- 3D support

**Pros**:
- Interactive (zoom, hover)
- Good for 3D (trajectories, point clouds)

**Cons**:
- Not for print (paper figures)

**Relevance to Our Research**: ⭐⭐⭐
- Interactive trajectory visualization
- **Use for**: 3D waypoint visualization

---

## 🎨 3D Visualization

### 11. Open3D

**Developer**: Intel
**License**: MIT
**GitHub**: https://github.com/isl-org/Open3D
**Stars**: ~10K

**Description**:
- 3D data processing and visualization
- Point clouds, meshes
- Real-time rendering

**Key Features**:
- Point cloud visualization
- Mesh rendering
- 3D reconstruction
- ICP, normal estimation
- GUI widgets

**Pros**:
- Fast (C++ backend)
- Great for point clouds
- Good documentation

**Cons**:
- Focused on geometry (not trajectories)

**Relevance to Our Research**: ⭐⭐⭐⭐⭐
- **Critical for 3D representations**
- Visualize point cloud observations
- Render 3D waypoints
- **Use for**: 3D world model visualization

**Getting Started**:
```python
pip install open3d

import open3d as o3d
import numpy as np

# Create point cloud
pcd = o3d.geometry.PointCloud()
pcd.points = o3d.utility.Vector3dVector(points)  # Nx3 array
pcd.colors = o3d.utility.Vector3dVector(colors)  # Nx3 RGB

# Visualize
o3d.visualization.draw_geometries([pcd])

# Add trajectories
lines = [[i, i+1] for i in range(len(waypoints)-1)]
line_set = o3d.geometry.LineSet()
line_set.points = o3d.utility.Vector3dVector(waypoints)
line_set.lines = o3d.utility.Vector2iVector(lines)

o3d.visualization.draw_geometries([pcd, line_set])
```

---

### 12. PyVista

**Developer**: PyVista developers
**License**: MIT
**GitHub**: https://github.com/pyvista/pyvista
**Stars**: ~2.4K

**Description**:
- 3D visualization and mesh analysis
- VTK bindings (easier API)
- Jupyter integration

**Pros**:
- Pythonic API (easier than raw VTK)
- Jupyter support
- Many mesh operations

**Cons**:
- VTK backend (heavy)

**Relevance to Our Research**: ⭐⭐⭐
- 3D visualization (alternative to Open3D)
- **Use for**: If need advanced mesh features

---

## 📊 Comparison Table

| Tool | Purpose | Ease of Use | Features | Community | Recommendation |
|------|---------|-------------|----------|-----------|----------------|
| **W&B** | Tracking | ⭐⭐⭐⭐⭐ | ⭐⭐⭐⭐⭐ | ⭐⭐⭐⭐⭐ | ⭐⭐⭐⭐⭐ |
| **TensorBoard** | Tracking | ⭐⭐⭐⭐ | ⭐⭐⭐⭐ | ⭐⭐⭐⭐⭐ | ⭐⭐⭐⭐ |
| **Imageio** | Video | ⭐⭐⭐⭐⭐ | ⭐⭐⭐ | ⭐⭐⭐⭐ | ⭐⭐⭐⭐⭐ |
| **Open3D** | 3D viz | ⭐⭐⭐⭐ | ⭐⭐⭐⭐⭐ | ⭐⭐⭐⭐ | ⭐⭐⭐⭐⭐ |
| **PyTorch Profiler** | Debug | ⭐⭐⭐ | ⭐⭐⭐⭐⭐ | ⭐⭐⭐⭐⭐ | ⭐⭐⭐⭐ |

---

## 🎯 Recommendations for Our Research

### Essential Stack:
1. **W&B**: Experiment tracking (or TensorBoard if prefer local)
2. **Imageio**: Save rollout videos
3. **Open3D**: 3D point cloud visualization
4. **Matplotlib/Seaborn**: Paper figures

### For Optimization:
- **PyTorch Profiler**: Find bottlenecks
- **Line Profiler**: Python-level profiling

### For 3D Work:
- **Open3D**: Point clouds, trajectories
- **Plotly**: Interactive 3D plots

---

## 🚀 Quick Start Visualization Pipeline

### For HiLoop Experiments:

```python
import wandb
import imageio
import open3d as o3d
import numpy as np

# 1. Initialize W&B
wandb.init(project="hiloop", name="exp_01")

# 2. Training loop
for epoch in range(num_epochs):
    loss = train_step()
    wandb.log({"loss": loss})

    # 3. Periodic evaluation
    if epoch % eval_freq == 0:
        # Rollout
        frames = []
        waypoints_3d = []

        obs = env.reset()
        for step in range(horizon):
            # Generate waypoint
            waypoint = generate_waypoint(obs)
            waypoints_3d.append(waypoint)

            # Execute
            action = execute_policy(obs, waypoint)
            obs, _, done, _ = env.step(action)

            # Render
            frame = env.render(mode='rgb_array')
            frames.append(frame)

            if done:
                break

        # 4. Save video
        video_path = f'rollout_epoch_{epoch}.mp4'
        imageio.mimsave(video_path, frames, fps=30)

        # 5. Log to W&B
        wandb.log({
            "rollout_video": wandb.Video(video_path),
            "success": done,
            "steps": len(frames)
        })

        # 6. 3D waypoint visualization (save image)
        pcd = o3d.geometry.PointCloud()
        pcd.points = o3d.utility.Vector3dVector(np.array(waypoints_3d))

        vis = o3d.visualization.Visualizer()
        vis.create_window(visible=False)
        vis.add_geometry(pcd)
        vis.capture_screen_image(f'waypoints_epoch_{epoch}.png')
        vis.destroy_window()

        wandb.log({"waypoints_3d": wandb.Image(f'waypoints_epoch_{epoch}.png')})

# 7. Paper figures
import matplotlib.pyplot as plt
import seaborn as sns

sns.set_style("whitegrid")
plt.figure(figsize=(10, 6))
plt.plot(epochs, losses, label='Training Loss')
plt.xlabel('Epoch')
plt.ylabel('Loss')
plt.title('HiLoop Training Curve')
plt.legend()
plt.savefig('paper_figure_loss.pdf', dpi=300, bbox_inches='tight')
```

---

## 📚 Resources

**W&B**:
- Docs: https://docs.wandb.ai/
- Tutorial: https://wandb.ai/site/tutorials

**Open3D**:
- Docs: http://www.open3d.org/docs/
- Tutorial: http://www.open3d.org/docs/latest/tutorial/

**PyTorch Profiler**:
- Tutorial: https://pytorch.org/tutorials/recipes/recipes/profiler_recipe.html

---

## 🔧 Installation

```bash
# Experiment tracking
pip install wandb

# Visualization
pip install matplotlib seaborn
pip install imageio imageio-ffmpeg
pip install opencv-python

# 3D
pip install open3d
pip install plotly

# Profiling
pip install line_profiler
# PyTorch profiler is built-in

# All-in-one
pip install wandb matplotlib seaborn imageio imageio-ffmpeg opencv-python open3d plotly
```

---

**Next**: Master README for all tools
