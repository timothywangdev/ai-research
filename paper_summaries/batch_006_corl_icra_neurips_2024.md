# CoRL 2024, ICRA 2024, NeurIPS 2024, Recent Papers - Batch 006

**Papers in this batch:** Papers 162-186 (25 papers)
**Category:** CoRL 2024, ICRA 2024, NeurIPS 2024, Recent arXiv 2023-2024
**Source:** Conference proceedings, arXiv recent papers

---

## CoRL 2024 PAPERS

### 162. HiRT: Enhancing Robotic Control with Hierarchical Robot Transformers
**arXiv:** 2410.05273
**Venue:** CoRL 2024
**Authors:** Jianke Zhang, Yanjiang Guo, Xiaoyu Chen, Yen-Jen Wang, et al.
**Key Points:**
- **Hierarchical framework:** VLM at low frequency + vision policy at high frequency
- Addresses VLA computational cost and latency issues
- 58% reduction in inference time delay
- Success rate improved from 48% to 75% on dynamic tasks
**Relevance:** IMPORTANT - Hierarchical VLA for dynamic manipulation
**Gap:** VLM-based hierarchy, not diffusion-based
**Novel Idea:** Dual-frequency hierarchical control for real-time interaction

### 163. InterACT: Inter-dependency Aware Action Chunking
**arXiv:** 2409.07914
**Venue:** CoRL 2024
**Authors:** Andrew Choong-Won Lee, Ian Chuang, Ling-Yuan Chen, Iman Soltani
**Key Points:**
- **Hierarchical attention for bimanual manipulation**
- Segment-wise and cross-segment attention mechanisms
- Multi-arm decoder with synchronization blocks
- Significantly outperforms existing bimanual methods
**Relevance:** IMPORTANT - Hierarchical attention for bimanual coordination
**Gap:** Attention-based, not diffusion or waypoint-based

### 164. FlowBotHD: History-Aware Diffuser for Articulated Objects
**arXiv:** 2410.07078
**Venue:** CoRL 2024
**Authors:** Yishu Li, Wen Hui Leng, Yiming Fang, Ben Eisner, David Held
**Key Points:**
- History-aware diffusion for ambiguous articulated objects
- Handles multi-modal manipulation distributions
- Addresses temporal dependency in manipulation
**Relevance:** Diffusion for articulated objects with history
**Gap:** Articulated objects focus, not hierarchical closed-loop

---

## ICML / ICRA / NeurIPS 2024 MAJOR PAPERS

### 165. 3D-VLA: A 3D Vision-Language-Action Generative World Model
**arXiv:** 2403.09631
**Venue:** ICML 2024
**Authors:** Haoyu Zhen, Xiaowen Qiu, Peihao Chen, et al.
**Key Points:**
- **3D-based world model for VLA**
- Links 3D perception, reasoning, and action
- Predicts goal images and point clouds using embodied diffusion
- Addresses 2D VLA limitation of missing 3D physical world
**Relevance:** ⭐ IMPORTANT - 3D world model for action prediction
**Gap:** Generative world model but not for closed-loop hierarchical control
**Novel Idea:** 3D-based LLM + embodied diffusion for world modeling

### 166. SARA-RT: Scaling up Robotics Transformers with Self-Adaptive Robust Attention
**arXiv:** 2312.01990
**Venue:** ICRA 2024 (🏆 Best Paper on Robot Manipulation)
**Authors:** Google DeepMind team
**Key Points:**
- Self-adaptive robust attention for scalable RT
- "Up-training" fine-tuning method
- 10.6% accuracy boost, 14% faster decision-making
- Best paper award at ICRA 2024
**Relevance:** ⭐ IMPORTANT - Scaling foundation models efficiently
**Gap:** Scaling approach, not hierarchical or world-model-based

### 167. Learning Multimodal Behaviors from Scratch with Diffusion Policy Gradient
**arXiv:** 2406.00681
**Venue:** NeurIPS 2024
**Authors:** Zechu Li, Rickmer Krohn, Tao Chen, Anurag Ajay, et al.
**Key Points:**
- **Deep Diffusion Policy Gradient (DDiffPG)**
- Learns multimodal policies parameterized as diffusion models
- Unsupervised clustering + novelty-based intrinsic motivation
- Mode-specific Q-learning to maintain all modes
**Relevance:** ⭐ IMPORTANT - Diffusion + RL for multimodal behaviors
**Gap:** RL from scratch, not imitation or hierarchical
**Novel Idea:** Multimodal diffusion policy training with RL

