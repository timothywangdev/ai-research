# arXiv 2023 Papers (Jun-Aug) + Additional Key Papers - Batch 007

**Papers in this batch:** Papers 187-236 (50 papers)
**Category:** arXiv 2023 Jun-Aug, Additional Diffusion/World Model papers
**Source:** arXiv listings, GitHub repositories (Awesome-Robotics-Diffusion, Awesome-World-Models)

---

## CRITICAL PAPERS FROM REPOSITORIES (Missed in Previous Batches)

### 187. Goal-Conditioned Imitation Learning Using Score-Based Diffusion
**arXiv:** 2304.02532
**Venue:** RSS 2023
**Key Points:**
- Score-based diffusion for goal-reaching tasks
- Goal-conditioning mechanism for diffusion policies
**Relevance:** Diffusion for goal-conditioned manipulation
**Gap:** Goal-conditioned but not hierarchical

### 188. Consistency Policy: Accelerated Visuomotor Policies via Consistency Distillation
**arXiv:** 2405.07503
**Venue:** RSS 2024
**Key Points:**
- Consistency models to accelerate diffusion-based policies
- Faster inference than standard diffusion
**Relevance:** IMPORTANT - Computational efficiency for diffusion
**Gap:** Acceleration focus, not hierarchical

### 189. SkillDiffuser: Interpretable Hierarchical Planning via Skill Abstractions
**arXiv:** 2312.11598
**Venue:** CVPR 2024
**Key Points:**
- **Skill-based hierarchy for diffusion**
- Chains learned skills for long-horizon tasks
- Interpretable skill decomposition
**Relevance:** ⭐ IMPORTANT - Hierarchical diffusion with skills
**Gap:** Skill abstractions vs waypoints, not closed-loop adaptation
**Novel Idea:** Skill diffusion for long-horizon planning

### 190. Generative Skill Chaining: Long-Horizon Skill Planning with Diffusion
**arXiv:** 2401.03360
**Venue:** CoRL 2023
**Key Points:**
- Chains skills using diffusion models
- Long-horizon planning via skill composition
**Relevance:** Hierarchical skill chaining with diffusion
**Gap:** Pre-defined skills, not online adaptation

### 191. PlayFusion: Skill Acquisition via Diffusion from Language-Annotated Play
**arXiv:** 2312.04549
**Venue:** CoRL 2023
**Key Points:**
- Learning skills from language-annotated play data
- Diffusion for skill acquisition
**Relevance:** Language-guided skill learning
**Gap:** Play data focus, not hierarchical execution

### 192. SE(3)-Diffusion Fields: Learning Cost Functions for Joint Grasp and Motion
**arXiv:** 2209.03855
**Venue:** ICRA 2023
**Key Points:**
- SE(3)-equivariant diffusion for grasping
- Joint grasp and motion optimization
**Relevance:** Equivariant diffusion for manipulation
**Gap:** Grasping focus, not general manipulation control

### 193. Shelving, Stacking, Hanging: Relational Pose Diffusion for Multi-Modal Rearrangement
**arXiv:** 2307.04751
**Venue:** CoRL 2023
**Key Points:**
- Multi-modal object placement using pose diffusion
- Relational reasoning for rearrangement
**Relevance:** Diffusion for object rearrangement
**Gap:** Placement focus, not closed-loop control

### 194. Reorient Diff: Diffusion Model Based Reorientation for Object Manipulation
**arXiv:** 2303.12700
**Venue:** ICRA 2024
**Key Points:**
- Object reorientation via diffusion models
- In-hand manipulation
**Relevance:** Diffusion for in-hand manipulation
**Gap:** Reorientation specific

### 195. Track2Act: Predicting Point Tracks from Internet Videos Enables Manipulation
**arXiv:** 2405.01527
**Venue:** ECCV 2024
**Key Points:**
- Leverages internet video tracking for manipulation
- Point tracking as affordance representation
**Relevance:** Internet-scale pre-training for manipulation
**Gap:** Tracking focus, not control paradigm

### 196. Vision-Language-Affordance-Based Robot Manipulation with Flow Matching
**arXiv:** 2409.01083
**Key Points:**
- Flow matching (diffusion alternative) for manipulation
- Affordance-aware with vision-language
**Relevance:** Flow matching variant for VLA
**Gap:** Affordance focus, not hierarchical

