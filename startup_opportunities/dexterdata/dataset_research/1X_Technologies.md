# 1X Technologies Training Data

## Overview
- **Organization:** 1X Technologies (formerly Halodi Robotics)
- **Known Scale/Scope:** "Large dataset of high resolution robot data across diverse scenarios"; hundreds of homes planned for 2025 deployment
- **Access/Availability:** Proprietary; limited NVIDIA research partnership access via dataset API
- **Estimated Cost/Value:** $125M+ raised (Series B2 in 2024); OpenAI as major investor

## What's Known

### Data Collection Infrastructure

**Internal Dataset:**
- Large-scale high-resolution robot data across diverse scenarios
- Data collected in 1X offices and employee homes
- Redwood AI model trained on this internal dataset
- Focused on NEO robot manipulation in varied locations

**NVIDIA Research Collaboration:**
- Created dataset API for NVIDIA to access 1X's proprietary data
- Data collected from 1X offices and employee homes
- Inference SDK built to serve model predictions at 5Hz vision-action loop
- Partnership enables joint research while maintaining data control

**Home Deployment Data Engine:**
- Building "data engine" that uploads data from deployed robot fleet
- Automated ETL (Extract, Transform, Load) pipelines for fleet-wide data
- Easy querying and training on collected data
- Planned deployment in "a few hundred" homes in 2025

### Data Collection Methods

**VR Teleoperation:**
- Humans control robots through android's eyes using VR
- Primary method for gathering training demonstrations
- Enables precise control for complex manipulation tasks

**Fleet Learning:**
- NEO robots in homes continuously collect operational data
- Data aggregated across entire fleet
- Iterative improvement through deployment feedback

**Selective Curation:**
- Careful curation prioritized over algorithmic innovation
- Selective labeling for scenarios where models fail
- Human-in-the-loop data quality control

### Hardware/Methods
- NEO Beta and NEO Gamma humanoid platforms
- VR teleoperation systems
- Multi-modal sensors on robots (vision, proprioception)
- Home environment instrumentation (details not public)

### Redwood AI: World Model
- 1X's proprietary AI system for android control
- Trained on internal dataset from offices and employee homes
- Designed to generalize to new objects and locations
- Focuses on manipulation tasks in real-world environments

### 1X World Model Vision
- Building world models for embodied AI
- Training data derived from real-world robot operation
- Focus on generalization across objects and environments

### Stated Goals
- Deploy NEO as consumer home robot ($20,000 price target)
- Enable robots to learn everyday tasks through teleoperation
- Build autonomous capabilities through fleet learning
- Create world models that understand physics and object interactions

## Industry Impact

### Market Positioning
- OpenAI-backed humanoid robotics startup
- Focus on home/consumer market (vs. warehouse/industrial)
- Norwegian company with U.S. operations
- EVE android deployed in security roles (commercial)

### Competitive Advantages
1. **OpenAI Partnership:** Access to cutting-edge AI and funding
2. **Home Focus:** Targeting underserved consumer market
3. **Deployment Strategy:** Real-world data from actual home use
4. **Efficient Design:** Wheeled EVE for security, bipedal NEO for homes
5. **Early Fleet Learning:** Building data flywheel through deployments

### Public Demonstrations
- NEO Beta demonstrations (2024)
- NEO Gamma unveiled (2025) - production-intent design
- EVE robots deployed in security applications
- Redwood AI model demonstrations

### Commercial Deployments
- EVE robots in security patrol applications
- NEO home trials with early adopters planned (2025)
- Focus on learning from real deployments vs. lab-only development

## Relevance to DexterData

### Could DexterData Compete/Complement?

**Competitive Challenges:**
- 1X's strong backing (OpenAI) and capital ($125M+)
- Integrated hardware + software approach
- Head start on home deployment strategy
- World model approach captures holistic behavior

**Complementary Opportunities:**
- 1X focused on whole-body android behavior, not hand specialization
- VR teleoperation expensive and time-consuming for hand-only tasks
- Home deployment prioritizes safety/navigation over dexterity
- DexterData could provide hand manipulation data 1X needs

