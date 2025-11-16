# ContactDB

## Overview
- **Release date**: April 2019 (arXiv), June 2019 (CVPR publication)
- **Organization/Institution**: Georgia Institute of Technology (Georgia Tech)
- **Scale**: 50 household objects, 375K frames, 3,750 3D contact maps, 25 participants
- **Cost to create**: Estimated $100K-200K (thermal camera ~$10K-30K, RGB-D cameras, 3D printing, scanning equipment, participant compensation)
- **License type**: Not explicitly stated; available at contactdb.cc.gatech.edu for research purposes

## Dataset Specifications
- **Hand tracking method**: Thermal imaging to capture contact maps (heat transfer from hand to object)
- **Finger DOF captured**: No hand pose/joint angles captured - focuses on contact regions only
- **Objects/tasks included**: 50 household objects (3D printed); participants grasp objects with specific functional intents
- **Annotations**:
  - Contact maps (thermal imaging showing where hand touched object)
  - 3D textured meshes with contact regions
  - RGB-D synchronized images (375K frames)
  - Binary contact labels on object surface
  - Functional grasp intent labels
- **Data formats**:
  - 3D meshes (OBJ/PLY with texture)
  - RGB-D images
  - Contact maps (heatmaps on 3D models)
  - Metadata (JSON/YAML)

## Research Community Reception
- **Citation count**: 187 citations (Semantic Scholar) - strong for specialized dataset
- **Key papers using it**:
  - ContactPose (ECCV 2020, Facebook Research) - successor dataset
  - Grasp synthesis papers
  - Hand-object contact modeling research
  - Tactile simulation work
- **Community feedback**:
  - Novel approach (first large-scale contact dataset using thermal imaging)
  - Praised for creativity and contact map quality
  - Cited as inspiration for contact-aware grasping research
- **Active development**: Moderate - dataset is stable, focus shifted to ContactPose (2020)

## Industry Adoption
- **Use in commercial products**: No known direct commercial products
- **Companies interested**:
  - Soft robotics companies (contact patterns inform gripper design)
  - AR/VR companies (hand-object contact for virtual interactions)
  - Research labs at industrial robotics companies

## Who Uses This Dataset
- **Research groups using it**:
  - Georgia Tech (creators)
  - CMU Robotics Institute
  - MIT CSAIL
  - Research groups studying grasp planning and contact modeling
  - Tactile sensing research groups
- **Application domains**:
  - Grasp contact prediction
  - Soft gripper design
  - Ergonomic tool design
  - Tactile simulation
  - AR/VR hand-object interaction rendering
- **Notable results**: Enabled prediction of contact maps from object geometry; informed design of contact-aware grasping algorithms

## Strengths & Weaknesses

### Strengths
- **Unique modality**: Only large-scale dataset using thermal imaging for contact
- **Contact precision**: Detailed contact maps showing exact touch regions
- **Functional intent**: Grasps are labeled by purpose (use vs. handover)
- **Real contact physics**: Captures actual physical contact, not estimated
- **3D textured models**: Contact maps mapped onto 3D geometry
- **Novel methodology**: Creative solution to hard contact sensing problem

### Weaknesses
- **No hand pose**: Zero information about finger joint angles or hand posture during grasping
- **No kinematic data**: Cannot be used for motion planning or trajectory generation
- **Static grasps only**: Post-grasp captures, not dynamic manipulation sequences
- **Thermal imaging cost**: Specialized equipment ($10K-30K) limits reproducibility
- **No temporal dynamics**: Contact over time not captured (single snapshot per grasp)
- **3D printed objects**: Not real household objects (texture/thermal properties differ)
- **No robot applicability**: Data cannot be directly used to train robot policies
- **Limited scale**: 50 objects is moderate compared to newer datasets

## Relevance to DexterData

### Direct competitor?
**NO** - ContactDB is complementary, not competitive. Focuses on contact maps, not joint angles.

### How does DexterData compare:

**Scale**
- ContactDB: 50 objects, 3,750 contact maps
- DexterData potential: 100+ objects, 10,000+ manipulation sequences (different metrics)

**Finger tracking quality**
- ContactDB: ❌ NO finger tracking at all - only contact regions
- DexterData: ✅ Full joint angle tracking (completely different data type)

**Task diversity**
- ContactDB: Static grasps with functional intent
- DexterData: Full manipulation sequences with temporal dynamics

**Ease of use for robot training**
- ContactDB: ❌ Cannot train robot controllers (no motion/pose data)
- DexterData: ✅ Direct robot training with joint trajectories

### Key differentiators

1. **Fundamentally different data**:
   - ContactDB: WHERE contact happens (spatial contact maps)
   - DexterData: HOW to move fingers (temporal joint trajectories)
   - These are complementary, not competing

2. **Use cases**:
   - ContactDB: Gripper design, contact prediction, grasp quality evaluation
   - DexterData: Robot motion planning, imitation learning, trajectory optimization

3. **Collection method**:
   - ContactDB: Thermal imaging (expensive, specialized)
   - DexterData: Motion capture gloves (scalable, direct measurement)

4. **Robot applicability**:
   - ContactDB: Indirect (informs grasp planning heuristics)
   - DexterData: Direct (train end-to-end policies)

5. **Temporal information**:
   - ContactDB: Static snapshots
   - DexterData: Dynamic sequences

**Competitive positioning**:

ContactDB is NOT a competitor - it's a potential data augmentation source:
- Combine ContactDB contact maps + DexterData joint angles = ultimate dataset
- ContactDB shows WHERE to touch, DexterData shows HOW to move

**Partnership/Integration opportunity**:
- Add pressure-sensing gloves to DexterData → generate contact maps like ContactDB
- Create "ContactDB 2.0" combining thermal contact + joint angle tracking
- Market as: "ContactDB tells you where to grip; DexterData tells you how to manipulate"

**Differentiator for DexterData**:
- Could add contact/pressure sensing to gloves (e.g., StretchSense, SenseGlove have pressure sensors)
- Provide BOTH joint angles AND contact forces → unique combined offering
- ContactDB proves contact data has value → validates adding pressure sensing to DexterData

**Key insight**: ContactDB's 187 citations prove researchers value contact information. DexterData could capture this PLUS joint angles in one system with pressure-sensing gloves.
