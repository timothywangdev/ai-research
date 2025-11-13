# BREAKTHROUGH 09: Foundation Models - The Wrong Kind of Transfer

**Discovery**: Foundation models used for perception, not control—missing the real opportunity
**Opportunity Level**: HIGH (8/10)
**Timeline**: Early stage, 2-4 years to maturity

---

## The Observation

After 800 papers, foundation models (FMs) are everywhere in robotics:

**Papers using foundation models**: ~200 out of 800 (25%)
- CLIP, BERT, GPT, LLaMA: NLP models
- CLIP, DINO, SAM: Vision models
- GPT-4V, Gemini: Multimodal models

**How they're used**:
1. **Perception** (~150 papers, 75%):
   - Visual encoder: Use CLIP/DINO for image features
   - Object detection: Use SAM for segmentation
   - Scene understanding: Use vision-language models
2. **Language grounding** (~40 papers, 20%):
   - Task specification: Natural language → task representation
   - LLM planning: GPT generates high-level plans
3. **Direct control** (~10 papers, 5%):
   - LLM outputs actions (rare, mostly fails)

**What's missing**: Foundation models for CONTROL (dynamics, actions, policies)
- Transfer perception: ✅ (everyone does this)
- Transfer control: ❌ (almost nobody)

---

## The Gap

### Perception Transfer Works:

**Evidence**:
- RT-2: Pre-trained vision encoder (from web images) → robot policy
- OpenVLA: Pre-trained VLM → manipulation
- PerAct: CLIP features for 3D voxel policies
- Success: Vision FMs transfer well to robotics

**Why it works**:
- Web images ≈ robot camera images (similar distribution)
- Object recognition: Same task (recognize "cup" in web vs robot data)
- Large-scale pre-training: Billions of images

---

### Control Transfer Doesn't Work (Yet):

**Current attempts** (~10 papers):
- LLM-based policies: GPT outputs actions directly
- Results: Poor, doesn't work
- Example: LLaRP (ICLR 2024) - tries but limited success

**Why it fails**:
- LLMs trained on text (no physics, no actions)
- No embodiment in pre-training
- Action space mismatch (words ≠ joint angles)
- No dynamics understanding from text alone

**The realization**: Can't transfer control from disembodied models (text/images)

---

## The Missed Opportunity

### There ARE Foundation Models for Control:

**Simulation**:
- MuJoCo, PyBullet, Isaac Gym: Millions of simulated trajectories
- Every RL paper generates millions of rollouts
- This IS embodied data (states, actions, dynamics)

**But**:
- Each paper trains from scratch
- Simulation data thrown away
- No transfer across sim experiments
- **We have millions of hours of simulated control data, UNUSED**

**Cross-robot data**:
- RT-X: 1M+ demonstrations from 22 robots
- Open X-Embodiment: Pooled multi-robot data
- This IS embodied data
- But: Used per-task (no foundation model for control)

**Video data**:
- Internet videos show physics (objects fall, people manipulate)
- Implicit dynamics, contact, motions
- Underutilized for learning control

---

## The Breakthrough Insight

### We need Foundation Models for DYNAMICS and CONTROL, not just perception

**Vision foundation models** (CLIP, DINO):
- Pre-trained on perception (images → labels)
- Transfer: Image understanding