### 168. DiffTORI: Differentiable Trajectory Optimization for Deep RL
**arXiv:** 2402.05421
**Venue:** NeurIPS 2024 (Spotlight)
**Authors:** Weikang Wan, Ziyu Wang, Yufei Wang, Zackory Erickson, David Held
**Key Points:**
- Differentiable trajectory optimization as policy representation
- Addresses "objective mismatch" in model-based RL
- Dynamics model learned to directly maximize task performance
- Outperforms SOTA on 15 model-based RL + 35 imitation tasks
**Relevance:** ⭐ IMPORTANT - Trajectory optimization + learning hybrid
**Gap:** Model-based RL, not diffusion-based hierarchical
**Novel Idea:** Differentiable TO for end-to-end learning

---

## DIFFUSION & GENERATIVE MODELS (arXiv 2023-2024)

### 169. DiffusionSeeder: Seeding Motion Optimization with Diffusion
**arXiv:** 2410.16727
**Key Points:**
- Diffusion generates trajectories to seed motion optimization
- Integrated with cuRobo for rapid planning
- Up to 36× speedup on complex tasks
**Relevance:** Diffusion for motion planning initialization
**Gap:** Planning focus, not manipulation control

### 170. Generalizable Humanoid Manipulation with 3D Diffusion Policies
**arXiv:** 2410.10803
**Key Points:**
- Whole-upper-body teleoperation for humanoids
- 25-DoF humanoid with 3D LiDAR
- Improved 3D Diffusion Policy for humanoids learning from noisy human data
**Relevance:** 3D diffusion for humanoid manipulation
**Gap:** Humanoid focus, not hierarchical waypoint-based

### 171. Zero-shot Robotic Manipulation with Pretrained Image-Editing Diffusion
**arXiv:** 2310.10639
**Authors:** Kevin Black, et al.
**Key Points:**
- Uses pretrained image-editing diffusion models
- Zero-shot manipulation without robot-specific training
- Leverages web-scale image editing knowledge
**Relevance:** Zero-shot transfer via diffusion models
**Gap:** Image editing, not policy or world model

### 172. NoMaD: Goal Masked Diffusion Policies for Navigation
**arXiv:** 2310.07896
**Authors:** Sridhar et al.
**Key Points:**
- Goal-masked diffusion for navigation and exploration
- Handles goal uncertainty through masking
**Relevance:** Diffusion for navigation with goal masking
**Gap:** Navigation, not manipulation

### 173. Diffusion-EDFs: Bi-equivariant Denoising on SE(3)
**arXiv:** 2309.02685
**Venue:** CVPR 2024
**Authors:** Ryu et al.
**Key Points:**
- Bi-equivariant denoising generative modeling on SE(3)
- Equivariant diffusion for visual robotic manipulation
**Relevance:** SE(3) equivariant diffusion for manipulation
**Gap:** Equivariance focus, not hierarchical control

### 174. EDMP: Ensemble-of-costs-guided Diffusion for Motion Planning
**arXiv:** 2309.11414
**Authors:** Saha et al.
**Key Points:**
- Ensemble of cost functions guides diffusion
- Motion planning with learned cost ensembles
**Relevance:** Diffusion for motion planning with costs
**Gap:** Planning, not manipulation control

### 175. Multimodal Diffusion Transformer: Learning Versatile Behavior from Multimodal Goals
**arXiv:** 2407.05996
**Authors:** Moritz Reuss, et al.
**Key Points:**
- Diffusion transformer for multimodal goal conditioning
- Learns versatile behaviors from diverse goal specifications
**Relevance:** Multimodal goal conditioning with diffusion
**Gap:** Goal conditioning, not hierarchical control

---

## FOUNDATION MODELS & CROSS-EMBODIMENT

### 176. RT-2: Vision-Language-Action Models Transfer Web Knowledge
**arXiv:** 2307.15818
**Venue:** CoRL 2023
**Authors:** Google DeepMind
**Key Points:**
- **VLA model co-fine-tuned on robot trajectories + Internet VL tasks**
- Actions as text tokens in LLM
- Emergent capabilities from Internet-scale training
- Improved generalization to novel objects
**Relevance:** ⭐⭐⭐ CRITICAL - Foundation VLA model, baseline for many works
**Gap:** Not hierarchical or world-model-based
**Novel Idea:** Web knowledge transfer to robot control via VLA

