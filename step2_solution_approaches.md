# Step 2: Solution Approaches for Error Accumulation in Long-Horizon World Models

**Research Gap:** Error Accumulation in Long-Horizon World Model Prediction
**Challenge:** Autoregressive world models accumulate error over 100+ timesteps, causing failure in multi-stage manipulation tasks

---

## Solution 1: Hierarchical Waypoint Diffusion with World Model Interpolation (HiWaDi)

### Core Technical Idea

**Two-Level Architecture:**
1. **High-Level:** Diffusion policy generates sparse waypoints (key states) at 10-20 timestep intervals
2. **Low-Level:** World model predicts transitions between consecutive waypoints (short horizon)

**Key Innovation:**
- Diffusion model learns to identify "stable states" where error can be reset
- World model only rolls out 10-20 steps before next waypoint correction
- Waypoints act as error correction checkpoints

**Mathematical Framework:**
```
τ = {s_0, s_w1, s_w2, ..., s_wk, s_goal}  # Waypoint trajectory
p_θ(τ | s_0, g) ~ Diffusion(s_0, g)        # Learn waypoint distribution
ŝ_t+1 = WM(ŝ_t, a_t)  for t ∈ [w_i, w_{i+1}]  # Short rollouts between waypoints
```

**Training Procedure:**
1. Collect expert demonstrations, identify waypoints via curvature in state space or value function gradients
2. Train diffusion model to generate waypoint sequences conditioned on task embedding
3. Train world model on short segments between waypoints
4. Fine-tune end-to-end with model-based RL using waypoint-constrained rollouts

### Why It's Novel

**Vs. Existing Work:**
- **Diffusion Policy (Chi et al. 2024):** Generates dense action sequences, no world model
- **Hierarchical Diffusion Policy (2025):** Uses contact points for hierarchy, not for error control
- **DTP (2024):** Generates trajectory sketch but doesn't use world model for interpolation

**Unique Contribution:**
- First to use diffusion for adaptive temporal abstraction to control world model error
- Waypoint spacing learned from data (not fixed intervals)
- Error bounds theoretically improve from O(T²) to O(k·h²) where k waypoints, h=horizon between waypoints

### Experimental Validation Plan

**Environments:**
1. **Long-Horizon MetaWorld Tasks:** Chain assembly, drawer/door opening sequences (50-200 steps)
2. **Custom Isaac Gym Tasks:**
   - Multi-object rearrangement (100-150 steps)
   - Sequential tool use (hammer→screwdriver→wrench, 150+ steps)
   - Bimanual coordination tasks (fold cloth, 200+ steps)

**Baselines:**
1. Dense Diffusion Policy (Chi et al.)
2. World Model + Model-Predictive Control (Dreamer-V3 style)
3. Hierarchical RL (HAC, HIRO)
4. VidMan (video diffusion model)

**Metrics:**
- **Success Rate** on long-horizon tasks (primary)
- **Error Accumulation:** MSE between predicted and actual states vs. horizon length
- **Waypoint Quality:** Distance between predicted and actual waypoints
- **Sample Efficiency:** Success rate vs. number of demonstrations
- **Compute:** Wall-clock time for rollout (world model should be faster than diffusion)

**Ablations:**
- Fixed vs. learned waypoint spacing
- Number of waypoints (5, 10, 20)
- World model architecture (transformer vs. CNN-LSTM)
- Waypoint identification method (curvature vs. value gradients vs. learned)

### Feasibility Assessment

**What You Have:**
- ✅ Diffusion model expertise (can implement waypoint diffusion)
- ✅ World model experience (can build transition model)
- ✅ Isaac Gym + MuJoCo access (can create long-horizon tasks)
- ✅ 6-month timeline sufficient for implementation + experiments

**Technical Risks:**
- ⚠️ **Medium Risk:** Waypoint identification may be task-dependent (mitigation: learn end-to-end)
- ⚠️ **Medium Risk:** World model may still drift between waypoints (mitigation: add state correction layer)
- ✅ **Low Risk:** Core components (diffusion, world model) are well-established

**Resource Requirements:**
- GPU: 1-2 A100s for training (diffusion + world model parallelizable)
- Compute Time: ~2 months training, 1 month experiments
- Data: 100-500 demos per task (reasonable for imitation learning)

**Timeline Breakdown:**
- Month 1: Implement waypoint diffusion model
- Month 2: Implement world model, integrate architecture
- Month 3: Train on MetaWorld + Isaac Gym tasks
- Month 4: Run baselines, collect results
- Month 5: Ablations, analysis, additional experiments
- Month 6: Paper writing, final experiments

**Overall Feasibility: ⭐⭐⭐⭐ (4/5 - Good)**

---

## Solution 2: Uncertainty-Aware World Model with Adaptive Replanning (UWMAR)

### Core Technical Idea

