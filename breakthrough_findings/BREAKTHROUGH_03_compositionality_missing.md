# BREAKTHROUGH 03: The Compositionality Gap in Generative Control

**Discovery**: Generative models learn monolithic policies, missing compositionality
**Opportunity Level**: VERY HIGH (9/10)
**Timeline**: Major research direction for next 3-5 years

---

## The Observation

After reviewing 800 papers, a striking pattern:

**Classical robotics** (pre-2020):
- Motion primitives (DMPs)
- Composable skills
- Libraries of behaviors
- Mix-and-match at test time

**Modern generative models** (2020-2024):
- End-to-end diffusion policies
- Task-specific training
- **No composition**
- Learn from scratch for each task

**We threw away compositionality when we moved to generative models!**

---

## The Problem

### Current Paradigm: Monolithic Learning

**Typical workflow**:
```
Task A → Train Diffusion Policy A (3000 demos)
Task B → Train Diffusion Policy B (3000 demos)
Task A+B → Train from scratch (6000 demos)
```

**Issues**:
1. No transfer learning
2. Data inefficient (need demos for everything)
3. Can't generalize to new combinations
4. No zero-shot composition

### What We Lost from Classical Robotics:

**Dynamic Movement Primitives (DMPs)**:
```
Primitive: reach(object)
Primitive: grasp()
Primitive: place(location)

New task: pick_and_place = reach → grasp → reach → place
```

**Worked via composition, no new training needed!**

**Why we abandoned it**:
- DMPs limited expressiveness
- Hard to learn from demos
- Fixed parametric forms

**What we gained with diffusion**:
- Expressive (multimodal, high-dimensional)
- Easy to learn from demos
- No parametric assumptions

**What we lost**:
- Compositionality
- Zero-shot generalization
- Data efficiency for new tasks

---

## Why Nobody Solved This Yet

### Challenge 1: Composition in Latent Space

**Traditional composition**: Add/sequence primitives in action space
```
action = primitive_1(s) + primitive_2(s)
```

**Diffusion composition**: ???
- Diffusion works in distribution space
- How to "add" distributions?
- Score addition works but limited to additive structure

**Why hard**: Composition in probability space non-trivial.

### Challenge 2: Temporal Composition

**Sequential composition**:
```
Task = Skill_1 → Skill_2 → Skill_3
```

**Questions**:
- When to transition? (termination conditions)
- How to handle skill boundaries? (smoothness)
- What if skills overlap? (blending)

**Current work (SCaR, EXTRACT)**: Skill chaining, but skills discrete
**Our gap**: Continuous diffusion primitive composition

### Challenge 3: Hierarchical Composition

**Tasks have structure**:
```
Make_coffee:
  - Reach_cup
    - Move_arm
      - Joint_commands
```

**Current**: Learn everything end-to-end
**Missing**: Compositional hierarchy

---

## The Breakthrough Insight

### Composable Diffusion Policies

**Key idea**: Learn a library of diffusion primitives, compose at test time

**Architecture**:
```
Library: {reach(·), grasp(·), place(·), ...}
Each primitive: Diffusion policy in latent space

Composition:
new_task = λ₁·reach(s) + λ₂·grasp(s) + ...
where λᵢ learned by meta-policy
```

**Advantages**:
- Zero-shot: Compose for unseen tasks
- Data-efficient: Reuse learned primitives
- Interpretable: See which primitives active

---

## Specific Opportunities

### 1. Latent Diffusion Composition

**Concept**: Learn primitives in shared latent space, compose there

**Technical approach**:
- Encode states to latent: z = φ(s)
- Learn primitive diffusions: π_i(a | z)
- Compose in latent space: π_new = Σ w_i(z) · π_i(a | z)
- Weights w_i learned or hand-specified

**Feasibility**: MEDIUM (6/10) - needs latent space engineering
**Novelty**: VERY HIGH (9/10)
**Impact**: VERY HIGH (9/10)

**Related work**: SkillDiffuser does skill composition, but discrete skills
**Our addition**: Continuous composition in latent space

---

### 2. Compositional Flow Matching

**Concept**: Flow matching may be EASIER to compose than diffusion

