# Idea #7: Adaptive Waypoint Density Learning - Comprehensive Summary

## Elevator Pitch
Learn how many waypoints are needed per task (sparse for simple, dense for complex) instead of fixed schedules.

---

## Key Idea

**Gap**: ChainedDiffuser uses fixed waypoint density (e.g., every 10 steps)
- Over-specified for simple tasks (inefficient)
- Under-specified for complex tasks (fails)

**Solution**: Learn waypoint density policy
```
K_task = f(s_0, task_description, complexity_estimate)
```

**Benefit**:
- Sparse waypoints for pick-and-place (K=3-5)
- Dense waypoints for assembly (K=15-20)
- Adaptive = efficient + effective

---

## Method

### Waypoint Density Predictor
**Input**: Initial observation + language command
**Output**: Number of waypoints K

**Training**:
- Supervised: Label demonstrations with optimal K (minimum K that succeeds)
- RL: Reward = task success - λ·K (penalize unnecessary waypoints)

### Dynamic Waypoint Generation
1. Predict K = density_predictor(s_0, l)
2. Generate K waypoints: W = diffusion_high(s_0, l, K)
3. Execute with low-level policy

---

## Experiments

**Hypothesis**: Adaptive K improves efficiency without hurting success

**Metrics**:
- Task success rate (should maintain)
- Average waypoints used (should decrease 20-40%)
- Inference time (should decrease)

**Expected Results**:
| Task Type | Fixed K | Adaptive K | Improvement |
|-----------|---------|------------|-------------|
| Simple (pick) | K=10 | K=4 | 2.5x faster |
| Complex (assembly) | K=10 | K=18 | +15% success |

---

## Feasibility: 8/10

**Pros**:
- Low risk (add density predictor to ChainedDiffuser)
- Clear benefit (efficiency)
- Easy to implement (MLP predictor)

**Cons**:
- Incremental contribution (limited novelty)
- Benefit may be modest (10-20% efficiency)

**Timeline**: 5 months (faster than complex projects)

**Confidence**: 85%

---

## Key Risks

### Risk #1: Limited Benefit (35%, MEDIUM)
- Fixed K may work well enough
- Adaptive K only 10-15% better

**Impact**: Weaker paper, workshop-level
**Mitigation**: Emphasize principle, show clear cases where it helps

### Risk #2: Density Prediction Hard (20%, LOW)
- May not predict K accurately
- Simple heuristics may work as well

**Mitigation**: Compare to heuristics (task length, object count)

---

## Confidence Scores

- **P(Technical success)**: 90%
- **P(Experimental success)**: 80%
- **P(CoRL acceptance)**: 60%

---

## Comparison

**vs Fixed Schedule**: More efficient, adaptive
**vs HiLoop**: Simpler, lower impact, safer

**Rank**: #7 overall (67% quality)

---

## Recommendation

**Choose if**:
- Want low-risk project
- Value efficiency over novelty
- Comfortable timeline

**Best Use**: Addition to HiLoop or ChainedDiffuser baseline

---

## Key References

[1] ChainedDiffuser - Fixed density baseline
[2] Task Complexity Estimation
[3] Adaptive Planning literature
[4] Waypoint-based manipulation methods
