# Competing Open Datasets Analysis - DexterData

**Analysis Date**: 2025-11-17
**Focus**: Datasets with finger tracking data (NOT vision-based, NOT tactile)

---

## Executive Summary

**Good News**: There are **very few** open datasets with direct finger-level tracking from sensors (like gloves/IMUs) during manipulation tasks. Most datasets either:
- Use vision-based hand pose estimation (not direct sensor data)
- Use MoCap markers (limited to lab settings, not scalable)
- Focus on gestures rather than manipulation tasks

**Key Insight**: Your DexterData approach (sensor gloves + everyday tasks at scale) has **minimal direct competition** in the open dataset space.

---

## Category 1: Sensor Glove Datasets (MOST SIMILAR)

### ✅ Ninapro Database
**Website**: http://ninaweb.hevs.ch/
**Zenodo**: https://zenodo.org/records/3480074

**What it is**:
- 77 subjects performing 40 hand movements/grasps
- CyberGlove II data glove (22 sensors per hand)
- Calibrated joint angle data available
- ~50GB total dataset

**Key Differences from DexterData**:
- ❌ Focused on prosthetics research (controlled gestures, not natural tasks)
- ❌ Lab setting only (not in-the-wild)
- ❌ Limited task diversity (40 predefined movements)
- ❌ Not focused on manipulation of everyday objects
- ✅ Similar sensor approach (direct finger tracking)

**Competitive Threat**: **LOW** - Different use case (prosthetics vs. robotics manipulation)

---

### ✅ DexCap Dataset (RSS 2024)
**Website**: https://dex-cap.github.io/
**Download**: https://huggingface.co/datasets/chenwangj/DexCap-Data
**GitHub**: https://github.com/j96w/DexCap

**What it is**:
- 90 minutes of hand mocap data (30 min wiping, 60 min packaging)
- Combines electromagnetic field tracking + SLAM
- Released under CC BY 4.0 license
- Hardware: Custom gloves with EM sensors + Intel RealSense cameras

**Key Differences from DexterData**:
- ❌ Small scale (90 minutes vs. your goal of 100+ hours)
- ❌ Limited task diversity (2 tasks)
- ❌ Custom hardware (not as portable as Rokoko)
- ❌ Academic project (not positioned as scalable dataset platform)
- ✅ Similar approach (sensor-based finger tracking)
- ✅ Focused on dexterous manipulation

**Competitive Threat**: **MEDIUM** - Similar vision but very limited scale. Could expand, but currently academic-only.

---

## Category 2: MoCap Marker Datasets (Lab-Only)

### ARCTIC Dataset (CVPR 2023)
**Website**: https://arctic.is.tue.mpg.de/
**GitHub**: https://github.com/zc-alexfan/arctic

**What it is**:
- 2.1M video frames with 3D hand/object meshes
- Bimanual dexterous manipulation
- 54 Vicon cameras (expensive lab setup)
- MoCap markers on hands + objects
- MoCap data available for download

**Key Differences**:
- ❌ Requires $500K+ Vicon setup (not scalable)
- ❌ Lab-only (no in-the-wild diversity)
- ❌ MoCap markers (not wearable sensor gloves)
- ✅ Dexterous manipulation focus
- ✅ High quality ground truth

**Competitive Threat**: **LOW** - Can't scale due to cost/infrastructure

---

### GRAB Dataset (ECCV 2020)
**Website**: https://grab.is.tue.mpg.de/
**GitHub**: https://github.com/otaheri/GRAB

**What it is**:
- Whole-body grasping dataset
- 10 subjects, 51 everyday objects
- MoCap-based (markers fitted to body/hand model)
- Includes finger articulation data

**Key Differences**:
- ❌ MoCap markers (lab-only)
- ❌ Small scale (10 subjects)
- ❌ Focused on grasping poses, not manipulation sequences
- ✅ Everyday objects

**Competitive Threat**: **LOW** - Limited scale, lab-only

---

### ContactPose Dataset (ECCV 2020)
**Website**: https://contactpose.cc.gatech.edu/
**GitHub**: https://github.com/facebookresearch/ContactPose

**What it is**:
- 2,306 unique grasps, 25 objects, 50 participants
- 2.9M RGB-D images
- OptiTrack MoCap markers
- Focus on contact patterns

**Key Differences**:
- ❌ MoCap-based (lab setting)
- ❌ Static grasps, not dynamic manipulation
- ✅ Good diversity (50 participants, 25 objects)

**Competitive Threat**: **LOW** - Static grasps, lab-only

---

## Category 3: Vision-Based (NOT Sensor Data)

These datasets use cameras to estimate hand pose, not direct sensor tracking:

