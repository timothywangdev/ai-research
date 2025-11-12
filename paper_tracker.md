# Paper Review Tracker

**Goal:** Review 500+ papers on robotics manipulation, world models, diffusion policies
**Current Count:** 161 / 500 (32.2%)
**Last Updated:** 2025-11-12

---

## Papers Reviewed by Batch

### Batch 001: Diffusion Policies (Papers 1-35)
**Source:** Awesome-Robotics-Diffusion GitHub
**Status:** ✅ COMPLETE
**File:** paper_summaries/batch_001_diffusion_policies.md

### Batch 002: World Models (Papers 36-68)
**Source:** Awesome-World-Models-for-Robots GitHub
**Status:** ✅ COMPLETE
**File:** paper_summaries/batch_002_world_models.md

### Batch 003: arXiv Sep-Dec 2024 (Papers 69-120)
**Source:** arXiv cs.RO Sep-Dec 2024
**Status:** ✅ COMPLETE
**File:** paper_summaries/batch_003_arxiv_recent_2024.md
**Papers:** 52

### Batch 004: arXiv Jul-Aug 2024 (Papers 121-135)
**Source:** arXiv cs.RO Jul-Aug 2024
**Status:** ✅ COMPLETE
**File:** paper_summaries/batch_004_arxiv_jul_aug_2024.md
**Papers:** 15

### Batch 005: arXiv Jan-Jun 2024 + RSS 2024 (Papers 136-161)
**Source:** arXiv cs.RO/cs.LG Jan-Jun 2024, RSS 2024 proceedings
**Status:** ✅ COMPLETE
**File:** paper_summaries/batch_005_arxiv_jan_jun_2024.md
**Papers:** 26

### Batch 006: CoRL 2024 (Papers 162-230)
**Source:** OpenReview CoRL 2024
**Status:** ⏳ PENDING
**Target:** ~70 papers

### Batch 007: ICRA 2024 (Papers 231-300)
**Source:** ICRA 2024 proceedings
**Status:** ⏳ PENDING
**Target:** ~70 papers

### Batch 008: NeurIPS 2024 Robotics (Papers 301-370)
**Source:** NeurIPS proceedings (filtered for robotics)
**Status:** ⏳ PENDING
**Target:** ~70 papers

### Batch 006: NeurIPS 2023-2024 Robotics (Papers 301-370)
**Source:** NeurIPS proceedings (filtered for robotics)
**Status:** ⏳ PENDING
**Target:** ~70 papers

### Batch 007: ICLR 2024 Robotics (Papers 371-410)
**Source:** ICLR proceedings (filtered)
**Status:** ⏳ PENDING
**Target:** ~40 papers

### Batch 008: arXiv Recent (Papers 411-480)
**Source:** arXiv cs.RO, cs.LG (robot manipulation)
**Status:** ⏳ PENDING
**Target:** ~70 papers

### Batch 009: Survey Papers & Citations (Papers 481-550)
**Source:** Citations from major surveys
**Status:** ⏳ PENDING
**Target:** ~70 papers

---

## Count by Category

- **Diffusion Policies:** 48 (batches 1, 3, 5)
- **World Models:** 38 (batches 2, 3, 5)
- **Hierarchical Methods:** 18 (includes Subgoal Diffuser, Hierarchical Diffuser, RT-H, EXTRACT, HACMan++)
- **Model-Based RL:** 8
- **Long-Horizon Tasks:** 12
- **Failure Recovery:** 2 (MoE-DP, reactive methods)
- **Contact-Rich:** 8
- **Bimanual:** 7 (Mobile ALOHA, RDT-1B, etc.)
- **Sim-to-Real:** 8 (Humanoid-Gym, DWL, etc.)
- **VLA Models:** 7 (OpenVLA, RT-H, Diffusion-VLA, etc.)
- **MPC/Control:** 8 (Subgoal Diffuser, D-MPC, RSS MPC papers)
- **Benchmarks:** 10
- **Foundation Models:** 9 (OpenVLA, RDT-1B, Cosmos, GR00T, etc.)
- **Other:** 18

**TOTAL REVIEWED: 161 / 500 (32.2%)**

---

## Research Gaps Identified (Running List)

### Critical Gaps:
1. ✅ **Open-loop execution in hierarchical diffusion policies** (ChainedDiffuser limitation)
2. ✅ **Dynamic adaptation during execution** (not addressed comprehensively)
3. ✅ **Online waypoint refinement** (missing in PIVOT-R, ChainedDiffuser)
4. ✅ **Error monitoring for replanning triggers** (MoE-DP is reactive, not predictive)

### Partially Addressed:
5. ⚠️ **Computational efficiency** (OneDP, Consistency Policy address, but ongoing issue)
6. ⚠️ **Long-horizon error accumulation** (acknowledged but not fully solved)
7. ⚠️ **Contact-rich manipulation** (some work but still challenging)
8. ⚠️ **Sim-to-real transfer** (ongoing challenge)

