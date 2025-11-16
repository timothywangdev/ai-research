# Dataset Landscape Index - Complete Analysis

**Last Updated**: 2025-11-16
**Total Datasets Analyzed**: 35+
**Research Scope**: Egocentric, Robot Manipulation, Dexterous, Hand Pose, Proprietary

---

## Purpose

This folder contains comprehensive research on all major datasets relevant to DexterData's market positioning. Each dataset has been analyzed for:
- Scale and specifications
- Research community reception
- Industry adoption
- Licensing and accessibility
- Competitive overlap with DexterData
- Strategic opportunities

---

## Dataset Categories

### 1. Egocentric Vision Datasets (4 datasets)
Focus: First-person perspective, human activities

| Dataset | Scale | License | Finger Tracking | Competitive Overlap |
|---------|-------|---------|----------------|---------------------|
| **EGO4D** | 3,670 hrs | Research-only | ❌ NO | LOW - Different domain (AR/VR vs robotics) |
| **EPIC-KITCHENS** | 100 hrs | CC-BY-NC | ❌ NO | MEDIUM - Kitchen tasks but non-commercial |
| **Ego-Exo4D** | 1,286 hrs | Restricted | ❌ NO | MEDIUM - Skilled activities, proprietary hardware |
| **Assembly101** | 513 hrs | CC-BY-NC | ❌ NO | MEDIUM - Assembly but toy-focused |

**Key Insight**: EGO4D proves egocentric data is valuable (600+ citations, powers Meta RayBan glasses), but **ALL lack finger tracking** for robotics.

**Files**:
- `EGO4D.md` - Already covered in COMPETITIVE_ANALYSIS.md
- `EPIC-KITCHENS.md`
- `Ego-Exo4D.md`
- `Assembly101.md`
- `Ego4D-Goal_Step.md`

---

### 2. Robot Manipulation Datasets (6 datasets)
Focus: Robot demonstrations, gripper-based manipulation

| Dataset | Scale | License | Finger Tracking | Robot Platforms |
|---------|-------|---------|----------------|-----------------|
| **DROID** | 76K traj | MIT | ❌ NO | 16 institutions, various grippers |
| **RH20T** | 110K seq | Open (pending) | ❌ NO | Contact-rich, multi-modal |
| **Open X-Embodiment** | 1M+ traj | CC-BY 4.0 | ❌ NO | 22 robot types |
| **Bridge Data V2** | 60K traj | MIT | ❌ NO | WidowX, Franka |
| **RT-X** | Foundation model | Proprietary | ❌ NO | Google DeepMind models |
| **RoboNet** | 15M frames | MIT | ❌ NO | 7 robots (legacy) |

**CRITICAL FINDING**: **ZERO datasets have finger tracking**. Authors explicitly identify this gap:
- BridgeData V2: "Dexterous tasks is an exciting avenue for future work"
- RH20T: "We hope to extend to multi-finger dexterous manipulation"

**Files**:
- `DROID.md`
- `RH20T.md`
- `Open_X_Embodiment.md`
- `Bridge_Data_V2.md`
- `RT-X.md`
- `RoboNet.md`
- `ROBOT_DATASETS_SUMMARY.md`

---

### 3. Dexterous Manipulation Datasets (7 datasets)
Focus: Hand-object interaction, finger tracking

| Dataset | Scale | Finger Tracking | Robot-Usable | License |
|---------|-------|----------------|--------------|---------|
| **RealDex** | 2.6K seq | ✅ YES (Shadow Hand) | ✅ YES | Open (NVIDIA) |
| **DexYCB** | 582K frames | ⚠️ MANO params | ❌ NO | CC-BY-NC 4.0 |
| **HO-3D** | 80K frames | ⚠️ MANO params | ❌ NO | Academic-only |
| **H2O** | 4M frames | ⚠️ MANO params | ❌ NO | Academic-only |
| **DexMV** | Method/pipeline | Vision-based | ⚠️ Indirect | Research demo |
| **ContactDB** | 375 grasps | Thermal contact | ❌ NO | CC-BY 4.0 |
| **GRAB** | 1.66M frames | Full-body MoCap | ❌ NO | ❌ Non-commercial |

