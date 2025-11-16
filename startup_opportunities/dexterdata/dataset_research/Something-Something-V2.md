# Something-Something V2

## Overview

Something-Something V2 (20BN-SOMETHING-SOMETHING-V2) is a large-scale video dataset containing 220,847 labeled video clips showing humans performing pre-defined basic actions with everyday objects. Created by Twenty Billion Neurons (20BN), the dataset was designed to train machine learning models in fine-grained understanding of human hand gestures and temporal reasoning.

Unlike traditional action recognition datasets that focus on scene classification, Something-Something V2 emphasizes the temporal dynamics and causal relationships in hand-object interactions. The dataset features 174 distinct action classes focused on manipulation primitives like "putting something into something," "turning something upside down," "covering something with something," and crucially, many actions performed with hands only.

**Key Innovation**: Focus on temporal reasoning and fine-grained hand manipulation understanding rather than scene recognition, requiring models to understand the physical dynamics of hand-object interactions.

## Dataset Specifications

### Scale and Content
- **Total Videos**: 220,847 video clips
- **Training Set**: 168,913 videos
- **Validation Set**: 24,777 videos
- **Test Set**: 27,157 videos
- **Action Classes**: 174 distinct manipulation actions
- **Video Duration**: ~3 seconds per clip
- **Resolution**: Various (crowd-collected)

### Key Characteristics
- **Hand-centric Actions**: Many classes focus on hand-only manipulation
- **Temporal Dynamics**: Actions require understanding object motion over time
- **Everyday Objects**: Common household items
- **Diverse Performers**: Large number of crowd workers
- **Action Primitives**: Basic manipulation verbs (push, pull, twist, cover, etc.)

### Annotation Quality
- Pre-defined action templates
- Crowd worker validation
- Focus on action execution rather than object identity
- Temporal consistency required

### Something-Else Extension
A subset (180,049 videos) includes:
- Per-frame bounding box annotations
- Object tracking throughout interaction
- Hand bounding boxes
- Enhanced temporal annotations

## Research Community Reception

### High Citation Impact
- Published at ICCV 2017 (original), extended for V2
- One of the most-cited video action recognition datasets
- Standard benchmark for temporal action understanding
- Featured in major computer vision conferences

### Widespread Academic Use
Used extensively for research in:
- Temporal action recognition
- Video understanding
- Hand-object interaction reasoning
- Compositional action learning
- Physical reasoning from video
- Common sense understanding

### Benchmark Status
- **Standard Benchmark**: De facto standard for fine-grained action recognition
- **Competition Dataset**: Used in challenges and competitions
- **Model Evaluation**: Standard test for video understanding models
- **SOTA Tracking**: Papers With Code tracks state-of-the-art results

### Research Impact Areas
1. **Computer Vision**: Temporal modeling, action recognition
2. **Video Understanding**: Long-term dependencies, motion patterns
3. **Robotics (Limited)**: Some use for action prediction, but limited robot training
4. **Physics Understanding**: Implicit physical reasoning from visual dynamics

## Industry Adoption

### Moderate-High Industry Awareness
- **Tech Companies**: Google, Meta, Microsoft have published results on this dataset
- **Qualcomm**: Official partner, hosts dataset for download
- **AI Startups**: Used for video understanding product development
- **Action Recognition Products**: Companies building gesture/action recognition systems

### Commercial Applications
1. **Video Understanding Services**: Action recognition APIs
2. **Gesture Recognition**: Hand gesture detection systems
3. **Content Moderation**: Understanding actions in video content
4. **Robotics (Emerging)**: Some exploration for action prediction
5. **Augmented Reality**: Hand-object interaction understanding

### Industry Limitations
- Primarily used for video understanding, not direct robot control
- Few examples of training physical robots on this data
- More common in perception than manipulation systems

## Who Uses This Dataset

### Primary Users
1. **Computer Vision Researchers**: Action recognition, video understanding
2. **Video Understanding Groups**: Temporal modeling, dynamics prediction
3. **Human-Computer Interaction**: Gesture and action recognition
4. **Robotics Researchers (Secondary)**: Action prediction, but limited for robot training
5. **Industry ML Teams**: Building video understanding products

### Research Institutions
- Major computer vision labs worldwide
- Video understanding research groups
- Human activity recognition researchers
- Some robotics labs for visual prediction tasks

### Use Cases
**Primary (Computer Vision):**
- Action recognition from video
- Temporal modeling benchmarking
- Hand gesture classification
- Physical reasoning evaluation

**Secondary (Robotics):**
- Visual action prediction
- Understanding manipulation primitives
- Pre-training visual encoders
- Action segmentation

### Notable Publications
Hundreds of papers using this dataset for:
- Transformer-based video models
- Temporal convolution networks
- Multi-modal learning
- Few-shot action recognition

## Strengths & Weaknesses

### Strengths
1. **Large Scale**: 220K+ videos provide substantial training data
2. **Hand-Focused Actions**: Many manipulation primitives with hands
3. **Temporal Dynamics**: Requires understanding motion, not just static scenes
4. **Diverse Actions**: 174 classes cover many manipulation types
5. **Quality Annotations**: Clear action labels with templates
6. **Benchmark Status**: Widely accepted standard in computer vision
7. **Something-Else Extension**: Bounding boxes for hands and objects
8. **Active Community**: Ongoing research and model development
9. **Available on HuggingFace**: Easy access through modern ML platforms
10. **Industry Partnerships**: Qualcomm hosting ensures availability

