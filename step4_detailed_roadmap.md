# Step 4: Detailed Roadmap for HiWaDi

**Project:** Hierarchical Waypoint Diffusion with World Model Interpolation
**Timeline:** 6 months (implementation + experiments + writing)
**Target:** CoRL 2026 submission

---

## Paper Outline

### Title Options
1. **"HiWaDi: Hierarchical Waypoint Diffusion for Error-Bounded Long-Horizon Manipulation"**
2. **"Error-Aware Waypoint Planning: Combining Diffusion Models with World Models for Long-Horizon Manipulation"**
3. **"Waypoints as Error Checkpoints: Hierarchical Diffusion for Robust Long-Horizon World Models"**

**Recommended:** Option 1 (concise, memorable acronym)

---

### Abstract (150-200 words)

**Structure:**
1. **Problem:** Long-horizon manipulation requires predicting 100+ steps, but world models accumulate error quadratically
2. **Gap:** Existing methods use either dense diffusion policies (slow) or autoregressive world models (inaccurate)
3. **Solution:** HiWaDi learns sparse waypoints via diffusion, uses world model for short interpolations
4. **Key Insight:** Waypoints act as error correction checkpoints, reducing accumulation from O(T²) to O(k·h²)
5. **Results:** X% improvement on 500-step tasks, Y% faster than dense diffusion
6. **Impact:** Enables reliable long-horizon planning in manipulation

---

### 1. Introduction (1.5 pages)

**Paragraph Structure:**
1. **Motivation:** Manipulation requires long-horizon planning (examples: assembly, cooking, cleaning)
2. **Challenge:** Two paradigms have complementary weaknesses
   - Diffusion policies: accurate but slow (100 denoising steps per action)
   - World models: fast but accumulate error over time
3. **Key Observation:** Not all timesteps are equal - some states are "stable" (waypoints)
4. **Our Approach:** Learn hierarchical decomposition
   - Diffusion generates waypoints (where to checkpoint)
   - World model interpolates between waypoints (fast rollout)
5. **Contributions:**
   - Novel hierarchical architecture combining diffusion + world models
   - Theoretical error analysis showing O(k·h²) bound
   - Benchmark of 6 long-horizon tasks (500-1000 steps)
   - State correction mechanism for robustness

**Key Figure: Figure 1 - Teaser**
- Top: Pure world model (100 steps) → large error accumulation → failure
- Middle: Pure diffusion policy → slow inference (100 denoising steps per action)
- Bottom: HiWaDi → waypoints at steps 0, 20, 40, 60, 80, 100 → bounded error, fast

---

### 2. Related Work (1.5 pages)

**Subsections:**

**2.1 World Models for Robot Manipulation**
- Dreamer-V3, PIVOT-R, IRASim, FOCUS
- **Gap:** Error accumulation in long-horizon tasks

**2.2 Diffusion Models for Robotics**
- Diffusion Policy (Chi et al. 2024)
- **Gap:** Slow inference, no world model

**2.3 Hierarchical Planning**
- SkillDiffuser (CVPR 2024): skill abstractions
- ChainedDiffuser (CoRL 2023): trajectory + keypose
- Hierarchical Diffusion Policy (TRO 2025): contact guidance
- **Gap:** Not designed for error control in world models

**2.4 Positioning:**
- Unlike ChainedDiffuser (fixed keyposes), we learn error-aware waypoints
- Unlike hierarchical RL (HIRO, HAC), we use diffusion for waypoint generation
- Unlike model-free methods, we leverage world model for efficiency

---

### 3. Preliminaries (0.5 pages)

**3.1 Problem Setup**
- State space S, action space A
- Task: reach goal g from initial state s_0 in T steps
- Demonstrations: D = {(s_0, a_0, ..., s_T, a_T)^(i)}

**3.2 Diffusion Policy (brief recap)**
- p_θ(a_{t:t+H} | s_t, g) via denoising process

**3.3 World Models (brief recap)**
- ŝ_{t+1} = f_φ(s_t, a_t)

---

### 4. Method (3 pages)

**4.1 Overview**
- Architecture diagram (Figure 2)
- High-level diffusion generates waypoints
- World model interpolates between waypoints
- State correction at waypoints

