# OakInk

## Overview

OakInk is a **large-scale knowledge repository for understanding hand-object interaction**, published at CVPR 2022 and extended with OakInk2 at CVPR 2024. Created by researchers from Shanghai Jiao Tong University and other institutions (Lixin Yang, Kailin Li, Xinyu Zhan, et al.), OakInk represents one of the most comprehensive hand-object interaction datasets available, with particular emphasis on **intent-oriented, affordance-aware manipulation**.

The original OakInk contains **230,000 image frames** showing 12 subjects performing up to 5 intent-oriented interactions with **100 objects from 32 categories**, captured from **4 third-person views**. Additionally, OakInk-Shape provides **3D models, part segmentation, and affordance labels for 1,800 common household objects**.

**OakInk2 (CVPR 2024)** extends this to **bimanual manipulation** in complex task completion scenarios, introducing three levels of abstraction: Affordance, Primitive Task, and Complex Task.

**Key Innovation**: First dataset to combine large-scale hand-object interaction capture with **intent and affordance annotations**, plus a massive object knowledge base (1,800 objects with affordances), enabling compositional understanding of manipulation.

## Dataset Specifications

### OakInk (CVPR 2022)

**OakInk-Image:**
- **Total Frames**: 230,000 image frames
- **Video Sequences**: 792 multi-view video clips
- **Subjects**: 12 different people
- **Objects**: 100 objects from 32 categories
- **Interactions per Object**: Up to 5 intent-oriented interactions
- **Camera Views**: 4 third-person calibrated cameras
- **Hand Annotations**: 3D hand poses (likely MANO or similar)
- **Object Poses**: 6D pose for objects
- **Intent Labels**: Intention annotation for each interaction

**OakInk-Shape:**
- **3D Object Models**: 1,800 common household objects
- **Part Segmentation**: Functional part labels
- **Affordance Annotations**: How objects can be used
- **Grasp Annotations**: Human grasp data for 100 objects
- **Category Diversity**: Broad coverage of everyday objects

**OakBase (Object Affordance Knowledge Base):**
- Part-level segmentation for objects
- Attribute annotations
- Functional affordance labels
- Knowledge graph structure

### OakInk2 (CVPR 2024)

**Enhanced Features:**
- **Bimanual Manipulation**: Both hands working together
- **Complex Task Completion**: Multi-step task sequences
- **Three Abstraction Levels**:
  1. **Affordance**: Object functional properties
  2. **Primitive Task**: Basic manipulation actions
  3. **Complex Task**: Sequences of primitives
- **Multi-view Image Streams**: Enhanced camera coverage
- **Precise Pose Annotations**: Human body, hands, and interacting objects
- **Applications**: Interaction reconstruction, motion synthesis

### Technical Details
- **Hand Representation**: 3D hand pose (meshes or keypoints)
- **Object Representation**: 6D pose + 3D mesh
- **Multi-view Calibration**: Camera parameters provided
- **Temporal Sequences**: Not just static, but manipulation over time
- **Intent/Affordance**: Semantic labels for why and how objects are used

## Research Community Reception

### High-Impact Publications

**OakInk (CVPR 2022):**
- Accepted at premier computer vision conference
- Well-cited in HOI and hand pose literature
- Recognized for scale and affordance focus

**OakInk2 (CVPR 2024):**
- Follow-up extends to bimanual and complex tasks
- Shows sustained research program
- Addresses limitations of original dataset

### Academic Adoption
Widely used for research in:
1. **Hand-Object Interaction**: Understanding grasping and manipulation
2. **Hand Pose Estimation**: 3D hand tracking from images
3. **Affordance Learning**: Understanding object functionality from interaction
4. **Grasp Synthesis**: Generating plausible hand grasps
5. **Motion Synthesis**: Creating realistic interaction motions
6. **Intent Recognition**: Inferring manipulation goals
7. **Compositional Learning**: Combining primitive actions into complex tasks

### Benchmark Status
- Standard benchmark for hand-object interaction
- Used to evaluate hand pose estimation methods
- Reference for affordance prediction
- Comparison point for grasp synthesis
- Foundation for bimanual manipulation research (OakInk2)

