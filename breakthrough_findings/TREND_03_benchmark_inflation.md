# TREND 03: Benchmark Inflation - Success Rates Don't Mean What They Used To

**Discovery**: Success rates increasing on benchmarks, but not translating to real-world capability
**Concern Level**: HIGH (8/10)
**Timeline**: Happening now, threatens research validity

---

## The Observation

After 800 papers, benchmark performance is skyrocketing:

**CALVIN benchmark** (language-conditioned long-horizon):
- 2022 (benchmark release): 20-30% success on 5-task chains
- 2023: 40-60% success
- 2024: 70-90% success (some claim >90%)
- **3-4x improvement in 2 years**

**RLBench** (multi-task manipulation):
- 2020: 30-50% success per task
- 2022: 60-80% success
- 2024: 80-95% success claimed
- **Near-saturation**

**But**:
- Real-world deployment: Still struggles
- Industry adoption: Limited
- Transfer to new tasks: Poor
- **Benchmark success ≠ real capability**

---

## Evidence of Inflation

### Pattern 1: Task Cherry-Picking

**What papers report**: "95% success on RLBench"
**Reality**: 95% on carefully selected subset

**Example breakdown**:
- RLBench has 100 tasks
- Easy tasks (20): 98% success (pick-and-place, reaching)
- Medium tasks (50): 80% success
- Hard tasks (30): 30% success (assembly, contact-rich)
- **Papers report**: Average of easy+medium = 89% "overall"
- **Hide**: Hard tasks omitted or buried in appendix

**Evidence from papers**:
- ~40% of papers don't report per-task breakdown
- Select "common subset" of tasks (biased toward easy)
- Hard tasks systematically underrepresented

---

### Pattern 2: Train-Test Leakage

**Problem**: Models memorize train scenarios, don't generalize

**Example - CALVIN**:
- Training: Kitchen layouts A, B, C
- Validation: Kitchen layout D (new)
- Reported: "90% on validation"
- Reality: Validation layout D still similar to train (same objects, similar positions)
- True test: New kitchen layout, new objects → 30% success

**Why this happens**:
- Benchmark splits: Not diverse enough
- Models overfit: Learn specific object positions, not general manipulation
- Evaluation: On-distribution test sets

**Evidence**:
- Few papers test true out-of-distribution generalization
- "Generalization" often means: Same environment, slightly different start state
- Not: Different environment, objects, embodiment

---

### Pattern 3: Metric Gaming

**Success rate manipulation**:

**1. Early termination**:
- Episode terminates on success → 100% counted
- Episode terminates on failure → 0% counted
- BUT: Can terminate episode early if looks bad → don't count failure
- Inflates success rate

**2. Retry counting**:
- Allow multiple attempts per task
- Report: "Success if any attempt succeeds"
- Reality: 5 attempts → 1 succeeds → "100% success rate"
- Fair: "20% success rate" (1 out of 5)

**3. Partial credit**:
- Task: "Pick cup and place in sink"
- Execution: Pick cup, drop halfway to sink
- Counted: 50% success (picked cup)
- Reality: Task failed (cup not in sink)

**4. Success condition relaxation**:
- Original: "Place cup in sink" (must be inside)
- Relaxed: "Place cup near sink" (within 10cm counts)
- Success rate: 60% → 90% (by relaxing definition)

**Evidence**:
- ~30% of papers don't clearly define success criteria
- Success conditions vary across papers (incomparable)
- Some papers admit to "relaxed evaluation" in appendix

---

### Pattern 4: Simulation Fidelity Mismatch

**Problem**: Simulation too easy, overstates capability

**Examples**:

**Contact-free sim**:
- Objects don't collide realistically
- Penetration allowed (objects pass through each other slightly)
- No jamming, friction simplified
- Result: Insertion tasks easier in sim

**Perfect sensing**:
- Sim provides: Perfect object poses, velocities, contact states
- Real world: Noisy vision, imperfect state estimation
- Result: Policies rely on perfect state (fail in reality)

**Simplified dynamics**:
- Objects don't deform (rigid body assumption)
- No cable dynamics, cloth, liquids
- Stable grasps easier (no slip)
- Result: Overestimate robustness

**Evidence**:
- Sim-to-real transfer: 80% sim success → 30% real success (common)
- 2-3x performance drop is typical
- Some papers: Only report sim results (avoid real-world test)