**Key Insight**: Only **RealDex has actionable robot joint angles** (direct competitor). Others use MANO parameters (computer vision focus, not robot control).

**Files**:
- `RealDex.md`
- `DexYCB.md`
- `HO-3D.md`
- `H2O.md`
- `DexMV.md`
- `ContactDB.md`
- `GRAB.md`

---

### 4. Hand Pose & Gesture Datasets (5 datasets)
Focus: Hand pose estimation, gesture recognition

| Dataset | Scale | Use Case | Manipulation Tasks | Commercial Use |
|---------|-------|----------|-------------------|----------------|
| **InterHand2.6M** | 2.6M images | AR/VR hand tracking | ❌ NO | ✅ YES (Meta) |
| **FreiHAND** | 130K images | Pose estimation benchmark | ❌ NO | ✅ YES |
| **ARCTIC** | 2.1M images | Articulated objects | ✅ LIMITED | ✅ YES |
| **First-Person Hand Action** | 100K frames | Action recognition | ✅ YES (45 tasks) | Research-only |
| **EgoHands** | 4,800 images | Segmentation benchmark | ❌ NO | ✅ YES |

**Key Insight**: ARCTIC (CVPR 2023) is most relevant - captures articulated object manipulation. But still lacks force/tactile, robot correspondence, task success metrics.

**Files**:
- `InterHand2.6M.md`
- `FreiHAND.md`
- `ARCTIC.md`
- `First-Person_Hand_Action_Benchmark.md`
- `EgoHands.md`

---

### 5. Additional Manipulation Datasets (8 datasets)
Focus: Various manipulation modalities

| Dataset | Scale | Key Feature | Relevance to DexterData |
|---------|-------|-------------|------------------------|
| **OakInk** | 230K frames | Affordance-aware, MIT license | HIGH - Closest match |
| **BEHAVE** | Multi-view RGB-D | 3D meshes + contact | HIGH - Methodology |
| **MIME** | 8,260 demos | Multi-modal robot data | MEDIUM - No fingers |
| **RoboTurk** | Crowdsourcing platform | Teleoperation at scale | MEDIUM - Platform model |
| **Something-Something V2** | 220K videos | Hand actions | LOW - Vision-only |
| **HAKE** | 7M+ annotations | 21-point hand tracking | MEDIUM - 2D only |
| **100 Days of Hands** | 131 days | Hand-contact focus | MEDIUM - No 3D |
| **CMU Panoptic Studio** | Multi-view MoCap | Gold-standard tracking | MEDIUM - Research-only |

**Files**:
- `OakInk.md`
- `BEHAVE.md`
- `MIME.md`
- `RoboTurk.md`
- `Something-Something-V2.md`
- `HAKE.md`
- `100_Days_of_Hands.md`
- `CMU_Panoptic_Studio.md`

---

### 6. Proprietary & Commercial Datasets (14 entities)
Focus: Company-specific data, foundation models

| Company | Known Scale | Key Differentiator | Market Position |
|---------|-------------|-------------------|-----------------|
| **Tesla Optimus** | Undisclosed (large) | 100+ data collectors, $48/hr | Humanoid leader |
| **Figure AI** | 500 hrs teleoperation | Project Go-Big, Brookfield video | $2.6B valuation |
| **1X Technologies** | Undisclosed | VR teleoperation, home deployment | Consumer-focused |
| **Sanctuary AI** | Undisclosed | Highest fidelity, tactile sensors | Manufacturing |
| **Physical Intelligence** | 10K+ hrs | π0 model (open-sourced) | Foundation model |
| **Covariant** | Tens of millions traj | 7-year warehouse moat | Warehouse automation |
| **NVIDIA Isaac GR00T** | 780K synthetic (11 hrs!) | Near-zero cost generation | Platform play |
| **AgiBot World** | **1M+ FREE datasets** | Chinese govt-backed, open | ⚠️ Major threat |
| **Boston Dynamics** | 20 hrs teleoperation | LBMs, simulation-heavy | Research leader |
| **Apptronik Apollo** | Manufacturing flywheel | GR00T integration | Manufacturing |
| **Agility Digit** | Billions sim steps | First humanoid RaaS | Logistics |
| **OptiTrack/Vicon** | Commercial MoCap | Research-grade hardware | Infrastructure |
| **ABB/KUKA/FANUC** | 400K robots (FANUC) | Industrial scale | Legacy automation |

