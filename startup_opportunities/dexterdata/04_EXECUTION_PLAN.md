# Execution Plan - Dual-Goal Validation Roadmap

**Last Updated**: 2025-11-15
**Status**: Pre-launch
**Timeline**: 6 weeks to validation, 5 months to dataset release
**Total Investment**: $13,500

---

## Overview

This is your step-by-step playbook with **dual objectives**:

### 🎯 Goal 1: Business Validation
Prove DexterData is a viable startup (data collection service for robotics companies)

### 🎓 Goal 2: Research Portfolio
Use this project as on-ramp to robotics research / PhD applications

**The strategy**: Start with 1 pair of gloves. Collect data + train policies in sim. Validate both market demand AND technical feasibility. This project becomes your research credential.

**Why this works**:
- ✅ If business succeeds → You have a startup
- ✅ If research succeeds → You have PhD portfolio
- ✅ Most likely: Both partially succeed → Multiple career options

**"Do things that don't scale"** - Paul Graham

---

## Phase 0: Technical + Business Validation (Weeks 1-6, $2,300)

### Objective
Prove BOTH that the dataset is valuable (business) AND that you can train policies (research).

**Success criteria (Business Validation)**:
- ✅ Collect 20 hours (200 demos) of research-quality data
- ✅ 15+ out of 30 robotics researchers say "we'd use a larger version"
- ✅ 5+ researchers successfully LOAD and USE your data (not just say they would)
- ✅ 2+ offer to collaborate/contribute

**Success criteria (Research Validation)**:
- ✅ Successfully retarget human hand data → simulated robot hand
- ✅ Train at least one manipulation policy in simulation
- ✅ Achieve >30% success rate on simple task (cube rotation or folding)
- ✅ Learn core skills: Isaac Gym, policy training, kinematics

**If this fails**: You learned it for $2,300 instead of $50K+. But you gained robotics skills worth 1-2 semesters of grad school.

---

### Week 1: Equipment & Setup + Simulation Prep

**Monday**

**Morning (Business Track)**: Purchase equipment
```
Shopping list:
□ Rokoko Smartgloves (1 pair): $1,795
  Link: https://www.rokoko.com/products/smartgloves

□ Smartphone mount (egocentric view): $20
  Recommendation: GoPro chest mount or head strap

□ Tripod (third-person view): $30
  Any basic tripod for phone/camera

□ Storage setup: $50/month
  Google Drive (2TB) or AWS S3

Total: $1,895
```

**Afternoon (Research Track)**: Simulation setup
```
□ Check hardware requirements
  - NVIDIA GPU required (GTX 1060+ or better)
  - CUDA 11.3+ installed
  - 16GB+ RAM recommended

□ Install Isaac Gym (NVIDIA's physics simulator)
  - Download from: https://developer.nvidia.com/isaac-gym
  - Follow installation guide
  - Run example: python examples/hand_example.py

□ If Isaac Gym installation fails:
  - Alternative: MuJoCo (easier installation)
  - Download: https://mujoco.org/
  - Run shadow hand example

□ Read 2-3 key papers (skim, don't deep read yet):
  - "Diffusion Policy" (Chi et al., 2023)
  - "DexMV: Imitation Learning for Dexterous Manipulation" (2023)
  - "Learning from Play" (Lynch et al., 2020)

Goal: Understand what you're building towards
```

**Evening**: Administrative setup
```
□ Create project tracking spreadsheet
  Columns: Demo ID, Task, Duration, Quality Score, Notes

□ Set up Google Drive folder structure:
  /raw_data
    /video_egocentric
    /video_third_person
    /glove_data
  /processed_data
  /documentation
  /samples_for_researchers
```

**Tuesday**

**Morning**: Research preparation
```
□ Identify 30 target robotics researchers

  Categories:
  - 10 manipulation labs (Berkeley, Stanford, CMU, MIT, UW)
  - 10 humanoid companies (Figure, 1X, Tesla, Sanctuary)
  - 10 recent dexterous manipulation paper authors

□ Find their emails (lab websites, papers, LinkedIn)

□ Draft validation email template (see template below)
```

**Afternoon**: Recording space setup
```
□ Choose recording location (kitchen ideal)

□ Set up lighting
  - Natural light preferred
  - No harsh shadows
  - Consistent across recordings

□ Set up camera positions
  - Egocentric: Chest or head mount
  - Third-person: Tripod at 45° angle, 3-4 feet away

□ Test recording (no gloves yet, just video quality)
```

**Wednesday** (Gloves arrive)

**Morning**: Glove setup & calibration
```
□ Unbox, charge gloves (2-3 hours)

□ Download Rokoko Studio (free)
  https://www.rokoko.com/studio

□ Complete calibration
  - Follow Rokoko's calibration wizard
  - Practice putting on/taking off gloves
  - Verify tracking quality (hand movements should be smooth)

□ Test export formats
  - FBX, BVH, CSV - try all
  - Understand data structure (joint angles, timestamps)
```

**Afternoon**: First test recordings
```
□ Record 10 simple test demos (5 min each)
  - Picking up objects
  - Opening containers
  - Folding cloth

□ Goals:
  - Get comfortable with workflow
  - Identify technical issues
  - Verify data quality

□ Review recordings
  - Check finger tracking accuracy
  - Verify video synchronization
  - Note any drift or errors
```

**Thursday-Sunday**: Build data pipeline

```
□ Create data processing workflow

  Step 1: Export glove data from Rokoko Studio
  Step 2: Trim video to match glove data timestamps
  Step 3: Sync video + glove data (aligned by timestamp)
  Step 4: Label task category, objects used, success/failure
  Step 5: Quality check (tracking drift <10°, video clear)

□ Document every issue/quirk

□ Create data format specification
  - Exactly what data is included
  - File structure, naming conventions
  - How to load/visualize

□ Build simple visualization tool
  - Plot joint angles over time
  - Overlay on video (if possible)
  - Makes data easier to understand for researchers
```

---

### Week 2-3: Collect 20 Hours (200 Demos)

**Objective**: High-quality demonstrations across diverse manipulation tasks

**Daily Routine**:
```
Morning (2 hours):
- Plan 10 tasks for the day
- Prepare objects/materials needed
- Set up recording area

Afternoon (2 hours):
- Record 10 demos (10-15 min each average)
- Short breaks between demos
- Stay fresh (quality over speed)

Evening (1 hour):
- Export glove data
- Label demonstrations
- Quality check recordings
- Back up to cloud storage
```

**Task Selection** (200 demos total)

**Category 1: In-Hand Manipulation** (80 demos) - **HIGHEST PRIORITY**
```
Why: RealDex only has 2.6K sequences - huge gap
      Essential for dexterous robots

Tasks:
□ Object reorientation (40 demos)
  - Rotate cube in hand (different sizes)
  - Rotate bottle, cylinder, irregular objects
  - Reposition for better grasp

□ Grasp transitions (40 demos)
  - Power grasp → precision pinch
  - Two-handed → one-handed transfer
  - Adjust grip without dropping

Objects: Cubes, bottles, tools, spheres, irregular shapes
```

**Category 2: Bimanual Coordination** (60 demos)
```
Why: Requires two-hand coordination
      Critical for humanoid robots

Tasks:
□ Container opening (20 demos)
  - Jars (twist lid while holding base)
  - Bottles (twist cap, pull cork)
  - Boxes (hold + pull tab)
  - Bags (hold + tear open)

□ Food preparation (20 demos)
  - Cutting vegetables (hold + knife)
  - Peeling (hold + peeler)
  - Pouring liquid (hold cup + pitcher)

□ Tool use requiring two hands (20 demos)
  - Screwdriver (hold object + turn screw)
  - Pliers (squeeze while manipulating wire)
  - Wrench (hold + turn)

Objects: Various containers, kitchen items, hand tools
```

**Category 3: Fabric Manipulation** (40 demos)
```
Why: Deformable objects underrepresented in datasets
      Very challenging for robots

Tasks:
□ Folding (30 demos)
  - T-shirts (different sizes)
  - Pants
  - Towels (bath, hand, dish)
  - Sheets

□ Hanging/draping (10 demos)
  - Hanging shirts on hangers
  - Draping towel over rack
  - Folding and placing in drawer

Objects: Various garments, different fabrics/sizes
```