### Research Impact
- **50,000 distinct affordance-aware interactions**: Unprecedented scale
- **Intent-oriented**: Captures why objects are manipulated, not just how
- **Part-level affordances**: Enables fine-grained understanding
- **Compositional tasks**: OakInk2 enables learning task hierarchies

### Community Resources
- **Official Website**: oakink.net with comprehensive documentation
- **GitHub Repositories**: Active repos for OakInk and OakInk2
- **HuggingFace Integration**: Easy access via HuggingFace Datasets
- **Visualization Tools**: Provided for exploring data
- **Baselines**: Reference implementations for benchmarking

## Industry Adoption

### Moderate Industry Awareness

**MIT License = Commercial Friendly:**
- OakInk is released under **MIT License**
- Fully permissive for commercial use
- No restrictions on redistribution or commercial products
- Can be used to train commercial robot systems

### Potential Commercial Applications
1. **Robotics Manipulation**: Training robot grasping and manipulation policies
2. **AR/VR Hand Tracking**: Understanding hand-object interactions in XR
3. **Hand Pose Estimation Products**: Training hand tracking systems
4. **Grasp Planning**: Commercial robot grasp synthesis
5. **Affordance Recognition**: Understanding object functionality in applications
6. **Animation/VFX**: Realistic hand-object interaction generation
7. **E-commerce**: Virtual object interaction for online shopping

### Industry Research Labs
- Robotics companies exploring OakInk for manipulation research
- AR/VR companies for hand interaction modeling
- Tech giants (Google, Meta, etc.) in research publications
- Startups in robot learning and hand tracking

### Commercial Barriers (Despite MIT License)
- **No finger articulation detail**: May lack precision needed for robot training
- **Primarily visual**: Missing tactile/force data for manipulation
- **Human demonstrations only**: No robot execution paired data
- **Unclear depth**: May be RGB-only, lacking depth information

## Who Uses This Dataset

### Primary Users
1. **Hand Pose Estimation Researchers**: 3D hand tracking from RGB
2. **Hand-Object Interaction Community**: Grasp understanding
3. **Affordance Learning Researchers**: Object functionality from interaction
4. **Robotics Researchers**: Understanding human manipulation strategies
5. **Grasp Synthesis Researchers**: Generating plausible hand configurations
6. **Motion Synthesis**: Creating realistic hand-object animations
7. **Compositional Learning Researchers**: Task hierarchies (OakInk2)

### Research Institutions
- Shanghai Jiao Tong University (creators)
- Major computer vision and robotics labs worldwide
- Hand pose estimation research groups
- Embodied AI researchers
- Graphics and animation labs

### Use Cases
**Primary (Computer Vision):**
- Hand pose estimation from RGB
- Hand-object interaction recognition
- Affordance prediction
- Grasp synthesis from object shape
- Intent recognition from interaction

**Robotics:**
- Understanding human grasping strategies
- Affordance-based manipulation planning
- Grasp transfer from human to robot
- Task decomposition for complex manipulation (OakInk2)
- Bimanual coordination learning (OakInk2)

**Graphics:**
- Hand-object animation
- Virtual object manipulation
- Contact-based physics simulation

### Application Areas
- Robot manipulation research
- Hand tracking for AR/VR
- Affordance recognition systems
- Grasp planning algorithms
- Virtual object interaction
- Animation and gaming

## Strengths & Weaknesses

### Strengths
1. **MIT License**: Fully open, commercial use allowed
2. **Large Scale**: 230K frames, 1,800 object models
3. **Affordance Focus**: Functional understanding, not just geometry
4. **Intent Annotations**: Why objects are manipulated
5. **Multi-view Capture**: 4 calibrated cameras
6. **3D Hand Poses**: Detailed hand configurations
7. **Object 3D Models**: 1,800 meshes with part segmentation
8. **Part-Level Affordances**: Fine-grained functional labels
9. **HuggingFace Integration**: Easy download and access
10. **Active Development**: OakInk2 shows ongoing commitment
11. **Bimanual Data**: OakInk2 includes two-handed manipulation
12. **Task Hierarchy**: Three abstraction levels in OakInk2
13. **Well-Documented**: Comprehensive website and papers
14. **Compositional**: Enables learning from primitives to complex tasks