### Market Opportunities

**What DexterData Could Offer:**

1. **Hand Manipulation Specialization:**
   - 1X optimizing for home safety and navigation
   - Cooking, cleaning, manipulation require dexterous hands
   - Glove data could accelerate 1X's manipulation capabilities

2. **Faster Hand Skill Collection:**
   - VR teleoperation resource-intensive for simple hand tasks
   - Gloves enable rapid collection of manipulation skills
   - More efficient than full-body teleoperation for hand-only learning

3. **Pre-training Data for NEO:**
   - NEO needs to learn household manipulation tasks
   - DexterData's cooking, cleaning, object handling datasets directly applicable
   - Could license to 1X as pre-training data source

4. **Complementary to World Models:**
   - World models need rich manipulation data
   - Glove sensors capture tactile feedback missing from vision
   - Multi-modal data improves world model accuracy

5. **Academic/Research Access:**
   - 1X data proprietary (except limited NVIDIA access)
   - Researchers need hand manipulation datasets
   - DexterData fills gap for academic community

### Licensing/Access Gaps

**1X's Controlled Access Model:**
- Internal dataset not publicly available
- NVIDIA partnership shows willingness to license selectively
- Home deployment data highly proprietary
- No open dataset offerings announced

**Opportunity for DexterData:**
- **Potential Partner:** 1X might license DexterData's hand datasets
  - Accelerates NEO manipulation training
  - Avoids expensive in-house hand data collection
  - Complements their whole-body behavioral data

- **Academic Alternative:** Researchers locked out of 1X data
  - Universities studying home robotics need datasets
  - DexterData provides accessible alternative

- **Competing Platforms:** Other humanoid companies need hand data
  - Companies competing with 1X can't access their data
  - DexterData serves the broader market

### Strategic Insights

**Key Observations:**

1. **Home Market Validates Hand Dexterity Need:**
   - Home tasks require sophisticated manipulation: cooking, cleaning, organizing
   - NEO's success depends on hand dexterity, not just navigation
   - Validates DexterData's focus on manipulation data

2. **Fleet Learning Creates Data Moat:**
   - 1X building proprietary dataset through home deployments
   - First-mover advantage in real home data collection
   - Shows data = sustainable competitive advantage

3. **Teleoperation Bottleneck:**
   - VR teleoperation expensive and slow
   - Limits data collection rate
   - Opportunity for complementary collection methods (gloves)

4. **Selective Partnership Model:**
   - NVIDIA partnership shows 1X willing to share data selectively
   - Suggests potential for DexterData partnership
   - Could provide hand datasets in exchange for access/licensing fees

**DexterData Strategic Positioning:**

| Aspect | 1X Technologies | DexterData Opportunity |
|--------|-----------------|----------------------|
| **Data Scope** | Whole-body android behavior | Hand manipulation specialization |
| **Collection** | VR teleoperation + fleet | Efficient glove-based capture |
| **Environment** | Home/security deployments | Any environment (lab, home, professional) |
| **Access** | Proprietary (selective partners) | Licensed/open model |
| **Focus** | Navigation + manipulation | Dexterity + tactile sensing |
| **Market** | Consumer androids | Research, medical, specialized robotics |

**Recommended Approach:**

1. **Partnership Opportunity:**
   - Approach 1X as potential customer for hand datasets
   - Offer pre-training data for NEO manipulation tasks
   - Complement their whole-body data with hand specialization

2. **Parallel Path:**
   - Serve researchers/competitors 1X won't support
   - Build datasets for home manipulation tasks (cooking, cleaning, etc.)
   - Position as "open alternative" to 1X's closed data

3. **Modality Advantage:**
   - Emphasize tactile/haptic data that teleoperation doesn't easily capture
   - Force feedback, texture sensing, grip pressure
   - Multi-modal approach (vision + haptics) superior to vision alone

4. **Market Validation:**
   - 1X's home focus validates need for household manipulation data
   - $20K price point shows consumer willingness to pay for capable androids
   - If androids are viable, training data is valuable input
