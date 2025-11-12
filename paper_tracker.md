# Paper Review Tracker

**Goal:** Review 500+ papers on robotics manipulation, world models, diffusion policies
**Current Count:** 68 / 500 (13.6%)
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

### Batch 003: ICRA 2024 (Papers 69-150) - IN PROGRESS
**Source:** ICRA 2024 proceedings, GitHub lists
**Status:** 🔄 IN PROGRESS
**Target:** ~80 papers

### Batch 004: CoRL 2023-2024 (Papers 151-230)
**Source:** OpenReview, CoRL proceedings
**Status:** ⏳ PENDING
**Target:** ~80 papers

### Batch 005: RSS 2023-2024 (Papers 231-300)
**Source:** RSS proceedings
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

- **Diffusion Policies:** 35
- **World Models:** 33
- **Hierarchical Methods:** 8 (from batches 1-2)
- **Model-Based RL:** 5 (from batches 1-2)
- **Long-Horizon Tasks:** 6 (from batches 1-2)
- **Failure Recovery:** 1 (from batch 1)
- **Contact-Rich:** 4 (from batches 1-2)
- **Bimanual:** 4 (from batches 1-2)
- **Sim-to-Real:** 3 (from batches 1-2)
- **VLA Models:** 3 (from batches 1-2)
- **MPC/Control:** 2 (from batches 1-2)
- **Benchmarks:** 8 (from batch 1)
- **Foundation Models:** 5 (from batch 2)
- **Other:** 3

**TOTAL REVIEWED: 68 / 500 (13.6%)**

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

### Direct Competitors:
1. **ChainedDiffuser** (CoRL 2023) - Open-loop limitation, 5.1 Hz control
2. **PIVOT-R** (NeurIPS 2024) - Waypoint-aware world model, no adaptation
3. **MoE-DP** (Nov 2024) - Failure recovery, no hierarchy
4. **D-MPC** (Oct 2024) - Diffusion MPC, no hierarchy
5. **KeyWorld** (2025) - Key frames + interpolation, NOT for control

### Related but Different Focus:
6. **Hierarchical Diffusion Policy** (CVPR 2024) - Contact-based hierarchy
7. **SkillDiffuser** (CVPR 2024) - Skill abstractions
8. **3D Diffuser Actor** (CoRL 2024) - 3D representations
9. **VidMan** (NeurIPS 2024) - Video diffusion for dynamics
10. **Unified World Models** (RSS 2025) - Video + action diffusion

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

**After 68 papers:**
- ✅ ChainedDiffuser open-loop limitation confirmed
- ✅ No existing work combines hierarchy + closed-loop + online waypoint adaptation
- ✅ Workshop priorities align (dynamic adaptation)
- ✅ Clear differentiation from all reviewed papers

**Confidence: 75% → maintaining confidence as more papers reviewed**

