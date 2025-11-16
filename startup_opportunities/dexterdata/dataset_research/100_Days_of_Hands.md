# 100 Days of Hands (100DOH)

## Overview

100 Days of Hands (100DOH) is a large-scale video dataset for understanding human hands in contact at internet scale. Developed by researchers at the University of Michigan (Dandan Shan, Jiaqi Geng, Michelle Shu, David Fouhey) and published at CVPR 2020 as an **oral presentation**, the dataset contains nearly **131 days of video footage** showing hands and hand-object interactions in everyday scenarios.

The dataset consists of 27,300 YouTube videos from 11 categories (cooking, crafts, gardening, home repair, music, etc.) and includes **100,000 annotated video frames** for hand-contact understanding. Unlike controlled lab datasets, 100DOH captures hands "in the wild" across diverse real-world activities, making it valuable for understanding natural hand usage patterns.

**Key Innovation**: Internet-scale collection of hand contact data from real-world videos, with focus on understanding when and where hands contact objects during everyday activities.

## Dataset Specifications

### Scale and Content
- **Total Videos**: 27,300 YouTube videos
- **Total Duration**: 131 days of footage
- **Annotated Frames**: 100,000 frames with hand-contact labels
- **Video Categories**: 11 activity types
  - Cooking
  - Crafts
  - Gardening
  - Home repair
  - Music playing
  - And other everyday activities

### Annotations
- **Hand Detection**: Bounding boxes for hands
- **Contact States**: Labels indicating hand-object contact
- **Activity Categories**: 11 broad categories of hand use
- **Frame-Level**: Annotations at video frame level

### Data Characteristics
- **In-the-Wild**: Real-world YouTube videos, not lab-controlled
- **Diverse Contexts**: Wide variety of lighting, backgrounds, objects
- **Natural Interactions**: Genuine everyday hand usage patterns
- **Egocentric & Third-Person**: Mix of viewpoints

### Additional Components
- **Hand Detector Models**: Pre-trained models on 100DOH available
- **Ego Dataset Overlap**: When using ego-view data, must cite Epic-Kitchens, EGTEA, CharadesEgo
- **Detectron2 Models**: Hand detection models trained on 100DOH using Detectron2 framework

## Research Community Reception

### High-Impact Publication
- **CVPR 2020 Oral**: Top-tier acceptance (oral presentations are ~5% of submissions)
- **Well-Cited**: Influential in hand detection and HOI literature
- **ArXiv**: https://arxiv.org/abs/2006.06669
- **Open Access**: Full paper available on CVPR proceedings

### Academic Impact
Used and cited for:
1. **Hand Detection**: Training robust hand detectors
2. **Hand-Object Interaction**: Understanding contact patterns
3. **Activity Recognition**: Hand-centric activity understanding
4. **Egocentric Vision**: First-person hand analysis
5. **Video Understanding**: Temporal hand contact reasoning

### Performance Contributions
- Enables training hand detectors that generalize to diverse scenarios
- Demonstrates value of internet-scale data for hand understanding
- Shows importance of contact annotations for interaction understanding

### Research Applications
- Hand detection in unconstrained videos
- Contact state estimation
- Activity recognition from hand interactions
- Egocentric action understanding
- Hand-object affordance learning

## Industry Adoption

### Limited Direct Commercial Use
100DOH is primarily an academic dataset with limited direct industry deployment. However, it has influenced:

**Indirect Impact:**
- **Hand Detection Systems**: Models trained on 100DOH used in products
- **Video Understanding Services**: Hand tracking in video analysis
- **Robotics Research**: Understanding human hand contact patterns
- **AR/VR Applications**: Hand detection and contact reasoning

### Potential Commercial Applications
- Video content analysis (e.g., recipe analysis, tutorial understanding)
- Hand gesture/contact recognition systems
- Robotics: understanding human manipulation strategies
- Training data for hand detection models
- AR/VR hand interaction systems

### Industry Barriers
- YouTube videos have copyright restrictions
- License for dataset unclear
- Not designed for commercial robot training
- Primarily detection/recognition, not control

## Who Uses This Dataset