**4.2 Waypoint Diffusion Model**
- Input: s_0, g, desired num_waypoints k
- Output: waypoint trajectory τ_w = {s_w1, ..., s_wk}
- Architecture: Transformer-based diffusion (U-Net on state sequences)
- Training: supervised on demonstrated waypoints (identified via curvature)

**4.3 World Model Interpolation**
- Between consecutive waypoints w_i and w_{i+1}
- Rollout: ŝ_t+1 = f_φ(ŝ_t, π(ŝ_t, w_{i+1}))
- Low-level policy: π(s, s_goal) = simple goal-conditioned BC
- Maximum horizon: h_max = 20 steps

**4.4 State Correction Mechanism**
- At waypoint: measure deviation ||s_actual - s_waypoint||
- If deviation > threshold: trigger diffusion policy to correct
- Else: continue with world model

**4.5 Training Procedure**
1. **Phase 1:** Identify waypoints in demonstrations
   - Use state space curvature: high curvature = waypoint
   - Or use value function gradients (requires critic)
2. **Phase 2:** Train waypoint diffusion model
   - Input: (s_0, g, k), Output: τ_w
   - Loss: L_waypoint = Σ ||s_wi - s*_wi||²
3. **Phase 3:** Train world model on short segments
   - Sample segments between waypoints from demos
   - Loss: L_world = Σ ||ŝ_t+1 - s_t+1||²
4. **Phase 4:** Train low-level policy
   - Goal-conditioned BC: (s_t, w_{i+1}) → a_t
5. **Phase 5 (optional):** Fine-tune end-to-end with model-based RL

**Key Figure: Figure 2 - Architecture**
- Flowchart: s_0, g → Waypoint Diffusion → {w1, ..., wk}
- For each segment: World Model + Low-level Policy → actions
- State Correction: if deviation > threshold, trigger Diffusion Policy

---

### 5. Theoretical Analysis (1.5 pages)

**5.1 Error Accumulation in Pure World Models**
- Theorem 1: Pure world model error ≤ O(T²) under Lipschitz assumptions
- Proof sketch: error compounds at each step

**5.2 Error Reduction with Waypoints**
- Theorem 2: HiWaDi error ≤ O(k·h²) where k waypoints, h=max segment length
- Proof: Error resets at each waypoint, only accumulates within segments
- Corollary: With h=T/k, error reduced from O(T²) to O(T²/k)

**5.3 Optimal Waypoint Spacing**
- Trade-off: more waypoints → less error, but slower (more diffusion inference)
- Optimal k* = argmin [error(k) + λ·compute(k)]

**Key Figure: Figure 3 - Theoretical Error Bounds**
- X-axis: horizon T, Y-axis: prediction error
- Lines: Pure WM (O(T²)), HiWaDi k=5 (O(T²/5)), HiWaDi k=10 (O(T²/10))

---

### 6. Experiments (4 pages)

**6.1 Experimental Setup**
- Environments: MetaWorld, Isaac Gym
- Tasks: 6 long-horizon tasks (500-1000 steps)
- Baselines: 5 methods
- Metrics: success rate, prediction error, compute time

**6.2 Long-Horizon Manipulation Tasks**

**Table 1: Task Descriptions**
| Task | Steps | Description | Key Challenges |
|------|-------|-------------|----------------|
| Multi-Stage Assembly | 500 | 5-part assembly | Precision, error accumulation |
| Sequential Tool Use | 600 | Hammer → Screwdriver → Wrench | Tool switching, long dependencies |
| Bimanual Cloth Folding | 800 | Fold cloth into square | Deformable object, coordination |
| Multi-Room Rearrangement | 1000 | Move objects across rooms | Navigation + manipulation |

**6.3 Main Results**

**Table 2: Success Rate Comparison**
| Method | Assembly | Tool Use | Cloth | Rearrange | Avg |
|--------|----------|----------|-------|-----------|-----|
| Pure Diffusion | X% | X% | X% | X% | X% |
| Pure WM + MPC | X% | X% | X% | X% | X% |
| ChainedDiffuser | X% | X% | X% | X% | X% |
| VidMan | X% | X% | X% | X% | X% |
| **HiWaDi (Ours)** | **X%** | **X%** | **X%** | **X%** | **X%** |

**Key Figure: Figure 4 - Success Rate vs. Task Horizon**
- X-axis: task length (100, 200, 500, 1000 steps)
- Y-axis: success rate
- Lines: all methods (show HiWaDi scales better)

