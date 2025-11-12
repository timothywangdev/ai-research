# Diffusion Policy Papers - Batch 001

**Papers in this batch:** 35
**Category:** Diffusion Policies for Robotics
**Source:** Awesome-Robotics-Diffusion GitHub

---

## 1. Diffusion policy: Visuomotor policy learning via action diffusion
**Venue:** RSS 2023
**Link:** https://arxiv.org/abs/2303.04137
**Key Points:**
- Foundation paper for diffusion policies in robotics
- Uses diffusion models to generate action sequences
- 46.9% improvement over SOTA on 15 tasks
- Handles multimodal action distributions
**Relevance:** Core method, baseline for all comparisons

---

## 2. Goal-conditioned imitation learning using score-based diffusion policies
**Venue:** RSS 2023
**Link:** https://arxiv.org/abs/2304.02532
**Key Points:**
- Score-based variant of diffusion policy
- Goal-conditioned formulation
- Improves generalization to new goals
**Relevance:** Goal conditioning approach

---

## 3. Consistency policy: Accelerated visuomotor policies via consistency distillation
**Venue:** RSS 2024
**Link:** https://arxiv.org/abs/2405.07503
**Key Points:**
- Accelerates diffusion policy inference
- Uses consistency models for distillation
- Maintains performance with faster inference
**Relevance:** Addresses computational efficiency

---

## 4. Vision-Language-Affordance-based Robot Manipulation with Flow Matching
**Date:** September 2024
**Link:** https://arxiv.org/abs/2409.01083
**Key Points:**
- Flow matching alternative to diffusion
- Vision-language-affordance integration
- More stable training than diffusion
**Relevance:** Alternative to diffusion sampling

---

## 5. Safe Flow Matching: Robot Motion Planning with Control Barrier Functions
**Link:** https://arxiv.org/abs/2504.08661
**Key Points:**
- Flow matching with safety constraints
- Control barrier functions for safety
- Guarantees safety during generation
**Relevance:** Safety-aware generation

---

## 6. RDT-1B: a Diffusion Foundation Model for Bimanual Manipulation
**Date:** December 2024
**Link:** https://arxiv.org/abs/2410.07864
**Key Points:**
- 1B parameter diffusion transformer
- Bimanual manipulation focus
- Foundation model approach
- Addresses vision-language quantization issues
**Relevance:** Large-scale foundation model

---

## 7. EquiBot: SIM(3)-Equivariant Diffusion Policy
**Venue:** CoRL 2024
**Link:** https://arxiv.org/abs/2407.01479
**Key Points:**
- SE(3)/SIM(3) equivariance
- Generalizes across poses
- Data efficient learning
**Relevance:** Geometric equivariance for generalization

---

## 8. Equivariant Diffusion Policy
**Venue:** CoRL 2024 (Outstanding Paper Finalist)
**Link:** https://arxiv.org/abs/2407.01812
**Key Points:**
- Equivariant architecture for diffusion
- Improved generalization
- Finalist for best paper
**Relevance:** Top-tier method, equivariance approach

---

## 9. SkillDiffuser: Interpretable Hierarchical Planning via Skill Abstractions
**Venue:** CVPR 2024
**Link:** https://arxiv.org/abs/2312.11598
**Key Points:**
- Hierarchical skill abstractions
- Interpretable planning
- Diffusion over skill sequences
**Relevance:** Hierarchical approach, NOT closed-loop

---

## 10. Hierarchical Diffusion Policy for Kinematics-Aware Multi-Task Robotic Manipulation
**Venue:** CVPR 2024
**Link:** https://arxiv.org/abs/2403.03890
**Key Points:**
- Kinematics-aware hierarchy
- Multi-task learning
- High-level + low-level diffusion
**Relevance:** Hierarchical structure, different from ChainedDiffuser

---

## 11. ChainedDiffuser: Unifying Trajectory Diffusion and Keypose Prediction
**Venue:** CoRL 2023
**Link:** https://openreview.net/forum?id=W0zgY2mBTA8
**Key Points:**
- Keyposes + trajectory segments
- Transformer for keypose, diffusion for trajectory
- **Limitation: "open-loop between keyframes"**
- Control frequency: 5.1 Hz (slow)
- Fails on CALVIN benchmark (multimodal demos)
**Relevance:** MAIN COMPETITOR - our work addresses its open-loop limitation

---

## 12. XSkill: Cross Embodiment Skill Discovery
**Venue:** CoRL 2023
**Link:** https://arxiv.org/abs/2307.09955
**Key Points:**
- Cross-embodiment skill transfer
- Discovers transferable skills
- Diffusion-based skill representation
**Relevance:** Transfer learning across robots

