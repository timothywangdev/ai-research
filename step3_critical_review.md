# Step 3: Critical Review (CoRL Reviewer Perspective)

**Reviewer Stance:** Skeptical, looking for novelty, rigor, and practical impact
**Date:** 2025-11-12

---

## Solution 1: Hierarchical Waypoint Diffusion with World Model Interpolation (HiWaDi)

### Prior Work Check ⚠️

**Closely Related Work:**
1. **ChainedDiffuser (CoRL 2023):** Already combines trajectory diffusion with keypose prediction
   - *Difference:* ChainedDiffuser generates dense trajectories, doesn't use world model between keyposes

2. **SkillDiffuser (CVPR 2024):** Hierarchical planning via skill abstractions in diffusion
   - *Difference:* Skills are pre-defined primitives, not learned waypoints for error control

3. **Hierarchical Diffusion Policy (IEEE TRO 2025):** Uses contact points for hierarchical guidance
   - *Difference:* Contact points are task-specific, not for general error accumulation

**Novelty Assessment:** ⚠️ Moderate concern - the waypoint + diffusion combination exists, need to clearly differentiate error control motivation

### Critical Weaknesses

**1. Waypoint Identification is Ill-Posed**
- ❌ What makes a "good" waypoint? Curvature in state space? Value gradients? Task-dependent?
- ❌ Different tasks may need different waypoint densities (precision tasks vs. coarse)
- ❌ No theoretical guarantee that waypoints reduce error accumulation
- **Reviewer Question:** "How do you ensure waypoints are semantically meaningful and not just arbitrary temporal discretization?"

**2. World Model May Still Drift Between Waypoints**
- ❌ If horizon between waypoints is 20 steps, error can still accumulate within that segment
- ❌ What if the world model is poor at specific transitions (e.g., contact moments)?
- ❌ Waypoint "correction" assumes reaching exact waypoint state, but world model error means you never reach it
- **Reviewer Question:** "What happens when the actual state deviates from predicted waypoint? Does the system recover?"

**3. Computational Cost Not Clearly Better**
- ❌ Need to run diffusion model k times (for k waypoints) PLUS world model rollouts
- ❌ May be slower than just running diffusion policy densely with receding horizon
- ❌ No analysis of compute-performance tradeoff
- **Reviewer Question:** "Why not just run diffusion policy with shorter horizons and replan frequently?"

**4. Experimental Design Concerns**
- ❌ MetaWorld tasks are only 50-200 steps - not clear this qualifies as "long-horizon"
- ❌ Baselines missing: simple receding horizon MPC with diffusion policy
- ❌ Ablation on waypoint identification method may show it's arbitrary
- **Reviewer Question:** "Can you show this works on 500+ step tasks? Otherwise, why not simpler solutions?"

### Strengths

✅ Clear motivation (error accumulation is real problem)
✅ Combines two powerful paradigms (diffusion + world models)
✅ Feasible implementation
✅ Good ablation plan

### Suggested Improvements

1. **Add theoretical analysis:** Prove error bound improvement O(T²) → O(k·h²) under assumptions
2. **Benchmark on genuinely long tasks:** 500-1000+ steps, multi-room navigation + manipulation
3. **Add "waypoint-free" baseline:** Learned temporal abstraction (e.g., via RL) to show waypoints aren't arbitrary
4. **State correction mechanism:** Add explicit state re-calibration when reaching waypoints
5. **Stronger differentiation from ChainedDiffuser:** Position as "error-aware keypose selection" vs. fixed keypose

### Verdict: **REVISE** ⚠️

**Rating:** 6/10 (Weak Accept with major revisions)

**Justification:**
- Problem is important and timely
- Approach has merit but novelty is incremental over ChainedDiffuser
- Needs stronger theoretical grounding and differentiation from prior work
- Experimental design needs longer horizons to be convincing

**Path to Accept:**
- Add theoretical error analysis
- Show 500+ step tasks where this clearly wins
- Clarify novelty over ChainedDiffuser in intro/related work
- Add state correction mechanism

---

## Solution 2: Uncertainty-Aware World Model with Adaptive Replanning (UWMAR)

### Prior Work Check ✅

**Related Work:**
1. **Diff-DAgger (Oct 2024):** Uses uncertainty for data collection, not planning
   - *Clear Difference:* Your approach uses uncertainty for adaptive replanning

2. **TAMPURA (March 2024):** Replanning under uncertainty for TAMP
   - *Difference:* High-level task planning, not low-level world model rollouts

3. **Model-Based RL with Ensembles:** Typically pessimistic planning, fixed horizon
   - *Difference:* Adaptive horizon based on cumulative uncertainty

**Novelty Assessment:** ✅ Strong - this specific combination appears novel

### Critical Weaknesses