### 177. Open X-Embodiment: Robotic Learning Datasets and RT-X Models
**arXiv:** 2310.08864
**Venue:** ICRA 2024
**Authors:** 21 institutions collaboration
**Key Points:**
- **Dataset from 22 robots, 527 skills**
- RT-1-X and RT-2-X models
- Demonstrates positive cross-embodiment transfer
- Large-scale robot learning dataset
**Relevance:** ⭐⭐⭐ CRITICAL - Largest cross-embodiment dataset
**Gap:** Dataset and foundation models, not control paradigm
**Novel Idea:** Massive-scale cross-embodiment learning

### 178. Scaling Cross-Embodied Learning: One Policy for All
**arXiv:** 2408.11812
**Authors:** Ria Doshi, Homer Walke, Oier Mees, Sudeep Dasari, Sergey Levine
**Key Points:**
- Single policy for manipulation, navigation, locomotion, and aviation
- URMA architecture for morphology-agnostic control
**Relevance:** Extreme cross-embodiment generalization
**Gap:** Cross-embodiment focus, not hierarchical

---

## TACTILE & MULTI-MODAL MANIPULATION

### 179. Learning Tactile Insertion in the Real World
**arXiv:** 2405.00383
**Key Points:**
- Model-based RL with Dreamer
- Vision-based tactile sensor feedback
- Tactile significantly enhances learning for insertion
**Relevance:** Tactile + vision for contact-rich tasks
**Gap:** Specific to insertion, not general hierarchical

### 180. AnyRotate: Gravity-Invariant In-Hand Rotation with Sim-to-Real Touch
**arXiv:** 2405.07391
**Key Points:**
- Dense tactile policy for multi-axis in-hand rotation
- Gravity-invariant control
- Sim-to-real for tactile sensing
**Relevance:** Tactile for dexterous manipulation
**Gap:** In-hand manipulation specific

### 181. 3D-ViTac: Fine-Grained Manipulation with Visuo-Tactile Sensing
**arXiv:** 2410.24091
**Key Points:**
- Integrates vision, tactile, and proprioception
- Four challenging long-horizon tasks
- Multi-modal fusion for fine-grained control
**Relevance:** Multi-modal sensing for manipulation
**Gap:** Sensing modalities, not control paradigm

---

## RECENT ADVANCES (Nov-Dec 2024)

### 182. Moto: Latent Motion Token as the Bridging Language
**arXiv:** 2412.04445
**Key Points:**
- Converts video to latent Motion Token sequences
- Moto-GPT pre-trained on motion tokens
- Superior robustness and efficiency on benchmarks
**Relevance:** Motion tokens for video-to-action
**Gap:** Representation learning, not hierarchical control

### 183. CogAct: A Foundational Vision-Language-Action Model
**arXiv:** 2411.19650
**Key Points:**
- Foundation model synergizing cognition and action
- Robotic manipulation with VLA
**Relevance:** Recent VLA foundation model
**Gap:** Foundation model, not control paradigm

### 184. ManiBox: Enhancing Spatial Grasping Generalization
**arXiv:** 2411.01850
**Key Points:**
- Scalable simulation data generation
- Spatial grasping generalization
**Relevance:** Data generation for grasping
**Gap:** Grasping specific, not general manipulation

---

## VIDEO GENERATION & WORLD MODELS

### 185. This&That: Language-Gesture Controlled Video Generation for Robot Planning
**arXiv:** 2407.05530
**Key Points:**
- Language + gesture control for video generation
- Video world model for robot planning
**Relevance:** Video generation as world model
**Gap:** Video generation focus, not closed-loop control

### 186. RoboCAS: A Benchmark for Complex Object Arrangement Scenarios
**arXiv:** 2407.06951
**Key Points:**
- Benchmark for complex object arrangement
- Evaluates manipulation in cluttered environments
**Relevance:** Benchmark for manipulation
**Gap:** Benchmark, not method

---

## Key Insights from Batch 006:

### HIERARCHICAL APPROACHES DIVERSITY:

1. **VLM-based Hierarchy** (HiRT): VLM low-freq + vision policy high-freq
2. **Attention-based Hierarchy** (InterACT): Hierarchical attention for bimanual
3. **Diffusion Hierarchy** (No new major work beyond Subgoal Diffuser/Hierarchical Diffuser)