**Category 4: Precision Assembly** (20 demos)
```
Why: Requires fine motor control
      Industrial application potential

Tasks:
□ Screwing/unscrewing (10 demos)
  - Screws into wood
  - Bolts with nuts
  - Different screw sizes

□ Insertion tasks (10 demos)
  - USB cable into port
  - Key into lock
  - Pen into holder
  - Plug into outlet (be careful!)

Objects: Screws, cables, connectors, various hardware
```

**Quality Standards** (Critical)

```
For EACH demo, verify:
✅ Glove calibration good (no drift >10°)
✅ Both hands tracked fully
✅ Video shows clear view of manipulation
✅ Task completed successfully (or intentional failure)
✅ Duration appropriate (5-15 min for most tasks)

If ANY quality issue:
❌ Delete and re-record
   (Better to have 180 perfect demos than 200 mediocre)
```

**Tracking Progress**

```
Spreadsheet columns:
| Demo ID | Date | Task | Objects | Duration | Quality | Notes |

Example:
| D001 | 2025-11-15 | Rotate cube in hand | Red cube 2" | 00:08:32 | 9/10 | Minor drift at end |
| D002 | 2025-11-15 | Open jar | Pickle jar | 00:05:15 | 10/10 | Perfect tracking |

Daily target: 10 demos
Weekly target: 70 demos
Total: 200 demos in 3 weeks (14 recording days)
```

---

### Week 4: Package & Validate with Researchers (Hands-On Testing)

**Monday-Tuesday**: Create professional dataset package

**Dataset README.md**:
```markdown
# DexManip-20: Dexterous Manipulation Dataset (Preview)

## Overview
20 hours of human manipulation demonstrations with full finger tracking
- 200 demonstrations across 4 task categories
- Rokoko Smartgloves (20 DOF per hand, 100Hz)
- Egocentric + third-person video (1080p, 30fps)
- Synchronized, timestamped, labeled

## Task Breakdown
| Category | Count | Examples |
|----------|-------|----------|
| In-hand manipulation | 80 | Object reorientation, grasp transitions |
| Bimanual coordination | 60 | Container opening, food prep, tool use |
| Fabric manipulation | 40 | Folding clothes, hanging garments |
| Precision assembly | 20 | Screwing, insertion tasks |

## Data Format
```
demo_001/
  glove_data.csv         # Joint angles (40 columns: 20 DOF × 2 hands)
  video_egocentric.mp4   # First-person view
  video_third_person.mp4 # External view
  metadata.json          # Task, objects, duration, quality score
```

## Quick Start
[Python code to load and visualize data]

## Sample Visualizations
[Include 3-5 impressive visualizations:
 - Joint angle trajectories
 - Hand pose rendered on video
 - Grasp type classification]

## Citation
If you use this data, please cite...

## Contact
[Your email]
```

**Create 2-minute demo video**:
```
Structure:
0:00-0:15 - Hook: "The first large-scale dexterous manipulation dataset"
0:15-0:30 - Problem: "Existing datasets lack finger-level tracking"
0:30-1:00 - Show best demos (montage of impressive manipulations)
1:00-1:30 - Data quality (visualizations, statistics)
1:30-1:45 - What's next: "Scaling to 100+ hours, need your feedback"
1:45-2:00 - CTA: "Try the data, email feedback"

Tools:
- iMovie / DaVinci Resolve (free) for editing
- Keep it professional but not overproduced
- Focus on impressive manipulations (wow factor)
```

**Set up Google Drive share**:
```
Folder structure:
/DexManip-20-Preview
  README.md
  demo_video.mp4
  /sample_data (10 best demos, ~5GB)
    /demo_001
    /demo_002
    ...
  /documentation
    data_format_spec.pdf
    visualization_examples.pdf
  /code
    load_data.py
    visualize.py

Share settings: Anyone with link can view
```

**Wednesday**: Send validation emails

**Email Template (Updated - Hands-On Testing)**:
```
Subject: Dexterous manipulation dataset - can you test 5 demos this week?

Hi [Professor/Researcher Name],

I saw your recent work on [their specific paper]. I'm building an open-source
dataset of human dexterous manipulation with full finger tracking (Rokoko
gloves + video).

Current datasets (DROID, RH20T) focus on gripper data. I'm focusing on tasks
that REQUIRE fingers: in-hand manipulation, bimanual coordination, fabric
handling.

I've collected 20 hours (200 demos) as a sample quality check before scaling
to 100+ hours.

**ASK: Can you spend 30 minutes THIS WEEK trying to load my data into your
pipeline?** I'd rather get real usage feedback than opinions.

Specifically:
1. Download 5 sample demos (2GB): [Google Drive link]
2. Try loading into your data loader / policy training code
3. Tell me:
   - Did it work? Any format issues?
   - Is tracking quality good enough for your use case?
   - What specific tasks would you pay for (if this were a service)?

**Demo video**: [YouTube link] (2 min overview)
**Code example**: load_data.py (loads demo into PyTorch)

If you successfully load and use the data, I'll:
- Add you to acknowledgments in dataset paper
- Prioritize your task requests for 100-hour version
- Give you early access (1 week before public release)

Best regards,
[Your Name]

P.S. I'm targeting submission to [CoRL/ICRA/RSS] - would love to collaborate
if there's interest. Also considering this as portfolio for PhD applications.
```

**Target list** (30 researchers):

**Manipulation Labs** (10):
```
□ Berkeley AUTOLAB (Ken Goldberg, Jeff Mahler)
□ Stanford IPRL (Karen Liu)
□ CMU Robotics Institute (Matthew Mason, Oliver Kroemer)
□ MIT CSAIL (Pulkit Agrawal, Russ Tedrake)
□ UW RSE Lab (Dieter Fox)
□ Columbia ROAM Lab (Matei Ciocarlie)
□ UT Austin RLG (Yuke Zhu)
□ USC CLVR (Joseph Lim)
□ Georgia Tech IRIM (Sonia Chernova)
□ Cornell Robot Learning Lab (Lerrel Pinto - NYU)
```

**Humanoid Companies** (10):
```
□ Figure AI (research team)
□ 1X Technologies
□ Sanctuary AI
□ Apptronik
□ Agility Robotics
□ Tesla Optimus (reach for the stars)
□ Boston Dynamics (AI Institute)
□ Covariant (Peter Chen, Pieter Abbeel)
□ Physical Intelligence
□ Skild AI
```

**Recent Paper Authors** (10):
```
Search Google Scholar for 2024 papers on:
- "dexterous manipulation"
- "in-hand manipulation"
- "bimanual coordination"
- "learning from demonstration"

□ Contact first/corresponding authors
□ Prioritize those with .edu emails (academics more responsive)
```

**Thursday-Sunday**: Collect responses & iterate

**Track responses** (Updated - Focus on Usage):
```
Spreadsheet:
| Name | Affiliation | Responded? | Actually Tested? | Feedback | Issues Found |

Target metrics (STRICTER):
- Response rate: >40% (12+ out of 30)
- Actually tested data: 10+ (not just opinions!)
- Successfully loaded: 5+ (proves format works)
- Positive feedback: 15+ would use 100-hour version
- Specific task requests: 5+
- Collaboration offers: 2+

Quality over quantity:
  - 5 researchers who USED the data > 20 who said "looks good"
  - Talk is cheap, usage is truth
```

**Common questions to expect**:
```
Q: "What's the glove accuracy?"
A: Rokoko Smartgloves: ±2-5° per joint, 100Hz sampling
   [Link to Rokoko specs]

Q: "How do I know demos are high-quality?"
A: Every demo manually quality-checked, tracking drift <10°
   Failed/low-quality demos excluded

Q: "What format is the data?"
A: CSV for joint angles, MP4 for video, JSON for metadata
   Compatible with standard robotics tools (PyTorch, etc.)

Q: "Can I get XYZ task?"
A: Absolutely! That's exactly what I want to know - what
   tasks are most valuable. Will include in 100-hour version.
```

**Schedule calls with most interested**:
```
If 5+ researchers very enthusiastic:
□ Offer 30-min Zoom call
□ Deep dive on their data needs
□ Ask: "What would make this dataset invaluable for you?"
□ Take detailed notes

This becomes your roadmap for 100-hour dataset.
```

