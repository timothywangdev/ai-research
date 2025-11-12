# Research Ideas Master Index - All 15 Opportunities from 500-Paper Review

**Date**: 2025-11-12
**Source**: Comprehensive review of 500 papers on robotics manipulation, world models, and diffusion policies
**Context**: CoRL 2026 submission target, 6-month timeline, simulation-only

---

## Quick Comparison Table

| # | Idea | Novelty | Feasibility | Impact | Timeline | Acceptance | Rank |
|---|------|---------|-------------|--------|----------|------------|------|
| 1 | **HiLoop** | 9/10 | 7.5/10 | 9/10 | 7/10 | 80% | **#1** |
| 2 | Equivariant Hierarchical | 7/10 | 8.5/10 | 7/10 | 8.5/10 | 70% | **#2** |
| 3 | Flow Matching Hierarchical | 6/10 | 7.5/10 | 6/10 | 7/10 | 65% | #3 |
| 4 | Diffusion + Online RL | 8/10 | 6/10 | 8/10 | 6/10 | 70% | #4 |
| 5 | 3D World Model Hierarchical | 8/10 | 6.5/10 | 7/10 | 6.5/10 | 68% | #5 |
| 6 | Multi-Modal WM Monitoring | 7/10 | 7/10 | 7/10 | 7/10 | 65% | #6 |
| 7 | Adaptive Waypoint Density | 6/10 | 8/10 | 6/10 | 8/10 | 60% | #7 |
| 8 | Contact-Aware Hierarchical | 7/10 | 7/10 | 7/10 | 7/10 | 65% | #8 |
| 9 | Bimanual Hierarchical | 6/10 | 7.5/10 | 6/10 | 7.5/10 | 60% | #9 |
| 10 | Predictive Failure Recovery | 8/10 | 6.5/10 | 8/10 | 6.5/10 | 70% | #10 |
| 11 | Language Waypoint Generation | 7/10 | 7.5/10 | 7/10 | 7.5/10 | 68% | #11 |
| 12 | Cross-Embodiment Hierarchical | 7/10 | 6/10 | 7/10 | 6/10 | 62% | #12 |
| 13 | Sim-to-Real Hierarchical | 6/10 | 5/10 | 8/10 | 5/10 | 55% | #13 |
| 14 | Efficient Real-Time WM | 7/10 | 7/10 | 6/10 | 7/10 | 62% | #14 |
| 15 | Uncertainty-Aware Refinement | 7/10 | 7/10 | 7/10 | 7/10 | 65% | #15 |

**Scoring**:
- Novelty: How original is the idea? (Gap in 500 papers)
- Feasibility: Can it be done in 6 months?
- Impact: How important is the problem solved?
- Timeline: Realistic for 6 months? (higher = easier)
- Acceptance: P(CoRL 2026 acceptance | good execution)

---

## Tier 1: PRIMARY CANDIDATES (Highest Priority)

### #1. HiLoop: Hierarchical Closed-Loop Diffusion with World Model Refinement ⭐⭐⭐

**Elevator Pitch**: Combine hierarchical diffusion with learned world models to enable dynamic waypoint refinement during execution.

**Gap Addressed**: No prior work combines hierarchical diffusion + world model monitoring + online waypoint adaptation

**Key Innovation**: World model predicts execution errors, triggers waypoint replanning proactively

**Closest Competitor**: Subgoal Diffuser (uses MPC, not world model)

**Differentiation**: Learning-based (WM) vs optimization-based (MPC), dynamic refinement vs static generation

**Pros**:
- Novel combination validated across 500 papers
- Addresses documented problem (ChainedDiffuser open-loop limitation)
- High impact (enables dynamic environments)
- Clear publication venue fit (CoRL 2026)

**Cons**:
- World model accuracy critical (highest risk component)
- Integration complexity (3 components)
- Ambitious timeline (6 months tight)

**Overall**: 26.5/30 = **88%** (Novelty 9 + Feasibility 7.5 + Impact 9)

**Status**: FULLY DOCUMENTED (draft paper, feasibility analysis, references)

**Recommendation**: **PRIMARY CHOICE - PROCEED**

---

### #2. Equivariant Hierarchical Diffusion ⭐⭐

**Elevator Pitch**: Add SE(3) equivariance to hierarchical diffusion for 3-5x data efficiency.

**Gap Addressed**: No work combines hierarchical diffusion with geometric equivariance

**Key Innovation**: Multi-scale equivariance (both waypoint and execution levels)