---

## 13. Scaling Up and Distilling Down: Language-Guided Robot Skill Acquisition
**Venue:** CoRL 2023
**Link:** https://arxiv.org/abs/2307.14535
**Key Points:**
- Language-guided skill acquisition
- Scaling + distillation approach
- Combines large models with efficient policies
**Relevance:** Language conditioning + scaling

---

## 14. Generative Skill Chaining: Long-Horizon Skill Planning with Diffusion Models
**Venue:** CoRL 2023
**Link:** https://arxiv.org/pdf/2401.03360
**Key Points:**
- Long-horizon skill chaining
- Diffusion for skill sequencing
- Addresses long-horizon planning
**Relevance:** Long-horizon approach

---

## 15. 3D Diffuser Actor: Policy Diffusion with 3D Scene Representations
**Venue:** CoRL 2024
**Link:** https://arxiv.org/abs/2402.10885
**Key Points:**
- 3D scene representations
- 9% improvement on CALVIN
- Better spatial understanding
**Relevance:** 3D representation learning

---

## 16. 3D Diffusion Policy: Generalizable Visuomotor Policy Learning via Simple 3D Representations
**Venue:** RSS 2024
**Link:** https://arxiv.org/abs/2403.03954
**Key Points:**
- Simple 3D representations (point clouds)
- Generalizes across tasks and embodiments
- 100% success rate with RL finetuning
**Relevance:** Generalization via 3D

---

## 17. RISE: 3D Perception Makes Real-World Robot Imitation Simple and Effective
**Venue:** IROS 2024
**Link:** https://arxiv.org/abs/2404.12281
**Key Points:**
- 3D perception for imitation
- Sim-to-real transfer
- Simple and effective approach
**Relevance:** 3D perception for real-world

---

## 18. GenDP: 3D Semantic Fields for Category-Level Generalizable Diffusion Policy
**Venue:** CoRL 2024
**Link:** https://arxiv.org/abs/2410.17488
**Key Points:**
- 3D semantic fields
- Category-level generalization
- Generalizes to new object categories
**Relevance:** Object-level generalization

---

## 19. Track2Act: Predicting Point Tracks from Internet Videos enables Generalizable Robot Manipulation
**Venue:** ECCV 2024
**Link:** https://arxiv.org/abs/2405.01527
**Key Points:**
- Point tracking from internet videos
- Image-goal conditioning
- Leverages web-scale data
**Relevance:** Web-scale pretraining

---

## 20. PlayFusion: Skill Acquisition via Diffusion from Language-Annotated Play
**Venue:** CoRL 2023
**Link:** https://arxiv.org/pdf/2312.04549
**Key Points:**
- Language-annotated play data
- Skill acquisition from unstructured play
- Language conditioning
**Relevance:** Play data for learning

---

## 21. Diffusion-VLA: Scaling Robot Foundation Models via Unified Diffusion and Autoregression
**Date:** December 2024
**Link:** https://arxiv.org/pdf/2412.03293
**Key Points:**
- Unified diffusion + autoregression
- Vision-language-action foundation model
- Scaling approach
**Relevance:** Foundation model architecture

---

## 22. Se(3)-diffusionfields: Learning cost functions for joint grasp and motion optimization
**Venue:** ICRA 2023
**Link:** https://arxiv.org/abs/2209.03855
**Key Points:**
- SE(3) diffusion for grasping
- Joint grasp + motion optimization
- Cost function learning
**Relevance:** Geometric diffusion for grasping

---

## 23. Composable Part-Based Manipulation
**Venue:** CoRL 2023
**Link:** https://arxiv.org/abs/2405.05876
**Key Points:**
- Part-based object decomposition
- Composable manipulation primitives
- Object-centric approach
**Relevance:** Object-centric manipulation

---

## 24. Shelving, stacking, hanging: Relational pose diffusion for multi-modal rearrangement
**Venue:** CoRL 2023
**Link:** https://arxiv.org/abs/2307.04751
**Key Points:**
- Relational pose diffusion
- Multi-modal rearrangement
- Spatial relationships
**Relevance:** Relational reasoning

---

## 25. Reorientdiff: Diffusion model based reorientation for object manipulation
**Venue:** ICRA 2024
**Link:** https://arxiv.org/abs/2303.12700
**Key Points:**
- Object reorientation with diffusion
- In-hand manipulation
- Pose optimization
**Relevance:** Dexterous manipulation

---