### Primary Users
1. **Computer Vision Researchers**: Hand detection and recognition
2. **Hand-Object Interaction Researchers**: Contact understanding
3. **Egocentric Vision Community**: First-person hand analysis
4. **Activity Recognition Researchers**: Hand-centric activity understanding
5. **Robotics Researchers (Secondary)**: Understanding human hand strategies

### Research Institutions
- University of Michigan (creators)
- Computer vision labs studying hands
- Egocentric vision research groups
- Robotics labs analyzing human manipulation
- Video understanding researchers

### Use Cases
**Primary:**
- Training hand detection models
- Hand-contact state estimation
- Activity recognition from hand interactions
- Benchmarking hand segmentation algorithms
- Understanding hand usage patterns in everyday tasks

**Secondary (Robotics):**
- Analyzing human hand contact strategies
- Understanding manipulation primitives
- Identifying common grasp types
- Activity segmentation for imitation learning

### Tools and Models
- **Hand Detector Models**: Pre-trained Detectron2 models available on GitHub
- **GitHub Repository**: https://github.com/ddshan/hand_detector.d2
- **Code**: Hand detection and contact estimation code released

## Strengths & Weaknesses

### Strengths
1. **Massive Scale**: 131 days of video footage
2. **Real-World Diversity**: YouTube videos cover diverse scenarios
3. **Hand-Contact Focus**: Explicit contact annotations
4. **100K Annotated Frames**: Substantial labeled data
5. **In-the-Wild**: Not lab-controlled, represents real usage
6. **CVPR Oral**: High-quality, well-vetted research
7. **Pre-trained Models**: Hand detectors available for use
8. **Multiple Viewpoints**: Ego and third-person perspectives
9. **Activity Diversity**: 11 categories covering many hand uses
10. **Open Code**: Detection models and code publicly available
11. **Egocentric Data**: Includes first-person view hand interactions

### Weaknesses
1. **2D Bounding Boxes Only**: No hand pose, keypoints, or 3D information
2. **NO Hand Pose**: No finger tracking or joint angles
3. **NO 3D Data**: No depth, no 3D hand meshes
4. **NO Robot Applicability**: Cannot train robot manipulation policies
5. **Contact Labels Only**: No detailed contact geometry or force
6. **YouTube Copyright**: Video content has usage restrictions
7. **License Unclear**: No explicit dataset license specified
8. **Detection-Level Annotations**: Not suitable for fine-grained manipulation
9. **No Object Meshes**: No 3D object models
10. **Variable Quality**: YouTube video quality inconsistent
11. **No Tactile Data**: Pure visual, no force/pressure information
12. **Coarse Annotations**: Frame-level, not pixel-accurate contact regions

### Critical Gaps for Manipulation
- **No finger-level detail**: Cannot understand finger articulation
- **No 3D geometry**: Cannot reconstruct hand-object spatial relationships
- **No robot data**: Not paired with robot demonstrations
- **Observation only**: No action labels for robot control

## Relevance to DexterData

### Direct Relevance: LOW-MODERATE

**Why It Has Some Value:**
1. **Hand-Contact Focus**: Emphasizes when/where hands touch objects
2. **Scale Demonstration**: 131 days of footage shows data volume possible
3. **In-the-Wild Approach**: Real-world diversity valuable
4. **Everyday Activities**: Covers common manipulation scenarios
5. **Contact Annotations**: Shows importance of labeling hand-object contact

**Critical Gaps for DexterData:**
1. **NO Hand Pose**: Only detection boxes, no finger tracking
2. **NO 3D Data**: Cannot train 3D-aware manipulation policies
3. **NO Robot Data**: Pure human observation, not robot compatible
4. **Coarse Annotations**: Detection-level, not manipulation-level detail
5. **NO Tactile/Force**: Missing physical interaction information
6. **YouTube Restrictions**: Copyright issues for commercial use

### Lessons for DexterData