### Weaknesses
1. **Unclear Depth Information**: May lack RGB-D data
2. **NO Tactile/Force Data**: Visual only, no contact forces
3. **NO Robot Demonstrations**: Human-only, no robot execution
4. **Hand Model Unclear**: Papers don't specify MANO vs. keypoints vs. other
5. **Limited Finger Detail**: May not capture full finger articulation
6. **Object Count**: 100 objects for interaction (though 1,800 in shape dataset)
7. **Subject Diversity**: Only 12 people
8. **Lab Capture**: Likely controlled environment, not "in-the-wild"
9. **Static Objects**: May focus on grasping, not dynamic manipulation
10. **No Contact Labels**: Affordances inferred, not explicit contact geometry
11. **Temporal Resolution**: Unclear frame rates for motion capture
12. **Multi-view Only**: No egocentric view for robot perspective

### For Robot Manipulation Training
- **Missing depth**: May need depth for robot grasp planning
- **No force feedback**: Cannot learn force-controlled manipulation
- **Human-only**: No robot replay or teleoperation data
- **Contact inference**: Contacts not explicitly labeled with geometry/force
- **Object pose only**: May lack object contact point annotations

## Relevance to DexterData

### Direct Relevance: MODERATE-HIGH

**Why It Matters A LOT:**
1. **Affordance-Aware Manipulation**: Emphasizes understanding object functionality
2. **Intent-Oriented**: Captures why objects are manipulated
3. **Large-Scale Hand-Object Data**: 230K frames with hand poses
4. **MIT License**: Commercial-friendly, can inspire similar licensing
5. **3D Hand Poses**: Includes hand configurations
6. **Massive Object Library**: 1,800 objects with affordances
7. **Part-Level Annotations**: Fine-grained object understanding
8. **Bimanual Focus**: OakInk2 addresses two-handed manipulation
9. **Task Hierarchy**: Complex task decomposition (OakInk2)
10. **Active Research**: Ongoing development shows sustained value

**Gaps for DexterData:**
1. **Depth Unclear**: May lack RGB-D needed for robot training
2. **No Tactile/Force**: Missing physical interaction data
3. **No Robot Demos**: Human demonstrations only
4. **Contact Geometry**: Affordances inferred, not explicit contact labels
5. **Limited Finger Detail**: May not capture full finger articulation
6. **Static Grasps**: May emphasize grasping over dynamic manipulation

### Lessons for DexterData

**What to Adopt:**
1. **MIT License**: Use same permissive licensing for commercial adoption
2. **Affordance Annotations**: Label object functional properties
3. **Intent Labels**: Capture why, not just how, objects are manipulated
4. **Part-Level Segmentation**: Fine-grained object annotations
5. **Multi-view Capture**: Multiple calibrated cameras
6. **Large Object Library**: Thousands of objects with metadata
7. **Task Hierarchy**: Primitive → Complex task structure (like OakInk2)
8. **Bimanual Focus**: Include two-handed manipulation
9. **HuggingFace Distribution**: Easy access through modern ML platforms
10. **3D Hand Poses**: Detailed hand configurations
11. **Compositional Design**: Enable learning from parts to wholes
12. **Active Maintenance**: Continuous updates and improvements

**What to Improve for DexterData:**
1. **Guarantee RGB-D**: Ensure depth information included
2. **Add Tactile/Force**: Include contact force measurements
3. **Add Robot Demonstrations**: Pair human demos with robot executions
4. **Explicit Contact Labels**: Annotate contact regions and geometry
5. **Full Finger Articulation**: Ensure detailed finger joint tracking
6. **Dynamic Manipulation**: Not just grasping, but in-hand manipulation
7. **Egocentric Views**: Include robot's perspective
8. **Force-Controlled Tasks**: Tasks requiring force modulation
9. **Contact Point Clouds**: Dense contact geometry
10. **Temporal Dynamics**: High-frequency capture for fast motions

### Strategic Positioning

**OakInk is the CLOSEST existing dataset to DexterData's vision.**

**Similarities:**
- Large-scale hand-object interaction
- Affordance and intent focus
- 3D hand poses and object models
- MIT license for commercial use
- Task hierarchy thinking (OakInk2)
- Bimanual manipulation (OakInk2)