### WORLD MODEL ADVANCES:

1. **3D-VLA**: 3D world model with embodied diffusion for goal prediction
2. **This&That**: Language-gesture video generation for planning
3. **Video-based** approaches growing (seen in batch 002)

### FOUNDATION MODELS DOMINANCE:

1. **RT-2**: Web knowledge transfer to robot control (CoRL 2023)
2. **Open X-Embodiment**: 22 robots, 527 skills, massive dataset (ICRA 2024)
3. **SARA-RT**: Best Paper ICRA 2024 on scaling transformers
4. **HiRT, CogAct**: Recent hierarchical VLA models

### DIFFUSION TRENDS:

1. **Diffusion + RL** (DDiffPG, DiffTORI): Combining diffusion with RL
2. **Equivariant Diffusion** (Diffusion-EDFs): SE(3) equivariance
3. **Motion Planning** (DiffusionSeeder, EDMP): Diffusion for planning
4. **Multimodal Goals** (Multimodal Diffusion Transformer)

### CROSS-EMBODIMENT LEARNING:

- Scaling Cross-Embodied Learning: One policy for manipulation, navigation, locomotion, aviation
- Open X-Embodiment: Largest cross-embodiment dataset
- Positive transfer across different robot morphologies

---

## NEW RESEARCH OPPORTUNITIES IDENTIFIED:

### Opportunity #19: VLM-based Hierarchical Closed-Loop Control
**Inspired by:** HiRT (CoRL 2024)
**Gap:** HiRT uses VLM at low-freq for semantic understanding but no online adaptation when VLM predictions fail
**Proposed:** VLM generates waypoints, world model monitors execution, triggers VLM re-planning when needed
**Novelty:** 7/10, Feasibility: 7/10, Impact: 8/10, Total: 22/30
**Note:** Combines VLM hierarchy with world model monitoring

### Opportunity #20: 3D World Model for Waypoint-based Control
**Inspired by:** 3D-VLA (ICML 2024)
**Gap:** 3D-VLA generates goal predictions but not used for closed-loop control during execution
**Proposed:** 3D world model predicts future 3D scenes, guides waypoint refinement based on 3D prediction errors
**Novelty:** 7/10, Feasibility: 7/10, Impact: 8/10, Total: 22/30

### Opportunity #21: Tactile-Informed Waypoint Adaptation
**Inspired by:** Learning Tactile Insertion, AnyRotate, 3D-ViTac
**Gap:** Tactile sensing improves contact-rich tasks but not integrated with hierarchical waypoint planning
**Proposed:** Tactile feedback triggers waypoint refinement for contact-rich manipulation
**Novelty:** 7/10, Feasibility: 8/10, Impact: 8/10, Total: 23/30

---

## HiLoop Comparison Update (After 186 Papers):

**vs HiRT (CoRL 2024):**
- HiRT: VLM (low-freq) + vision policy (high-freq) for computational efficiency
- HiLoop: Diffusion waypoints + world model monitoring for error-driven adaptation
- Different hierarchy levels: semantic (VLM) vs spatial (waypoints)

**vs 3D-VLA (ICML 2024):**
- 3D-VLA: 3D world model for goal image/point cloud prediction
- HiLoop: World model for execution monitoring and waypoint refinement
- Different use of world model: generative vs predictive/monitoring

**vs DiffTORI (NeurIPS 2024):**
- DiffTORI: Trajectory optimization as policy representation with differentiable TO
- HiLoop: Diffusion policy with world model for online adaptation
- Different approach: optimization-based vs learning-based

**vs Subgoal Diffuser (still closest competitor):**
- Subgoal Diffuser: Diffusion + MPC + static subgoal density
- HiLoop: Diffusion + world model + dynamic waypoint refinement
- Key difference remains: MPC (optimization) vs world model (learning)

---

**Papers Reviewed So Far: 186 / 500 (37.2%)**

**Status:** HiLoop remains viable. Subgoal Diffuser is still the closest competitor. New findings show:
1. VLM-based hierarchies are emerging (HiRT) - different from waypoint-based
2. 3D world models exist (3D-VLA) but not for closed-loop control
3. No new hierarchical diffusion + world model + online adaptation work found
4. Foundation models (RT-2, Open X-Embodiment) dominate but don't address hierarchical closed-loop

**Confidence: 70%** (maintaining after 186 papers)