---

### Week 5-6: Simulation Experiments (Research Track) 🎓

**NEW SECTION - This is your robotics learning bootcamp**

**Objective**: Train your first manipulation policy in simulation. This teaches you:
- ✅ How to use robotics simulators (Isaac Gym/MuJoCo)
- ✅ How to train policies (behavior cloning, diffusion policy)
- ✅ How retargeting works (human hand → robot hand)
- ✅ Portfolio piece for PhD applications ("I trained manipulation policies")

**IMPORTANT Reality Check**:
```
⏰ Timeline: This will take 2-3 weeks, not 2 days
   - First time setup: 3-5 days (debugging CUDA, environments)
   - Retargeting code: 3-5 days (kinematics is hard)
   - Training first policy: 5-7 days (debugging why it doesn't learn)

💡 Manage expectations:
   - Your first policy will probably fail (success rate <10%)
   - That's NORMAL - you're learning
   - Even 20-30% success is publishable for first attempt

🎯 Goal: Learn the skills, not achieve SOTA results
```

---

**Week 5: Setup Simulation Environment**

**Monday-Tuesday: Environment Setup**
```
□ Install Isaac Gym (if not done in Week 1)
  - Requires: NVIDIA GPU, CUDA 11.3+
  - Follow: https://developer.nvidia.com/isaac-gym
  - Test: Run shadow_hand.py example

□ Alternative (if Isaac Gym fails): MuJoCo
  - Easier installation, cross-platform
  - Download: https://mujoco.org/
  - Load Shadow Hand model

□ Verify you can:
  - Launch sim environment
  - Visualize Shadow Hand (or Allegro Hand)
  - Step forward in time (physics working)
  - Read joint states (observations)
```

**Wednesday-Thursday: Understand Data Pipeline**
```
□ Study existing retargeting papers
  - DexMV (human video → robot policies)
  - RoboAgent (human data for robot learning)
  - Hand-Object Retargeting (how to map hands)

□ Understand the problem
  - Human: 27 DOF (degrees of freedom)
  - Shadow Hand (sim): 24 DOF
  - Mapping is non-trivial (different joint structure)

□ Pick simple approach first
  Method 1: Joint-level mapping
    - Map each human joint → closest robot joint
    - Simple, won't work perfectly
    - Good first attempt

  Method 2: Task-space mapping (advanced)
    - Match fingertip positions (not joint angles)
    - Requires inverse kinematics (IK)
    - More accurate, but harder to implement

  Start with Method 1, try Method 2 if time permits
```

**Friday-Sunday: First Retargeting Attempt**
```
□ Choose 1 simple task from your 20-hour dataset
  Recommended: In-hand cube rotation (most studied)
  Alternative: Simple pick-and-place

□ Load 5 demos of that task

□ Write retargeting code
  Input: Human hand joint angles (27 DOF)
  Output: Robot hand joint angles (24 DOF)

  Pseudocode:
  ```python
  def retarget_human_to_shadow(human_joints):
      # Map thumb, index, middle, ring, pinky
      # Shadow has different joint ranges
      robot_joints = map_joints(human_joints)
      return robot_joints
  ```

□ Visualize in sim
  - Play back retargeted motion in Isaac Gym
  - Does it look reasonable?
  - Does the task complete (e.g., cube rotates)?

  If motion looks wrong:
    - Adjust joint mappings
    - Scale joint ranges
    - Try different mapping strategy

Goal: Get ONE demo to replay somewhat correctly in sim
```

---

**Week 6: Train First Policy**

**Monday-Tuesday: Prepare Training Data**
```
□ Clean and format data for policy training

□ Standard format for imitation learning:
  observations = [joint_positions, joint_velocities, object_state]
  actions = [target_joint_positions] (from next timestep)

□ Create train/val split
  - 4 demos for training
  - 1 demo for validation

□ Sanity checks:
  - Data shapes correct? (batch_size, sequence_length, features)
  - Actions normalized? (between -1 and 1)
  - No NaN values?
```

**Wednesday-Thursday: Train Baseline Policy**
```
□ Start with simplest algorithm: Behavior Cloning
  - Supervised learning (predict actions from observations)
  - Not SOTA, but easiest to get working
  - Use MLP or simple LSTM (not Diffusion Policy yet)

□ Training loop:
  ```python
  for epoch in range(100):
      for batch in dataloader:
          obs, actions = batch
          pred_actions = policy(obs)
          loss = MSE(pred_actions, actions)
          loss.backward()
          optimizer.step()
  ```

□ Track metrics:
  - Training loss (should go down)
  - Validation loss (should go down but not as much)
  - If val loss increases: overfitting (too little data)

□ Debug common issues:
  - Loss not decreasing → Learning rate too high/low
  - Loss explodes → Gradient clipping needed
  - Val loss much higher than train → Overfitting
```

**Friday-Sunday: Evaluate in Simulation**
```
□ Test policy in simulation
  - Load trained policy
  - Run in Isaac Gym environment
  - Record success rate over 10-20 trials

□ Evaluation metrics:
  - Success rate: Did task complete? (e.g., cube rotated 90°)
  - Average reward (if using reward function)
  - Qualitative: Does motion look reasonable?

□ Expected results (REALISTIC):
  Scenario A: Policy gets 0-10% success
    → NORMAL for first attempt
    → Debug: Retargeting wrong? Not enough data? Policy too simple?

  Scenario B: Policy gets 20-40% success
    → GOOD for first attempt!
    → This is publishable at workshops
    → Proves human data transfers to robot

  Scenario C: Policy gets 50%+ success
    → AMAZING for first attempt
    → You got lucky or task was very easy
    → Definitely publishable

□ Next steps based on results:
  If <20%: Iterate on retargeting or try more demos
  If 20-40%: Good enough to prove concept, move to Phase 1
  If >40%: Definitely continue, this could be a strong paper
```

**Week 6 Evening: Document Learnings**
```
□ Write up what you learned (for yourself)
  - What worked? What didn't?
  - Key challenges (retargeting? policy training? sim?)
  - What would you do differently?

□ Take screenshots/videos
  - Retargeted motion in sim
  - Policy rollouts (successful and failed)
  - Training curves

□ Save for later use:
  - PhD application materials
  - Dataset paper (include sim experiments as validation)
  - Future paper (if results good)
```

---

### Week 7: GO / NO-GO Decision (Updated for Dual Goals)

**Criteria for GO (Business Validation)**:
```
✅ 15+ researchers responded positively
✅ 10+ said "yes, I'd use a 100-hour version"
✅ 5+ researchers ACTUALLY TESTED the data (loaded it successfully)
✅ 5+ provided specific task requests
✅ 2+ offered to collaborate or contribute data
✅ Zero major quality concerns raised
✅ Clear demand for dexterous manipulation data confirmed
```

**Criteria for GO (Research Validation)**:
```
✅ Successfully installed and ran Isaac Gym or MuJoCo
✅ Retargeted at least 1 demo from human → robot hand
✅ Trained at least 1 policy (even if it failed)
✅ Learned core skills: simulation, policy training, data processing
✅ Have screenshots/videos documenting progress

Bonus (not required, but great):
⭐ Policy achieves >20% success rate in sim
⭐ Results good enough to include in dataset paper
⭐ Made contact with professor willing to advise
```

**Combined Decision Matrix**:
```
Scenario A: BOTH validations succeed
  → GO to Phase 1 (100-hour dataset)
  → Pursue both startup AND research paper
  → This is the BEST outcome

Scenario B: Business succeeds, Research struggles
  → GO to Phase 1, but focus on business
  → Simulation harder than expected (normal)
  → Revisit research component later with mentorship

Scenario C: Research succeeds, Business lukewarm
  → PIVOT to pure research path
  → Focus on making this a strong paper
  → Apply to PhD programs / research positions
  → Dataset becomes research contribution, not startup

Scenario D: BOTH fail
  → NO-GO, but iterate or pivot
  → See "If NO-GO" section below
```

**Criteria for NO-GO** (iterate or pivot):
```
❌ <10 positive responses
❌ Consistent feedback: "Quality not good enough"
❌ "We only use vision-based methods" (no need for glove data)
❌ "We can't use this data format"
```

