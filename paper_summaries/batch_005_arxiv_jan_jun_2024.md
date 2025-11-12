# arXiv January-June 2024 Papers - Batch 005

**Papers in this batch:** Papers 136-161 (26 papers)
**Category:** arXiv cs.RO/cs.LG Jan-Jun 2024 + RSS 2024
**Source:** arXiv listings + RSS 2024 proceedings

---

## CRITICAL FINDINGS - MAJOR COMPETITORS TO HILOOP

### 136. ⭐ Hierarchical Diffuser: Simple Hierarchical Planning with Diffusion
**arXiv:** 2401.02644
**Authors:** Chang Chen, Fei Deng, Kenji Kawaguchi, Caglar Gulcehre, Sungjin Ahn
**Key Points:**
- **Two-level hierarchical planning with diffusion**
- High-level generates subgoals, low-level refines
- "Jumpy" strategy reduces computational cost
- Superior performance on offline RL benchmarks
**Relevance:** ⭐⭐⭐ CRITICAL - Direct hierarchical diffusion competitor
**Gap:** Offline RL focus, not for online robot manipulation with closed-loop adaptation
**Novel Idea:** Jumpy planning for computational efficiency
**Comparison to HiLoop:** No world model for monitoring, no online waypoint refinement, not manipulation-focused

### 137. ⭐ Subgoal Diffuser: Coarse-to-fine Subgoal Generation to Guide MPC
**arXiv:** 2403.13085
**Authors:** Zixuan Huang, Yating Lin, Fan Yang, Dmitry Berenson
**Key Points:**
- **Diffusion generates subgoals to guide MPC**
- **Closed-loop control via MPC**
- Dynamic subgoal density based on reachability
- Focuses computational resources on challenging task phases
- MPC handles disturbance rejection
**Relevance:** ⭐⭐⭐ CRITICAL - MOST SIMILAR TO HILOOP!
**Gap:** Uses MPC (optimization-based) vs world model (learning-based)
**Key Difference from HiLoop:**
  - Subgoal Diffuser: Static subgoal generation → MPC follows (density adjustment is pre-determined)
  - HiLoop: Dynamic waypoint refinement based on world model predictions (error-driven replanning)
**Novel Idea:** Adaptive subgoal density allocation
**Status:** Published March 2024

### 138. Waypoint-Based Reinforcement Learning for Robot Manipulation
**arXiv:** 2403.13281
**Authors:** Shaunak A. Mehta, Soheil Habibian, Dylan P. Losey
**Key Points:**
- Learn trajectory of waypoints, interpolate with controllers
- Formulated as sequence of multi-armed bandits
- Lower regret bounds than standard RL
**Relevance:** Waypoint-based approach, model-free RL
**Gap:** Not diffusion-based, not hierarchical in same sense as ChainedDiffuser

---

## JANUARY 2024 PAPERS

### 139. Mobile ALOHA: Learning Bimanual Mobile Manipulation
**arXiv:** 2401.02117
**Authors:** Zipeng Fu, Tony Z. Zhao, Chelsea Finn
**Key Points:**
- Low-cost whole-body teleoperation system
- Bimanual + mobile manipulation
- Co-training with static ALOHA datasets (90% improvement)
- Complex tasks: cooking, cabinet opening, elevator navigation
**Relevance:** Mobile manipulation platform
**Gap:** Imitation learning, not diffusion or world models

### 140. AutoRT: Embodied Foundation Models for Large-Scale Orchestration
**arXiv:** 2401.12963
**Authors:** Various (Google DeepMind)
**Key Points:**
- Large-scale robot orchestration with foundation models
- Fleet coordination and task distribution
**Relevance:** Foundation model deployment at scale
**Gap:** Orchestration focus, not low-level control

---

## FEBRUARY 2024 PAPERS

### 141. Diffusion World Model: Future Modeling Beyond Step-by-Step Rollout
**arXiv:** 2402.03570
**Authors:** Zihan Ding, Amy Zhang, Yuandong Tian, Qinqing Zheng
**Key Points:**
- **Multistep future prediction in single forward pass**
- Avoids recursive rollouts (faster inference)
- Predicts states + rewards concurrently
- 44% improvement over one-step baselines
**Relevance:** IMPORTANT - World model using diffusion
**Gap:** Offline RL focus, not for online manipulation control
**Novel Idea:** Single-pass long-horizon prediction vs autoregressive