**6.4 Error Accumulation Analysis**

**Key Figure: Figure 5 - Prediction Error Over Time**
- X-axis: timestep (0-500)
- Y-axis: MSE between predicted and actual state
- Lines: Pure WM (exponential), HiWaDi (sawtooth - resets at waypoints)

**6.5 Computational Efficiency**

**Table 3: Inference Time**
| Method | Avg Rollout Time (500 steps) | Speedup |
|--------|-------------------------------|---------|
| Pure Diffusion | X sec | 1.0x |
| HiWaDi (k=5) | X sec | Xx |
| HiWaDi (k=10) | X sec | Xx |

**Key Figure: Figure 6 - Pareto Frontier**
- X-axis: inference time
- Y-axis: success rate
- Points: different methods (show HiWaDi dominates)

**6.6 Ablation Studies**

**Table 4: Ablation on Key Components**
| Variant | Success Rate | Notes |
|---------|--------------|-------|
| HiWaDi (full) | X% | - |
| - No state correction | X% | -Y% |
| - Fixed waypoints | X% | -Y% |
| - Dense waypoints (k=20) | X% | +compute |
| - Sparse waypoints (k=3) | X% | -accuracy |

**6.7 Qualitative Analysis**

**Key Figure: Figure 7 - Learned Waypoints**
- Visualization of where waypoints occur in state space
- Show they align with task structure (e.g., after grasping, after placing)

**6.8 Failure Modes**
- When does HiWaDi fail?
- Analysis: world model drifts too much between waypoints on specific tasks

---

### 7. Discussion (0.5 pages)

**Limitations:**
- Requires waypoint labels or identification method (not always obvious)
- World model still needs sufficient data
- State correction adds overhead

**Future Work:**
- Learn waypoint spacing dynamically per task
- Combine with uncertainty estimation (hybrid with UWMAR)
- Extend to multi-task setting (shared waypoint diffusion)

---

### 8. Conclusion (0.5 pages)

**Summary:**
- Presented HiWaDi: hierarchical waypoint diffusion with world models
- Reduces error accumulation from O(T²) to O(k·h²)
- Achieves X% improvement on 500-1000 step tasks
- Y× faster than dense diffusion policy

**Impact:**
- Enables reliable long-horizon manipulation
- Combines strengths of diffusion (accuracy) and world models (efficiency)

---

## Key Figures Summary

1. **Figure 1:** Teaser (comparison of pure WM, pure diffusion, HiWaDi)
2. **Figure 2:** Architecture diagram
3. **Figure 3:** Theoretical error bounds
4. **Figure 4:** Success rate vs. task horizon
5. **Figure 5:** Prediction error over time (sawtooth pattern)
6. **Figure 6:** Pareto frontier (success vs. compute)
7. **Figure 7:** Learned waypoint visualization

**Total:** 7 figures (good for 8-page CoRL paper)

---

## 6-Month Implementation Plan

### Month 1: Foundation (Weeks 1-4)

**Week 1: Environment Setup**
- ✅ Set up Isaac Gym environment
- ✅ Install MuJoCo
- ✅ Create 2-3 simple long-horizon tasks (100-200 steps)
- ✅ Collect 100 expert demonstrations per task

**Week 2-3: Waypoint Diffusion Model**
- ✅ Implement waypoint identification (state space curvature method)
- ✅ Implement U-Net or Transformer-based diffusion model for waypoints
- ✅ Train on simple tasks, verify waypoints are reasonable
- ✅ Sanity check: waypoints should occur at task transitions

**Week 4: World Model**
- ✅ Implement world model (transformer or MLP)
- ✅ Train on short segments (10-20 steps) between waypoints
- ✅ Evaluate prediction accuracy on held-out data
- ✅ Sanity check: should achieve <5% state error at 20 steps

**Deliverable:** Working prototype of waypoint diffusion + world model (not integrated yet)

---

### Month 2: Integration & Initial Experiments (Weeks 5-8)

**Week 5: Low-Level Policy & Integration**
- ✅ Implement goal-conditioned policy (BC to reach waypoints)
- ✅ Integrate all components: waypoint diffusion → world model → low-level policy
- ✅ Test on simple 100-step tasks
- ✅ Debug: likely issues with waypoint reaching