**Why**:
- Flows are vector fields: v₁(x) + v₂(x) = v_composed(x)
- Additive composition natural
- No probability space issues

**This could be HUGE**: Flow matching + compositionality

**Feasibility**: HIGH (7/10) - mathematically cleaner
**Novelty**: VERY HIGH (9/10)
**Impact**: VERY HIGH (9/10)

**Nobody tried this** (800 papers, found 0)

---

### 3. Hierarchical Compositional Diffusion

**Concept**: Compose at multiple levels

**Level 1 (High)**: Task composition
```
new_task = compose(task_primitives)
```

**Level 2 (Mid)**: Waypoint composition
```
waypoint_sequence = compose(waypoint_primitives)
```

**Level 3 (Low)**: Action composition
```
action = compose(motion_primitives)
```

**Feasibility**: LOW (5/10) - very complex
**Novelty**: EXTREME (10/10)
**Impact**: EXTREME (10/10) if successful

---

### 4. Meta-Learning for Composition Weights

**Concept**: Learn how to weight primitives for new tasks

**Setup**:
- Pre-train: Library of K primitives
- Meta-train: Learn weighting function w(task, state)
- Test: Compose primitives with learned weights

**This is few-shot learning via composition**

**Feasibility**: MEDIUM (6/10)
**Novelty**: HIGH (8/10)
**Impact**: HIGH (8/10)

**Related**: MAML, meta-RL, but not for diffusion

---

### 5. Compositional World Models

**Concept**: Compose not just policies, but world models too

**Idea**:
- Learn object-centric world models
- Each object has dynamics model
- Compose for multi-object scenes

**Enables**: Combinatorial generalization (new object combinations)

**Feasibility**: MEDIUM (6/10)
**Novelty**: HIGH (8/10)
**Impact**: HIGH (8/10)

---

## Evidence from 800 Papers

### Papers that hint at compositionality:

**1. SkillDiffuser** (CVPR 2024):
- Skill-based hierarchy with diffusion
- But: Discrete skills, not continuous composition

**2. EXTRACT** (CoRL 2024):
- Extracts skills from offline data
- But: No composition mechanism

**3. SCaR** (NeurIPS 2024):
- Skill chaining for long-horizon
- But: Sequential only, no parallel composition

**4. Subgoal Diffuser**:
- Composes subgoals
- But: MPC-based, not learned composition

**Common pattern**: Everyone realizes need for composition, nobody solved it for generative models.

---

## Why This Matters

### Data Efficiency:

**Current**: N tasks → N×M demos
**With composition**: K primitives → K×M demos, compose to N tasks

**If K << N**: Massive data savings

**Example**:
- 100 tasks, each needs 1000 demos = 100K demos
- vs 20 primitives, 1000 demos each = 20K demos
- **5x data efficiency**

### Zero-Shot Generalization:

**Current**: Unseen task → Need demos, retrain
**With composition**: Compose existing primitives

**Example**:
- Learned: reach(red), reach(blue), grasp_sphere, grasp_cube
- New task: reach(red) + grasp_cube
- **Zero-shot**: No training needed

### Combinatorial Generalization:

**K primitives → 2^K possible compositions**

If K=20 primitives → 1 million combinations
Only need to learn 20, get million for free

**This is holy grail of generalization**

---

## Connection to Other Insights

### Relates to Hierarchical-Generative Gap:

**Hierarchical RL** has compositional skills (options framework)
**Generative models** lack composition

**Bridge**: Bring compositionality from RL to diffusion

### Relates to Flow Matching:

**Flow matching may enable composition** (vector field addition)

**Opportunity**: Compositional Flow Matching (new research direction)

### Relates to World Models:

**Object-centric world models** are compositional
**Policy composition** + **WM composition** = **Compositional control system**

---

## Technical Challenges

### Challenge 1: Primitive Discovery

**Question**: How to discover good primitives?

**Options**:
- Hand-design (domain knowledge)
- Unsupervised discovery (clustering demos)
- Mutual information maximization
- Successor features

**This is a research problem** (unsolved for diffusion)

### Challenge 2: Smooth Transitions

**Question**: How to smoothly transition between primitives?