**1. Uncertainty Calibration is Hard**
- ❌ Ensemble disagreement ≠ true prediction error (Diff-DAgger paper shows this!)
- ❌ Model may be confidently wrong (overconfident predictions)
- ❌ Calibration requires extensive validation data (expensive in robotics)
- **Reviewer Question:** "How do you ensure uncertainty estimates are calibrated? What if the model is confidently wrong?"

**2. Threshold Learning is Unstable**
- ❌ RL over threshold policy adds another layer of complexity
- ❌ Reward function λ·(num_replans) is arbitrary - how to set λ?
- ❌ May oscillate: threshold too low → constant replanning, too high → never replan
- ❌ Threshold may need to be task-dependent
- **Reviewer Question:** "Why not just use fixed conservative threshold? Is learned threshold worth the complexity?"

**3. Diffusion Policy as "Safety Net" is Expensive**
- ❌ If uncertainty triggers often, you're essentially running diffusion policy (defeats purpose)
- ❌ Diffusion inference is slow (~20-100 steps), may not be practical for real-time control
- ❌ No analysis of compute-accuracy tradeoff
- **Reviewer Question:** "What's the average replanning frequency? If it's high, why use world model at all?"

**4. Distribution Shift Experiments May Not Transfer**
- ❌ Mass/friction changes are "easy" uncertainty - model knows it doesn't know
- ❌ Real failures are often structured errors the model doesn't recognize (e.g., wrong contact model)
- ❌ Adversarial perturbations in sim don't reflect real-world deployment
- **Reviewer Question:** "Can you show this works on real distribution shifts like sim-to-real, not just artificial perturbations?"

### Strengths

✅ Novel combination of techniques
✅ Addresses practical concern (when to trust model)
✅ Clear calibration metrics
✅ Good experimental design with distribution shift tasks

### Suggested Improvements

1. **Use conformal prediction:** Provides distribution-free uncertainty calibration
2. **Simple threshold first:** Show learned threshold is necessary via comparison with fixed threshold
3. **Compute budget analysis:** Plot Pareto frontier of compute vs. success rate
4. **Real sim-to-real experiment:** Even in simulation, train on one set of physics params, test on another
5. **Failure mode analysis:** What types of errors does uncertainty miss? When is it overconfident?

### Verdict: **REVISE** ⚠️

**Rating:** 5.5/10 (Borderline - needs substantial improvements)

**Justification:**
- Uncertainty calibration is a known hard problem
- May be overly complex (learned threshold, RL over thresholds)
- Compute efficiency unclear - may not be practical
- Risk: method works in principle but calibration issues kill it

**Path to Accept:**
- Demonstrate well-calibrated uncertainty (conformal prediction or extensive validation)
- Simplify: use fixed threshold, show it works well
- Add compute efficiency analysis (critical for practical adoption)
- Show this works on real distribution shift, not just artificial perturbations

---

## Solution 3: Physics-Informed World Model with Differentiable Simulator Correction (PIWS)

### Prior Work Check ❌ **MAJOR CONCERN**

**Very Similar Work:**
1. **"Sim-to-Real of Soft Robots with Learned Residual Physics" (2024):** Combines numerical solvers with deep learning for residuals
   - *Identical Concept:* Physics simulator + learned residual
   - *Difference:* They focus on soft robots, you focus on manipulation - weak differentiation

2. **PINNs for Robotics (Various 2024 papers):** Physics-informed NNs for modeling/control
   - *Overlap:* Using physics knowledge to inform learned models

3. **Differentiable Simulators (2024 reviews):** Well-established field
   - *Concern:* Your contribution is incremental - applying existing technique to manipulation

**Novelty Assessment:** ❌ Weak - very similar work exists, differentiation is insufficient

### Critical Weaknesses

**1. Novelty is Questionable**
- ❌ Learned residuals on physics simulators is not new (2024 soft robotics paper)
- ❌ Differentiable simulators for robotics is well-studied
- ❌ What is the core contribution beyond "apply existing technique to manipulation"?
- **Reviewer Question:** "What is novel here? This seems like a direct application of existing methods."