**What to Learn:**
1. **Scale Matters**: 100K+ annotated instances and 131 days of footage
2. **In-the-Wild Value**: Real-world diversity important for generalization
3. **Contact is Critical**: Explicitly annotating hand-object contact is valuable
4. **Pre-trained Models**: Releasing models encourages adoption
5. **Multiple Viewpoints**: Include egocentric and third-person views
6. **Activity Diversity**: Cover many manipulation types
7. **Code Release**: Open-source tools increase dataset impact
8. **Ego-Centric Data**: First-person view valuable for robot applications

**What DexterData Must Add:**
1. **3D Hand Poses**: MANO meshes or detailed keypoints, not just boxes
2. **Finger Tracking**: Joint angles for all finger joints
3. **Depth Information**: RGB-D for 3D reconstruction
4. **Detailed Contact**: Contact regions, contact forces when possible
5. **Robot Demonstrations**: Include robot executions
6. **Object 3D Models**: Meshes with affordance annotations
7. **Clear Licensing**: MIT/Apache for commercial robot training
8. **Manipulation-Specific**: Focus on manipulation tasks, not just general hand use
9. **Tactile Data**: Force, pressure, texture information
10. **Action Labels**: Task goals, rewards, trajectory annotations

### Strategic Positioning

**100DOH Strength**: Large-scale hand detection and contact labels in real-world videos
**DexterData Need**: 3D hand poses + manipulation focus + robot compatibility

**Potential Uses of 100DOH for DexterData:**
1. **Pre-training**: Train visual hand encoders on 100DOH detection task
2. **Contact Prior**: Learn contact probability maps from 100DOH
3. **Activity Mining**: Identify common manipulation tasks from 100DOH categories
4. **Negative Examples**: Use non-manipulation hand usage as contrastive examples

**Cannot Use Directly For:**
- Training robot policies (no 3D, no robot data)
- Finger-level manipulation learning (no pose)
- Grasp synthesis (no detailed contact geometry)
- Force-controlled manipulation (no force data)

### Comparison: 100DOH vs. DexterData

| Aspect | 100DOH | DexterData (Goal) |
|--------|--------|-------------------|
| **Hand Representation** | 2D bounding box | 3D MANO mesh |
| **Finger Tracking** | None | Full articulation |
| **Contact Annotation** | Binary labels | Geometry + force |
| **Robot Data** | None | Central component |
| **3D Geometry** | None | RGB-D + meshes |
| **Purpose** | Detection/recognition | Manipulation training |
| **License** | Unclear | MIT/Apache |
| **Scale** | 131 days | Target 100K+ demos |
| **Viewpoints** | Ego + 3rd person | Multi-view + ego |
| **Objects** | In-the-wild | Annotated meshes |

### Use Case Complementarity

**100DOH** → "Where are hands and are they touching objects?"
**DexterData** → "How are fingers configured and what forces are applied to manipulate objects?"

100DOH answers detection and contact questions.
DexterData answers manipulation execution questions.

### Bottom Line Assessment

100DOH is valuable for **hand detection and contact recognition** but insufficient for **training dexterous manipulation**.

**For DexterData Strategy:**
1. **Don't rely on 100DOH data directly**: Too coarse for manipulation learning
2. **Learn from collection approach**: Internet-scale + diverse scenarios
3. **Use for pre-training**: Hand detection encoders
4. **Reference for task selection**: What manipulation tasks are common?
5. **Differentiate clearly**: DexterData must capture finger-level 3D detail

**Key Takeaway**: 100DOH validates large-scale hand data collection but represents only the first layer (detection). DexterData needs to go much deeper (pose, contact, force, 3D) to enable manipulation learning.

**Quote from 100DOH**: "Understanding human hands in contact at internet scale"
**DexterData Goal**: "Understanding and replicating human hand manipulation at finger scale"

---

**Dataset Access**: https://fouheylab.eecs.umich.edu/~dandans/projects/100DOH/
**GitHub**: https://github.com/ddshan/hand_detector.d2
**Paper**: https://arxiv.org/abs/2006.06669 (CVPR 2020 Oral)
**Citation**: Shan et al., "Understanding Human Hands in Contact at Internet Scale," CVPR 2020
**License**: Not specified (check website or contact authors)
**Institution**: University of Michigan
**Year**: 2020