**Pros**:
- Lower risk than HiLoop (no world model)
- Clear measurable benefit (data efficiency)
- Theoretical grounding (equivariance is principled)
- Faster timeline (simpler implementation)

**Cons**:
- Less novel (combining two existing techniques)
- Incremental contribution
- Benefit limited to low-data regime

**Overall**: 22.5/30 = **75%** (Novelty 7 + Feasibility 8.5 + Impact 7)

**Status**: FULLY DOCUMENTED

**Recommendation**: **STRONG BACKUP - Pivot here if HiLoop WM fails**

---

## Tier 2: STRONG ALTERNATIVES

### #3. Flow Matching for Hierarchical Manipulation

**Elevator Pitch**: Replace diffusion with flow matching for 5-10x faster inference.

**Gap**: Flow matching unexplored for hierarchical manipulation

**Key Benefit**: Real-time control (40 Hz vs 6.7 Hz)

**Overall**: 19.5/30 = **65%** (Novelty 6 + Feasibility 7.5 + Impact 6)

**Status**: Draft paper + feasibility analysis

**Recommendation**: Plan C if both HiLoop and EqHD fail

---

### #4. Diffusion Policy with Online RL Hybrid

**Elevator Pitch**: Pre-train with diffusion (imitation), fine-tune with online RL (adaptation).

**Gap**: No work combines diffusion pre-training with online adaptation RL

**Key Benefit**: Best of both worlds (multimodal + adaptation)

**Overall**: 22/30 = **73%** (Novelty 8 + Feasibility 6 + Impact 8)

**Pros**: High impact, addresses real problem
**Cons**: Two complex components, RL notoriously difficult

**Recommendation**: High-risk, high-reward alternative

---

### #5. 3D World Model for Hierarchical Control

**Elevator Pitch**: Use 3D representations (point clouds) for world model predictions in hierarchical policies.

**Gap**: World models mostly 2D/video, not 3D-aware for hierarchical control

**Key Benefit**: Better spatial reasoning, occlusion handling

**Overall**: 21.5/30 = **72%** (Novelty 8 + Feasibility 6.5 + Impact 7)

**Pros**: Leverages 3D-VLA insights, strong motivation
**Cons**: Complex (3D + WM + hierarchy), ambitious

**Recommendation**: Interesting but risky

---

## Tier 3: FOCUSED IMPROVEMENTS

### #6. Multi-Modal World Model Monitoring

**Elevator Pitch**: Use vision + force + tactile in world model for better prediction.

**Gap**: World models mostly vision-only

**Overall**: 21/30 = **70%**

**Recommendation**: Good for hardware-equipped labs (requires sensors)

---

### #7. Adaptive Waypoint Density Learning

**Elevator Pitch**: Learn how many waypoints needed (sparse vs dense) per task.

**Gap**: Fixed waypoint schedules in prior work

**Overall**: 20/30 = **67%**

**Pros**: Low risk, clear benefit
**Cons**: Limited novelty, incremental

**Recommendation**: Safe but incremental

---

### #8. Contact-Aware Hierarchical Diffusion

**Elevator Pitch**: Condition waypoints on predicted contact events.

**Gap**: Hierarchical diffusion not contact-aware

**Overall**: 21/30 = **70%**

**Pros**: Addresses contact-rich tasks
**Cons**: Contact prediction challenging

**Recommendation**: For contact-focused applications

---

### #9. Bimanual Hierarchical Diffusion

**Elevator Pitch**: Extend hierarchical diffusion to coordinated bimanual manipulation.

**Gap**: ChainedDiffuser single-arm only

**Overall**: 19.5/30 = **65%**

**Pros**: Clear application (bimanual tasks growing)
**Cons**: Incremental extension

**Recommendation**: If bimanual data available

---

### #10. Predictive Failure Recovery with World Model

**Elevator Pitch**: Use world model to predict failures before they happen, trigger recovery.

**Gap**: Existing recovery reactive (MoE-DP), not predictive

**Overall**: 22.5/30 = **75%**

**Pros**: High impact (safety-critical)
**Cons**: World model accuracy critical

**Recommendation**: Interesting safety-focused project

---

## Tier 4: SPECIALIZED DIRECTIONS

### #11. Language-Conditioned Waypoint Generation

**Elevator Pitch**: VLM generates waypoints from language, diffusion executes.

**Gap**: Language used for tasks, not waypoint planning

**Overall**: 21.5/30 = **72%**