**Confidence-Based Rollout Control:**
1. World model outputs both state prediction AND uncertainty estimate (epistemic + aleatoric)
2. Monitor cumulative uncertainty during autoregressive rollout
3. Trigger replanning when uncertainty crosses threshold

**Key Innovation:**
- Uncertainty is not just for OOD detection, but actively controls planning horizon
- Diffusion policy acts as "safety net" when world model loses confidence
- Adaptive compute: use fast world model when confident, expensive diffusion when uncertain

**Mathematical Framework:**
```
(ŝ_t+1, σ_t+1) = WM_θ(ŝ_t, a_t)          # Predict state + uncertainty
U_t = ∑_{i=0}^t σ_i²                       # Cumulative uncertainty
if U_t > threshold:
    a_{t:t+H} ~ Diffusion(s_t, g)          # Replan with diffusion policy
    reset U_t = 0
else:
    continue world model rollout
```

**Training Procedure:**
1. Train ensemble of world models (5-10 members) or Bayesian neural network
2. Train diffusion policy separately on demonstration data
3. Learn threshold policy via RL: reward = task success - λ·(num_replans)
4. Optional: Fine-tune world model with active learning on high-uncertainty states

### Why It's Novel

**Vs. Existing Work:**
- **Diff-DAgger (Oct 2024):** Uses uncertainty for data collection, not adaptive planning
- **Dreamer-V3:** Fixed replanning horizon, no uncertainty-based adaptation
- **Model-Based RL with Ensembles:** Typically pessimistic planning, not adaptive replanning

**Unique Contribution:**
- First to combine world model uncertainty with diffusion policy replanning
- Learns when to trust world model vs. replan (adaptive compute allocation)
- Theoretical guarantee: expected error bounded by uncertainty estimates

### Experimental Validation Plan

**Environments:**
1. **Distribution Shift Tasks (Isaac Gym):**
   - Object mass/friction variations (world model should be uncertain)
   - Lighting/texture changes (should NOT trigger uncertainty if state-based)
   - Novel object shapes (should trigger uncertainty)

2. **Long-Horizon Manipulation:**
   - Same tasks as Solution 1 for comparison
   - Add adversarial perturbations to test uncertainty calibration

**Baselines:**
1. Pure Diffusion Policy (no world model)
2. Pure World Model MPC (no replanning)
3. Fixed-Interval Replanning (e.g., every 20 steps)
4. POLO (Posterior Sampling RL, pessimistic planning)

**Metrics:**
- **Success Rate** vs. uncertainty threshold
- **Compute Efficiency:** Avg. rollout time vs. num_replans
- **Calibration:** Predicted uncertainty vs. actual prediction error
- **Pareto Front:** Success rate vs. compute cost
- **Failure Mode Analysis:** What causes uncertainty spikes?

**Ablations:**
- Uncertainty estimation method (ensemble vs. dropout vs. Bayesian)
- Threshold selection (fixed vs. learned)
- Replanning horizon after reset (10 vs. 20 vs. full-horizon)
- Include aleatoric uncertainty or epistemic only

### Feasibility Assessment

**What You Have:**
- ✅ World model + diffusion expertise (core requirements)
- ✅ Uncertainty estimation well-studied (can use ensemble)
- ✅ Simulation environment allows controlled distribution shifts

**Technical Risks:**
- ⚠️ **Medium Risk:** Uncertainty calibration may require significant tuning
- ⚠️ **High Risk:** Threshold learning may be unstable (mitigation: use curriculum)
- ✅ **Low Risk:** Individual components (ensemble, diffusion) are proven

**Resource Requirements:**
- GPU: 2-3 A100s (need ensemble of world models)
- Compute Time: ~3 months training (ensemble expensive)
- Data: 100-500 demos + uncertainty calibration data

**Timeline Breakdown:**
- Month 1: Implement ensemble world model with uncertainty estimation
- Month 2: Implement adaptive replanning logic, integrate with diffusion policy
- Month 3: Calibration experiments, threshold tuning
- Month 4: Main experiments on long-horizon + distribution shift tasks
- Month 5: Baselines, ablations, analysis
- Month 6: Paper writing, additional experiments

**Overall Feasibility: ⭐⭐⭐ (3/5 - Moderate, higher technical risk)**

---

## Solution 3: Physics-Informed World Model with Differentiable Simulator Correction (PIWS)

### Core Technical Idea

**Hybrid Learned + Physics Architecture:**
1. Learned world model predicts "residuals" on top of fast differentiable physics simulator
2. Physics simulator provides structure (contact, collision, gravity)
3. Neural network learns un-modeled dynamics (friction, deformation, actuator lag)

**Key Innovation:**
- Physics simulator acts as strong inductive bias, reducing learned model's error accumulation
- Residual learning: neural network only needs to predict small corrections
- Differentiable simulator enables end-to-end gradient flow for policy optimization