**If GO → Proceed to Phase 1**:
```
Next steps:
□ Order 4 more pairs of gloves ($7,180)
□ Begin recruiting 5 contributors
□ Plan 100-hour dataset based on feedback
□ Target: Dataset release in 3 months
```

**If NO-GO → Iterate**:
```
Common issues & fixes:

Issue: "Tracking quality not good enough"
Fix: Upgrade to Manus Prime II gloves ($3,500/pair, higher precision)
     Or: Improve calibration/processing pipeline

Issue: "Wrong tasks"
Fix: Focus on exactly what they requested
     Re-collect 20 hours with better task selection

Issue: "Don't need glove data"
Fix: Pivot to camera-only + MediaPipe hand tracking (free)
     Gloves become optional premium tier

Issue: "Can't use this format"
Fix: Add export to their preferred format
     Provide better documentation/examples

Timeline: 2-4 weeks to iterate, then re-validate
```

**If HARD FAILURE** (no interest):
```
Pivot options:

1. Camera-only human demonstrations (no gloves)
   - Lower quality but free hardware
   - Focus on task diversity, not finger detail

2. Purely custom collection service
   - Skip open dataset
   - B2B from day 1
   - Requires different GTM

3. Different vertical entirely
   - Maybe robotics data isn't the opportunity
   - Cut losses at $2,300 (acceptable)

Don't throw good money after bad. Validation exists to filter bad ideas.
```

---

## Phase 1: 100-Hour Dataset (Months 2-4, $9,200)

**Only proceed if Phase 0 validation succeeded.**

### Objective
Build credible, citable dataset that establishes you as the dexterous data expert.

**Why 100 hours, not 300**:
- ✅ Achievable in 3 months
- ✅ Substantial (DROID-scale)
- ✅ Faster to market → faster feedback
- ✅ Can expand later based on demand

---

### Month 2: Recruit & Onboard Contributors

**Week 1: Purchase equipment**
```
□ Order 4 more pairs of Rokoko gloves: $7,180
  (You have 1, need 5 total for parallel collection)

□ Budget for shipping: $500
  (International shipping to contributors)

□ Total: $7,680
```

**Week 1-2: Recruit 5 contributors**

**Recruitment channels**:
```
□ University robotics labs
  - Email professors: "Looking for students to contribute to dataset"
  - Post on lab Slack/Discord

□ Twitter #RoboticsTwitter
  - Thread about the project
  - "Contributors wanted" post

□ Reddit r/robotics, r/MachineLearning
  - "Open-source robotics dataset - contributors needed"

□ Robotics Discord servers
  - Learn Robotics Discord
  - AI Alignment

□ Personal network
  - Friends in tech/robotics
  - Former classmates/colleagues
```

**The recruitment pitch**:
```
Subject: Open-Source Dexterous Manipulation Dataset - Contributors Wanted

I'm building the first large-scale dataset of human finger-level manipulation
data for training humanoid robots. This will be released free to the research
community (like DROID, RH20T).

**What I'm looking for**: 5 contributors to help collect 100 hours total

**Your commitment**:
- 20 hours of recording over 2 months
- Follow data collection protocols
- Access to household objects/kitchen

**What you get**:
- Co-creator credit (your name on the dataset paper)
- Citations in papers using the data (career building)
- $200 stipend
- Keep the Rokoko gloves ($1,795 value) after completing 20 hours
- Resume/portfolio builder (hands-on robotics/ML experience)

**Ideal for**: PhD students, robotics engineers, ML enthusiasts, VR developers

**Timeline**: Kickoff January 2025, dataset release April 2025

Interested? Reply with:
1. Your background (student/engineer/enthusiast)
2. Why you're interested
3. Availability (hours/week you can commit)

Limited to 5 spots. First come, first served.

Best,
[Your Name]

[Link to Phase 0 sample data]
[Link to project website/GitHub]
```

**Selection criteria**:
```
Prioritize:
✅ Robotics/ML background (understands the purpose)
✅ Reliable (can commit to 20 hours over 2 months)
✅ Communication (responsive, English proficiency)
✅ Diverse locations (different homes/environments)

Red flags:
❌ Can't commit to timeline
❌ Poor communication
❌ Expecting more than $200 stipend
❌ Doesn't understand the project
```

**Week 3-4: Onboard & train contributors**

**Ship gloves**:
```
For each contributor:
□ Ship Rokoko gloves (1 pair)
□ Include:
  - Quick start guide
  - Recording checklist
  - Your contact info
  - Prepaid return label (in case they drop out)

□ Tracking number + delivery confirmation
```

**Onboarding materials**:
```
Create:
□ Video tutorial (15 min)
  - Unboxing and charging
  - Calibration walkthrough
  - Recording your first demo
  - Common mistakes to avoid

□ Written guide (PDF, 10 pages)
  - Equipment setup
  - Task list with examples
  - Quality standards
  - Troubleshooting

□ Task assignment sheet
  - Each person gets 4 task categories
  - 50 demos total per person (20 hours avg)
  - Specific tasks assigned to avoid duplicates
```

**1-hour onboarding call** (each contributor):
```
Agenda:
1. Introductions (5 min)
2. Project overview & your role (10 min)
3. Equipment walkthrough (15 min)
   - They unbox on the call
   - Walk through calibration together
4. Record first test demo together (20 min)
   - They do a simple task while you watch
   - Give real-time feedback
5. Q&A (10 min)

Goal: They leave confident to record independently
```

**Set expectations**:
```
□ Quality over quantity
  "If a demo has tracking issues, delete and redo.
   I'd rather have 18 perfect demos than 20 mediocre."

□ Weekly check-ins
  "Every Monday, send me:
   - How many demos completed last week
   - Any issues/questions
   - Preview of 1 demo for quality check"

□ Completion timeline
  "Target: 50 demos in 8 weeks (6-7 per week)
   That's ~1 hour of recording per day, 5 days/week"

□ Stipend payment
  "$100 after 25 demos (midpoint)
   $100 after 50 demos (completion)
   Keep gloves after finishing"
```

---

### Month 3: Data Collection Sprint

**Your role**: Project manager + quality control

**Weekly routine**:
```
Monday:
□ Collect status updates from all 5 contributors
□ Review sample demos submitted
□ Give feedback (quality, suggestions)
□ Answer questions

Wednesday:
□ Check in with anyone behind schedule
□ Troubleshoot technical issues
□ Adjust task assignments if needed

Friday:
□ Review week's data
□ Quality check random sample (10%)
□ Update progress tracker
□ Plan next week

Quality metrics to track:
- Demos completed per person per week (target: 6-7)
- Quality score (1-10) for each demo
- Technical issues reported
- Dropout risk (anyone going silent?)
```

**Handling issues**:
```
Issue: Contributor behind schedule
Fix:
  - Check in: "Everything okay?"
  - Adjust: "Can we reduce to 40 demos instead of 50?"
  - Replace: If unresponsive for 2 weeks, find replacement

Issue: Low quality data
Fix:
  - Provide specific feedback
  - Do another training session
  - Last resort: Pay for completed demos, find replacement

Issue: Contributor drops out
Fix:
  - Pay pro-rated stipend for demos completed
  - Request return of gloves (or charge deposit)
  - Recruit replacement ASAP
  - Adjust timeline if needed

Budget buffer: Assume 1 dropout, recruit 6 people initially
```

**Data organization**:
```
Folder structure:
/DexManip-100
  /contributor_001
    /demo_001
    /demo_002
    ...
  /contributor_002
  ...

As data comes in:
□ Automated backup (Google Drive, AWS S3)
□ Quality check script (flag drift, duration, missing files)
□ Metadata database (track all demos)
```

---

### Month 4: Processing, Packaging, Release Prep

**Week 1-2: Data processing**

**Quality filtering**:
```
□ Review all 250-300 demos (5 people × 50 demos)

□ Filter out low-quality:
  ❌ Tracking drift >10°
  ❌ Video quality issues (bad lighting, obstruction)
  ❌ Task not completed
  ❌ Duration too short (<3 min) or too long (>20 min)

□ Target: Keep 200-250 high-quality demos = 100+ hours

Quality over quantity. 100 hours of perfection > 120 hours of mediocrity.
```