## 26. Planning-Guided Diffusion Policy Learning for Generalizable Contact-Rich Bimanual Manipulation (GLIDE)
**Date:** December 2024
**Link:** https://arxiv.org/abs/2412.02676
**Key Points:**
- Planning-guided diffusion
- Contact-rich bimanual tasks
- Uses motion planner for demonstration generation
- High-fidelity physics simulation
**Relevance:** Contact-rich + bimanual, recent

---

## Benchmarks Referenced

### 27. Meta-World: A Benchmark and Evaluation for Multi-Task and Meta Reinforcement Learning
**Venue:** CoRL 2020
**Link:** https://arxiv.org/abs/1910.10897
**Key Points:**
- 50 distinct tasks
- Multi-task and meta-RL benchmark
- Standard benchmark for policies
**Relevance:** Standard benchmark

---

### 28. CALVIN: A Benchmark for Language-conditioned Policy Learning
**Venue:** RAL 2022
**Link:** https://arxiv.org/abs/2112.03227
**Key Points:**
- Language-conditioned long-horizon tasks
- 34 tasks with chaining
- 24 hours of play data
- Tests multimodal learning
**Relevance:** Long-horizon + language benchmark

---

### 29. RLBench: The Robot Learning Benchmark & Learning Environment
**Venue:** RAL 2020
**Link:** https://arxiv.org/abs/1909.12271
**Key Points:**
- 106 diverse manipulation tasks
- Standard simulation benchmark
- CoppeliaSim/PyRep based
**Relevance:** Standard manipulation benchmark

---

### 30. LIBERO: Benchmarking Knowledge Transfer in Lifelong Robot Learning
**Venue:** NeurIPS 2023 Dataset and Benchmark Track
**Link:** https://arxiv.org/abs/2306.03310
**Key Points:**
- Lifelong learning benchmark
- Knowledge transfer evaluation
- Multiple task suites
**Relevance:** Lifelong learning evaluation

---

### 31. BridgeData V2: A Dataset for Robot Learning at Scale
**Venue:** CoRL 2023
**Link:** https://arxiv.org/abs/2308.12952
**Key Points:**
- Large-scale real robot data
- 60K trajectories
- Multi-robot, multi-task
**Relevance:** Large-scale real data

---

### 32. Bridge data: Boosting generalization of robotic skills with cross-domain datasets
**Venue:** RSS 2022
**Link:** https://arxiv.org/abs/2109.13396
**Key Points:**
- Cross-domain datasets
- Generalization via diverse data
- Real robot manipulation
**Relevance:** Data diversity for generalization

---

### 33. Towards Human-Level Bimanual Dexterous Manipulation with Reinforcement Learning
**Venue:** NeurIPS 2022 Datasets and Benchmarks Track
**Link:** https://arxiv.org/abs/2206.08686
**Key Points:**
- Bimanual dexterity benchmark
- Human-level manipulation
- Complex coordination tasks
**Relevance:** Bimanual benchmark

---

### 34. DexArt: Benchmarking generalizable dexterous manipulation with articulated objects
**Venue:** CVPR 2023
**Link:** https://arxiv.org/abs/2305.05706
**Key Points:**
- Articulated object manipulation
- Dexterous hand control
- Generalization across objects
**Relevance:** Dexterous manipulation benchmark

---

### 35. Learning Complex Dexterous Manipulation with Deep Reinforcement Learning and Demonstrations
**Venue:** RSS 2018
**Link:** https://arxiv.org/abs/1709.10087
**Key Points:**
- Early dexterous manipulation work
- RL + demonstrations
- In-hand object manipulation
**Relevance:** Historical context for dexterous manipulation

---

## Key Insights from Batch 001:

1. **Diffusion Policy** (RSS 2023) is the foundation - all methods build on it
2. **ChainedDiffuser** has documented open-loop limitation - our opportunity!
3. **Hierarchical approaches** exist but none with closed-loop adaptation
4. **3D representations** improve generalization significantly
5. **Flow matching** emerging as alternative to diffusion sampling
6. **Equivariance** provides data efficiency and generalization
7. **Computational efficiency** major concern - OneDP, Consistency Policy address this
8. **Benchmarks:** CALVIN (language), RLBench (manipulation), MetaWorld (multi-task)

## Gaps Identified:
- ✅ Open-loop execution in hierarchical methods (ChainedDiffuser)
- ⚠️ Slow inference (being addressed: OneDP, Consistency Policy)
- ⚠️ Dynamic adaptation during execution (not addressed)
- ⚠️ Online error correction (not addressed)

**Papers Reviewed So Far: 35 / 500**