---

## WORLD MODEL PAPERS (2023-2024)

### 197. Understanding World or Predicting Future? A Comprehensive Survey
**arXiv:** 2411.14499
**Key Points:**
- Comprehensive world model survey
- Taxonomy of world modeling approaches
**Relevance:** Survey paper, overview of field
**Gap:** Survey, not method

### 198. DINO-WM: World Models on Pre-trained Visual Features
**Key Points:**
- Uses DINOv2 features for world modeling
- Zero-shot planning with MPC
**Relevance:** Vision foundation model for world models
**Gap:** MPC-based, not diffusion hierarchical

### 199. Multi-Task Interactive Robot Fleet Learning with Visual World Models
**arXiv:** 2410.22689
**Venue:** CoRL 2024
**Key Points:**
- Visual world models for fleet learning
- Anomaly detection across multiple robots
**Relevance:** Multi-robot world modeling
**Gap:** Fleet focus, not single-agent hierarchical

### 200. iVideoGPT: Interactive VideoGPTs are Scalable World Models
**Venue:** NeurIPS 2024
**Key Points:**
- Scalable video generation as world model
- Interactive video synthesis
**Relevance:** Video-based world models
**Gap:** Video generation, not for control

### 201. MoDem-V2: Visuo-Motor World Models for Real-World Manipulation
**arXiv:** 2309.14236
**Key Points:**
- Visuomotor world models for real robots
- Manipulation-specific world modeling
**Relevance:** IMPORTANT - World models for manipulation
**Gap:** Not hierarchical or waypoint-based

### 202. Learning to Model the World with Language
**arXiv:** 2308.01399
**Key Points:**
- Language grounding in world modeling
- Language-conditioned dynamics prediction
**Relevance:** Language + world models
**Gap:** Language focus, not hierarchical control

### 203. Hierarchical World Models as Visual Whole-Body Humanoid Controllers
**Key Points:**
- **Hierarchical world models for humanoid control**
- Visual whole-body coordination
**Relevance:** ⭐ IMPORTANT - Hierarchical world models!
**Gap:** Humanoid locomotion, not manipulation
**Novel Idea:** Hierarchy in world models for control

### 204. Affordances from Human Videos as a Versatile Representation
**arXiv:** 2304.08488
**Key Points:**
- Extract affordances from human videos
- Versatile representation for downstream tasks
**Relevance:** Video pre-training for affordances
**Gap:** Affordance extraction, not control

### 205. Structured World Models from Human Videos
**arXiv:** 2308.10901
**Key Points:**
- Learn structured action representations from videos
- Human video pre-training for manipulation
**Relevance:** Structured world models from video
**Gap:** Pre-training focus, not online control

### 206. Finetuning Offline World Models in the Real World
**arXiv:** 2310.16029
**Key Points:**
- Offline-to-online world model adaptation
- Manipulation in real environments
**Relevance:** World model adaptation for manipulation
**Gap:** Fine-tuning approach, not hierarchical

---

## JULY 2023 PAPERS (arXiv:2307)

### 207. ROMAN: Hybrid Hierarchical Learning for Complex Sequential Tasks
**arXiv:** 2307.00125
**Key Points:**
- **Hybrid hierarchical learning**
- Complex sequential task decomposition
**Relevance:** ⭐ IMPORTANT - Hierarchical learning for manipulation
**Gap:** Hybrid approach, not diffusion-based
**Novel Idea:** Combines multiple hierarchical learning paradigms

### 208. Crossway Diffusion: Improving Diffusion-based Visuomotor Policy
**arXiv:** 2307.01849
**Key Points:**
- Self-supervised learning improves diffusion policies
- Cross-modal learning for visuomotor control
**Relevance:** Diffusion policy improvement
**Gap:** Self-supervision focus, not hierarchical

### 209. RH20T: A Comprehensive Robotic Dataset for Diverse Skills
**arXiv:** 2307.00595
**Key Points:**
- Large-scale dataset: diverse skills in one-shot
- Supports few-shot learning research
**Relevance:** Dataset for manipulation learning
**Gap:** Dataset, not method