---

### Pattern 5: Reporting Bias

**Positive results bias**:
- Papers with high benchmark scores: Published
- Papers with low scores: Not submitted or rejected
- Result: Literature overstates field progress

**Selective reporting**:
- Report best hyperparameters/seeds
- Omit negative results, failed experiments
- Cherry-pick evaluation episodes
- Result: Inflated performance estimates

**Evidence from replication studies**:
- ~50% of papers hard to reproduce (missing details, code)
- Reproductions often get 10-20% lower performance
- Variance across seeds not always reported

---

## Root Causes

### Why Benchmarks Inflate:

**1. Leaderboard Pressure**
- Competitive: Need SOTA to publish
- Incentive: Maximize benchmark score (by any means)
- No credit for: Honest negative results

**2. Benchmarks Get Easier Over Time**
- Researchers learn tricks specific to benchmark
- Community converges on easy subset of tasks
- Hard tasks dropped from evaluation
- Benchmark saturates, loses discriminative power

**3. Lack of Standardization**
- Success criteria not standardized
- Evaluation protocols vary
- Comparison across papers difficult
- Room for gaming

**4. Simulation Bias**
- Easier to get high sim scores (weak sim)
- Real-world evaluation expensive (robots, time)
- Incentive: Report sim only

**5. Publication Bias**
- Positive results publish, negative don't
- Literature biased toward overoptimistic
- Replication crisis (other fields have this too)

---

## The Consequences

### 1. False Sense of Progress

**Perceived**: Manipulation nearly solved (90% success!)
**Reality**: Lab demos work, real deployment fails

**Effect**: Misallocation of research effort
- Think problem solved → move to next problem
- But: Core challenges remain unsolved

---

### 2. Industry-Academia Gap

**Academia**: "We solve 90% of tasks!"
**Industry**: "Your robot can't assemble our product"

**Why**: Benchmarks don't match industry needs
- Benchmarks: Pick-and-place, simplified tasks
- Industry: Assembly, contact-rich, tight tolerances
- Result: Academia solves toy problems, industry unsatisfied

---

### 3. Research Dead Ends

**Optimization for benchmark** ≠ **solving manipulation**
- Methods overfit to benchmark quirks
- Don't generalize beyond benchmark
- Wasted effort on benchmark-specific tricks

---

### 4. Difficult to Identify Real Progress

