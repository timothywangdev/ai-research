# Idea #9: Bimanual Hierarchical Diffusion - Comprehensive Summary

## Elevator Pitch
Extend hierarchical diffusion to coordinated bimanual manipulation with synchronized waypoints.

---

## Key Idea

**Gap**: ChainedDiffuser single-arm only, bimanual coordination challenging

**Solution**: Bimanual hierarchical diffusion
- Generate synchronized waypoints for both arms
- Coordinate low-level execution
- Handle relative positioning constraints

**Benefit**: Long-horizon bimanual tasks (folding, carrying, assembly)

---

## Method

### Bimanual Waypoint Generation
**Input**: Scene + dual-arm state + task
**Output**: Waypoint pairs {(w_left, w_right)}

**Constraint**: Maintain relative positioning
```
L_sync = ||d(w_left, w_right) - d_desired||
```

### Coordinated Execution
**Low-level**: Two policies conditioned on respective waypoints
**Synchronization**: Enforce time alignment

---

## Experiments

**Benchmarks**:
- Mobile ALOHA tasks (bimanual demonstrations available)
- Simulated bimanual tasks (folding, carrying)

**Expected**: 20-30% success improvement over single-arm baselines

**Ablations**:
1. Independent vs coordinated waypoint generation
2. Synchronized vs unsynchronized execution
3. Different relative constraints

---

## Feasibility: 7.5/10

**Pros**:
- Mobile ALOHA demonstrates bimanual IL works
- Straightforward extension of ChainedDiffuser
- Clear applications (folding, carrying)

**Cons**:
- Bimanual data less available than single-arm
- Coordination challenging (timing, relative pose)
- Incremental contribution (extension work)

**Timeline**: 6 months comfortable

**Confidence**: 75%

---

## Key Risks

### Risk #1: Limited Data (35%, MEDIUM)
- Bimanual demonstrations scarce
- May need to collect own data

**Mitigation**: Use Mobile ALOHA dataset, simulated tasks

### Risk #2: Coordination Complexity (25%, LOW-MEDIUM)
- Synchronization hard to get right
- May need careful constraint design

**Mitigation**: Start with simple relative constraints

---

## Confidence Scores

- **P(Technical success)**: 80%
- **P(Experimental success)**: 75%
- **P(CoRL acceptance)**: 60%

---

## Comparison

**vs Mobile ALOHA**: We add hierarchy
**vs ChainedDiffuser**: We add bimanual

**Rank**: #9 overall (65% quality)

---

## Recommendation

**Choose if**:
- Have bimanual robot/data
- Interested in coordination
- Want safer project (lower risk)

**Best Use**: If bimanual data readily available

---

## Key References

[1] Mobile ALOHA - Bimanual demonstrations
[2] RDT-1B - Diffusion for bimanual
[3] ChainedDiffuser - Add bimanual extension
[4] Bimanual manipulation surveys
[5] Coordination in multi-agent RL
