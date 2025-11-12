# Idea #5: 3D World Model for Hierarchical Control - Comprehensive Summary

## Elevator Pitch

Use 3D point cloud representations in world models for better spatial reasoning and occlusion handling in hierarchical manipulation policies.

---

## Paper Outline

### Title
**3D World Models for Hierarchical Robot Manipulation: Better Spatial Prediction for Closed-Loop Control**

### Abstract
World models for manipulation typically operate on 2D images, losing 3D spatial information crucial for predicting contact and occlusions. We introduce **3D-HiLoop**, which uses 3D point cloud representations in a learned world model to guide hierarchical diffusion policies. By predicting 3D scenes directly, our model handles occlusions better, reasons about contacts more accurately, and enables robust closed-loop refinement. On CALVIN and RLBench manipulation benchmarks, 3D-HiLoop reduces prediction error by 30-40% compared to 2D world models and achieves 20-25% higher task success rates in cluttered scenes.

### Method

**Architecture**:
1. **3D Encoder**: Point cloud (RGB-D) → PointNet++/Transformer
2. **3D World Model**: Predict next point cloud p_{t+1} from p_t and actions
3. **Hierarchical Policy**: Diffusion generates 3D waypoints, low-level executes
4. **Refinement**: Use 3D WM prediction error for replanning

**Key Innovation**: 3D representation maintains spatial structure
- Better contact prediction
- Occlusion-aware
- Multi-view consistent

**Loss Functions**:
```
L_3D_WM = Chamfer(p_{t+1}^pred, p_{t+1}^true) + L_feature
L_refine = ||d_3D(s_pred, w_k)||
```

### Experiments

**Benchmarks**:
- CALVIN (table-top manipulation with occlusions)
- RLBench (20 tasks with multi-object scenes)

**Metrics**:
- World model prediction error (Chamfer distance)
- Task success rate (especially cluttered scenes)
- Occlusion handling (hide objects, measure adaptation)

**Expected Results**:
| Method | Clean | Cluttered | Occlusions |
|--------|-------|-----------|-----------|
| 2D WM | 0.70 | 0.45 | 0.30 |
| **3D WM** | 0.72 | **0.60** | **0.50** |

**Improvement**: 30-40% in challenging scenes

### Ablations
1. 3D encoder vs 2D (isolate representation benefit)
2. Point cloud density (sparse vs dense)
3. Multi-view vs single-view

---

## Feasibility Analysis

### Technical Feasibility: 6.5/10

**Pros**:
- 3D representations mature (PointNet++, Transformers)
- 3D-VLA demonstrates 3D WMs work [Tong et al., ICML 2024]
- Point cloud processing well-established

**Cons**:
- THREE complex components (3D, WM, hierarchy)
- Computational cost high (point clouds expensive)
- Integration complexity

### Key Risks

**Risk #1: 3D WM Accuracy (35%, HIGH)**
- 3D prediction harder than 2D
- Point cloud noise sensitivity
- Chamfer distance may be misleading

**Risk #2: Computational Cost (30%, MEDIUM)**
- Point cloud networks slow (PointNet++: ~50-100ms)
- May not meet real-time requirements
- GPU memory intensive

**Risk #3: Integration with Hierarchy (25%, MEDIUM)**
- Three components to integrate
- Debugging complexity
- Error attribution difficult

### Timeline: 6.5/10 (6 months - VERY TIGHT)

**Month 1-2**: 3D encoder + world model
**Month 3**: Integration with hierarchical policy
**Month 4**: Experiments + debugging (likely overrun)
**Month 5-6**: Writing

**Assessment**: AMBITIOUS - three novel components

**Confidence**: 60%

### Resource Requirements

**Computational**:
- 4-8 GPUs (point clouds memory-intensive)
- ~$5-8K compute budget

**Data**:
- RGB-D demonstrations (CALVIN has depth)
- Point cloud preprocessing pipeline

**Expertise**:
- 3D deep learning (moderate difficulty)
- World models (user has)
- Hierarchical policies (user has)

---

## Confidence Scores

**P(Technical success)**: 65%
- 3D WM works: 70%
- Integration stable: 60%
- Computational feasible: 70%

**P(Experimental success)**: 70%
- Improvement in cluttered scenes: 75%
- Occlusion handling: 70%
- Overall success rate: 65%

**P(Publication - CoRL 2026)**: 68%
- Novel: 3D + WM + hierarchy (first combination)
- Risk: Complex, three components
- Fit: Good for CoRL

---

## Comparison to Other Ideas

**Advantages**:
- Clear motivation (3D spatial reasoning)
- Addresses occlusion problem (well-motivated)
- 3D-VLA validates 3D WMs work

**Disadvantages**:
- Complex (three components)
- Computationally expensive
- Higher risk than HiLoop (more components)

**Rank**: #5 overall (72% quality score)

---

## Recommendation

**Choose if**:
- Interested in 3D representations
- Have GPU resources (memory-intensive)
- Want to combine multiple frontier techniques

**Avoid if**:
- Risk-averse
- Limited compute
- Want simpler project

**Best Use**: Extension of HiLoop (if HiLoop succeeds, add 3D as follow-up)

---

## Key References

**3D Representations**:
[1] 3D-VLA [Tong et al., ICML 2024] - 3D world model for VLA
[2] DP3 [Ze et al., RSS 2024] - 3D diffusion policies
[3] 3D Diffuser Actor [Ke et al., CoRL 2024] - 3D scene representations

**Point Cloud Networks**:
[4] PointNet++ [Qi et al., NeurIPS 2017]
[5] Point Transformer [Zhao et al., ICCV 2021]

**World Models**:
[6] MoDem-V2 [Feng et al., 2024] - Manipulation world models
[7] DWL [Jiang et al., RSS 2024] - Denoising world models

**Hierarchical Policies**:
[8] ChainedDiffuser [Xian et al., CoRL 2023]
[9] HiLoop (our primary idea #1)

---

## Success Criteria

**Minimum Viable**:
- 15-20% improvement in cluttered scenes
- 3D WM prediction works (even if expensive)
- Demonstrate occlusion handling

**Target**:
- 30-40% improvement in challenging scenes
- Real-time feasible (<100ms per step)
- Strong ablations showing 3D benefit

**Stretch**:
- Multi-view consistency
- Generalizes to novel objects
- Real-world demonstration

---

## Alternative Formulations

If full 3D WM too complex:

**Simplification #1**: 3D encoder only (keep 2D WM)
- Use 3D features but predict in 2D
- Reduces complexity

**Simplification #2**: Voxel grid instead of point cloud
- Fixed resolution, easier to process
- Less flexible but faster

**Simplification #3**: Single-view depth (not full 3D)
- 2.5D representation
- Simpler than point clouds

---

## Strategic Fit

**Timeline**: Can pivot to this if HiLoop successful (Month 7-12)
**Resources**: Requires more compute than HiLoop
**Expertise**: Learnable but challenging
**Publication**: Good CoRL fit but higher risk

**Overall**: INTERESTING but RISKY for 6-month timeline
**Recommendation**: Extension/follow-up rather than primary project