### Emerging Trends:
9. 📈 **Foundation models for robotics** (Cosmos, GR00T, Genie)
10. 📈 **Flow matching as diffusion alternative** (faster, more stable)
11. 📈 **3D representations** (DP3, 3D Diffuser Actor)
12. 📈 **LLM integration** (RoboHorizon, language-guided methods)

---

## Key Papers for HiLoop Comparison

### CRITICAL Direct Competitors (⭐⭐⭐):
1. **⭐ Subgoal Diffuser** (March 2024) - MOST SIMILAR! Diffusion + MPC + closed-loop
   - Difference: MPC (optimization) vs world model (learning), static subgoals vs dynamic refinement
2. **⭐ Hierarchical Diffuser** (Jan 2024) - Two-level hierarchical diffusion
   - Difference: Offline RL, no online adaptation, no world model monitoring
3. **ChainedDiffuser** (CoRL 2023) - Open-loop limitation, 5.1 Hz control
   - Difference: Open-loop between waypoints, no error monitoring
4. **PIVOT-R** (NeurIPS 2024) - Waypoint-aware world model, no adaptation
   - Difference: No online waypoint refinement

### Related with Partial Overlap:
5. **DISCO** (June 2024) - VLM keyframes + diffusion, notes keyframe enforcement issues
6. **RT-H** (March 2024, RSS 2024) - Language-based action hierarchies
7. **MoE-DP** (Nov 2024) - Failure recovery, no hierarchy
8. **D-MPC** (Oct 2024) - Diffusion MPC, no hierarchy
9. **DWL** (Aug 2024, RSS Best Paper Finalist) - Denoising world model for locomotion

### Different Focus:
10. **Hierarchical Diffusion Policy** (CVPR 2024) - Contact-based hierarchy
11. **SkillDiffuser** (CVPR 2024) - Skill abstractions
12. **EXTRACT** (CoRL 2024) - Skill extraction from offline data
13. **3D Diffuser Actor** (CoRL 2024) - 3D representations
14. **OpenVLA** (June 2024) - 7B VLA beats Diffusion Policy by 20.4%
15. **Unified World Models** (RSS 2025) - Video + action diffusion

---

## Insights Across Papers

### Technical Trends:
- **Diffusion dominates** policy learning (35 papers)
- **Video-based world models** popular (iVideoGPT, GR1, VidMan)
- **Hierarchical approaches** common but all open-loop
- **3D perception** improves generalization significantly
- **Real-world deployment** remains challenging

### Methodological Patterns:
- **Imitation learning** + diffusion standard combination
- **Pre-training on human videos** emerging (HRP, affordances)
- **Equivariance** provides data efficiency (EquiBot, Equivariant DP)
- **Foundation models** trend toward larger scale (1B+ parameters)

### Gaps in Literature:
- **No closed-loop hierarchical diffusion** with online adaptation
- **No proactive error monitoring** (only reactive failure recovery)
- **Limited dynamic environment** benchmarks
- **Insufficient long-horizon** evaluation (most <200 steps)

---

## Next Steps

1. ✅ Complete ICRA 2024 batch (target: 80 papers)
2. ⏳ CoRL 2023-2024 comprehensive review
3. ⏳ RSS 2023-2024 comprehensive review
4. ⏳ NeurIPS robotics papers
5. ⏳ Survey paper citations
6. ⏳ arXiv recent preprints

**Target: 500 papers by end of comprehensive review**

---

## Confidence in HiLoop Decision

**After 161 papers:**
- ✅ ChainedDiffuser open-loop limitation confirmed
- ⚠️ **CRITICAL FINDING:** Subgoal Diffuser (March 2024) is VERY similar to HiLoop!
  - Uses diffusion + MPC + closed-loop control
  - Key difference: MPC (optimization, needs model) vs world model (learning, generalizes)
  - Key difference: Static subgoals + density adjustment vs dynamic waypoint refinement
- ✅ Hierarchical Diffuser exists but for offline RL, not online manipulation
- ✅ DISCO shows VLM keyframes + diffusion but explicitly notes keyframe enforcement issues
- ✅ RT-H uses language hierarchies, different abstraction than waypoints
- ✅ DWL shows denoising world models work well (RSS Best Paper Finalist)
- ✅ Workshop priorities align (dynamic adaptation)

**Differentiation Strategy Required:**
- Position HiLoop as world model-based (learning, generalizable) vs MPC-based (optimization, model-dependent)
- Emphasize error-driven dynamic replanning vs predetermined density adjustment
- Highlight online waypoint refinement (adapts waypoints themselves) vs static subgoal following

**Confidence: 75% → 70% (Subgoal Diffuser is a strong competitor, need clear differentiation)**

**Action: Continue review to ensure no other similar work exists, strengthen differentiation**