### 142. DINOBot: Robot Manipulation via Vision Foundation Models
**arXiv:** 2402.13181
**Authors:** Norman Di Palo, Edward Johns
**Venue:** ICRA 2024
**Key Points:**
- Leverages DINO Vision Transformer features
- One-shot imitation learning
- Retrieval + alignment approach
**Relevance:** Vision foundation models for manipulation
**Gap:** Not diffusion-based, retrieval-based approach

### 143. Diffusion Meets DAgger: Supercharging Eye-in-hand Imitation Learning
**arXiv:** 2402.17768
**Venue:** RSS 2024
**Authors:** Various
**Key Points:**
- Combines diffusion models with DAgger
- Synthesizes out-of-distribution samples using diffusion
- 80% success with 8 demos (vs 20% for BC)
- Eye-in-hand camera setting
**Relevance:** IMPORTANT - Diffusion for sample efficiency
**Gap:** DAgger focus, not hierarchical

### 144. D3IL Benchmark: Towards Diverse Behaviors with Human Demonstrations
**arXiv:** 2402.14606
**Key Points:**
- Benchmark for multi-modal imitation learning
- Evaluates handling of diverse human behaviors
**Relevance:** Benchmark for multi-modal learning
**Gap:** Benchmark, not method

---

## MARCH 2024 PAPERS

### 145. RT-H: Action Hierarchies Using Language
**arXiv:** 2403.01823
**Venue:** RSS 2024
**Authors:** Suneel Belkhale, Tianli Ding, Ted Xiao, Pierre Sermanet, et al.
**Key Points:**
- **Hierarchical control using language motions**
- Predicts language motions (e.g., "move arm forward")
- Then predicts actions conditioned on language motions
- 15% improvement over RT-2
- 2500+ language motions extracted automatically
**Relevance:** ⭐ IMPORTANT - Hierarchical approach with language
**Gap:** Language-based hierarchy, not waypoint/diffusion-based
**Novel Idea:** Fine-grained language motions for low-level control

---

## APRIL 2024 PAPERS

### 146. Policy-Guided Diffusion
**arXiv:** 2404.06356
**Authors:** Matthew Thomas Jackson, Michael Tryfan Matthews, et al.
**Key Points:**
- Diffusion for trajectory generation in offline RL
- Policy guidance to move experience on-policy
- Alternative to autoregressive world models
- Lower dynamics error than world model baselines
**Relevance:** Diffusion for trajectory generation
**Gap:** Offline RL, not online manipulation

### 147. Humanoid-Gym: RL for Humanoid with Zero-Shot Sim2Real
**arXiv:** 2404.05695
**Venue:** ICRA 2024 Workshop
**Authors:** Xinyang Gu, Yen-Jen Wang, Jianyu Chen
**Key Points:**
- RL framework for humanoid locomotion
- Isaac Gym-based
- Zero-shot sim-to-real transfer
- Tested on XBot-S (1.2m) and XBot-L (1.65m)
**Relevance:** RL for humanoid control
**Gap:** Locomotion, not manipulation

---

## JUNE 2024 PAPERS

### 148. Learning Manipulation by Predicting Interaction (MPI)
**arXiv:** 2406.00439
**Venue:** RSS 2024
**Authors:** Jia Zeng, Qingwen Bu, Bangjun Wang, et al.
**Key Points:**
- Predicts interaction transition frames
- Learns "how-to-interact" and "where-to-interact"
- 10-64% improvement over SOTA
- Pre-training approach
**Relevance:** Interaction prediction for manipulation
**Gap:** Pre-training focus, not control paradigm

### 149. OpenVLA: An Open-Source Vision-Language-Action Model
**arXiv:** 2406.09246
**Authors:** Moo Jin Kim, Karl Pertsch, Ted Xiao, Sergey Levine, Chelsea Finn, et al.
**Key Points:**
- **7B parameter VLA model**
- 970k real-world robot demonstrations
- 16.5% better than RT-2-X (55B params) with 7x fewer parameters
- 20.4% improvement over Diffusion Policy
- Efficient fine-tuning on consumer GPUs
**Relevance:** ⭐ IMPORTANT - Large VLA foundation model
**Gap:** VLA approach, not hierarchical diffusion
**Novel Idea:** Open-source large VLA with efficient fine-tuning