### Weaknesses
1. **NO 3D Hand Poses**: Only 2D video, no finger tracking or hand mesh
2. **NO Depth Information**: RGB only, no depth or 3D reconstruction
3. **NO Robot Applicability**: Not designed for robot training, human videos only
4. **Limited for Manipulation**: Cannot train robot hands from this data
5. **Commercial License Required**: Free for academic, must pay for commercial use
6. **Variable Quality**: Crowd-sourced, inconsistent lighting/backgrounds
7. **Short Clips**: 3 seconds may miss full task context
8. **No Tactile/Force Data**: Pure visual, no contact information
9. **No Object Metadata**: Limited object-level annotations (except Something-Else)
10. **Action Templates**: Constrained to pre-defined action classes

### Critical Limitations for Robot Learning
- **Cannot train robot hands**: No finger poses, contact points, or force data
- **Human-only demonstrations**: Not teleoperation or robot execution
- **2D video only**: Missing 3D geometry needed for manipulation
- **No embodiment**: Cannot map to robot action spaces directly

## Relevance to DexterData

### Direct Relevance: LOW-MODERATE

**Why It Has Some Value:**
1. **Hand Manipulation Focus**: Emphasizes hand-object interactions
2. **Action Primitives**: Catalog of manipulation verbs (push, twist, cover, etc.)
3. **Large Scale**: Demonstrates value of 200K+ examples
4. **Temporal Understanding**: Shows importance of motion dynamics
5. **Hand-Only Actions**: Many actions without tools, pure hand manipulation

**Critical Gaps for DexterData:**
1. **NO Finger Tracking**: Zero 3D hand pose or finger joint data
2. **NO Depth/3D**: Cannot reconstruct 3D hand-object geometry
3. **NO Robot Training**: Not usable for training robot manipulation policies
4. **Commercial License Barrier**: Requires paid license for commercial robot companies
5. **NO Contact/Force**: Missing tactile information critical for manipulation
6. **Human-only**: Not paired with robot demonstrations

### Lessons for DexterData

**What to Learn From:**
1. **Action Taxonomy**: Study the 174 action classes for manipulation primitives
2. **Scale Matters**: 220K examples shows data volume needed
3. **Crowd-sourcing Works**: Demonstrates scalable data collection via crowds
4. **Temporal Information**: Emphasize motion dynamics, not just static poses
5. **Quality Control**: Pre-defined templates ensure action consistency
6. **Community Building**: Active benchmark creates research momentum
7. **Multiple Splits**: Clear train/val/test for reproducibility

**What DexterData Must Do Differently:**
1. **Add 3D Hand Tracking**: MANO/SMPL-H or similar hand meshes
2. **Include Depth**: RGB-D or multi-view for 3D reconstruction
3. **Capture Contacts**: Annotate hand-object contact regions
4. **Force/Tactile Data**: Include pressure, force measurements when possible
5. **Robot Compatibility**: Ensure data can train robot policies
6. **Commercial-Friendly License**: MIT/Apache 2.0, not paid commercial
7. **Finger-Level Granularity**: Joint angles, fingertip positions
8. **Object Metadata**: Mesh models, affordances, grasp annotations
9. **Multi-view Capture**: Enable 3D reconstruction
10. **Paired Robot Demos**: Include robot replications when possible

### Strategic Positioning

**Something-Something V2 Strengths**: Large-scale, hand-focused, temporal dynamics
**Something-Something V2 Gaps**: No 3D, no finger tracking, no robot applicability

**DexterData Should:**
1. **Borrow Action Taxonomy**: Use similar manipulation primitives
2. **Match or Exceed Scale**: Aim for 200K+ demonstrations
3. **Add Critical Missing Pieces**: 3D hand poses, depth, robot compatibility
4. **Open Licensing**: Don't require commercial licenses
5. **Richer Annotations**: Contact, force, object affordances
6. **Cross-Modal**: Video + depth + hand pose + robot telemetry

### Use Case Overlap

**Something-Something V2**: Train video understanding models to recognize manipulation actions
**DexterData**: Train robot policies to EXECUTE manipulation actions

These are complementary but distinct:
- Something-Something V2 → perception/recognition
- DexterData → control/execution

**Potential Synergy:**
- Use Something-Something V2 for visual encoder pre-training
- Then fine-tune on DexterData for robot control
- Could annotate Something-Something V2 subset with hand poses (massive effort)
- Reference their action taxonomy for DexterData task definitions

### Bottom Line Assessment

Something-Something V2 is a **reference point** for DexterData, not a **direct competitor** or **usable training source**.

**Why Reference:**
- Proves demand for hand manipulation understanding
- Shows scale needed (200K+)
- Demonstrates successful crowdsourcing
- Provides action taxonomy

**Why Not Usable Directly:**
- Zero 3D hand/finger tracking
- No robot applicability
- Commercial license barriers
- Missing contact/force data
- Cannot train dexterous manipulation from 2D video alone

**DexterData Positioning**: "Something-Something V2 for robot hands" - similar scale and manipulation focus, but with 3D hand tracking, depth, contact data, and robot-compatible annotations under permissive licensing.

---

**Dataset Access**: https://www.qualcomm.com/developer/software/something-something-v-2-dataset
**Alternative**: https://huggingface.co/datasets/HuggingFaceM4/something_something_v2
**Paper**: https://arxiv.org/abs/1706.04261
**License**: Free for academic research; commercial license required
**Organization**: Twenty Billion Neurons (20BN)
**Year**: 2017 (V1), 2018 (V2)