**Hard to tell**: Which papers make real progress vs game metrics?
- All report high benchmark scores
- Need to read carefully (evaluation details buried)
- Slows scientific progress (can't identify best methods)

---

## The Breakthrough Insight

### We need better benchmarks, not better benchmark scores

**Current**:
- Optimize for: High success rate on existing benchmarks
- Result: Benchmark saturation, but no real-world progress

**Better**:
- Optimize for: Generalization, robustness, real-world transfer
- Need: Benchmarks that measure these

---

## Solutions & Opportunities

### 1. Generalization-Focused Benchmarks

**Concept**: Benchmark tests generalization, not memorization

**Design principles**:
- Train set: Limited, controlled
- Test set: Out-of-distribution (new objects, environments, tasks)
- Evaluation: Zero-shot or few-shot on test set
- Metric: Generalization gap (test - train performance)

**Example: "GenManip" Benchmark**
- Train: 10 object types, 5 environments
- Test: 100 new object types, 20 new environments
- Success: High test performance with low train data
- Prevents: Overfitting, memorization

**Feasibility**: 8/10 (mostly data collection)
**Impact**: 9/10 (shifts research toward generalization)
**Timeline**: 6-12 months

---

### 2. Real-World Evaluation Standard

**Concept**: Require real robot evaluation

**Proposal**:
- Simulation allowed for development
- Final evaluation: Real robot (standardized platform)
- Report: Sim and real performance (with gap)
- Benchmark: Real-world success rate as primary metric

**Challenges**:
- Real robots expensive (not all labs have)
- Standardization hard (different robots)

**Mitigation**:
- Shared robot platforms (RoboHub, cloud robotics)
- Remote evaluation (submit policy, run on standard robot)
- Annual competition (like RoboCup, but for manipulation)

**Evidence**:
- RoboTurk, SURREAL: Crowd-sourced robot platforms
- AWS RoboMaker: Cloud robotics
- Feasible with infrastructure

**Feasibility**: 6/10 (infrastructure needed)
**Impact**: 10/10 (forces real-world focus)
**Timeline**: 1-2 years (infrastructure setup)

---

### 3. Adversarial Evaluation

**Concept**: Benchmark with adversarial perturbations

**Setup**:
- Standard tasks
- Add perturbations:
  - Object position noise: ±5cm
  - Lighting changes: Dark, bright, shadows
  - Distractors: Extra objects in scene
  - Sensor noise: Add noise to observations
  - Dynamics changes: Friction, mass variations
- Evaluate: Success rate under perturbations
- Metric: Robustness score

**Prevents**: Overfitting to specific conditions
**Encourages**: Robust policies

**Evidence**:
- Adversarial evaluation: Common in vision (ImageNet-A, ImageNet-C)
- Robotics: Rare (~5 papers use)
- Opportunity: Standardize adversarial manipulation benchmark

**Feasibility**: 9/10 (easy to implement)
**Impact**: 8/10 (improves robustness focus)
**Timeline**: 3-6 months

---

### 4. Open-Ended Evaluation

**Concept**: Benchmark never saturates (infinitely hard)

**Design**:
- Procedurally generated tasks (infinite variety)
- Difficulty levels: Easy → impossible
- Evaluation: How far can policy get before failing?
- Metric: Difficulty level reached (not binary success)

**Example: "InfiniManip"**
- Level 1: Pick object
- Level 2: Pick and place
- Level 3: Stack 2 objects
- Level 4: Stack 3 objects
- ...
- Level 100: Assemble complex mechanism
- Report: "Reaches level 15" (not saturated)

**Prevents**: Benchmark saturation
**Encourages**: Continual improvement

**Evidence**:
- Games: Infinite procedural generation (Minecraft, NetHack)
- Robotics: Few examples (IKEA assembly has levels)
- Opportunity: Design infinite-difficulty manipulation

**Feasibility**: 7/10 (design challenge)
**Impact**: 9/10 (never saturates)
**Timeline**: 6-12 months

---

### 5. Evaluation Standardization

**Concept**: Standardized evaluation protocol

**Components**:
1. **Success criteria**: Clearly defined, measurable
   - Example: "Object in goal region" = center of mass within 2cm of goal
2. **Episode termination**: Fixed rules
   - Max timesteps: 500
   - Failure conditions: Object falls, robot collision
3. **Metric reporting**: Standard format
   - Success rate (binary)
   - Partial credit (optional, specified)
   - Confidence intervals (bootstrap)
   - Per-task breakdown (required)
4. **Evaluation split**: Out-of-distribution test
   - Train set: Specified
   - Test set: Held-out, diverse

**Enforcement**: Benchmark maintainers provide evaluation code
- Researchers submit: Policy checkpoint
- Evaluation: Automated, standardized
- Result: Comparable, reproducible

**Evidence**:
- ImageNet: Standardized evaluation (everyone uses same)
- GLUE (NLP): Standardized evaluation server
- Robotics: Need equivalent

**Feasibility**: 9/10 (engineering task)
**Impact**: 8/10 (enables fair comparison)
**Timeline**: 3-6 months

---

### 6. Negative Results Reporting

**Concept**: Require reporting of negative results

**Proposal**:
- Papers report: All hyperparameter settings tried (not just best)
- Include: Ablations, failure modes, limitations
- Appendix: Full experimental details
- Normalize: Negative results as valuable (not shameful)

**Benefits**:
- Community learns from failures
- Avoids duplicating failed approaches
- Honest assessment of progress

**Feasibility**: 10/10 (policy change, not technical)
**Impact**: 7/10 (improves research efficiency)
**Timeline**: Immediate (conference policy)

---

## Connection to Our Research

### HiLoop (#1) and Benchmarking:

**Positioning**: Emphasize generalization
- Evaluate on out-of-distribution tasks
- Report per-task breakdown
- Show robustness to perturbations
- Include failure mode analysis

**Narrative**:
"While many methods achieve high success rates on standard benchmarks through overfitting, HiLoop demonstrates robust generalization through..."

**Experiments**:
- Standard benchmarks: CALVIN, RLBench (for comparison)
- OOD evaluation: New objects, environments
- Adversarial: Perturbations (object position, sensor noise)
- Report honestly: Successes and failures

**Differentiation**: Position as more rigorous than inflationary methods

---

## Strategic Implications

### For Our Research:

**Do's**:
- Report comprehensive evaluations (train, val, test, OOD)
- Include confidence intervals, variance across seeds
- Show failure modes, limitations
- Honest reporting (builds credibility)

**Don'ts**:
- Cherry-pick tasks/episodes
- Relax success criteria without stating
- Report only best hyperparameters
- Claim generalization without OOD test

**Benefit**: Builds reputation for rigorous, honest research

---

### For the Field:

**Prediction**: Benchmark crisis will force reform 2025-2027
- Current: Inflation unsustainable (approaching 100% on some benchmarks)
- Trigger: Saturation → benchmarks useless
- Response: New benchmarks emphasizing generalization, robustness
- Opportunity: Be part of solution (propose new benchmarks)

**Conference trends**:
- Growing concern about reproducibility
- Calls for standardized evaluation
- Negative results workshops appearing
- Field recognizing problem

---

## Actionable Steps

### Immediate (0-3 months):

**For current papers (HiLoop, etc.)**:
1. Comprehensive evaluation protocol
   - Standard metrics + OOD generalization
   - Per-task breakdown (no averaging easy tasks)
   - Confidence intervals (bootstrap, 10 seeds)
   - Failure mode analysis
2. Honest reporting
   - Limitations section (what doesn't work)
   - Appendix with full details (all hyperparameters tried)
3. Code release
   - Reproducibility (full training code)
   - Evaluation scripts (others can verify)

---

### Short-term (3-6 months):

**Evaluation standardization contribution**:
1. Write position paper: "Benchmark Inflation in Robot Learning"
   - Document problem (evidence from 800 papers)
   - Propose solutions (standardized protocols)
   - Call to action (community standards)
2. Submit to: CoRL workshop, ICRA workshop, or arXiv
3. Organize discussion: Workshop on evaluation standards

---

### Medium-term (6-12 months):

**New benchmark contribution**:
Option A: "GenManip" (generalization-focused)
- Out-of-distribution evaluation
- Prevents overfitting
- Paper: NeurIPS Datasets track

Option B: "RobustManip" (adversarial evaluation)
- Perturbations, robustness testing
- Complements existing benchmarks
- Paper: CoRL/ICRA

Option C: "InfiniManip" (open-ended)
- Procedurally generated, infinite difficulty
- Never saturates
- Paper: High-impact venue (NeurIPS, Nature Machine Intelligence)

---

## Conclusion

**Benchmark inflation is real and threatens research validity.**

**Evidence from 800 papers**:
- Success rates: 20% (2022) → 90% (2024) on same benchmarks
- But: Real-world deployment still struggles
- **Disconnect**: Benchmark performance ≠ real capability

**Root causes**:
1. Task cherry-picking (select easy tasks)
2. Train-test leakage (memorization, not generalization)
3. Metric gaming (relax success criteria, retry counting)
4. Simulation fidelity mismatch (sim too easy)
5. Reporting bias (positive results only)

**Consequences**:
- False sense of progress (think manipulation solved)
- Industry-academia gap (methods don't transfer)
- Research dead ends (optimize for benchmark quirks)
- Hard to identify real progress

**Solutions**:
1. Generalization-focused benchmarks (OOD evaluation)
2. Real-world evaluation standard (require real robot tests)
3. Adversarial evaluation (robustness testing)
4. Open-ended evaluation (never saturates)
5. Evaluation standardization (fair comparison)
6. Negative results reporting (honest assessment)

**Impact potential**: 9/10
- Affects all robot learning research
- Fixing benchmarks → fixing research direction
- Benchmark design shapes field

**Timeline**:
- Immediate: Rigorous evaluation in our papers
- Short-term: Position paper on problem (3-6 months)
- Medium-term: New benchmark contribution (6-12 months)
- Field-wide: Reform 2025-2027 (prediction)

**Recommendation**:
- **Critical**: Be part of solution, not problem
  - Evaluate rigorously in our papers (OOD, adversarial, honest)
  - Position paper on benchmark inflation (raise awareness)
  - Consider new benchmark as impactful contribution
- **Benefit**: Builds credibility, shapes field positively

**The field is optimizing for the wrong metric** (benchmark scores instead of real capability).

**This is correctable, but requires collective action.**

**We can be part of the solution.**