**What we need** (doesn't exist):
- Pre-trained on control (states, actions → outcomes)
- Transfer: Dynamics, affordances, control primitives

**Analogy**:
- 2018: ImageNet pre-training → task-specific fine-tuning
- 2024: CLIP → zero-shot image understanding
- 2025?: **"ControlNet"** → zero-shot control transfer?

---

## Why This Hasn't Happened

### Challenges:

**1. Action Space Heterogeneity**
- Vision: Images are uniform (224×224 RGB)
- Control: Actions vary (7-DoF arm, 12-DoF hand, humanoid, quadruped)
- Can't pre-train single model for all embodiments (yet)

**2. Embodiment Gap**
- Different robots ≠ different cameras (easy to align)
- Different robots = different action spaces (hard to align)
- Transfer unclear

**3. Simulation Diversity**
- Each paper uses different sim environments
- Different physics engines, object models, tasks
- Hard to pool data

**4. Lack of Standardization**
- No "ImageNet for control"
- No standard benchmark for control transfer
- Each paper reinvents wheel

**5. Dynamics are Local**
- Vision: Object "chair" looks similar across scenes (global concept)
- Dynamics: Specific to robot, object, contact (local)
- Harder to generalize

---

## Specific Research Opportunities

### 1. Dynamics Foundation Model

**Concept**: Pre-trained model for dynamics prediction

**Pre-training**:
- Data: Millions of simulated trajectories (across environments)
- Task: Predict s_{t+1} given s_t, a_t
- Model: Transformer over state-action sequences
- Goal: Learn general dynamics priors

**Transfer**:
- Fine-tune on target robot with small real-world data
- Leverage sim-to-real for dynamics understanding
- Zero-shot: Predict dynamics on new robot?

**Benefits**:
- Data efficiency: Pre-trained dynamics → less real data needed
- Sim-to-real: Bridge gap through massive sim pre-training
- Generalization: Cross-task dynamics transfer

**Evidence**:
- Gato (DeepMind, 2022): Multi-task, multi-embodiment model (proof of concept)
- RDT-1B (2024): Billion-parameter robotics Transformer (scaling laws apply)
- World models: Foundation models for video prediction (Sora, etc.)

**Feasibility**: 7/10 (data availability, action space challenge)
**Impact**: 9/10 (foundation for all robot learning)
**Timeline**: 2-3 years (requires large-scale effort)

---

### 2. Action Representation Foundation Model

**Concept**: Learn universal action representation (like word embeddings for actions)

**Problem**: Actions are heterogeneous
- 7-DoF robot: a ∈ ℝ⁷
- 12-DoF hand: a ∈ ℝ¹²
- Humanoid: a ∈ ℝ⁵⁰
- Can't train single model

**Solution**: Action embeddings
- Map diverse action spaces → shared embedding space
- Example: Task space actions (end-effector poses) instead of joint space
- Or: Learn embedding function per robot, align embedding spaces

**Architecture**:
```
Robot A actions: a_A ∈ ℝ⁷
Encoder: E_A(a_A) → z ∈ ℝ²⁵⁶ (shared space)

Robot B actions: a_B ∈ ℝ¹²
Encoder: E_B(a_B) → z ∈ ℝ²⁵⁶ (shared space)

Policy: π(z | s) in shared space
Decoder: D_A(z) → a_A for robot A
         D_B(z) → a_B for robot B
```

**Benefits**:
- Cross-embodiment transfer (learn on robot A, deploy on robot B)
- Compositional actions (combine action primitives)
- Interpretable (action embeddings have semantic meaning)

**Evidence**:
- Word embeddings: word2vec, GloVe (success in NLP)
- Action embeddings: Few papers (~5), underexplored
- RT-X: Attempts cross-embodiment, but no shared action space

**Feasibility**: 6/10 (research problem, not engineering)
**Impact**: 9/10 (enables cross-embodiment transfer)
**Timeline**: 1-2 years

---

### 3. Affordance Foundation Model

**Concept**: Learn affordances (what actions are possible) from web data

**Affordances**: What can I do with this object?
- Cup: Grasp, pour, place
- Door: Push, pull, open
- Button: Press

**Pre-training**:
- Data: Web videos (millions showing people manipulating objects)
- Task: Predict possible actions given object + context
- Model: Video-language model → action affordances

**Transfer**:
- Zero-shot: Given new object, predict affordances
- Fine-tune: Few demonstrations → full policy

**Benefits**:
- Leverage web data (abundant, free)
- Semantic understanding (not just pixels)
- Generalization to novel objects

**Evidence**:
- CLIP: Learns visual affordances implicitly (recognizes "chair" implies "sit")
- VoxPoser (2023): LLM generates affordances, but limited
- Affordance learning: Classical robotics (Gibson, 1979), revived with FMs

**Feasibility**: 7/10 (web video data available, affordance annotation hard)
**Impact**: 8/10 (enables zero-shot object manipulation)
**Timeline**: 1-2 years

---

### 4. Policy Distillation from Foundation Models

**Concept**: Distill control knowledge from large foundation model → small policy

**Setup**:
- Large model: GPT-4V, Gemini (100B+ parameters)
  - Can reason about manipulation (language + vision)
  - Too slow for real-time control (seconds per query)
- Small policy: Diffusion/flow policy (100M parameters)
  - Fast (real-time control)
  - Task-specific

**Distillation**:
- Large model: Teacher (generates plans, waypoints, guidance)
- Small policy: Student (learns to execute)
- Training: Student mimics teacher on many tasks
- Deployment: Only student needed (fast)

**Benefits**:
- Leverage large model reasoning (teacher)
- Real-time control (student)
- Data efficiency (teacher augments training data)

**Evidence**:
- LLM distillation: Common in NLP (BERT → DistilBERT)
- Robotics: Few papers (~10) try this
- RT-2: Distills vision-language model, but not online reasoning

**Feasibility**: 8/10 (distillation well-understood)
**Impact**: 7/10 (improves data efficiency)
**Timeline**: 6-12 months

---

### 5. "ControlNet" - Universal Control Prior

**Concept**: Like CLIP (image-text alignment), but for states-actions-outcomes

**CLIP**: Image ↔ Text (shared embedding space)
**ControlNet**: State-Action ↔ Outcome (shared embedding space)

**Pre-training**:
- Data: Massive dataset of (state, action, outcome) tuples
  - From simulation (millions)
  - From robots (RT-X, Open-X)
  - From videos (inferred actions)
- Objective: Contrastive learning
  - Positive: (s, a, s') from same trajectory
  - Negative: (s, a, s'') where s'' ≠ actual outcome
- Result: Embeddings capture control relationships

**Transfer**:
- Zero-shot: Given new state, predict action → outcome
- Few-shot: Fine-tune with few demonstrations
- Evaluation: Control similarity (like image similarity in CLIP)

**Benefits**:
- Foundation model FOR CONTROL (not just perception)
- Cross-task transfer (similar controls transfer)
- Interpretable (embedding space semantics)

**Feasibility**: 5/10 (very challenging, needs massive data + research)
**Impact**: 10/10 (foundational, field-defining)
**Timeline**: 3-5 years (moonshot project)

---

## Evidence from 800 Papers

### Foundation model usage:

**Perception encoders** (~150 papers):
- CLIP, DINO, SAM for visual features
- Success: Transfer works well
- Examples: RT-2, OpenVLA, PerAct, 3D-VLA, etc.

**Language models** (~40 papers):
- GPT, LLaMA for task specification
- Success: Moderate (language grounding helpful but not sufficient)
- Examples: VoxPoser, ManipLLM, LLM-Planner, etc.

**Multimodal models** (~30 papers):
- GPT-4V, Gemini for vision-language-action
- Success: Early, mixed results
- Examples: RT-2, PaLM-E, etc.

**Control foundation models** (~0 papers):
- Dynamics pre-training: 0 papers
- Action representation learning: ~5 papers (not foundation scale)
- Affordance foundation models: 0 papers
- **Gap: ZERO foundation models for control**

---

## Why This Matters Now

### Trends making control FMs critical:

**1. Scaling Laws Validated**
- NLP: Scaling works (GPT-3 → GPT-4)
- Vision: Scaling works (ViT → huge ViTs)
- Robotics: Starting to scale (RDT-1B, RT-X)
- Implication: Control FMs will scale too

**2. Data Availability Increasing**
- Simulation: Cheap, massive scale (millions of episodes)
- Multi-robot datasets: RT-X, Open-X (1M+ demos)
- Videos: Billions showing physics/manipulation
- Opportunity: Pool for control FM pre-training

**3. Transfer Learning Standard**
- Vision: Everyone uses pre-trained encoders
- NLP: Everyone uses pre-trained LLMs
- Robotics: Everyone uses pre-trained perception, but NOT control
- Next step: Pre-trained control

**4. Compute Available**
- Training large models: Feasible (GPUs cheaper)
- Foundation models: Standard practice
- Robotics behind, catching up

---

## Connection to Our Research Ideas

### HiLoop (#1) + Control FM:

**Opportunity**: Pre-trained world model
- Current: Train world model from scratch
- Better: Pre-train on simulation (millions of trajectories)
- Fine-tune: Real robot (100-1000 trajectories)
- Benefit: Data efficiency, better generalization

**Implementation**:
- Pre-train world model in MuJoCo/Isaac Gym (diverse tasks)
- Transfer: Fine-tune on target task
- HiLoop refinement benefits from better world model

---

### Flow Matching (#3) + Control FM:

**Opportunity**: Pre-trained flow model
- Pre-train flow matching on diverse manipulation trajectories
- Transfer: Few-shot to new task
- Benefit: Data efficiency from foundation model

---

### New Idea: Foundation Model Hierarchical Diffusion

**Concept**: Use control FM at waypoint level
- High-level: Pre-trained control FM generates waypoints
- Low-level: Task-specific diffusion executes
- Combines: Foundation model generalization + task-specific execution

**Feasibility**: 6/10 (depends on control FM availability)
**Impact**: 8/10 (if control FMs exist)

---

## Strategic Implications

### For Our Research:

**Short-term**: Use existing perception FMs (already doing)
- CLIP, DINO for visual features
- Standard practice, not novel

**Medium-term**: Consider control FM projects
- Dynamics pre-training for world models
- Affordance learning from videos
- Could be strong follow-up papers

**Long-term**: "ControlNet" as moonshot
- Multi-year, multi-institution effort
- High-risk, high-reward
- Could be career-defining

---

### For the Field:

**Prediction**: Control FMs will emerge 2025-2028
- 2024: Foundation models for perception (standard)
- 2025-2026: First control FM attempts (dynamics, affordances)
- 2027-2028: "ControlNet" or equivalent (universal control prior)

**First-mover advantage**: Huge
- NLP: GPT-3 defined field
- Vision: CLIP defined field
- Robotics: Control FM will define next era

**Window of opportunity**: 2-3 years
- Current: Nobody leading (wide open)
- Early papers: Will be highly influential

---

## Risks & Challenges

### Challenge 1: Data Heterogeneity

**Problem**: Robot data more diverse than images/text
- Different embodiments, tasks, environments
- Hard to pool into unified dataset

**Mitigation**:
- Focus on common representations (task space, not joint space)
- Learn embodiment-agnostic features
- Multi-task training with embodiment conditioning

### Challenge 2: Dynamics are Local

**Problem**: Dynamics depend on specific robot/object/environment
- Cup dynamics: Different per material, shape, weight
- Not universal like "cup" visual concept

**Mitigation**:
- Learn priors, fine-tune to specifics
- Hierarchical: General dynamics + object-specific
- Meta-learning: Quick adaptation to new dynamics

### Challenge 3: Simulation-to-Reality

**Problem**: Pre-training in sim, deploy in reality
- Sim2real gap for control > gap for perception

**Mitigation**:
- Massive sim diversity (randomization)
- Small real-world fine-tuning
- Residual learning (sim model + real correction)

---

## Actionable Steps

### Immediate (0-3 months):

**For current work**:
- Use existing perception FMs (CLIP, DINO)
- Standard practice, minimal effort
- Baseline for comparisons

---

### Short-term (3-6 months):

**Dynamics pre-training experiment**:
1. Pre-train world model on MuJoCo tasks (100+ diverse tasks)
2. Fine-tune on target task (CALVIN or RLBench)
3. Compare: Pre-trained vs from-scratch
4. Hypothesis: Pre-trained needs less real data

Result: If successful, add to HiLoop or separate short paper

---

### Medium-term (6-12 months):

**Dedicated control FM project**:
Option A: Dynamics foundation model
- Pre-train on sim (massive scale)
- Evaluate transfer to real robots
- Paper: ICLR/NeurIPS (ML conference, foundation model focus)

Option B: Affordance foundation model
- Collect web video + affordance annotations
- Train video-to-affordance model
- Zero-shot evaluation on novel objects
- Paper: CVPR/ICCV (vision + robotics)

Option C: Action representation learning
- Learn shared action embedding across robots
- Cross-embodiment transfer experiments
- Paper: CoRL/RSS

---

### Long-term (1-2 years):

**"ControlNet" moonshot**:
- Requires: Large team, compute, data
- Scope: PhD thesis or multi-institution collaboration
- Venue: Nature/Science (if successful), or NeurIPS/ICLR
- Risk: High, but transformative impact

---

## Conclusion

**Foundation models are used for perception, not control—the real opportunity is missed.**

**Evidence from 800 papers**:
- 200 papers use foundation models (25%)
- 75% for perception (CLIP, DINO)
- 20% for language grounding (GPT)
- 5% for direct control (mostly fails)
- **0% for control foundation models** (dynamics, actions, affordances)

**The gap**:
- Perception FMs: ✅ (work well, widely used)
- Control FMs: ❌ (don't exist yet)

**Why it matters**:
- Perception alone insufficient (need control understanding)
- Massive data available (sim, multi-robot, videos) but unused
- Scaling laws apply to robotics (RDT-1B shows this)

**Opportunities**:
1. Dynamics foundation model (pre-trained world models)
2. Action representation learning (cross-embodiment)
3. Affordance foundation model (from web videos)
4. Policy distillation (large teacher → small student)
5. "ControlNet" (universal control prior) ← **Moonshot**

**Impact potential**: 9/10
- Foundation models revolutionized NLP/vision
- Control FMs will revolutionize robotics
- First movers will define field

**Timeline**:
- Short-term experiments: 3-6 months
- Full control FM: 6-12 months
- Universal control prior: 2-3 years (moonshot)

**Recommendation**:
- Short-term: Dynamics pre-training for HiLoop world model (quick experiment)
- Medium-term: Dedicated control FM project (strong impact)
- Long-term: Consider "ControlNet" as multi-year research program

**Foundation models are THE paradigm shift in AI.**
**Robotics adopted them for perception.**
**Control is next.**

**The question is not IF control foundation models will happen, but WHO will build them first.**