- **HO3D**: Hand-object pose from RGB-D (vision-based estimation)
- **HO-Cap**: Multi RGB-D camera system (no sensor gloves)
- **FPHA**: First-Person Hand Action (vision + some MoCap validation)

**Competitive Threat**: **NONE** - Different data modality

---

## Category 4: Emerging Systems (Hardware Only)

### FSGlove, DOGlove (2024-2025)
- IMU-based hand tracking systems
- No public datasets released yet
- Academic research prototypes

**Competitive Threat**: **WATCH** - Could release datasets in future

---

## Key Competitive Insights

### 1. **The Gap You're Filling**

| Feature | Ninapro | DexCap | ARCTIC/GRAB | **DexterData** |
|---------|---------|--------|-------------|----------------|
| **Sensor-based** | ✅ | ✅ | ❌ (MoCap) | ✅ |
| **Scalable** | ❌ | ❌ | ❌ | ✅ |
| **Everyday tasks** | ❌ | ⚠️ (2 tasks) | ❌ | ✅ |
| **In-the-wild** | ❌ | ❌ | ❌ | ✅ |
| **100+ hours** | ❌ | ❌ | ❌ | ✅ (goal) |
| **Crowdsourced** | ❌ | ❌ | ❌ | ✅ |

**Conclusion**: No existing dataset combines sensor-based finger tracking + scalability + task diversity + in-the-wild collection.

---

### 2. **Why No One Has Done This**

Based on the landscape:

1. **Academic datasets** (ARCTIC, GRAB, ContactPose):
   - Have expensive MoCap labs
   - Don't think about crowdsourcing
   - Prioritize precision over scale
   - No incentive to scale beyond paper publication

2. **Sensor glove datasets** (Ninapro, DexCap):
   - Ninapro: Designed for prosthetics (different use case)
   - DexCap: Academic project, small scale (90 min)

3. **No one has applied the Scale AI playbook**:
   - Gig workers for data collection
   - Scalable hardware (affordable gloves)
   - Platform approach (not one-off dataset)

---

### 3. **Competitive Positioning**

**Your unique value**:
- "The only large-scale, sensor-based, in-the-wild finger tracking dataset"
- "Ninapro at 100× scale for robotics (not prosthetics)"
- "DROID/RH20T but with finger-level data"

**Comparisons you can make**:
- "DexCap showed sensor-based tracking works for manipulation (90 min). We're scaling to 1000+ hours."
- "ARCTIC proved dexterous manipulation data is valuable. We're making it scalable and affordable."
- "Ninapro validated sensor gloves for hand data. We're applying it to robotics manipulation tasks."

---

### 4. **Timing Advantage**

**Why you should move fast**:

1. **DexCap is recent** (2024): Validates your approach, but still tiny scale
2. **No commercial player** has entered this space yet
3. **Foundation model companies** (Physical Intelligence, Skild) are desperately collecting data internally
4. **12-24 month window** before Scale AI might notice

---

## Recommendations

### 1. **Differentiate Clearly**
In your marketing, emphasize:
- ✅ **Scale**: "100× larger than existing sensor-based datasets"
- ✅ **Diversity**: "In-the-wild vs. lab-controlled"
- ✅ **Tasks**: "Everyday manipulation vs. controlled gestures"
- ✅ **Platform**: "Ongoing collection vs. one-off dataset"

### 2. **Reference, Don't Compete**
- **Cite** existing datasets (Ninapro, DexCap, ARCTIC) in your papers
- **Position** as complementary: "We combine DexCap's sensor approach with DROID's scale philosophy"
- **Collaborate**: Reach out to DexCap authors - they might be interested in helping scale

### 3. **Move Fast on Initial Release**
- Release your 100-hour dataset ASAP
- No one else is positioned to scale sensor-based finger data
- First-mover advantage is significant

### 4. **Monitor These Signals**
Watch for:
- DexCap expanding beyond 90 minutes
- Scale AI announcing robotics hand data collection
- Ninapro pivoting to manipulation tasks
- New academic datasets at RSS/CoRL/ICRA 2025

---

## Bottom Line

**You have a clear runway**. The only dataset that's somewhat similar (DexCap) is:
- 100× smaller (90 min vs. your 100+ hour goal)
- Academic project (not platform)
- No signs of scaling

**The market is yours to lose.** Execute fast on your 100-hour release and establish yourself as "the finger tracking data people" before anyone else realizes this opportunity.

---

## References

1. **Ninapro**: http://ninaweb.hevs.ch/
2. **DexCap**: https://dex-cap.github.io/
3. **ARCTIC**: https://arctic.is.tue.mpg.de/
4. **GRAB**: https://grab.is.tue.mpg.de/
5. **ContactPose**: https://contactpose.cc.gatech.edu/

---

[← Back to README](README.md)