**Standardization**:
```
□ Resample all glove data to 100Hz (if inconsistent)
□ Trim videos to match glove data timestamps exactly
□ Rename all files consistently
□ Verify all metadata complete (task, objects, duration)
```

**Create dataset splits**:
```
Train: 70% (140-175 demos)
Val: 15% (30-37 demos)
Test: 15% (30-37 demos)

Stratified by task category (balanced representation)
```

**Week 3: Dataset packaging**

**Documentation**:
```
□ README.md (comprehensive)
  - Overview
  - Dataset statistics
  - Data format specification
  - How to download
  - Example code
  - Citation

□ Data format spec (detailed technical doc)
  - Glove data schema
  - Video formats
  - Metadata structure
  - Coordinate systems

□ Datasheet for datasets (optional but professional)
  - Motivation, composition, collection process
  - Recommended uses, limitations
  - Maintenance plan
```

**Code & tools**:
```
□ Python data loader
  - Load demo by ID
  - Batch loading
  - PyTorch Dataset wrapper

□ Visualization tools
  - Plot joint angles
  - Render hand skeleton on video
  - Task statistics/distributions

□ Evaluation scripts
  - Baseline manipulation policy
  - Benchmark on 3 tasks
  - Provide baseline results in paper
```

**Week 4: Website & launch prep**

**Dataset website** (GitHub Pages free):
```
dexmanip-dataset.github.io

Pages:
□ Home
  - Hero video
  - Download button (prominent)
  - Key statistics

□ Explore
  - Sample demos (embedded videos)
  - Visualizations
  - Task breakdown

□ Download
  - Instructions
  - Multiple download options (Google Drive, Hugging Face)
  - Data format docs

□ Paper
  - Preprint link (ArXiv)
  - Bibtex citation

□ Team
  - You + 5 contributors (photos, bios)

□ Contact
  - Email, GitHub issues

Tools: Jekyll, Hugo, or simple HTML/CSS
```

**Professional demo video** (3 min):
```
Structure:
0:00-0:20 - Hook: "Current datasets lack finger tracking"
0:20-0:40 - Solution: "DexManip-100: First large-scale dexterous dataset"
0:40-1:20 - Dataset showcase (best demos, montage)
1:20-2:00 - Technical details (data format, quality metrics)
2:00-2:30 - Applications (humanoids, research, industry)
2:30-3:00 - Call to action (download, cite, collaborate)

Hire editor on Fiverr ($200-500) or use free tools (DaVinci Resolve)
```

---

## Phase 2: Release & Amplify (Month 5, $2,000)

### Objective
Maximum visibility and credibility in robotics community.

---

### Week 1: Dataset Paper

**Submit to top conference**:
```
Target venues (in order):
1. CoRL (Conference on Robot Learning) - Deadline: June
2. ICRA (Int'l Conf on Robotics & Automation) - Deadline: Sept
3. RSS (Robotics: Science & Systems) - Deadline: January

Paper type: Dataset track (4-8 pages)
```

**Paper structure**:
```
Title: "DexManip-100: A Large-Scale Dataset of Dexterous Manipulation
        with Full Finger Tracking"

Abstract (200 words):
- Motivation: Lack of finger-level tracking in existing datasets
- Contribution: 100 hours, 1000+ demos, diverse tasks, open-source
- Impact: Enables training of dexterous policies for humanoid robots

1. Introduction
   - Problem: Foundation models need massive demo datasets
   - Gap: DROID/RH20T lack finger data (gripper-focused)
   - Solution: DexManip-100 with Rokoko gloves

2. Related Work
   - DROID, RH20T, Open X-Embodiment (gripper data)
   - RealDex (small-scale, 2.6K sequences)
   - Teleoperation datasets (expert-collected, expensive)

3. Dataset Collection
   - Hardware: Rokoko Smartgloves, cameras
   - Tasks: 4 categories, 50+ specific tasks
   - Quality control: Calibration, filtering criteria
   - Diversity: 5 collectors, varied environments

4. Dataset Analysis
   - Statistics: Task distribution, duration, quality metrics
   - Visualizations: Joint angle distributions, grasp types
   - Comparison to existing datasets

5. Benchmark Experiments
   - Train baseline policy (Diffusion Policy or ACT)
   - Test on 3 tasks: Folding, in-hand rotation, bimanual opening
   - Results: Success rates, learning curves
   - Ablation: With vs without finger data

6. Discussion & Future Work
   - Limitations: Data diversity, quality variations
   - Future: Expand to 300+ hours, add tactile data
   - Applications: Humanoid training, sim-to-real, retargeting

Authors: You + 5 contributors + (optional) academic advisor
```

**Increasing acceptance odds**:
```
□ Get academic advisor (co-author)
  - Reach out to professors you contacted in Phase 0
  - "Would you co-author if you help with benchmark experiments?"
  - Adds credibility

□ Strong benchmark results
  - Show that finger data improves policy performance
  - Quantify the benefit (X% higher success rate)
  - INCLUDE your Phase 0 simulation experiments if results good

□ High-quality visualizations
  - Professional figures, clear plots
  - Supplementary video (upload with submission)

□ Open-source commitment
  - "Dataset available at [URL]"
  - Code for reproducibility
```

---

### PARALLEL TRACK: PhD Applications (for Fall 2026 or 2027) 🎓

**If your goal includes getting into robotics PhD programs**, this project is your portfolio piece.

**Timeline for Fall 2026 Applications** (Aggressive):
```
Dec 2025: Phase 0 complete (20 hours + sim experiments)
Jan 2026: Draft dataset paper + statement of purpose
Feb-Mar 2026: Collect 100 hours
Apr 2026: Submit paper to CoRL (deadline ~June)
May-Aug 2026: Dataset release, community traction
Sep-Nov 2026: Prepare applications
Dec 2026: Submit PhD applications (deadline ~Dec 15)

Admissions decisions: March 2027
Start PhD: September 2027
```

**Timeline for Fall 2027 Applications** (Recommended - more realistic):
```
Nov 2025-Jan 2026: Phase 0 complete
Feb-May 2026: 100-hour dataset + paper submission
Jun-Aug 2026: Dataset release, wait for paper reviews
Sep 2026-Mar 2027: Real robot experiments (collaboration or LEAP Hand)
  - Visit lab with robot hardware, OR
  - Build LEAP Hand and run experiments yourself
Apr-Aug 2027: Write second paper (real robot results)
Sep-Nov 2027: Prepare PhD applications
Dec 2027: Submit applications

Admissions decisions: March 2028
Start PhD: September 2028
```

**What This Project Gives You for PhD Applications**:
```
✅ Published dataset (even if just on ArXiv + HuggingFace)
✅ Evidence you can:
   - Design and execute research project independently
   - Collect and process data at scale
   - Train manipulation policies
   - Write papers
   - Engage with research community

✅ Strong statement of purpose:
   "I built DexManip-100, a 100-hour dexterous manipulation dataset,
    and demonstrated that human finger tracking data can improve robot
    policy learning by X% in simulation [and Y% on real robots].
    I now want to study cross-embodiment transfer learning and
    foundation models for dexterous manipulation at your lab."

✅ Letters of recommendation:
   - Professor who co-authored paper (strong!)
   - Researchers who used your dataset (credible!)
   - Advisor from visiting researcher position (best!)

✅ Differentiation from typical applicants:
   Most: "I took robotics classes, did undergrad research"
   You: "I independently built a dataset used by 50+ research groups,
        published 1-2 papers, and trained policies on real robots"
```

**How to Maximize PhD Application Strength**:
```
□ Month 5-6: After dataset release
  - Email 10-15 professors whose work aligns with yours
  - Subject: "DexManip-100 dataset - potential collaboration?"
  - Body:
    "I built this dataset and got X downloads. I'm applying to PhD
     programs for Fall 2027. Would you be interested in collaborating
     on real robot experiments? I can visit for 2-3 months."

  Target responses: 3-5 positive replies
  Best case: One offers visiting researcher position

□ Month 6-12: Visiting researcher position (if you get one)
  - Work in lab with robot hardware for 3-6 months
  - Co-author paper on real robot experiments
  - Get strong letter of recommendation
  - Insider advantage for PhD admission to that lab

□ Alternative (if no visiting position):
  - Build LEAP Hand yourself ($2-5K)
  - Run real robot experiments solo
  - Less strong than collaboration, but still valuable

□ Month 12+: Application prep
  - Statement of purpose (iterate 10+ times)
  - Reach out to professors at target schools
  - Mention your dataset in initial emails
  - Request letters from co-authors/collaborators
```

