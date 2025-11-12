# Step 1: Research Gaps Analysis for CoRL 2026

**Date:** 2025-11-12
**Focus Area:** World Models for Robot Manipulation with Diffusion Control
**Context:** 6-month timeline, simulation-only (Isaac Gym, MuJoCo), strong LLM/world model/diffusion background

---

## Key Papers & Trends (2024-2025)

### World Models for Manipulation
1. **IRASim** (ICCV 2025) - Fine-grained world model for robot manipulation
2. **FOCUS** (2025) - Object-centric world model for manipulation
3. **PIVOT-R** (NeurIPS 2024) - Primitive-driven waypoint-aware world model
4. **VidMan** (NeurIPS 2024) - Exploits implicit dynamics from video diffusion models
5. **RSS 2025 Workshop** - Structured World Models for Robotic Manipulation (June 2025)
6. **1X Technologies** - Learning simulators directly from raw sensor data
7. **NVIDIA Cosmos** (Jan 2025) - World Foundation Model Platform for Physical AI

### Diffusion Policy Advances
1. **Diffusion Policy** (IJRR 2024) - 46.9% improvement over SOTA, benchmarked on 15 tasks
2. **TinyVLA** (2025) - Integrates diffusion head with pretrained VLA
3. **Hierarchical Diffusion Policy** (2025) - Contact-guided trajectory generation
4. **Diffusion Trajectory-guided Policy (DTP)** - Framework for long-horizon tasks
5. **Flow Matching** - Alternative to diffusion with more stable training

---

## Identified Research Gaps & Limitations

### 1. **Error Accumulation in Long-Horizon World Model Prediction** ⭐⭐⭐
**What Authors Say:**
- "Autoregressive frame-wise simulation is slow and prone to significant error accumulation for long-horizon tasks"
- "Key challenges include long-horizon prediction, error accumulation, and sim-to-real transfer"
- Diffusion policies show "poor performance during transition between stages due to high multimodality"

**Benchmark Failures:**
- Diffusion Policy struggles with multi-stage tasks (transition phases)
- World models accumulate error over 100+ step horizons
- Common failure: premature termination or getting stuck in loops

**Unrealistic Assumptions:**
- Assumes perfect state observation at each timestep
- No error correction mechanisms in autoregressive rollouts
- Treats all timesteps equally (no awareness of critical transition points)

**Novelty Potential:** ⭐⭐⭐⭐⭐ (High - not directly addressed in current literature)
**Feasibility:** ⭐⭐⭐⭐ (Good - can validate in simulation)
**Impact:** ⭐⭐⭐⭐⭐ (Critical for real deployment)

---

### 2. **Multimodal Uncertainty & Out-of-Distribution Detection in Diffusion Policies** ⭐⭐⭐
**What Authors Say:**
- "Fundamental limitations in out-of-distribution failures that persist due to compounding errors"
- "Existing methods like Ensemble-DAgger struggle with highly expressive policies and often misinterpret policy disagreements as uncertainty at multi-modal decision points"
- "Image-based and depth-based diffusion policies often deliver unpredictable behaviors in real-world experiments"

**Benchmark Failures:**
- Diff-DAgger misinterprets multimodal decisions as uncertainty
- Unpredictable behaviors require human intervention for safety
- Common failure modes: missed grasps, incorrect grasp recovery, out-of-domain positioning

**Unrealistic Assumptions:**
- Policy disagreement = high uncertainty (not always true)
- All modalities in action distribution are equally likely
- OOD can be detected through ensemble variance

**Novelty Potential:** ⭐⭐⭐⭐ (Moderate-High - Diff-DAgger exists but insufficient)
**Feasibility:** ⭐⭐⭐⭐⭐ (Excellent - can create OOD scenarios in sim)
**Impact:** ⭐⭐⭐⭐ (High - critical for safety)

---

### 3. **Contact-Rich Manipulation in Learned Simulators** ⭐⭐⭐
**What Authors Say:**
- "Physics-based simulators are mostly designed for rigid body dynamics... difficult to simulate robot hands opening cardboard boxes, cutting fruit, unscrewing frozen jars"
- "Current 1B parameter models generate accurate predictions for simple scenes, while generating complex collisions or other humans remains challenging"
- Traditional simulators "require a lot of manual asset authoring"

**Benchmark Failures:**
- World models fail on deformable objects, friction-dependent tasks
- Physical plausibility issues in learned simulators
- Manual asset authoring bottleneck