### 210. DoReMi: Grounding LLM by Detecting and Recovering from Misalignment
**arXiv:** 2307.00329
**Key Points:**
- Language model planning with error recovery
- Execution monitoring and replanning
**Relevance:** IMPORTANT - Error detection and recovery!
**Gap:** LLM-based, not diffusion or world model
**Novel Idea:** Plan-execution misalignment detection

### 211. Enhancing Dexterity via Hierarchical Contact Exploration
**arXiv:** 2307.00383
**Key Points:**
- **Hierarchical methods for manipulation**
- Contact exploration for dexterity
**Relevance:** Hierarchical approach for contact-rich tasks
**Gap:** Contact exploration, not waypoint-based

### 212. Rearrangement Planning for General Part Assembly
**arXiv:** 2307.00206
**Key Points:**
- Sequential planning for assembly
- Part-level manipulation
**Relevance:** Planning for manipulation
**Gap:** Assembly focus, not hierarchical control

---

## AUGUST 2023 PAPERS (arXiv:2308)

### 213. LEMMA: Learning Language-Conditioned Multi-Robot Manipulation
**arXiv:** 2308.00937
**Key Points:**
- Multi-agent manipulation with language
- Distributed policy learning
**Relevance:** Multi-robot manipulation
**Gap:** Multi-agent focus, not hierarchical

### 214. VL-Grasp: 6-DoF Interactive Grasp Policy for Language Objects
**arXiv:** 2308.00640
**Key Points:**
- Language-conditioned grasping
- Interactive grasp generation
**Relevance:** Language-guided grasping
**Gap:** Grasping focus

### 215. HANDAL: A Dataset of Manipulable Object Categories
**arXiv:** 2308.01477
**Key Points:**
- Dataset with pose, affordances, reconstructions
- Supports manipulation research
**Relevance:** Dataset for manipulation
**Gap:** Dataset, not method

### 216. Learning Complex Motion Plans using Neural ODEs
**arXiv:** 2308.00186
**Key Points:**
- Neural ODE-based planning
- Safety and stability guarantees
**Relevance:** Learning-based planning with guarantees
**Gap:** ODE-based, not diffusion

### 217. DMFC-GraspNet: Differentiable Multi-Fingered Grasp Generation
**arXiv:** 2308.00456
**Key Points:**
- Differentiable grasping in clutter
- Multi-fingered hand control
**Relevance:** Dexterous grasping
**Gap:** Grasping specific

---

## JUNE 2023 PAPERS (arXiv:2306)

### 218. Efficient Deep Learning of Robust Policies from MPC
**arXiv:** 2306.00286
**Key Points:**
- Imitation from MPC trajectories
- Tube-guided data augmentation
**Relevance:** IMPORTANT - MPC to policy distillation
**Gap:** MPC distillation, not hierarchical diffusion
**Novel Idea:** Combines MPC with learned policies

### 219. Train Offline, Test Online: A Real Robot Learning Benchmark
**arXiv:** 2306.00942
**Key Points:**
- Offline-to-online benchmark
- Real robot evaluation
**Relevance:** Benchmark for offline learning
**Gap:** Benchmark, not method

### 220. LIV: Language-Image Representations and Rewards for Robotic Control
**arXiv:** 2306.00958
**Key Points:**
- Multimodal representations for control
- Language-image reward learning
**Relevance:** Multimodal learning for control
**Gap:** Reward learning focus

### 221. Data Quality in Imitation Learning
**arXiv:** 2306.02437
**Key Points:**
- Examines demonstration quality requirements
- Data collection best practices
**Relevance:** Imitation learning data quality
**Gap:** Data analysis, not method

### 222. Conformal Predictive Safety Filter for RL Controllers
**arXiv:** 2306.02551
**Key Points:**
- Safety constraints for RL policies
- Conformal prediction for safety
**Relevance:** Safety for learned policies
**Gap:** Safety focus, not hierarchical

### 223. Efficient Multi-Task and Transfer RL with Parameter Composition
**arXiv:** 2306.01839
**Key Points:**
- Parameter-compositional framework
- Multi-task and transfer learning
**Relevance:** Multi-task RL efficiency
**Gap:** Parameter composition focus

---