### 150. DISCO: Language-Guided Manipulation with Diffusion Policies
**arXiv:** 2406.09767
**Authors:** Ce Hao, Kelvin Lin, Siyuan Luo, Harold Soh
**Key Points:**
- **VLM generates 3D keyframes, diffusion fills in**
- Constrained inpainting for diffusion
- Balances keyframe adherence with learned motion priors
- **Limitation noted:** "Strictly enforcing keyframes can degrade performance"
**Relevance:** ⭐ IMPORTANT - Language-guided hierarchical diffusion
**Gap:** Language focus, keyframe enforcement issues, no online adaptation
**Novel Idea:** VLM-to-3D translation with diffusion inpainting

### 151. GEM: Grounded Equivariant Manipulation
**arXiv:** 2406.15677
**Authors:** Mingxi Jia, Haojie Huang, et al.
**Key Points:**
- Pretrained VLMs + equivariant language mapping
- Orders of magnitude fewer data than CLIPort/VIMA
- Language-conditioned manipulation
**Relevance:** Equivariance + language
**Gap:** Not diffusion or hierarchical

### 152. EXTRACT: Efficient Policy Learning by Extracting Transferable Skills
**arXiv:** 2406.17768
**Venue:** CoRL 2024
**Authors:** Jesse Zhang, Minho Heo, et al.
**Key Points:**
- Uses VLMs to extract discrete skills from offline data
- Skills have continuous parameters
- Hierarchical: skill selection + parameter adjustment
- No human supervision for skill discovery
**Relevance:** IMPORTANT - Hierarchical skill-based learning
**Gap:** Skill extraction focus, not waypoint-based diffusion

### 153. Cross-Embodiment Robot Manipulation Skill Transfer
**arXiv:** 2406.01968
**Key Points:**
- Projects state/action spaces to common latent space
- Sim-to-sim and sim-to-real transfer
- Cross-embodiment policy transfer
**Relevance:** Cross-embodiment transfer
**Gap:** Transfer focus, not hierarchical control

### 154. ManiWAV: Audio-Visual Robot Manipulation
**arXiv:** 2406.19464
**Key Points:**
- "Ear-in-hand" data collection
- Audio-visual learning for contact-rich manipulation
- Audio helps when visual info ambiguous
**Relevance:** Multi-modal manipulation
**Gap:** Contact-rich focus, audio modality

### 155. Redundancy-aware Action Spaces for Robot Learning
**arXiv:** 2406.04144
**Key Points:**
- ER action space formulation
- Addresses redundancies in manipulators
- Combines joint and task space advantages
**Relevance:** Action space design
**Gap:** Not about control paradigm

---

## AUGUST 2024 (RSS 2024 Paper, published later)

### 156. ⭐ DWL: Denoising World Model Learning for Humanoid Locomotion
**arXiv:** 2408.14472
**Venue:** RSS 2024 (Best Paper Award Finalist, score 4.0/4.0)
**Authors:** Xinyang Gu, Yen-Jen Wang, Xiang Zhu, et al.
**Key Points:**
- **World model learning with denoising**
- First humanoid to master challenging real-world terrains
- Snowy/inclined land, stairs, extremely uneven terrain
- Zero-shot sim-to-real transfer
- Tested on XBot-S (1.2m) and XBot-L (1.65m)
**Relevance:** ⭐⭐⭐ CRITICAL - World model for robot control!
**Gap:** Locomotion focus, not manipulation
**Novel Idea:** Denoising approach for robust world model learning

---

## RSS 2024 ADDITIONAL PAPERS (Identified from proceedings)

### 157. Render and Diffuse: Aligning Image and Action Spaces
**Venue:** RSS 2024 (ID 51)
**Key Points:**
- Aligns image and action spaces for diffusion-based BC
- Rendering approach for better alignment
**Relevance:** Diffusion policy architecture
**Gap:** Not hierarchical