**Key Differentiators for DexterData:**
- **Guaranteed RGB-D**: Depth required, not optional
- **Tactile/Force Data**: Physical interaction measurements
- **Robot Compatibility**: Designed for robot training from day one
- **Contact Annotations**: Explicit contact geometry and forces
- **In-Hand Manipulation**: Dynamic re-grasping, not just static grasps
- **Egocentric + Multi-view**: Include robot perspective
- **Even More Scale**: 500K-1M+ demonstrations
- **Real Robot Validation**: Show that data trains working robots

### Comparison: OakInk vs. DexterData

| Aspect | OakInk + OakInk2 | DexterData (Goal) |
|--------|------------------|-------------------|
| **Scale** | 230K frames | 500K-1M+ frames |
| **Hand Poses** | 3D (unclear model) | MANO meshes guaranteed |
| **Depth** | Unclear | RGB-D required |
| **Objects** | 100 interact, 1800 models | 1000+ with full metadata |
| **Affordances** | Yes, part-level | Yes, plus contact affordances |
| **Intent** | Yes | Yes, plus task rewards |
| **Tactile/Force** | No | Yes, when possible |
| **Robot Data** | No | Yes, central component |
| **Contact Labels** | Inferred | Explicit geometry + force |
| **License** | MIT (perfect!) | MIT/Apache |
| **Bimanual** | OakInk2 has it | Yes, emphasized |
| **Task Hierarchy** | OakInk2 has it | Yes, with RL rewards |
| **Distribution** | HuggingFace + website | Same approach |

### Collaboration Potential

**OakInk and DexterData could be highly complementary:**

1. **Data Augmentation**: Use OakInk for pre-training, fine-tune on DexterData
2. **Object Library**: Leverage OakInk-Shape's 1,800 objects
3. **Affordance Taxonomy**: Adopt OakInk's affordance ontology
4. **Task Hierarchy**: Use OakInk2's abstraction levels
5. **Cross-Dataset**: Train on both for maximum diversity

**DexterData Could:**
- Annotate OakInk subset with depth, contact, force (if possible)
- Use OakInk's objects in new manipulation scenarios
- Reference OakInk's affordance labels
- Collaborate with OakInk team on shared standards

### Use Case Differentiation

**OakInk**: Understanding hand-object interaction (perception)
**DexterData**: Executing manipulation tasks (control)

But there's significant overlap:
- Both need 3D hand poses
- Both need object affordances
- Both target robot manipulation

**DexterData's Edge**: Robot-first design with depth, contact, force, and robot demos

### Bottom Line Assessment

**OakInk is DexterData's closest inspiration and potential partner.**

**What OakInk Does Brilliantly:**
- Large-scale hand-object data
- Affordance and intent focus
- MIT license for commercial use
- Part-level object understanding
- Task hierarchy (OakInk2)
- Bimanual manipulation (OakInk2)

**What DexterData Must Add:**
- Guaranteed depth (RGB-D)
- Tactile and force data
- Robot demonstrations and validation
- Explicit contact geometry
- Even larger scale
- In-hand dynamic manipulation
- Proven robot training results

**Strategic Positioning**: "DexterData is OakInk for robot manipulation training: same affordance-aware, intent-oriented philosophy, with added depth, contact, force, and robot data needed to actually train dexterous manipulation policies."

**Partnership Opportunity**: If DexterData team could collaborate with OakInk team:
- Shared object library (1,800+ objects)
- Shared affordance ontology
- Cross-dataset training protocols
- Unified hand-object interaction knowledge repository

**Competitive Differentiation**: DexterData is "OakInk + depth + tactile + robots"

**Quote-worthy**: "OakInk pioneered large-scale, affordance-aware hand-object interaction data. DexterData brings this vision to robot manipulation training with depth, contact, and force annotations."

---

**Dataset Access**: https://oakink.net/ (OakInk), https://oakink.net/v2/ (OakInk2)
**GitHub**: https://github.com/oakink/OakInk (v1), https://github.com/oakink/OakInk2 (v2)
**HuggingFace**: OakInk-v1 available on HuggingFace Datasets
**License**: MIT (commercial use allowed)
**Papers**:
- OakInk: CVPR 2022
- OakInk2: CVPR 2024
**Institution**: Shanghai Jiao Tong University + collaborators
**Years**: 2022 (v1), 2024 (v2)