**CRITICAL THREATS**:
1. **NVIDIA synthetic data**: 780K trajectories in 11 hours (volume competition impossible)
2. **AgiBot 1M+ free datasets**: Direct competition with free alternative

**OPPORTUNITIES**:
1. **Tactile/haptic modality**: Only Sanctuary has this (proprietary)
2. **Real-world grounding**: Synthetic + real = 40% better (NVIDIA finding)
3. **Western/licensed access**: Geopolitical concerns about Chinese datasets

**Files**:
- `Tesla_Optimus.md`
- `Figure_AI.md`
- `1X_Technologies.md`
- `Sanctuary_AI.md`
- `Physical_Intelligence.md`
- `Covariant.md`
- `NVIDIA_Isaac_GR00T.md`
- `AgiBot.md`
- `Boston_Dynamics.md`
- `Apptronik_Apollo.md`
- `Agility_Robotics_Digit.md`
- `Motion_Capture_Commercial.md`
- `Industrial_Robotics_ABB_KUKA_FANUC.md`
- `PROPRIETARY_DATASETS_SUMMARY.md`

---

## Summary Statistics

### Total Datasets Analyzed: 35+

**By Category**:
- Egocentric vision: 5
- Robot manipulation: 6
- Dexterous manipulation: 7
- Hand pose/gesture: 5
- Additional manipulation: 8
- Proprietary/commercial: 14

**By Finger Tracking**:
- ✅ Has finger tracking: 8 datasets (23%)
- ❌ No finger tracking: 27 datasets (77%)

**By Robot-Usability**:
- ✅ Robot-actionable data: 2 datasets (RealDex, RoboTurk)
- ⚠️ Potentially usable: 5 datasets (MANO-based)
- ❌ Vision/research only: 28 datasets

**By Commercial License**:
- ✅ Permissive (MIT, CC-BY, Apache): 12 datasets (34%)
- ⚠️ Non-commercial (CC-BY-NC): 8 datasets (23%)
- ❌ Research-only or restricted: 8 datasets (23%)
- ? Unknown/proprietary: 7 entities (20%)

**Total Citations**: 5,000+ combined (validates massive research demand)

**Top Cited**:
1. GRAB: 500+
2. EGO4D: 600+
3. EPIC-KITCHENS: 1,154+
4. BridgeData V2: 322
5. HO-3D: 307

---

## Strategic Insights for DexterData

### Market Validation ✅

**Egocentric data is proven valuable**:
- EGO4D: 600+ citations, powers Meta RayBan glasses
- EPIC-KITCHENS: 1,154 citations, largest kitchen dataset
- Validates first-person perspective for understanding human activities

**Robot learning datasets are thriving**:
- Open X-Embodiment: ICRA 2024 Best Paper Award
- 1M+ trajectories standard, foundation models emerging
- RT-X shows 50-300% improvement with diverse data

**Dexterous manipulation has clear demand**:
- RealDex proves concept (NVIDIA-backed)
- Multiple authors explicitly call for this data
- ARCTIC, OakInk show manipulation focus works

### Competitive Landscape

**Direct Competitors (2)**:
1. **RealDex**: Only other dataset with robot joint angles
   - DexterData advantage: 10x cheaper collection, multi-platform
2. **AgiBot World**: 1M+ FREE datasets (Chinese)
   - DexterData advantage: Western/licensed, specialized domains

**Indirect Competitors (Many)**:
- Robot datasets: Lack finger tracking entirely
- Hand pose datasets: Lack robot-actionable data
- Egocentric datasets: Lack manipulation focus

