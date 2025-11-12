# Research Opportunities & Gaps Tracker

**Purpose:** Track ALL research gaps and novel opportunities discovered during comprehensive paper review
**Papers Reviewed:** 68 / 500+
**Last Updated:** 2025-11-12

---

## RESEARCH OPPORTUNITY #1: HiLoop (Hierarchical Closed-Loop Diffusion)

### Gap Identified:
ChainedDiffuser and hierarchical diffusion policies execute open-loop between waypoints, failing in dynamic environments.

### Supporting Evidence:
- ChainedDiffuser (CoRL 2023): "operates open-loop between keyframes, struggles to adapt to dynamic environments"
- Control frequency only 5.1 Hz
- Fails on CALVIN benchmark with multimodal demos
- Workshop emphasis on dynamic adaptation (CoRL 2024)

### Proposed Solution:
Two-level closed-loop: diffusion generates waypoints, world model monitors error, triggers online refinement when threshold exceeded.

### Novelty Score: 8/10
### Feasibility: 8/10
### Impact: 9/10
### Overall: 25/30

### Status: PRIMARY CANDIDATE

---

## RESEARCH OPPORTUNITY #2: Multi-Stage Contact Prediction for Manipulation

### Gap Identified:
Contact-rich manipulation remains challenging. Current methods struggle with:
- Predicting contact transitions
- Planning through contact sequences
- Generalizing across contact types

### Supporting Evidence:
- DIPCOM (Oct 2024): compliance control but no contact sequence planning
- Hierarchical Diffusion Policy: uses contact points but task-specific
- GLIDE (Dec 2024): planning-guided but requires motion planner

### Papers Mentioning Gap:
- "Hierarchical Diffusion Policy" (CVPR 2024)
- "Planning-Guided Diffusion" (Dec 2024)
- Diffusion survey: "contact-rich manipulation remains challenging"

### Proposed Solution Ideas:
1. **Contact-Aware Waypoints:** Waypoints at predicted contact transitions
2. **Contact Diffusion Model:** Diffusion over contact sequences + poses
3. **Physics-Informed Contact Prediction:** Use differentiable physics for contacts

### Novelty Score: 7/10 (some work exists)
### Feasibility: 6/10 (contact physics hard)
### Impact: 9/10 (critical for real-world)
### Overall: 22/30

### Status: BACKUP OPTION

---

## RESEARCH OPPORTUNITY #3: Uncertainty-Calibrated Failure Prevention

### Gap Identified:
MoE-DP recovers from failures AFTER they occur. No proactive failure prevention using calibrated uncertainty.

### Supporting Evidence:
- MoE-DP (Nov 2024): reactive recovery, no prediction
- Diff-DAgger (Oct 2024): uncertainty for data collection, not prevention
- Lack of calibrated uncertainty in diffusion policies

### Proposed Solution Ideas:
1. **Conformal Prediction for Diffusion:** Distribution-free uncertainty bounds
2. **Predictive Failure Detection:** World model predicts failure before occurrence
3. **Uncertainty-Guided Replanning:** Replan proactively when uncertainty high

### Novelty Score: 7/10
### Feasibility: 6/10 (calibration hard)
### Impact: 8/10
### Overall: 21/30

### Status: INTERESTING BUT RISKY

---

## RESEARCH OPPORTUNITY #4: Cross-Embodiment Hierarchical Transfer

### Gap Identified:
Cross-embodiment transfer focuses on low-level policies. No hierarchical transfer of waypoints/skills across robots.

### Supporting Evidence:
- XSkill (CoRL 2023): skill discovery across embodiments
- Open X-Embodiment: dataset work, not hierarchical transfer
- Most work transfers dense policies, not hierarchical structure

### Proposed Solution Ideas:
1. **Embodiment-Invariant Waypoints:** SE(3) representations transfer across robots
2. **Skill Abstraction Transfer:** High-level skills transfer, low-level adapted
3. **Morphology-Conditioned Diffusion:** Condition on robot morphology

### Novelty Score: 8/10
### Feasibility: 7/10
### Impact: 8/10
### Overall: 23/30

### Status: INTERESTING ALTERNATIVE

---