### 158. Don't Start From Scratch: Behavioral Refinement via Interpolant-based Policy Diffusion
**Venue:** RSS 2024 (ID 122)
**Key Points:**
- Policy refinement using diffusion
- Interpolant-based approach
**Relevance:** Diffusion for policy improvement
**Gap:** Refinement focus, not hierarchical

### 159. HACMan++: Spatially-Grounded Motion Primitives
**Venue:** RSS 2024 (ID 129)
**Key Points:**
- Spatially-grounded motion primitives
- Hierarchical approach for manipulation
**Relevance:** IMPORTANT - Hierarchical manipulation
**Gap:** Motion primitives, not waypoint-based diffusion

### 160. Parallel and Proximal Linear-Quadratic Methods for Real-Time MPC
**Venue:** RSS 2024 (ID 2)
**Key Points:**
- Real-time constrained MPC
- Parallel optimization methods
**Relevance:** MPC methodology
**Gap:** Classical control, not learning-based

### 161. Differentiable Robust Model Predictive Control
**Venue:** RSS 2024 (ID 3)
**Key Points:**
- Differentiable MPC with robustness
- Can be integrated with learning
**Relevance:** MPC + learning
**Gap:** Not diffusion-based

---

## Key Insights from Batch 005:

### CRITICAL COMPETITIVE LANDSCAPE:

**Direct Competitors to HiLoop:**

1. **Subgoal Diffuser** (March 2024) - MOST SIMILAR
   - Diffusion generates subgoals → MPC follows
   - Closed-loop via MPC
   - Dynamic subgoal density
   - **Difference:** Uses MPC (optimization) vs world model (learning)
   - **Difference:** Static generation + density adjustment vs dynamic refinement

2. **Hierarchical Diffuser** (January 2024)
   - Two-level hierarchical diffusion planning
   - Offline RL focus (not online manipulation)
   - **Difference:** No closed-loop adaptation during execution

3. **DISCO** (June 2024)
   - VLM keyframes + diffusion fills in
   - **Explicitly notes:** "Strictly enforcing keyframes can degrade performance"
   - **Difference:** No online refinement, language-guided

### NEW PATTERNS IDENTIFIED:

1. **Hierarchical + Language** (RT-H) - Language as abstraction layer
2. **World Model + Denoising** (DWL) - Denoising for robust world models
3. **Diffusion + DAgger** - Sample efficiency improvements
4. **Foundation VLAs** (OpenVLA) - 7B+ parameters, beats Diffusion Policy

### RESEARCH OPPORTUNITIES:

**Opportunity #17: World Model-Based Waypoint Refinement** (Papers #136, #137, #141, #156)
- Subgoal Diffuser uses MPC, but world models could be more sample-efficient
- DWL shows denoising world models work well for locomotion
- Combine diffusion waypoints + world model monitoring + online refinement
- Novelty: 7/10 (Subgoal Diffuser exists), Feasibility: 7/10, Impact: 8/10, Total: 22/30

**Opportunity #18: Language-Conditioned Hierarchical Diffusion** (Papers #145, #150)
- RT-H shows language motions work well for hierarchy
- DISCO shows VLM keyframes + diffusion, but has enforcement issues
- Combine language guidance with online waypoint adaptation
- Novelty: 7/10, Feasibility: 8/10, Impact: 8/10, Total: 23/30

---

## HiLoop Differentiation Strategy (Updated):

**vs Subgoal Diffuser:**
- World model (learning-based, generalizes) vs MPC (optimization-based, needs accurate model)
- Error-driven replanning (reactive to prediction errors) vs density-based allocation (predetermined)
- Online waypoint refinement (adapts waypoints) vs static subgoals (follows fixed sequence)

**vs Hierarchical Diffuser:**
- Online manipulation with closed-loop vs offline RL
- World model monitoring vs no execution monitoring
- Dynamic replanning vs static hierarchical plan

**vs DISCO:**
- No keyframe enforcement issues (soft guidance via error threshold)
- World model-based vs VLM-based keyframe generation
- Online refinement vs static keyframes

---

**Papers Reviewed So Far: 161 / 500 (32.2%)**

**HiLoop remains viable but differentiation from Subgoal Diffuser is CRITICAL!**

**Key message: Learning-based world model for online adaptation vs optimization-based MPC**