**Complementary (Several)**:
- EGO4D: High-level task understanding
- Open X-Embodiment: Foundation model pre-training
- NVIDIA GR00T: Synthetic data augmentation

### Critical Gaps (DexterData Opportunities)

**1. Finger Tracking for Robots** ⭐ PRIMARY
- Only RealDex has this (expensive, Shadow Hand-locked)
- All major robot datasets lack fingers
- Researchers explicitly request this

**2. Tactile/Haptic Data** ⭐ STRONGEST DIFFERENTIATOR
- Only Sanctuary has tactile (proprietary, manufacturing)
- Multi-modal (vision + haptics) proven valuable
- Glove-based tactile largely unexplored

**3. Commercial Licensing** ⭐ MEDIUM OPPORTUNITY
- Many top datasets non-commercial (GRAB, EPIC-KITCHENS, H2O)
- Enterprise needs clear licenses
- Defense/govt requires domestic sources

**4. Specialized Domains** ⭐ NICHE VIABLE
- Medical/surgical (regulatory barriers)
- Defense (geopolitical barriers)
- Expert crafts (rare demonstrations)

**5. Real-World Grounding** ⭐ COMPLEMENTARY
- NVIDIA: synthetic + real = 40% better
- Position as "grounding datasets"
- Validation for foundation models

### Threats

**Existential**:
1. **NVIDIA synthetic generation**: 780K trajectories in 11 hours
   - Can't compete on volume
   - Must focus on unique modalities

2. **AgiBot free datasets**: 1M+ open-source
   - Direct competition
   - Need strong differentiation

**Moderate**:
3. **RealDex scaling**: If NVIDIA expands this
4. **Foundation model data moats**: Companies hoarding proprietary data

### Revised Strategy

**OLD**: Large-scale general hand manipulation, license broadly

**NEW**: Tactile/haptic specialization for niche domains, complement free/synthetic

**Key Pivots**:
1. ✅ ALL-IN on tactile modality (pressure-sensing gloves)
2. ✅ Specialize in 2-3 domains (medical, defense, expert crafts)
3. ✅ Complement free datasets (not compete)
4. ✅ Partner with foundation model ecosystems (π0, GR00T)
5. ✅ Prove quantitative value (empirical studies showing tactile improves X%)

---

## Next Actions

Based on this comprehensive dataset landscape analysis:

### Immediate (Week 1-2):
1. Download and evaluate AgiBot dataset (understand free competitor)
2. Design tactile data value experiment (prove haptics improve manipulation)
3. Identify 2-3 specialized domains (medical, defense, or crafts)

### Short-term (Month 1-3):
4. Partner discussions with NVIDIA Isaac, Physical Intelligence π0
5. Pilot tactile data collection (5-10 hours proof-of-concept)
6. Quantitative study: Vision vs Vision+Tactile performance

### Medium-term (Month 3-6):
7. Publish empirical results (establish thought leadership)
8. Build self-service platform (like RoboTurk model)
9. Target niche customers (defense contractors, medical robotics)

---

## Conclusion

This comprehensive analysis of 35+ datasets reveals:

✅ **Market is real**: 5,000+ citations, billion-dollar companies, proven demand

⚠️ **Landscape changed**: NVIDIA synthetic + AgiBot free datasets shift dynamics

✅ **Opportunity remains**: Tactile/haptic modality largely unexplored

⚠️ **Window closing**: 6-12 months before market consolidates

**DexterData can succeed IF**:
1. Pivot to tactile/haptic specialization
2. Focus on defensible niches
3. Prove quantitative value empirically
4. Execute in next 6-12 months

The dataset research is complete. Strategy refinement is critical.

---

## File Organization

All dataset research files are in:
```
/home/user/ai-research/startup_opportunities/dexterdata/dataset_research/
```

**Index files**:
- `00_DATASET_LANDSCAPE_INDEX.md` (this file)
- `ROBOT_DATASETS_SUMMARY.md`
- `PROPRIETARY_DATASETS_SUMMARY.md`

**Individual dataset files**: 35+ markdown files, one per dataset

---

[← Back to Main README](../README.md)