**Week 6: State Correction Mechanism**
- ✅ Implement deviation detection at waypoints
- ✅ Implement diffusion-based correction when deviation too large
- ✅ Tune threshold via grid search
- ✅ Verify: correction triggers appropriately

**Week 7-8: Initial Experiments**
- ✅ Run HiWaDi on 3 tasks (100-200 steps)
- ✅ Implement 2 baselines: pure diffusion, pure world model MPC
- ✅ Collect results: success rate, error accumulation
- ✅ **GO/NO-GO DECISION:** If success rate improvement <10%, debug or pivot

**Deliverable:** End-to-end system working on simple tasks, initial results

---

### Month 3: Scaling & Baseline Implementation (Weeks 9-12)

**Week 9: Scale to Long-Horizon Tasks**
- ✅ Create 3 tasks with 500-800 steps in Isaac Gym
  - Multi-stage assembly (pick → place → insert → rotate → screw)
  - Sequential tool use (3-4 tools)
  - Bimanual coordination (fold cloth)
- ✅ Collect 200-500 demonstrations per task
- ✅ Train HiWaDi on these tasks (may take several days)

**Week 10-11: Implement Strong Baselines**
- ✅ ChainedDiffuser (adapt to your tasks)
- ✅ Receding Horizon Diffusion Policy (critical baseline!)
- ✅ VidMan (if feasible, or cite paper results)
- ✅ Hierarchical RL (HAC or HIRO)

**Week 12: Run Baselines & Collect Results**
- ✅ Run all baselines on all tasks
- ✅ Collect metrics: success rate, prediction error, compute time
- ✅ Initial analysis: where does HiWaDi win/lose?

**Deliverable:** Results on 500-800 step tasks, comparison with strong baselines

---

### Month 4: Ablations & Analysis (Weeks 13-16)

**Week 13: Ablation Experiments**
- ✅ Ablate state correction mechanism
- ✅ Ablate waypoint identification method (curvature vs. random)
- ✅ Ablate number of waypoints (k=3, 5, 10, 20)
- ✅ Collect all ablation results

**Week 14: Error Accumulation Analysis**
- ✅ Implement error tracking over time
- ✅ Generate sawtooth error plot (Figure 5)
- ✅ Verify theoretical predictions (O(k·h²) scaling)
- ✅ Analyze: where does world model drift most?

**Week 15: Compute Efficiency Analysis**
- ✅ Profile inference time for all methods
- ✅ Generate Pareto frontier plot (Figure 6)
- ✅ Measure: num diffusion calls, world model rollout time
- ✅ Optimize: any obvious bottlenecks?

**Week 16: Qualitative Analysis**
- ✅ Visualize learned waypoints (Figure 7)
- ✅ Analyze failure modes
- ✅ Record videos of successful/failed rollouts
- ✅ Prepare supplementary material

**Deliverable:** Complete experimental results, all figures/tables

---

### Month 5: Additional Experiments & Refinement (Weeks 17-20)

**Week 17: 1000-Step Tasks (Stretch Goal)**
- ✅ Create 1-2 very long tasks (1000+ steps)
  - Multi-room rearrangement
  - Complex assembly with 8+ parts
- ✅ Run HiWaDi and best baseline (likely receding horizon)
- ✅ Show scaling: HiWaDi maintains performance, baselines degrade

**Week 18: Theoretical Analysis Implementation**
- ✅ Implement error bound calculations
- ✅ Generate theoretical plot (Figure 3)
- ✅ Verify: empirical results match theory
- ✅ Write up proofs (if not already done)

**Week 19-20: Buffer & Refinement**
- ✅ Re-run any failed experiments
- ✅ Add any missing ablations
- ✅ Improve visualizations
- ✅ Collect additional data if needed
- ✅ **CRITICAL:** Leave time for unexpected issues!

**Deliverable:** All experiments complete, ready for paper writing

---

### Month 6: Paper Writing & Submission (Weeks 21-24)

**Week 21: First Draft**
- ✅ Write introduction, related work, method
- ✅ Fill in results tables/figures
- ✅ Write preliminary discussion/conclusion
- ✅ Internal review: check for gaps

**Week 22: Revision**
- ✅ Refine method section (ensure clarity)
- ✅ Improve figures (make them publication-quality)
- ✅ Add missing details (hyperparameters, compute resources)
- ✅ Write supplementary material