**2. Physics Simulator May Be Wrong Structure**
- ❌ If physics model is fundamentally wrong (e.g., wrong contact model), residual can't fix it
- ❌ Residual may need to be large, defeating the purpose
- ❌ For deformable objects, physics simulator itself is poor (can't learn residual on bad base)
- **Reviewer Question:** "When does this fail? If physics is very wrong, can residual even help?"

**3. Differentiable Simulator Limitations**
- ❌ Isaac Gym has limited differentiability (not all features supported)
- ❌ MuJoCo JAX exists but less mature than standard MuJoCo
- ❌ May not support complex contact scenarios (friction, deformation)
- **Reviewer Question:** "Can your differentiable simulator actually handle the contact-rich tasks you propose?"

**4. Error Accumulation Still Exists**
- ❌ Even with physics + residual, error accumulates (just slower)
- ❌ No mechanism to reset/correct error over long horizons
- ❌ May only delay the problem, not solve it
- **Reviewer Question:** "You claim bounded error, but do you have theoretical guarantees? Or just empirical observation?"

**5. Experimental Claims Are Weak**
- ❌ Contact-rich manipulation (peg insertion) is well-studied, not novel testbed
- ❌ IKEA assembly is ambitious but likely infeasible in 6 months
- ❌ Comparing to "pure physics" is not a strong baseline (everyone knows physics parameters need tuning)
- **Reviewer Question:** "What's the value over system ID or domain randomization, which are simpler and proven?"

### Strengths

✅ Physically-grounded approach (interpretable)
✅ Residual magnitude is a good diagnostic metric
✅ Could be sample efficient (physics provides strong prior)

### Suggested Improvements

1. **Find truly novel angle:** What can you do with residuals that system ID can't?
2. **Theoretical analysis:** When do residuals help vs. hurt? Derive conditions.
3. **Active learning:** Use residual magnitude to guide data collection (this could be novel)
4. **Compositional generalization:** Show physics prior enables zero-shot transfer to new objects
5. **Compare to sim-to-real methods:** Domain randomization, domain adaptation, system ID

### Verdict: **REJECT** ❌

**Rating:** 4/10 (Reject - insufficient novelty)

**Justification:**
- 2024 soft robotics paper does essentially the same thing
- Novelty over existing work is unclear
- Application to manipulation is not sufficient contribution
- Multiple technical risks with differentiable simulators

**Path to Accept (requires major pivot):**
- Find novel angle: e.g., "physics-guided active learning for world models"
- Strong comparison to sim-to-real baseline methods
- Theoretical contribution: when/why residuals help
- Demonstrate something system ID or domain randomization can't do

---

## Overall Ranking

### 🥇 Best Choice: Solution 1 (HiWaDi)
**Verdict:** REVISE (6/10)
- **Pros:** Clear motivation, feasible, good fit for your skills
- **Cons:** Moderate novelty, needs differentiation from ChainedDiffuser
- **Path Forward:** Add theory, longer tasks, state correction
- **Risk Level:** ⭐⭐ (Low-Medium)

### 🥈 Second Choice: Solution 2 (UWMAR)
**Verdict:** REVISE (5.5/10)
- **Pros:** Novel combination, addresses practical problem
- **Cons:** Uncertainty calibration is hard, may be overly complex
- **Path Forward:** Simplify, prove calibration works, compute efficiency analysis
- **Risk Level:** ⭐⭐⭐⭐ (Medium-High)

### 🥉 Not Recommended: Solution 3 (PIWS)
**Verdict:** REJECT (4/10)
- **Pros:** Physically grounded, interpretable
- **Cons:** 2024 soft robotics paper is too similar, insufficient novelty
- **Path Forward:** Major pivot needed (e.g., active learning angle)
- **Risk Level:** ⭐⭐⭐⭐⭐ (High - may not be publishable as-is)

---

## Final Recommendation

**Pursue Solution 1 (HiWaDi) with following modifications:**

1. ✅ **Add Theoretical Error Analysis**
   - Prove error bound: E[||s_T - ŝ_T||] ≤ O(k·h²) vs. O(T²) for pure world model
   - Show conditions under which waypoints reduce error accumulation

2. ✅ **Genuinely Long-Horizon Tasks (500-1000 steps)**
   - Multi-room navigation + manipulation in Isaac Gym
   - Sequential tool use with 5+ tools
   - Bimanual assembly tasks

3. ✅ **State Correction Mechanism**
   - When reaching waypoint, "snap" to nearest valid state
   - Use diffusion model to generate correction if deviation is large

4. ✅ **Stronger Baselines**
   - Receding horizon diffusion policy (most important!)
   - ChainedDiffuser adapted to your tasks
   - Learned temporal abstraction (to show waypoints aren't arbitrary)

5. ✅ **Clear Positioning vs. ChainedDiffuser**
   - ChainedDiffuser: fixed keyposes, no world model
   - HiWaDi: error-aware waypoint selection, world model for efficiency

**Estimated Accept Probability with Improvements:** 70-80%

**If Solution 1 Doesn't Pan Out:** Pivot to Solution 2, but simplify (fixed threshold, focus on calibration)

---

## Next Steps

1. Validate theoretical error analysis is tractable
2. Implement HiWaDi prototype (4 weeks)
3. Run initial experiments on 200-step MetaWorld tasks
4. If promising, scale to 500+ step tasks
5. If not, pivot to simplified Solution 2

**Critical Go/No-Go Decision Point:** After 2 months, if HiWaDi isn't showing 20%+ improvement over baselines on 200-step tasks, pivot to Solution 2 or reconsider problem altogether.