## RESEARCH OPPORTUNITY #5: Long-Horizon Benchmark with Perturbations

### Gap Identified:
Existing benchmarks (RLBench, CALVIN, MetaWorld) don't systematically evaluate dynamic adaptation. No standard perturbation protocol.

### Supporting Evidence:
- Most benchmarks static environments
- No standard perturbation evaluation
- Workshop emphasis on dynamic environments but no benchmark

### Proposed Solution:
Create benchmark with:
- 500-1000 step tasks
- Standardized perturbations (object moved, friction change, occlusions)
- Multiple difficulty levels

### Novelty Score: 6/10 (benchmarks exist, but this specific focus is new)
### Feasibility: 9/10 (just engineering)
### Impact: 7/10 (enables community progress)
### Overall: 22/30

### Status: COMPLEMENTARY CONTRIBUTION

---

## RESEARCH OPPORTUNITY #6: Foundation Models with Online Adaptation

### Gap Identified:
Foundation models (RDT-1B, GR00T, Cosmos) are trained offline. No online adaptation to new environments/tasks during deployment.

### Supporting Evidence:
- RDT-1B: 1B parameters but no online learning
- GR00T: foundation model but static after training
- Trend toward larger models but no adaptation mechanisms

### Proposed Solution Ideas:
1. **Meta-Learning for Fast Adaptation:** Foundation model + MAML-style adaptation
2. **Online Parameter-Efficient Fine-tuning:** LoRA-style adaptation during deployment
3. **Memory-Augmented Foundation Models:** Episodic memory for context

### Novelty Score: 8/10
### Feasibility: 5/10 (foundation models expensive)
### Impact: 9/10 (critical for deployment)
### Overall: 22/30

### Status: HIGH IMPACT BUT RESOURCE-INTENSIVE

---

## RESEARCH OPPORTUNITY #7: Equivariant World Models

### Gap Identified:
World models (video-based) lack geometric equivariance. Equivariant diffusion policies exist (EquiBot, Equivariant DP) but not equivariant world models.

### Supporting Evidence:
- Equivariant Diffusion Policy (CoRL 2024): equivariance for policies
- World models (iVideoGPT, GR1): no equivariance, learn from scratch
- 3D representations help but not fully equivariant

### Proposed Solution:
SE(3)-equivariant world model: state prediction respects geometric transformations.

### Novelty Score: 9/10
### Feasibility: 6/10 (geometric deep learning complex)
### Impact: 8/10
### Overall: 23/30

### Status: NOVEL BUT TECHNICAL RISK

---

## RESEARCH OPPORTUNITY #8: Human-in-the-Loop Waypoint Correction

### Gap Identified:
Hierarchical methods generate waypoints automatically. No human-in-the-loop correction when waypoints suboptimal.

### Supporting Evidence:
- ChainedDiffuser: fully automatic, no human feedback
- VLM-based methods exist but not for waypoint correction
- TRANSIC (2024): human-in-loop for sim-to-real, not for waypoints

### Proposed Solution:
Interactive system where human can:
1. Visualize predicted waypoints
2. Correct/adjust waypoints
3. System learns from corrections

### Novelty Score: 6/10 (HCI + robotics)
### Feasibility: 8/10
### Impact: 7/10
### Overall: 21/30

### Status: INTERESTING HCI ANGLE

---

## RESEARCH OPPORTUNITY #9: Multimodal Waypoint Prediction

### Gap Identified:
ChainedDiffuser's deterministic keypose prediction fails on multimodal data (CALVIN). Diffusion for waypoints could handle multimodality but not explored.

### Supporting Evidence:
- ChainedDiffuser limitation: "deterministic keypose prediction fails on CALVIN"
- Diffusion excels at multimodal distributions
- But most hierarchical work uses deterministic high-level

### Proposed Solution:
Use diffusion model for waypoint generation (not just trajectory segments) to handle multimodal waypoint distributions.

### Novelty Score: 7/10
### Feasibility: 8/10
### Impact: 7/10
### Overall: 22/30

### Status: COULD COMBINE WITH HILOOP

---

## RESEARCH OPPORTUNITY #10: Provable Guarantees for Hierarchical Policies