**Options**:
- Soft weighting (blend probabilities)
- Learned transitions
- Hierarchical structure

**Need to solve** for practical systems

### Challenge 3: Credit Assignment

**Question**: Which primitive helped/hurt?

**Options**:
- Track primitive activations
- Gradient attribution
- Ablation studies

**Important for learning** weights

---

## Theoretical Foundation Needed

### Compositionality Theory for Diffusion

**Questions to answer**:
1. When is composition valid? (conditions)
2. How does composition affect distribution? (theory)
3. What are optimality conditions? (guarantees)

**This could be ICML/NeurIPS theory paper**

**Math needed**:
- Probability theory (composition of distributions)
- Optimal transport (for flow matching)
- Category theory? (composition algebra)

---

## Strategic Roadmap

### Phase 1 (2024-2025): Proof of Concept

**Goal**: Show compositional diffusion works

**Approach**:
- Simple setting (2-3 primitives)
- Hand-designed primitives
- Manual composition

**Publication**: Workshop paper or short paper

### Phase 2 (2025-2026): Scaled System

**Goal**: Learn primitive library, automatic composition

**Approach**:
- 10-20 primitives
- Learned composition weights
- Meta-learning for new tasks

**Publication**: CoRL/RSS main conference

### Phase 3 (2026-2027): Theoretical Foundation

**Goal**: Understand when/why composition works

**Approach**:
- Theoretical analysis
- Sample complexity bounds
- Optimality conditions

**Publication**: ICML/NeurIPS theory track

---

## Practical Applications

### Robotics:

**Task**: "Tidy the room"
**Decomposition**:
- Reach(object_1) → Grasp(object_1) → Place(shelf)
- Reach(object_2) → Grasp(object_2) → Place(drawer)
- ...

**With composition**:
- Learn once: reach, grasp, place primitives
- Apply to all objects
- No retraining needed

### Manipulation:

**Task**: "Assemble furniture"
**Decomposition**:
- Align(part_1, part_2)
- Insert(screw, hole)
- Tighten(screw)

**Composition enables**:
- Transfer to new furniture
- Generalize to different parts

---

## Comparison to Alternatives

### vs Mixture of Experts (MoE):

**MoE**: Discrete switching between experts
**Composition**: Continuous blending

**Advantages**:
- Smooth transitions
- Richer expressiveness
- No hard boundaries

### vs Multi-Task Learning:

**Multi-task**: Joint training on all tasks
**Composition**: Combine separately learned primitives

**Advantages**:
- Add new primitives without retraining all
- More modular
- Better interpretability

### vs Meta-Learning:

**Meta-learning**: Adapt to new tasks quickly
**Composition**: Zero-shot via recombination

**Advantages**:
- No adaptation needed
- Truly zero-shot
- Faster at test time

**Could combine**: Meta-learn composition weights

---

## Risks & Challenges

### Risk 1: Primitive Interference

**Problem**: Primitives may conflict
- reach_left vs reach_right
- What's correct composition?

**Mitigation**:
- Mutual exclusion constraints
- Learned arbitration
- Context-dependent weighting

### Risk 2: Curse of Dimensionality

**Problem**: Too many primitives → hard to search

**Mitigation**:
- Hierarchical organization
- Semantic clustering
- Attention mechanisms

### Risk 3: Negative Transfer

**Problem**: Wrong primitive hurts performance

**Mitigation**:
- Sparse composition (only activate relevant primitives)
- Regularization
- Ablation

---

## Conclusion

**Compositionality is the missing ingredient in generative control.**

**Evidence**:
- Classical robotics had it (DMPs, primitives)
- Modern generative models lost it
- 800 papers: 3-4 touch it, none solve it

**Opportunity**:
- Massive data efficiency gains
- Zero-shot generalization
- Combinatorial generalization

**Challenges**:
- Technical (composition in probability space)
- Theoretical (when is composition valid?)
- Practical (primitive discovery)

**Timeline**: This is 3-5 year research direction, not 6-month project

**Our role**: HiLoop doesn't directly address this, but compositional diffusion waypoints could be future work

**Recommendation**: Keep on radar, potentially pursue after HiLoop

**This is FRONTIER research** - solving this would be major contribution to the field.