**Pros**: Timely (VLMs hot), clear motivation
**Cons**: VLM quality dependency

**Recommendation**: If interested in LLM integration

---

### #12. Cross-Embodiment Hierarchical Transfer

**Elevator Pitch**: Train hierarchical policy on multiple robot morphologies, transfer to new robots.

**Gap**: Cross-embodiment work doesn't leverage hierarchy

**Overall**: 20/30 = **67%**

**Pros**: Foundation model direction
**Cons**: Needs multi-robot data

**Recommendation**: For multi-robot settings

---

### #13. Sim-to-Real for Hierarchical Policies

**Elevator Pitch**: Domain randomization + hierarchical structure for better sim-to-real.

**Gap**: Sim-to-real hasn't leveraged hierarchical structure

**Overall**: 21/30 = **70%** (impact high but feasibility low without real robot)

**Pros**: High practical impact
**Cons**: Requires real robot (user has simulation only)

**Recommendation**: NOT FEASIBLE for current setup

---

### #14. Efficient Real-Time World Models

**Elevator Pitch**: Lightweight world model architectures for <10ms inference.

**Gap**: World models too slow for real-time control

**Overall**: 20/30 = **67%**

**Pros**: Clear engineering contribution
**Cons**: Primarily systems/optimization work

**Recommendation**: For efficiency-focused work

---

### #15. Uncertainty-Aware Waypoint Refinement

**Elevator Pitch**: Use world model uncertainty to decide when to refine waypoints.

**Gap**: No uncertainty-aware refinement strategies

**Overall**: 21/30 = **70%**

**Pros**: Principled approach (Bayesian)
**Cons**: Uncertainty estimation challenging

**Recommendation**: Extension of HiLoop

---

## Strategic Recommendations

### Primary Strategy: **HiLoop** (Idea #1)
- Highest novelty + impact
- Validated gap across 500 papers
- Addresses documented problem
- Clear differentiation from competitors
- Risk-managed with fallbacks

**Decision Point**: Month 2 (World model accuracy validation)
- If WM prediction error <20%: Continue HiLoop
- If WM prediction error 20-30%: Conservative threshold, simplified WM
- If WM prediction error >30%: Pivot to Backup

### Backup Strategy: **Equivariant Hierarchical** (Idea #2)
- Lower risk, clearer benefit
- Measurable contribution (data efficiency)
- Faster timeline
- Can start in parallel with HiLoop

**When to pivot**: If HiLoop WM fails validation by Month 2

### Plan C: **Flow Matching** (Idea #3) or **Diffusion + RL** (Idea #4)
- If both HiLoop and EqHD show problems
- Flow Matching: Safe, guaranteed results
- Diffusion + RL: High risk, high reward

---

## Gap Analysis Summary

From 500 papers reviewed, these **critical gaps** were identified:

### Gap #1: ✅ **No hierarchical diffusion + world model + online adaptation**
→ Addressed by **HiLoop** (Idea #1)

### Gap #2: ✅ **No equivariant hierarchical policies**
→ Addressed by **EqHD** (Idea #2)

### Gap #3: ✅ **Open-loop execution in hierarchical diffusion**
→ Addressed by **HiLoop** (Idea #1), **Predictive Recovery** (Idea #10)

### Gap #4: ✅ **No flow matching for manipulation hierarchies**
→ Addressed by **Flow Matching** (Idea #3)

### Gap #5: ✅ **Limited online adaptation in diffusion policies**
→ Addressed by **Diffusion + RL** (Idea #4), **HiLoop** (Idea #1)

### Gap #6: ⚠️ **Partially addressed: Long-horizon robustness**
→ Multiple ideas address this (1, 2, 4, 10)

---

## Publication Venue Fit Analysis

### CoRL 2026 (Primary Target)

**Best Fit (>70% acceptance if executed well)**:
1. HiLoop (80%) - Novel, timely, addresses documented problem
2. Equivariant Hierarchical (70%) - Clear benefit, strong evaluation
3. Diffusion + RL (70%) - High impact, addresses adaptation

**Good Fit (60-70%)**:
4. 3D World Model (68%)
5. Predictive Failure Recovery (70%)
6. Language Waypoint Generation (68%)
7. Flow Matching (65%)
8. Contact-Aware (65%)
9. Multi-Modal WM (65%)
10. Uncertainty-Aware (65%)

**Moderate Fit (50-60%)**:
11. Adaptive Density (60%)
12. Bimanual (60%)
13. Cross-Embodiment (62%)
14. Efficient WM (62%)

**Lower Fit (<55%)**:
15. Sim-to-Real (55% - but not feasible without robot)

---

## Timeline & Risk Matrix

### Low Risk, Comfortable Timeline (>7.5/10 feasibility, >7/10 timeline):
- **Equivariant Hierarchical** (#2): Best backup
- Adaptive Waypoint Density (#7): Safe but incremental
- Bimanual Hierarchical (#9): Extension work
- Efficient Real-Time WM (#14): Engineering-focused

### Medium Risk, Tight Timeline (6-7.5/10 feasibility, 6-7/10 timeline):
- **HiLoop** (#1): PRIMARY - manageable risk with mitigation
- Flow Matching (#3): Medium novelty, medium risk
- Contact-Aware (#8): Contact prediction challenging
- Multi-Modal WM (#6): Sensor fusion complexity
- Language Waypoint (#11): VLM dependency
- Uncertainty-Aware (#15): Uncertainty estimation hard

### High Risk, Ambitious Timeline (<6/10 feasibility, <6.5/10 timeline):
- Diffusion + RL (#4): RL notoriously difficult
- 3D World Model (#5): Multiple complex components
- Predictive Failure Recovery (#10): WM accuracy critical
- Cross-Embodiment (#12): Data requirements
- Sim-to-Real (#13): Real robot needed (NOT FEASIBLE)

---

## Resource Requirements

### Computational (All ideas):
- 2-4 NVIDIA A100 GPUs (or 4-8 RTX 3090s)
- ~500GB storage
- ~$2-4K cloud compute (if needed)

### Software (All ideas):
- Isaac Gym, MuJoCo ✓
- CALVIN benchmark ✓
- Diffusion Policy codebase ✓
- Various open-source implementations ✓

### Human Expertise (User has):
- ✓ Diffusion models
- ✓ World models
- ✓ PyTorch/JAX implementation
- (~) Equivariant learning (learnable)
- (~) Online RL (learnable but challenging)
- ✗ Real robot setup (not available)

---

## Decision Tree

```
Start: Choose Research Direction
├─ Risk Tolerance: HIGH
│  └─ Choose HiLoop (#1)
│     ├─ Month 2: WM validation
│     │  ├─ Success (error <20%) → Continue HiLoop
│     │  ├─ Moderate (error 20-30%) → Simplified HiLoop
│     │  └─ Failure (error >30%) → Pivot to EqHD (#2)
│     └─ Month 4: Experimental validation
│        ├─ Success → Paper writing
│        └─ Mixed → Deep analysis + alternative venue
│
├─ Risk Tolerance: MEDIUM
│  └─ Choose EqHD (#2)
│     └─ Months 3-4: Data efficiency validation
│        ├─ >3x improvement → Strong paper
│        ├─ 2-3x improvement → Good paper
│        └─ <2x improvement → Ablation focus
│
└─ Risk Tolerance: LOW
   └─ Choose Flow Matching (#3) or Adaptive Density (#7)
      └─ Safe, publishable, lower ceiling
```

---

## Final Recommendations Ranked

**For CoRL 2026 Main Conference:**

1. **HiLoop** (#1) - 88% quality, 80% acceptance, HIGH RISK
   - Best choice if comfortable with world model risk
   - Mitigation: Early WM validation, staged implementation

2. **Equivariant Hierarchical** (#2) - 75% quality, 70% acceptance, MEDIUM RISK
   - Best backup, can develop in parallel
   - Pivot destination if HiLoop fails

3. **Diffusion + RL** (#4) - 73% quality, 70% acceptance, HIGH RISK
   - Alternative high-impact direction
   - Choose if more interested in RL/adaptation

4. **3D World Model** (#5) - 72% quality, 68% acceptance, HIGH RISK
   - Interesting alternative, multiple novelties

5. **Predictive Failure Recovery** (#10) - 75% quality, 70% acceptance, MEDIUM-HIGH RISK
   - Safety-critical angle, strong motivation

**For Workshops / Alternative Venues:**

6-15: All other ideas are publishable at workshops or as focused contributions

---

## Detailed Documentation Status

### Complete Documentation (Paper + Feasibility + References):
- ✅ #1: HiLoop (PRIMARY)
- ✅ #2: Equivariant Hierarchical (BACKUP)
- ⏳ #3: Flow Matching (Draft paper + feasibility)

### In Progress:
- ⏳ #4-15: Creating draft papers + feasibility analyses

**Next Steps**: Complete detailed documentation for ideas #4-15