## ADDITIONAL CoRL 2024 PAPERS

### 224. OKAMI: Teaching Humanoid Robots Manipulation via Single Video
**Venue:** CoRL 2024
**Key Points:**
- One-shot imitation for humanoid manipulation
- Single video demonstration
**Relevance:** One-shot learning for humanoids
**Gap:** Humanoid focus, imitation not hierarchical

### 225. ALOHA Unleashed: A Simple Recipe for Robot Dexterity
**Venue:** CoRL 2024
**Key Points:**
- Simplified ALOHA system
- Bimanual dexterous manipulation
**Relevance:** Bimanual manipulation platform
**Gap:** Platform/system, not control paradigm

### 226. ReMix: Optimizing Data Mixtures for Large Scale Imitation Learning
**Venue:** CoRL 2024
**Key Points:**
- Data mixture optimization for IL
- Large-scale imitation learning
**Relevance:** Data optimization for scaling
**Gap:** Data strategy, not control method

### 227. WoCoCo: Learning Whole-Body Control with Sequential Contacts
**Venue:** CoRL 2024
**Key Points:**
- Whole-body humanoid control
- Sequential contact reasoning
**Relevance:** Whole-body coordination
**Gap:** Humanoid locomotion focus

### 228. Harmon: Whole-Body Motion from Language Descriptions
**Venue:** CoRL 2024
**Key Points:**
- Language to whole-body motion generation
- Humanoid control from language
**Relevance:** Language-conditioned control
**Gap:** Language focus, not hierarchical

### 229. A Versatile Planner for Dexterous and Whole-body Manipulation
**Venue:** CoRL 2024
**Key Points:**
- Unified planner for dexterous manipulation
- Whole-body coordination
**Relevance:** Planning for manipulation
**Gap:** Planning focus, not learning-based hierarchical

### 230. Sparse Diffusion Policy: A Sparse, Reusable, Flexible Policy
**Venue:** CoRL 2024
**Key Points:**
- Sparse diffusion for efficiency
- Reusable policy components
**Relevance:** Efficient diffusion policies
**Gap:** Sparsity focus, not hierarchical

### 231. D³Fields: Dynamic 3D Descriptor Fields for Generalizable Rearrangement
**Venue:** CoRL 2024
**Key Points:**
- Dynamic 3D descriptors for rearrangement
- Zero-shot generalization
**Relevance:** 3D representations for manipulation
**Gap:** Rearrangement focus

### 232. RAM: Retrieval-Based Affordance Transfer
**Venue:** CoRL 2024
**Key Points:**
- Retrieval-based zero-shot manipulation
- Affordance transfer across objects
**Relevance:** Zero-shot generalization
**Gap:** Retrieval-based, not hierarchical

### 233. Physically Embodied Gaussian Splatting: A Realtime World Model
**Venue:** CoRL 2024
**Key Points:**
- Gaussian splatting for world modeling
- Real-time correctable world model
**Relevance:** IMPORTANT - Real-time world model!
**Gap:** Gaussian splatting focus, not for hierarchical control
**Novel Idea:** Physically embodied 3D Gaussians

### 234. Learning Differentiable Tensegrity Dynamics using GNN
**Venue:** CoRL 2024
**Key Points:**
- Graph neural networks for dynamics
- Soft robot modeling
**Relevance:** Dynamics learning with GNN
**Gap:** Soft robotics focus

### 235. Modeling the Real World with High-Density Visual Particle Dynamics
**Venue:** CoRL 2024
**Key Points:**
- Particle-based world modeling
- High-density visual dynamics
**Relevance:** Particle-based world models
**Gap:** Representation focus, not control

### 236. Surgical Robot Transformer: Imitation Learning for Surgical Subtasks
**Venue:** CoRL 2024
**Key Points:**
- Transformer for surgical manipulation
- Imitation learning for surgery
**Relevance:** Surgical manipulation
**Gap:** Surgical domain-specific

---

## Key Insights from Batch 007:

### HIERARCHICAL APPROACHES IN 2023:

1. **ROMAN** (2307.00125): Hybrid hierarchical learning for sequential tasks
2. **SkillDiffuser** (2312.11598): Skill-based hierarchical diffusion (CVPR 2024)
3. **Generative Skill Chaining** (2401.03360): Skill chaining with diffusion (CoRL 2023)
4. **Hierarchical World Models** (2024.05): Hierarchy in world models for humanoids
5. **Hierarchical Contact Exploration** (2307.00383): Hierarchy for dexterity

**Pattern:** Skill-based hierarchies dominate 2023, waypoint-based less explored

### WORLD MODEL ADVANCES:

1. **MoDem-V2**: Visuomotor world models for manipulation
2. **Hierarchical World Models**: For humanoid control
3. **Physically Embodied Gaussian Splatting**: Real-time correctable WM
4. **Structured World Models from Human Videos**: Video pre-training

**Pattern:** World models for manipulation exist but not integrated with hierarchical control

### DIFFUSION TRENDS IN 2023:

1. **Equivariant approaches**: SE(3)-Diffusion Fields, Diffusion-EDFs
2. **Skill-based**: SkillDiffuser, Generative Skill Chaining
3. **Language-conditioned**: PlayFusion
4. **Object-centric**: Shelving/Stacking/Hanging, Reorient Diff

**Pattern:** No hierarchical diffusion + world model + online adaptation in 2023

### MPC + LEARNING CONNECTIONS:

1. **Efficient Deep Learning from MPC** (2306.00286): Distills MPC to policies
2. **DINO-WM**: World models with MPC for zero-shot
3. **Subgoal Diffuser** (found earlier): Diffusion + MPC hybrid

**Pattern:** MPC-learning hybrids explored, but optimization-based

---

## NEW RESEARCH OPPORTUNITIES:

### Opportunity #22: Skill Diffusion with Online Adaptation
**Inspired by:** SkillDiffuser, Generative Skill Chaining
**Gap:** Skill-based hierarchies exist but no online adaptation when skill fails
**Proposed:** Diffusion generates skill sequences, world model monitors, triggers skill re-selection
**Novelty:** 7/10, Feasibility: 7/10, Impact: 8/10, Total: 22/30

### Opportunity #23: MPC-to-Diffusion Policy Distillation for Hierarchical Control
**Inspired by:** Efficient Deep Learning from MPC, Subgoal Diffuser
**Gap:** MPC provides good closed-loop control but requires accurate models; can we distill to diffusion?
**Proposed:** Use MPC for data collection, distill to hierarchical diffusion policy with world model
**Novelty:** 6/10, Feasibility: 8/10, Impact: 7/10, Total: 21/30

### Opportunity #24: Real-time World Models for Waypoint Refinement
**Inspired by:** Physically Embodied Gaussian Splatting
**Gap:** Real-time world models exist but not used for online waypoint adaptation
**Proposed:** Gaussian splatting world model for fast online waypoint refinement
**Novelty:** 7/10, Feasibility: 7/10, Impact: 8/10, Total: 22/30

---

## HiLoop Comparison Update (After 236 Papers):

**Key Finding:** No hierarchical diffusion + world model + online waypoint adaptation found in 2023 papers!

**vs SkillDiffuser (CVPR 2024):**
- SkillDiffuser: Skill-based hierarchical diffusion for planning
- HiLoop: Waypoint-based hierarchical diffusion for control + online adaptation
- Difference: Skills (discrete abstractions) vs waypoints (continuous spatial goals); no online adaptation in SkillDiffuser

**vs Hierarchical World Models (humanoid):**
- Hierarchical WM: For locomotion control
- HiLoop: For manipulation with waypoint refinement
- Difference: Locomotion vs manipulation; their hierarchy is in WM structure, ours is in policy + WM monitoring

**vs MoDem-V2 (world model for manipulation):**
- MoDem-V2: Visuomotor world model for manipulation
- HiLoop: World model for monitoring + triggering waypoint refinement
- Difference: World model use (prediction vs monitoring + adaptation)

**Subgoal Diffuser remains closest competitor** (from batch 005)

---

**Papers Reviewed So Far: 236 / 500 (47.2%)**

**Status:** Nearly halfway! No new competitors found in 2023 papers. Hierarchical skill diffusion exists but different from waypoint-based. World models for manipulation exist but not for online hierarchical adaptation.

**Confidence: 70% → 72%** (slight increase: 2023 papers show no similar work)