**Target PhD Programs** (based on manipulation research strength):
```
Tier 1 (Top manipulation labs):
□ Berkeley (Goldberg, Levine, Abbeel labs)
□ Stanford (Liu, Bohg labs)
□ CMU (Mason, Kroemer labs)
□ MIT (Tedrake, Agrawal labs)
□ UW (Fox lab)

Tier 2 (Strong robotics programs):
□ Columbia (Ciocarlie lab)
□ UT Austin (Zhu lab)
□ USC (Lim lab)
□ Georgia Tech (IRIM)
□ Cornell / NYU (Pinto lab)

Tier 3 (Good safety schools):
□ UC San Diego
□ U Michigan
□ Northwestern
□ Brown
□ University of Toronto

Strategy: Apply to 10-12 programs (3-4 from each tier)
```

**Realistic Expectations**:
```
Acceptance rates for top robotics PhD programs:
- MIT/Berkeley/Stanford: 3-5% (200+ applicants, 5-10 spots)
- CMU/UW/Columbia: 5-10%
- Others: 10-20%

Your advantages with DexManip-100:
✅ Demonstrated research ability (independent project)
✅ Community impact (dataset downloads, citations)
✅ Technical skills (data, ML, robotics)
✅ Clear research vision (continuation of this work)

Even with strong project:
- 50% chance of getting into at least one Tier 1 program
- 80% chance of getting into at least one Tier 2 program
- 95% chance of getting into at least one program overall

Backup plan: If rejections
- Apply to MS programs (easier admission)
- Work as research engineer for 1-2 years
- Re-apply with even stronger profile
```

**Decision Point: Startup vs PhD**
```
After Phase 0 and Phase 1, you'll have better info:

Scenario A: Dataset business takes off
  - 100+ downloads in first month
  - 5+ companies interested in paying
  - $50K+ revenue potential Year 1
  → Delay PhD, pursue startup for 1-2 years
  → Can always apply to PhD later with even more experience

Scenario B: Research traction but weak business
  - Paper accepted to CoRL/ICRA
  - 10+ citations within 6 months
  - Professors excited to collaborate
  - But <$20K revenue
  → Pursue PhD, use this as application portfolio
  → Can continue dataset as side project

Scenario C: Both succeed moderately
  - Dataset has some users, some revenue ($20-50K/yr)
  - Paper published or under review
  → You have options!
  → Can do startup then PhD, or PhD then startup
  → Or keep dataset as bootstrap business while in PhD

The beauty of this plan: Multiple exit routes
You're not locked into one path
```

---

### Week 2: Public Release

**Upload dataset**:
```
□ Hugging Face Datasets (recommended)
  - Free hosting
  - Easy download for ML community
  - Good discoverability

□ Google Drive (backup)
  - Direct download link
  - No account required

□ Academic torrents (optional)
  - For very large files
  - Community-supported
```

**GitHub repository**:
```
github.com/yourname/DexManip-100

Contents:
□ README (comprehensive)
□ Data loading code
□ Visualization tools
□ Benchmark code
□ Documentation
□ Issues (for community feedback)

Make it professional:
  - Clean code, commented
  - Examples/tutorials
  - CI/CD (automated tests)
  - License (CC-BY 4.0 for data, MIT for code)
```

---

### Week 3-4: Launch Campaign

**Day 1: Coordinated launch**

**Morning**:
```
□ Publish dataset (Hugging Face, GitHub)
□ Publish paper (ArXiv preprint)
□ Launch website
□ Upload demo video (YouTube)
```

**Afternoon**:
```
□ Twitter thread (10-15 tweets)

  Tweet 1: Hook
  "We're releasing DexManip-100: the first large-scale dataset of
   dexterous manipulation with full finger tracking. 100 hours,
   1000+ demos, fully open-source. 🧵"

  Tweet 2-3: Problem/motivation
  "Current datasets (DROID, RH20T) focus on parallel-jaw grippers.
   But the next generation of humanoid robots have multi-fingered hands.
   They need finger-level data."

  Tweet 4-6: Dataset details + visualizations
  [Images of demos, statistics, cool visualizations]

  Tweet 7-8: Technical specs
  "Rokoko Smartgloves (20 DOF), egocentric video, diverse tasks..."

  Tweet 9: Benchmark results
  "We show that finger data improves policy performance by X%..."

  Tweet 10: Call to action
  "Download now: [link]
   Paper: [ArXiv link]
   Code: [GitHub link]

   Excited to see what the community builds with this!"

  Tag relevant people:
  @PhysicalAI, @SkildAI, @GoogleDeepMind, @OpenAI,
  Robotics researchers you contacted

□ Reddit posts
  - r/MachineLearning
  - r/robotics
  - r/datasets

  Title: "DexManip-100: Large-scale dexterous manipulation dataset
          with finger tracking (100 hours, open-source)"

  Post content: Summary + links

□ Hacker News
  - Submit ArXiv paper or GitHub repo
  - Title: Clear, factual, no hype
  - Post in morning (8-10am PT for visibility)
```

**Week 1 post-launch**:
```
□ Email the 30 researchers from Phase 0

  Subject: DexManip-100 is live - 100 hours of dexterous manipulation data

  "Hi [Name],

  Thanks for your feedback on the 20-hour preview. I've now completed
  DexManip-100: 100 hours of dexterous manipulation with full finger
  tracking, fully open-source.

  Dataset: [link]
  Paper: [ArXiv]
  Code: [GitHub]

  Would love your thoughts. Happy to collaborate if there are specific
  tasks you'd like added in future versions.

  Best,
  [You]"

□ Post on robotics Discord/Slack channels

□ Submit to robotics newsletters
  - Import AI (Jack Clark)
  - The Batch (Andrew Ng)
  - Robot Report

□ Reach out to robotics journalists
  - IEEE Spectrum
  - TechCrunch (robotics beat)
  - VentureBeat AI

  Pitch: "First large-scale dataset with finger tracking for humanoids"
```

**Week 2-4: Community engagement**:
```
□ Monitor GitHub issues
  - Respond to every question within 24 hours
  - Fix bugs reported
  - Accept pull requests

□ Twitter engagement
  - Reply to everyone who tweets about it
  - Retweet community projects using the data
  - Share interesting findings

□ Track metrics
  - GitHub stars
  - Dataset downloads
  - Paper citations (Google Scholar alerts)
  - Media coverage

Goal: 500+ GitHub stars, 100+ downloads in Month 1
```

---

## Phase 3 (OPTIONAL): Real Robot Experiments (Months 6-12, $0-5K) 🤖

**Only pursue if you're targeting PhD applications or want to publish a stronger paper**

**Two Paths**: Collaboration (recommended) vs Solo Build

---

### Path A: Collaboration with Existing Lab (RECOMMENDED) 💡

**Why this is better**:
```
✅ Access to better hardware (Shadow Hand $100K, better than LEAP $2K)
✅ Expert mentorship (professor, PhD students help you)
✅ Stronger paper (affiliation with known lab adds credibility)
✅ Better for PhD apps (letter from that professor, insider track)
✅ Lower cost ($0 if they host you as visiting researcher)
✅ Faster (no hardware assembly/debugging needed)
```

**How to get visiting researcher position**:
```
Month 5-6: After dataset release
□ Email 10-15 professors whose labs have dexterous robot hands

Subject: "DexManip-100 dataset - collaboration on real robot experiments?"

Body:
"Hi Professor [Name],

I recently released DexManip-100, a 100-hour dataset of dexterous
manipulation with finger tracking. It's gotten [X downloads, Y GitHub
stars] and been featured in [Z].

I showed in simulation that this data can improve manipulation policies
by X%. I'd like to validate this on real robot hardware.

Would you be interested in hosting me as a visiting researcher for
2-3 months? I can:
- Test my dataset on your Shadow/Allegro/LEAP Hand
- Help with your lab's ongoing projects
- Co-author paper on results

I'm flexible on timing (summer 2026 or fall 2026) and am applying to
PhD programs for Fall 2027. Your lab is top of my list.

Dataset: [link]
Paper: [ArXiv]
Background: [brief bio]

Best,
[Your Name]"

Target labs with dexterous hands:
□ CMU (Shadow Hand, Allegro Hand)
□ Berkeley (various hands)
□ Stanford (dexterous manipulation groups)
□ Columbia ROAM Lab (Yale Hand, others)
□ UW (manipulation hardware)
□ MIT (dexterous manipulation)

Success metric: 2-3 positive responses
```