**Unrealistic Assumptions:**
- Rigid body dynamics sufficient for most tasks
- Learned models can implicitly capture contact physics
- Visual similarity implies physical accuracy

**Novelty Potential:** ⭐⭐⭐⭐⭐ (Very High - active research frontier)
**Feasibility:** ⭐⭐⭐ (Moderate - requires physics priors)
**Impact:** ⭐⭐⭐⭐⭐ (Critical for real-world tasks)

---

### 4. **Rapid Environmental Adaptation (Days-Scale Degradation)** ⭐⭐
**What Authors Say:**
- "Model performance can rapidly degrade within days due to subtle environmental changes like background variations or ambient lighting"
- "Making old experiments unreproducible because the old environment no longer exists"
- "Limited training data availability compared to language models"

**Benchmark Failures:**
- No standard benchmarks for environmental robustness
- Deployment studies show rapid degradation
- Retraining required frequently

**Unrealistic Assumptions:**
- Environment remains static after training
- Small visual changes don't affect policy/model
- Sufficient data diversity during training

**Novelty Potential:** ⭐⭐⭐ (Moderate - domain adaptation well-studied)
**Feasibility:** ⭐⭐⭐ (Moderate - requires temporal data collection)
**Impact:** ⭐⭐⭐⭐ (High for deployment)

---

### 5. **Compositional Generalization Across Object Categories** ⭐⭐⭐
**What Authors Say:**
- Object-centric world models (FOCUS) are emerging but limited
- "Single modality is limited, hindering perception, cognition, and interaction performance"
- Most methods train on specific object sets, struggle with novel objects

**Benchmark Failures:**
- RLBench/MetaWorld use fixed object sets
- No systematic evaluation of cross-category generalization
- Zero-shot object manipulation rarely tested

**Unrealistic Assumptions:**
- Test objects similar to training distribution
- Object affordances can be inferred from appearance alone
- Manipulation skills transfer across object categories

**Novelty Potential:** ⭐⭐⭐⭐ (Moderate-High - some work exists)
**Feasibility:** ⭐⭐⭐⭐ (Good - can create diverse object sets in sim)
**Impact:** ⭐⭐⭐⭐ (High - essential for general manipulation)

---

## Gap Ranking (Novelty × Feasibility × Impact)

### 🥇 Rank 1: Error Accumulation in Long-Horizon World Model Prediction
**Score: 5 × 4 × 5 = 100**
- **Why Top:** Directly addresses critical limitation in both world models AND diffusion policies
- **Your Strengths:** World model expertise + diffusion control background
- **Timeline Fit:** Can implement and validate in 6 months
- **CoRL Appeal:** Practical impact + theoretical contribution

### 🥈 Rank 2: Contact-Rich Manipulation in Learned Simulators
**Score: 5 × 3 × 5 = 75**
- **Why Second:** Very high impact but moderate feasibility (physics integration challenging)
- **Risk:** May require more than 6 months for robust solution
- **CoRL Appeal:** Frontier research but competitive area

### 🥉 Rank 3: Compositional Generalization Across Object Categories
**Score: 4 × 4 × 4 = 64**
- **Why Third:** Solid all-around but less novel (object-centric models exist)
- **Your Strengths:** LLM background could help with semantic understanding
- **CoRL Appeal:** Good practical contribution

### Rank 4: Multimodal Uncertainty & OOD Detection
**Score: 4 × 5 × 4 = 80**
- **Why Fourth:** Excellent feasibility but Diff-DAgger paper is recent (Oct 2024)
- **Risk:** May be crowded by CoRL 2026 deadline
- **Note:** Still viable as complementary contribution

### Rank 5: Rapid Environmental Adaptation
**Score: 3 × 3 × 4 = 36**
- **Why Last:** Domain adaptation well-studied, lower novelty
- **Challenge:** Requires real-world or very realistic sim data

---

## Recommended Focus: Gap #1

**Error Accumulation in Long-Horizon World Model Prediction**

This gap offers the best combination of:
1. ✅ High novelty (not directly solved)
2. ✅ Strong feasibility (your expertise + simulation resources)
3. ✅ Critical impact (blocks real-world deployment)
4. ✅ Clear validation path (existing benchmarks + new long-horizon tasks)
5. ✅ Integrates your strengths (world models + diffusion control)

**Next Step:** Generate 3 distinct solution approaches for this gap.
