# CoRL 2026 Research Opportunity: Executive Summary

**Generated:** 2025-11-12
**Target Conference:** CoRL 2026
**Timeline:** 6 months
**Researcher Profile:** Strong in LLMs, world models, diffusion control; simulation-only (Isaac Gym, MuJoCo)

---

## 🎯 Recommended Research Direction

**Project:** HiWaDi (Hierarchical Waypoint Diffusion with World Model Interpolation)

**One-Line Pitch:** Use diffusion models to generate sparse waypoints as error checkpoints, with world models for fast interpolation between waypoints, reducing error accumulation in long-horizon manipulation from O(T²) to O(k·h²).

---

## 📊 Research Gap Analysis

We identified 5 major research gaps in world models + diffusion for robotics:

| Rank | Gap | Novelty | Feasibility | Impact | Score |
|------|-----|---------|-------------|--------|-------|
| 🥇 **1** | **Error Accumulation in Long-Horizon Prediction** | ⭐⭐⭐⭐⭐ | ⭐⭐⭐⭐ | ⭐⭐⭐⭐⭐ | **100** |
| 🥈 2 | Multimodal Uncertainty & OOD Detection | ⭐⭐⭐⭐ | ⭐⭐⭐⭐⭐ | ⭐⭐⭐⭐ | 80 |
| 🥉 3 | Contact-Rich Manipulation in Learned Simulators | ⭐⭐⭐⭐⭐ | ⭐⭐⭐ | ⭐⭐⭐⭐⭐ | 75 |
| 4 | Compositional Generalization Across Objects | ⭐⭐⭐⭐ | ⭐⭐⭐⭐ | ⭐⭐⭐⭐ | 64 |
| 5 | Rapid Environmental Adaptation | ⭐⭐⭐ | ⭐⭐⭐ | ⭐⭐⭐⭐ | 36 |

**Why Gap #1?**
- ✅ Not directly solved in current literature
- ✅ Perfect match for your expertise (world models + diffusion)
- ✅ Clear validation path in simulation
- ✅ Critical for real-world deployment

---

## 💡 Three Solution Approaches

### Solution 1: HiWaDi (RECOMMENDED) ⭐⭐⭐⭐
**Core Idea:** Diffusion generates waypoints, world model interpolates between them
**Novelty:** First to use diffusion for error-aware temporal abstraction in world models
**Feasibility:** High (4/5) - proven components, straightforward integration
**Review Score:** 6/10 (Revise) → 8-9/10 with suggested improvements

**Key Improvements Needed:**
- Add theoretical error analysis (O(k·h²) bound)
- Test on genuinely long tasks (500-1000 steps)
- Implement state correction mechanism
- Differentiate clearly from ChainedDiffuser (CoRL 2023)

---

### Solution 2: UWMAR (BACKUP)
**Core Idea:** World model with uncertainty estimation triggers adaptive replanning with diffusion policy
**Novelty:** Novel combination, addresses "when to trust model" problem
**Feasibility:** Moderate (3/5) - uncertainty calibration is hard
**Review Score:** 5.5/10 (Revise) - needs substantial work on calibration

---

### Solution 3: PIWS (NOT RECOMMENDED)
**Core Idea:** Differentiable physics simulator + learned residual for world model
**Novelty:** Weak - 2024 soft robotics paper does essentially the same thing
**Feasibility:** Moderate (3/5) - differentiable sim limitations
**Review Score:** 4/10 (Reject) - insufficient novelty

---

## 📅 6-Month Timeline (HiWaDi)

### Month 1: Foundation
- Implement waypoint diffusion model
- Implement world model
- Create initial 100-200 step tasks

### Month 2: Integration
- Integrate all components
- Implement state correction
- **GO/NO-GO Decision:** Need 10%+ improvement

### Month 3: Scaling & Baselines
- Create 500-800 step tasks
- Implement strong baselines (ChainedDiffuser, receding horizon)
- Collect initial results

### Month 4: Ablations & Analysis
- Complete ablation studies
- Error accumulation analysis
- Compute efficiency analysis

### Month 5: Additional Experiments
- 1000-step tasks (stretch goal)
- Theoretical analysis implementation
- Buffer for unexpected issues

### Month 6: Paper Writing
- First draft (week 21)
- Revision (week 22-23)
- Submission (week 24)

---

## 📈 Expected Results

### Success Metrics
- **Best Case (70%):** 15-25% improvement, 2-3× speedup → Strong Accept
- **Expected Case (20%):** 5-15% improvement → Revise & Resubmit
- **Worst Case (10%):** <5% improvement → Pivot to Solution 2

### Key Contributions
1. Novel hierarchical architecture (diffusion + world model)
2. Theoretical error analysis (O(k·h²) bound)
3. Benchmark on 6 long-horizon tasks (500-1000 steps)
4. State correction mechanism for robustness

---

## 🔑 Critical Success Factors

### Must-Haves
- ✅ Strong baselines (especially receding horizon diffusion policy)
- ✅ Genuinely long-horizon tasks (500+ steps minimum)
- ✅ Theoretical error analysis
- ✅ Clear positioning vs. ChainedDiffuser

### Nice-to-Haves
- 1000+ step tasks showing scaling
- Real-world validation (if opportunity arises)
- Connection to LLM planning (leveraging your background)

