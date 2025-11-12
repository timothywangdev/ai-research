# Idea #8: Contact-Aware Hierarchical Diffusion - Comprehensive Summary

## Elevator Pitch
Condition waypoint generation on predicted contact events for better planning in contact-rich tasks.

---

## Key Idea

**Gap**: Hierarchical diffusion ignores contact physics
- Waypoints may be infeasible (require contact violations)
- Contact-rich tasks (insertion, assembly) challenging

**Solution**: Contact-aware waypoint generation
```
W = diffusion_high(s_t, l, contact_predictions)
```

**Benefit**: Feasible waypoints that respect contact constraints

---

## Method

### Contact Prediction Module
**Input**: Current scene (objects, robot)
**Output**: Predicted contact events {(t_i, object_i, type_i)}

**Training**: Supervised on labeled contact data from demonstrations

### Contact-Conditioned Diffusion
**Architecture**: Cross-attention to contact events
```
waypoint_features = cross_attention(visual_features, contact_features)
```

**Loss**: Standard diffusion + contact feasibility loss
```
L_total = L_diffusion + λ·L_contact_violation
```

---

## Experiments

**Benchmarks**: Contact-rich manipulation
- Peg insertion
- Assembly tasks
- Drawer opening (contact required)

**Expected**: 25-35% success rate improvement on contact-rich tasks

**Ablations**:
1. With vs without contact prediction
2. Different contact representations
3. Violation penalty weight λ

---

## Feasibility: 7/10

**Pros**:
- Contact prediction studied (prior work exists)
- Clear benefit for contact-rich tasks
- Hierarchical Diffusion Policy (CVPR 2024) shows contact-based hierarchy works

**Cons**:
- Contact prediction challenging (physics simulation complex)
- May not generalize well (model inaccuracies)
- Limited to contact-rich tasks (not general)

**Timeline**: 6 months feasible

**Confidence**: 70%

---

## Key Risks

### Risk #1: Contact Prediction Inaccurate (40%, HIGH)
- Physics models imperfect
- Learning-based predictors noisy

**Mitigation**: Use ground-truth contacts in simulation for upper bound

### Risk #2: Benefit Limited (30%, MEDIUM)
- Diffusion may learn contacts implicitly from data
- Explicit contact conditioning may not help much

**Mitigation**: Compare to implicit baseline carefully

---

## Confidence Scores

- **P(Technical success)**: 70%
- **P(Experimental success)**: 70%
- **P(CoRL acceptance)**: 65%

---

## Comparison

**vs Hierarchical Diffusion Policy (CVPR 2024)**: They use contact, we add hierarchy
**vs ChainedDiffuser**: We add contact awareness

**Rank**: #8 overall (70% quality)

---

## Recommendation

**Choose if**:
- Interested in contact-rich manipulation
- Have contact-rich benchmarks
- Want physics-informed learning

**Best Use**: Specialized for contact-rich applications

---

## Key References

[1] Hierarchical Diffusion Policy (CVPR 2024) - Contact-based hierarchy
[2] Contact Prediction for Manipulation
[3] Physics-Informed Neural Networks
[4] Contact-Rich Manipulation Surveys
[5] ChainedDiffuser - Add contact awareness