**Week 23: Finalization**
- ✅ Proofread entire paper
- ✅ Check references (ensure all related work cited)
- ✅ Prepare video for supplementary
- ✅ Internal review #2: simulate reviewer comments

**Week 24: Submission**
- ✅ Final polishing
- ✅ Format for CoRL (use LaTeX template)
- ✅ Submit to arXiv (optional, recommended)
- ✅ Submit to CoRL 2026
- ✅ Celebrate! 🎉

**Deliverable:** Submitted paper to CoRL 2026

---

## Code Repositories to Build On

### 1. Diffusion Policy (Chi et al.)
**Repo:** https://github.com/real-stanford/diffusion_policy
- **Use:** Diffusion model architecture, training loop
- **Adapt:** Modify to output waypoints instead of dense actions
- **License:** MIT (check latest)

### 2. Dreamer-V3
**Repo:** https://github.com/danijar/dreamerv3
- **Use:** World model architecture (RSSM), training
- **Adapt:** Simplify for state-based (not image-based) if needed
- **License:** MIT

### 3. Isaac Gym Environments
**Repo:** https://github.com/NVIDIA-Omniverse/IsaacGymEnvs
- **Use:** Base environments for manipulation tasks
- **Adapt:** Create custom long-horizon tasks
- **License:** BSD 3-Clause

### 4. Stable-Baselines3
**Repo:** https://github.com/DLR-RM/stable-baselines3
- **Use:** Goal-conditioned policy (HER), RL utilities
- **Adapt:** For low-level waypoint reaching policy
- **License:** MIT

### 5. ChainedDiffuser (if code available)
**Repo:** Search for CoRL 2023 paper code
- **Use:** As baseline comparison
- **Adapt:** Run on your tasks
- **Note:** May need to implement if code not released

---

## Potential Pitfalls & Mitigation Strategies

### Pitfall 1: Waypoint Identification is Arbitrary
**Symptom:** Learned waypoints don't align with task structure
**Mitigation:**
- ✅ Try multiple methods: curvature, value gradients, fixed intervals
- ✅ Visualize waypoints (Figure 7) to ensure they make sense
- ✅ Ablation: show learned waypoints > random waypoints
- ✅ Fallback: use task-specific waypoints (e.g., after grasping)

### Pitfall 2: World Model Drifts Between Waypoints
**Symptom:** Success rate doesn't improve over baselines
**Mitigation:**
- ✅ Reduce waypoint spacing (more frequent corrections)
- ✅ Improve world model architecture (add attention, GNN for objects)
- ✅ Add more training data for world model
- ✅ Implement better state correction mechanism

### Pitfall 3: State Correction Threshold is Hard to Tune
**Symptom:** Either corrects too often (slow) or too rarely (inaccurate)
**Mitigation:**
- ✅ Grid search over thresholds: [0.01, 0.05, 0.1, 0.5]
- ✅ Learn threshold via RL (like UWMAR approach)
- ✅ Use adaptive threshold based on task progress
- ✅ Ablation: show correction helps (Table 4)

### Pitfall 4: Baselines Are Too Strong
**Symptom:** Receding horizon diffusion policy achieves similar success rate
**Mitigation:**
- ✅ Focus on compute efficiency (HiWaDi should be faster)
- ✅ Scale to very long tasks (1000+ steps) where baselines degrade
- ✅ Add sample efficiency experiments (success vs. num demos)
- ✅ Position as "Pareto improvement" (similar accuracy, less compute)

### Pitfall 5: Tasks Are Too Easy
**Symptom:** All methods achieve >90% success rate
**Mitigation:**
- ✅ Increase task complexity (more objects, longer sequences)
- ✅ Add distribution shift (change object properties)
- ✅ Reduce training data (100 demos → 50 demos)
- ✅ Add perturbations during execution

### Pitfall 6: Theoretical Analysis is Too Weak
**Symptom:** Reviewers ask for stronger guarantees
**Mitigation:**
- ✅ Derive error bounds under Lipschitz assumptions
- ✅ Empirically verify theoretical predictions (Figure 3)
- ✅ Cite existing theory from model-based RL literature
- ✅ If stuck, downplay theory and focus on empirical results