**Mathematical Framework:**
```
s_t+1 = Sim_physics(s_t, a_t) + Δ_θ(s_t, a_t)  # Physics + learned residual
Δ_θ: small correction to physics (bounded ||Δ|| < ε)
Loss = ||s_t+1 - s*_t+1||² + λ||Δ_θ||²         # Encourage small residuals
```

**Training Procedure:**
1. Use MuJoCo/Isaac Gym as differentiable physics simulator
2. Collect demonstrations, extract physics state (positions, velocities, contacts)
3. Train residual network to predict errors between physics and actual next state
4. Train diffusion policy using hybrid model for imagination/planning
5. Fine-tune with model-based RL using hybrid rollouts

### Why It's Novel

**Vs. Existing Work:**
- **IRASim (ICCV 2025):** Pure learned simulator, no physics integration
- **Traditional MuJoCo/Isaac Gym:** Pure physics, requires manual asset tuning
- **DiffTaichi (2020):** Differentiable physics but for design optimization, not learned residuals

**Unique Contribution:**
- First to combine differentiable physics with learned residuals for manipulation world models
- Residual learning bounds error accumulation (error in physics + bounded residual error)
- Leverages existing simulators (MuJoCo) rather than learning from scratch

### Experimental Validation Plan

**Environments:**
1. **Contact-Rich Manipulation (Isaac Gym/MuJoCo):**
   - Peg insertion with friction (physics approximate, needs residual)
   - Rope/cable manipulation (physics inaccurate for deformables)
   - Tool use: hammer, screwdriver (contact-rich)

2. **Long-Horizon Assembly:**
   - IKEA furniture assembly (multi-step, contacts critical)
   - Block stacking/unstacking (stability matters)

**Baselines:**
1. Pure Learned World Model (IRASim-style)
2. Pure Physics (MuJoCo/Isaac Gym with default params)
3. Domain Randomization (randomize physics params)
4. System ID (fit physics params to data)

**Metrics:**
- **Long-Horizon Accuracy:** Prediction error at 50, 100, 200 steps
- **Contact Prediction:** Precision/recall of contact events
- **Sample Efficiency:** Prediction accuracy vs. training data size
- **Residual Magnitude:** ||Δ_θ|| over time (should stay bounded)
- **Task Success:** On contact-rich manipulation tasks

**Ablations:**
- Residual network architecture (MLP vs. GNN for objects)
- Residual regularization strength λ
- Physics update rate (1Hz vs. 10Hz vs. 100Hz)
- Which dynamics to model with residual (friction only vs. full correction)

### Feasibility Assessment

**What You Have:**
- ✅ MuJoCo + Isaac Gym (both differentiable)
- ✅ Strong ML background (can implement residual network)
- ⚠️ Physics knowledge needed (but can learn/collaborate)

**Technical Risks:**
- ⚠️ **Medium Risk:** Differentiable physics may not support all features (e.g., Isaac Gym limited)
- ⚠️ **High Risk:** Residual training may be unstable if physics is very wrong
- ⚠️ **Medium Risk:** May still accumulate error (just slower than pure learned)

**Resource Requirements:**
- GPU: 2 A100s (physics sim + neural network training)
- Compute Time: ~2-3 months (physics sim faster than full learned model)
- Data: 100-500 demos per task
- **Extra:** May need to learn differentiable physics APIs (Isaac Gym, MuJoCo JAX)

**Timeline Breakdown:**
- Month 1: Learn differentiable physics APIs, implement residual architecture
- Month 2: Train residual models on contact-rich tasks
- Month 3: Integrate with diffusion policy, run initial experiments
- Month 4: Baselines, ablations
- Month 5: Long-horizon experiments, analysis
- Month 6: Paper writing, final experiments

**Overall Feasibility: ⭐⭐⭐ (3/5 - Moderate, requires physics learning curve)**

---

## Summary Comparison

| Aspect | HiWaDi (Sol 1) | UWMAR (Sol 2) | PIWS (Sol 3) |
|--------|----------------|---------------|--------------|
| **Novelty** | ⭐⭐⭐⭐⭐ | ⭐⭐⭐⭐ | ⭐⭐⭐⭐⭐ |
| **Feasibility** | ⭐⭐⭐⭐ | ⭐⭐⭐ | ⭐⭐⭐ |
| **Your Strengths** | Perfect fit | Good fit | Moderate fit |
| **Technical Risk** | Low-Medium | Medium-High | Medium-High |
| **6-Month Fit** | Excellent | Good | Moderate |
| **CoRL Appeal** | High | High | Very High |

## Recommendation

**Primary: Solution 1 (HiWaDi)** - Best balance of novelty, feasibility, and timeline fit
**Backup: Solution 3 (PIWS)** - If you want higher novelty and don't mind physics learning curve
**Risky: Solution 2 (UWMAR)** - Uncertainty calibration may be challenging, but interesting if solved

**Next Step:** Critical review of all three approaches (CoRL reviewer perspective)