**What to expect from visiting position**:
```
Duration: 2-3 months (summer internship style)
Compensation: Usually unpaid, but sometimes small stipend
Housing: You pay (find sublet near university)
Cost: $2-4K total (rent + food + travel)

What you do:
- Week 1-2: Learn their robot system, codebase
- Week 3-6: Run experiments (test your data on real robot)
- Week 7-10: Analyze results, write paper draft
- Week 11-12: Wrap up, prepare to leave

Outcome:
✅ Co-authored paper (your data + their robot)
✅ Strong letter of recommendation for PhD apps
✅ Inside track for PhD admission to that lab
✅ Real robot videos for portfolio
```

**Backup if no one responds**:
```
Try these alternatives:

Option 1: Pay for robot access
  - Some labs rent robot time ($50-100/hour)
  - Expensive but gets you real robot data
  - 20-40 hours = $1-4K

Option 2: Contact industry labs
  - Figure, 1X, Physical Intelligence
  - "Can I test my dataset on your humanoid?"
  - Less likely, but worth trying

Option 3: Build LEAP Hand yourself (see Path B below)
```

---

### Path B: Build LEAP Hand Solo (BACKUP PLAN) 🛠️

**Only do this if Path A fails**

**Why this is harder**:
```
❌ 3-4 months to build + debug (hardware is unpredictable)
❌ No mentorship (you're learning alone)
❌ Weaker for PhD apps (no professor co-author)
❌ More expensive ($2-5K)
❌ Higher failure risk (hardware might not work)
```

**When to choose this path**:
```
✅ You REALLY want hands-on hardware experience
✅ No labs responded to collaboration requests
✅ You have time (not rushing PhD applications)
✅ You're okay with possibility of failure
```

**LEAP Hand Build Timeline** (Realistic):
```
Month 1 (Ordering & Planning):
□ Purchase LEAP Hand kit: $2,000
  - From: https://leaphand.com/ (check if available)
  - Shipping: 2-4 weeks

□ Purchase additional components: $500-1,000
  - Cables, power supply, mounting
  - Computer with good GPU
  - 3D printed parts (if needed)

□ Study documentation
  - Assembly guide
  - Software setup
  - Control examples

Month 2 (Assembly):
□ Week 1-2: Mechanical assembly
  - Follow build guide carefully
  - Expect: Some parts don't fit perfectly
  - Budget: 20-30 hours of work

□ Week 3: Electronics setup
  - Connect motors, sensors
  - Test each finger individually
  - Debug wiring issues (expect 5-10 hours debugging)

□ Week 4: Software setup
  - Install LEAP control software
  - Test in simulation first
  - Calibrate real hardware

Realistic: 50% chance you get it working by end of month 2
If not working: Another 2-4 weeks of debugging

Month 3-4 (Experiments):
□ ONLY start if hardware is working reliably

□ Retargeting (3-4 weeks):
  - Map human data → LEAP Hand
  - Different from sim retargeting (real hardware limits)
  - Expect many iterations

□ Policy training (2-3 weeks):
  - Collect baseline demos on real robot (10-20 demos)
  - Train policy on your retargeted human data
  - Test on real hardware

□ Evaluation (1-2 weeks):
  - Run 50-100 trials
  - Record videos
  - Analyze results

Expected results:
- 10-30% success rate (realistic for first attempt)
- Proves concept works on real hardware
- Videos for portfolio/paper

Month 5: Write paper + prepare for PhD apps
```

**Cost breakdown (LEAP Hand path)**:
```
LEAP Hand kit:                 $2,000
Additional hardware:             $500
Filament/parts:                  $200
Replacement parts (breaks):      $300
Workspace setup:                 $200
─────────────────────────────────────
Total:                       $3,200

Alternative: Pre-built LEAP Hand
  - Some vendors sell assembled: $4-5K
  - Saves 1-2 months assembly time
  - Decide based on your budget vs time
```

**Risk mitigation**:
```
Before committing $2K:

□ Join LEAP Hand community (Discord, forums)
  - Ask: "How long did assembly take you?"
  - Ask: "What issues did you hit?"
  - Talk to 5+ people who built it

□ Verify you have skills needed:
  - Mechanical assembly (built complex things before?)
  - Electronics (comfortable with wiring, motors?)
  - Software (can debug Linux, drivers, C++ code?)

If ANY of these is weak: Collaboration path safer
```

---

### Decision Matrix: Collaboration vs Solo

```
Choose COLLABORATION if:
✅ You want best outcome for PhD applications
✅ You value mentorship and learning from experts
✅ You want to minimize risk
✅ You're applying to PhD programs soon (next 6-12 months)

Choose SOLO BUILD if:
✅ You want hands-on hardware experience
✅ You have 4-6 months of available time
✅ You're okay with possibility of partial failure
✅ You have budget ($3-5K)
✅ No collaboration opportunities materialized

Choose NEITHER if:
✅ Business is taking off (focus on that instead)
✅ You're not pursuing PhD (sim results sufficient)
✅ Budget/time constraints
✅ Want to move fast (real robots slow you down)
```

---

### Expected Outcomes (Real Robot Track)

**Best case** (20% probability):
```
✅ Collaboration with top lab (CMU, Berkeley, Stanford)
✅ Policy achieves 40-50% success on real robot
✅ Paper accepted to CoRL or ICRA (top venue)
✅ Strong letter of rec for PhD apps
✅ Admission to that lab's PhD program
```

**Realistic case** (60% probability):
```
✅ Collaboration with good lab OR solo build succeeds
✅ Policy achieves 15-30% success on real robot
✅ Paper accepted to workshop or smaller conference
✅ Portfolio piece for PhD applications
✅ Admission to decent PhD program (Tier 2-3)
```

**Worst case** (20% probability):
```
❌ No collaboration offers
❌ LEAP Hand build fails or takes too long
❌ Only have sim results (not real robot)
→ Still okay! Sim results alone are publishable at workshops
→ PhD applications still viable with dataset contribution
→ Can try real robots later (after starting PhD)
```

**Key insight**: Real robot experiments are NICE TO HAVE, not REQUIRED
- For startup: Not needed at all (focus on data business)
- For PhD apps: Helpful but sim + dataset already strong
- For learning: Very valuable (but mentorship > solo)

**Recommendation**: Try collaboration first (costs $0, low risk). Only build LEAP Hand if you really want the experience and have time/money.

---

### Phase 0 Success (Week 6-7) - DUAL GOALS

**Business Validation**:
```
✅ 15+ researchers confirm dataset is valuable
✅ 5+ researchers ACTUALLY TESTED (loaded and used data)
✅ 5+ specific task requests
✅ 2+ collaboration offers
✅ Clear demand validated

→ Proceed to Phase 1 (business track)
```

**Research Validation**:
```
✅ Successfully installed Isaac Gym or MuJoCo
✅ Retargeted at least 1 demo to simulated robot hand
✅ Trained at least 1 policy (even if success rate low)
✅ Learned core skills: sim, retargeting, policy training
✅ Documented results for potential paper

→ Proceed to Phase 1 (research track)
```

**Combined Decision**:
- If BOTH succeed: → Pursue both startup AND research paper
- If business succeeds only: → Focus on dataset business
- If research succeeds only: → Pivot to pure research/PhD path
- If BOTH fail: → Iterate or pivot (see NO-GO section in plan)

### Phase 1 Success (Month 4)
```
✅ 100 hours collected
✅ 5 contributors completed
✅ Dataset packaged professionally
✅ Paper drafted (includes Phase 0 sim experiments if successful)
✅ Paper submitted to CoRL/ICRA/RSS

→ Proceed to Phase 2 (release)
```

### Phase 2 Success (Month 5)
```
✅ 100+ dataset downloads in first week
✅ 500+ GitHub stars in first month
✅ Media coverage (1+ article in robotics press)
✅ Conference acceptance OR positive reviews
✅ 5+ research groups using data

→ Decision: Monetization OR PhD applications OR both
```