---

## ⚠️ Key Risks & Mitigations

| Risk | Probability | Impact | Mitigation |
|------|-------------|--------|------------|
| Baselines too strong | Medium | High | Focus on compute efficiency, scale to 1000+ steps |
| Waypoint ID is arbitrary | Medium | Medium | Try multiple methods, ablation study |
| World model still drifts | Medium | High | Reduce spacing, improve architecture |
| Novelty concerns | Medium | Critical | Strong positioning, include ChainedDiffuser baseline |

---

## 📚 Key Papers to Know

### Must Read
1. **Diffusion Policy** (Chi et al., IJRR 2024) - Foundation
2. **ChainedDiffuser** (CoRL 2023) - Main prior work to differentiate from
3. **Hierarchical Diffusion Policy** (IEEE TRO 2025) - Related hierarchical approach
4. **IRASim** (ICCV 2025) - Recent world model work
5. **Diff-DAgger** (Oct 2024) - Uncertainty in diffusion policies

### Good to Know
- PIVOT-R (NeurIPS 2024) - Waypoint-aware world model
- VidMan (NeurIPS 2024) - Video diffusion for manipulation
- SkillDiffuser (CVPR 2024) - Hierarchical skills
- Dreamer-V3 - Model-based RL baseline

---

## 🛠️ Code Repositories to Use

1. **Diffusion Policy:** https://github.com/real-stanford/diffusion_policy
2. **Dreamer-V3:** https://github.com/danijar/dreamerv3
3. **Isaac Gym Envs:** https://github.com/NVIDIA-Omniverse/IsaacGymEnvs
4. **Stable-Baselines3:** https://github.com/DLR-RM/stable-baselines3

---

## 💰 Resource Requirements

- **Compute:** 2-3 A100 GPUs for 3-4 months (~5000-10000 GPU-hours)
- **Cost:** $5-10K on cloud (or use university cluster)
- **Data:** 100-500 demonstrations per task
- **Time:** 6 months (3 months implementation + 2 months experiments + 1 month writing)

---

## 🎓 Estimated Publication Outcome

**CoRL 2026 Accept Probability:** 60-70% (with recommended improvements)

**Fallback Options:**
- ICRA 2026 (if CoRL rejects, broader audience)
- RSS 2025 Workshop on Structured World Models
- ArXiv preprint + iterate for future conference

---

## 📁 Document Structure

This research package includes 4 detailed documents:

1. **step1_research_gaps_analysis.md**
   - Survey of 2024-2025 papers
   - 5 ranked research gaps with detailed analysis
   - Justification for Gap #1 selection

2. **step2_solution_approaches.md**
   - 3 distinct solution approaches
   - Technical details, novelty analysis, experimental plans
   - Feasibility assessments

3. **step3_critical_review.md**
   - CoRL reviewer perspective on each solution
   - Prior work checks, weaknesses, suggested improvements
   - Accept/Revise/Reject verdicts with concrete paths forward

4. **step4_detailed_roadmap.md**
   - Complete paper outline (8 pages, 7 figures)
   - 6-month week-by-week implementation plan
   - Code repositories, pitfalls, contingency plans

---

## 🚀 Next Steps

### Immediate (Week 1)
1. Read ChainedDiffuser paper thoroughly (main prior work)
2. Set up Isaac Gym environment
3. Implement simple waypoint identification on toy task
4. Verify compute resources (2-3 A100 GPUs)

### Short-term (Month 1)
1. Implement waypoint diffusion model
2. Implement world model
3. Create 2-3 simple long-horizon tasks (100-200 steps)
4. Collect initial demonstrations

### Mid-term (Month 2-3)
1. Integrate all components
2. Run initial experiments
3. **Critical GO/NO-GO decision** based on 10%+ improvement threshold

---

## 💪 Why This Will Succeed

1. ✅ **Clear Gap:** Error accumulation in long-horizon prediction is a real, unsolved problem
2. ✅ **Your Strengths:** Perfect match for your expertise (LLMs, world models, diffusion)
3. ✅ **Feasibility:** Proven components, simulation-based validation
4. ✅ **Novelty:** First to combine waypoint diffusion with world models for error control
5. ✅ **Impact:** Enables reliable long-horizon manipulation (critical for deployment)
6. ✅ **Timeline:** 6 months is realistic with built-in buffer
7. ✅ **Contingency:** Clear pivot plans if experiments don't work

---

## 📞 Final Advice

**Be brutally honest with yourself:**
- After 2 months, if improvement <10% → debug or pivot
- After 4 months, if improvement <15% → consider reframing or Solution 2
- Don't chase a dead end → pivoting early is better than weak paper

**Focus on story:**
- "Error-aware waypoint planning" is more compelling than "hierarchical diffusion"
- Emphasize practical impact (enables 500+ step tasks)
- Position as Pareto improvement (accuracy + efficiency)

**Work smart:**
- Use existing codebases (don't reinvent wheel)
- Start simple, add complexity incrementally
- Strong baselines are critical (especially receding horizon)

---

**Good luck! This is a solid research opportunity with high probability of success.** 🎯

---

*Generated by Claude for CoRL 2026 research planning*
*All documents are research proposals - implementation and validation required*