### Gap Identified:
Hierarchical methods lack theoretical guarantees. "Provable Guarantees for BC" (NeurIPS 2023) exists but not for hierarchical.

### Supporting Evidence:
- Provable Guarantees paper: flat policies only
- Hierarchical methods empirical only
- No error bound analysis for waypoint-based methods

### Proposed Solution:
Extend provable guarantees framework to hierarchical setting:
- Error bounds for waypoint-based policies
- Conditions for hierarchical decomposition
- Stability analysis

### Novelty Score: 9/10 (strong theory contribution)
### Feasibility: 5/10 (requires strong theory background)
### Impact: 7/10 (theory papers have different impact)
### Overall: 21/30

### Status: THEORY TRACK OPTION

---

## EMERGING THEMES (Across 68 Papers):

### Theme 1: Computational Efficiency
**Papers:** OneDP, Consistency Policy, Flow Matching, D-MPC
**Gap:** Real-time control still challenging
**Opportunity:** Novel acceleration methods for diffusion

### Theme 2: 3D Representations
**Papers:** DP3, 3D Diffuser Actor, GenDP
**Gap:** Point clouds vs voxels vs features - no consensus
**Opportunity:** Optimal 3D representation for manipulation

### Theme 3: Foundation Models
**Papers:** RDT-1B, Cosmos, GR00T, Genie
**Gap:** Deployment and adaptation
**Opportunity:** Lightweight adaptation methods

### Theme 4: Sim-to-Real
**Papers:** TRANSIC, NavDP, RISE, 3D Diffusion Policy
**Gap:** Domain randomization vs adaptation vs system ID
**Opportunity:** Unified framework for sim-to-real

### Theme 5: Language Integration
**Papers:** CALVIN, PlayFusion, Diffusion-VLA, RoboHorizon
**Gap:** Grounding language to actions
**Opportunity:** Better language-motion alignment

---

## RANKING ALL OPPORTUNITIES (After 68 Papers):

| Rank | Opportunity | Novelty | Feasibility | Impact | Total | Risk |
|------|-------------|---------|-------------|--------|-------|------|
| 🥇 1 | **HiLoop** | 8 | 8 | 9 | 25 | Medium |
| 🥈 2 | Cross-Embodiment Hierarchical | 8 | 7 | 8 | 23 | Medium |
| 🥉 3 | Equivariant World Models | 9 | 6 | 8 | 23 | High |
| 4 | Multi-Stage Contact Prediction | 7 | 6 | 9 | 22 | High |
| 5 | Foundation Model Online Adapt | 8 | 5 | 9 | 22 | High |
| 6 | Multimodal Waypoint Prediction | 7 | 8 | 7 | 22 | Low |
| 7 | Long-Horizon Benchmark | 6 | 9 | 7 | 22 | Low |
| 8 | Uncertainty-Calibrated Prevention | 7 | 6 | 8 | 21 | Medium |
| 9 | Human-in-Loop Waypoint | 6 | 8 | 7 | 21 | Low |
| 10 | Provable Guarantees Hierarchical | 9 | 5 | 7 | 21 | High |

---

## COMBINATIONS WORTH EXPLORING:

### Combination A: HiLoop + Multimodal Waypoints
Use diffusion for waypoint generation (handles multimodality) + closed-loop adaptation
**Total Score:** 8 novelty, 8 feasibility, 9 impact = 25
**Status:** STRONGEST CANDIDATE

### Combination B: HiLoop + Equivariance
Closed-loop hierarchical with SE(3)-equivariant representations
**Total Score:** 8.5 novelty, 7 feasibility, 8.5 impact = 24
**Status:** VERY STRONG

### Combination C: Contact-Aware HiLoop
Waypoints at contact transitions + closed-loop adaptation
**Total Score:** 7.5 novelty, 7 feasibility, 9 impact = 23.5
**Status:** PRACTICAL FOCUS

---

## ACTION ITEMS:

1. ✅ Continue systematic paper review (target 500+)
2. ⏳ Update this document with new gaps as found
3. ⏳ Compare all opportunities after complete review
4. ⏳ Make final decision on research direction

**Current Leader: HiLoop (potentially combined with multimodal waypoints)**

Will reassess after reviewing all 500+ papers.