### Monetization Success (Month 6-12) - Business Path
```
✅ First custom collection project ($10K+)
✅ 3-5 premium subscribers ($3K each)
✅ 1-2 consulting engagements ($5K each)
✅ Total revenue: $50K+ in first 6 months

→ Decision: Bootstrap vs Raise funding
```

### PhD Application Success (Month 6-18) - Research Path
```
✅ Dataset paper accepted or published
✅ 10+ citations to dataset
✅ 2-3 visiting researcher offers OR LEAP Hand experiments completed
✅ Strong letters of recommendation secured
✅ Applications submitted to 10-12 programs

→ Target: Admission to at least one Tier 1 or Tier 2 program
```

---

## Budget Summary (UPDATED)

```
Phase 0 (Validation - REQUIRED):
  Rokoko gloves (1 pair):        $1,795
  Recording equipment:               $50
  Storage (3 months):               $150
  Researcher outreach:              $305
  Isaac Gym/MuJoCo:                 FREE ✅
  ─────────────────────────────────────
  Subtotal:                       $2,300

Phase 1 (100-hour dataset - REQUIRED):
  Rokoko gloves (4 pairs):        $7,180
  Contributor stipends (5×$200):  $1,000
  Shipping/logistics:               $500
  Processing/storage:               $520
  ─────────────────────────────────────
  Subtotal:                       $9,200

Phase 2 (Release - REQUIRED):
  Professional video:               $500
  Website hosting:                  $200
  Conference fees:                  $100
  Launch marketing:                 $200
  Travel (if presenting):         $1,000
  ─────────────────────────────────────
  Subtotal:                       $2,000

Phase 3 (Real Robots - OPTIONAL, PhD track only):
  Path A: Collaboration
    Housing (2-3 months):         $2,000-4,000
    Travel:                         $500
    ─────────────────────────────────────
    Subtotal:                     $2,500-4,500

  Path B: Solo LEAP Hand Build
    LEAP Hand kit:                 $2,000
    Additional hardware:            $1,000
    Workspace/materials:              $500
    ─────────────────────────────────────
    Subtotal:                      $3,500

═════════════════════════════════════════
TOTAL (Required - Phases 0-2):   $13,500
TOTAL (With PhD track):          $16,000-19,000
```

**Budget Notes**:
- Phase 0-2 sufficient for business validation + dataset release
- Phase 3 only if pursuing PhD applications (optional)
- Simulation experiments (Phase 0 weeks 5-6) are FREE (open-source software)

**Funding sources**:
- Personal savings: $5-10K (covers Phase 0)
- Angel investor: $10-20K (covers Phases 1-2)
- NSF SBIR Phase I: $50K (apply after validation for scaling)
- Crowdfunding (Kickstarter): $20-30K (if dataset gets traction)
- PhD program stipend: Covers living costs if admitted (Fall 2027+)

---

## Timeline Overview (UPDATED for Dual Goals)

```
PHASE 0: VALIDATION (6-7 weeks) 🔬

Week 1:     Equipment + simulation setup
Week 2-3:   Collect 20 hours (data validation)
Week 4:     Validate with researchers (hands-on testing)
Week 5-6:   Simulation experiments (research validation)
Week 7:     ✅ GO/NO-GO DECISION (business + research)

PHASE 1: 100-HOUR DATASET (Months 2-4) 📊

Month 2:    Recruit contributors, ship gloves, onboard
Month 3:    Data collection sprint (contributors collect 80+ hours)
Month 4:    Processing, packaging, paper writing

PHASE 2: RELEASE + LAUNCH (Month 5) 🚀

Month 5:    Dataset release + ArXiv paper + launch campaign
            Community engagement, track metrics

PHASE 3 (OPTIONAL): REAL ROBOTS (Months 6-12) 🤖

Month 6-8:  Seek visiting researcher position OR build LEAP Hand
Month 9-12: Real robot experiments + paper writing
            (Only if pursuing PhD applications)

PARALLEL TRACK: PhD APPLICATIONS 🎓

Month 5-6:  Email professors about collaborations
Month 6-12: Real robot work (optional)
Month 12+:  Prepare PhD applications (Fall 2027)
Dec 2027:   Submit applications

─────────────────────────────────────
MILESTONES:

Day 1 → Phase 0 validation: 6-7 weeks
Day 1 → Dataset release: 5 months
Day 1 → First revenue OR paper submission: 6 months
Day 1 → Real robot results (if pursuing): 9-12 months
Day 1 → PhD admission decisions (if applying Fall 2027): 18 months
```

---

## Next Actions (This Week) ⚡

**Monday (Business + Research Tracks)**:
- [ ] 🛒 Order Rokoko Smartgloves ($1,795)
- [ ] 📊 Set up project tracking spreadsheet
- [ ] 👥 Create researcher target list (30 names)
- [ ] 💻 Check GPU/hardware for Isaac Gym requirements

**Tuesday (Business Track)**:
- [ ] 🔍 Research robotics labs/companies (30 targets)
- [ ] ✉️ Draft validation email (hands-on testing version)
- [ ] 🎥 Set up recording space (lighting, cameras)

**Tuesday Evening (Research Track)**:
- [ ] 🎮 Install Isaac Gym OR MuJoCo (expect 2-4 hours)
- [ ] 📄 Skim 2-3 key papers (Diffusion Policy, DexMV, Learning from Play)
- [ ] 🧪 Run shadow hand example in simulation

**Wednesday** (gloves arrive):
- [ ] 📦 Unbox, charge, calibrate Rokoko gloves
- [ ] 🎬 Record 10 test demos (get comfortable with workflow)
- [ ] ✅ Review data quality (tracking accuracy, video sync)

**Thursday-Friday (Data Pipeline)**:
- [ ] 🔧 Build data processing pipeline (export, sync, label)
- [ ] 📝 Document every step (you'll need this later)
- [ ] 🧪 Try loading 1 demo into Isaac Gym (early retargeting test)
- [ ] 📋 Prepare for Week 2 recording sprint

**Weekend (Planning)**:
- [ ] 📋 Plan first 50 demos (task breakdown)
- [ ] 🧰 Gather objects/materials needed
- [ ] 🎥 Finalize recording setup
- [ ] 📚 Read one more retargeting paper if Isaac Gym working

---

## What Success Looks Like 🎯

**End of Week 1**:
✅ Gloves ordered (arriving Wednesday)
✅ Isaac Gym installed and running (OR identified as too hard, will use MuJoCo)
✅ Recorded 10 test demos successfully
✅ Understand full data collection → simulation pipeline
✅ Ready to start Week 2 data collection sprint

**End of Phase 0 (Week 6-7)**:
✅ 20 hours collected + validated with researchers (business)
✅ First policy trained in simulation (research)
✅ Clear GO/NO-GO decision on both tracks
✅ Learned skills worth 1-2 semesters of grad school
✅ Multiple career paths open (startup, PhD, or both)

---

## You Have Everything You Need. Now Execute. 💪

**This plan gives you**:
- ✅ Business validation (data marketplace opportunity)
- ✅ Research portfolio (PhD application credential)
- ✅ Multiple exit routes (not locked into one path)
- ✅ Fast feedback (know in 6 weeks if either track works)
- ✅ Low cost ($2,300 for Phase 0)

**The next 6 weeks will determine**:
- Is DexterData a viable business? (15+ researchers say yes)
- Can you train robot policies? (>20% success rate in sim)
- Should you pursue PhD or startup? (or both!)

**Either way, you'll know the answer.**

And you'll have learned robotics skills, built a portfolio, and made connections in the field.

That's worth $2,300 regardless of outcome.

---

**Final Thought**: This is a well-designed experiment with dual goals. You're not betting everything on one path. You're creating optionality.

Most people spend years in school before getting these skills. You're front-loading the learning into 6 intensive weeks.

If you execute well, in 6 weeks you'll have:
- A dataset that researchers want
- A trained policy (proof you can do research)
- Clear next steps (startup, PhD, or pivot)

**Stop planning. Start building.** 🚀

---

[← Back to README](README.md) | [Next: Scaling Roadmap →](05_SCALING_ROADMAP.md)