### Pitfall 7: Novelty Over ChainedDiffuser is Insufficient
**Symptom:** Reviewers say "this is just ChainedDiffuser with world model"
**Mitigation:**
- ✅ Strong positioning in intro/related work
- ✅ Emphasize error control motivation (not just speed)
- ✅ Show learned waypoints adapt to task (Figure 7)
- ✅ Include ChainedDiffuser as baseline, show improvement

### Pitfall 8: Implementation Takes Longer Than Expected
**Symptom:** Month 2 arrives, system doesn't work end-to-end
**Mitigation:**
- ✅ Start with simplest possible version (fixed waypoints, simple WM)
- ✅ Incremental development: test each component separately
- ✅ Use existing codebases (don't reinvent wheel)
- ✅ **Critical:** Build in 2-week buffer in Month 5

---

## Risk Assessment & Contingency Plans

### Best Case (70% probability)
- ✅ HiWaDi shows 15-25% improvement on 500-step tasks
- ✅ 2-3× compute speedup over dense diffusion
- ✅ Strong paper, likely accept at CoRL

### Expected Case (20% probability)
- ⚠️ HiWaDi shows 5-15% improvement
- ⚠️ Compute savings less than expected
- ⚠️ Revise & resubmit, or accept at workshop

### Worst Case (10% probability)
- ❌ No significant improvement over baselines
- ❌ **Contingency:** Pivot to UWMAR (Solution 2) at Month 3
- ❌ Or: reframe as "efficiency" paper (same accuracy, less compute)

---

## Success Metrics (for Go/No-Go Decisions)

### After Month 2 (Initial Experiments)
- ✅ **GO:** Success rate improvement ≥10% on 200-step tasks
- ⚠️ **REVISE:** Improvement 5-10%, debug and continue
- ❌ **NO-GO:** Improvement <5%, consider pivot

### After Month 4 (Main Results)
- ✅ **GO:** Success rate improvement ≥15% on 500-step tasks
- ⚠️ **REVISE:** Improvement 10-15%, focus on efficiency/theory
- ❌ **NO-GO:** Improvement <10%, pivot to Solution 2 or reframe

### After Month 5 (Final Experiments)
- ✅ **STRONG PAPER:** Improvement ≥20%, compelling story
- ⚠️ **DECENT PAPER:** Improvement 10-20%, needs strong writing
- ❌ **WEAK PAPER:** Improvement <10%, consider workshop submission

---

## Collaboration & Resources

### Required Compute
- **Training:** 2× A100 GPUs (40GB each) for 2-3 months
- **Experiments:** 1× A100 GPU for 1-2 months
- **Total GPU-hours:** ~5000-10000 hours
- **Cost Estimate:** $5-10K on cloud (or use university cluster)

### Optional Collaborations
- **Theory:** Collaborate with someone on rigorous error analysis
- **Benchmarks:** Partner with lab that has real robots for validation
- **Baselines:** Reach out to ChainedDiffuser authors for code/advice

### Key Papers to Monitor
- Check arXiv weekly for new "world model" + "diffusion" papers
- Watch for CoRL 2025 accepted papers (October 2025) for latest trends
- Subscribe to: cs.RO, cs.LG, cs.AI on arXiv

---

## Final Checklist

### Before Starting (Week 0)
- [ ] Confirm compute resources (GPUs, storage)
- [ ] Set up code repository with version control
- [ ] Install dependencies (Isaac Gym, MuJoCo, PyTorch)
- [ ] Download Diffusion Policy and Dreamer-V3 codebases
- [ ] Set up experiment tracking (Weights & Biases or similar)

### Mid-Project (Month 3)
- [ ] Have end-to-end system working
- [ ] Initial results on 500-step tasks
- [ ] GO/NO-GO decision made
- [ ] Baselines implemented

### Before Submission (Month 6)
- [ ] All experiments complete
- [ ] Paper written and proofread
- [ ] Supplementary material prepared
- [ ] Code cleaned and ready for release (post-acceptance)

---

## Conclusion

This roadmap provides a detailed plan for implementing HiWaDi over 6 months. Key success factors:

1. ✅ **Clear milestones** with go/no-go decision points
2. ✅ **Realistic timeline** with 2-week buffer
3. ✅ **Strong baselines** especially receding horizon diffusion
4. ✅ **Compelling story** error control for long-horizon tasks
5. ✅ **Contingency plans** if experiments don't work out

**Estimated probability of CoRL accept:** 60-70% with proposed improvements

**Good luck! 🚀**
