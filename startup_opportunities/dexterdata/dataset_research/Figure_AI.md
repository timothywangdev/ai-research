# Figure AI Training Data

## Overview
- **Organization:** Figure AI
- **Known Scale/Scope:** 500 hours of teleoperated robot data; 100% egocentric human video from real homes; ongoing large-scale collection via Brookfield partnership
- **Access/Availability:** Fully proprietary - not publicly available
- **Estimated Cost/Value:** $675M+ raised (including $675M Series B in Feb 2024); multi-year Brookfield partnership suggests 8-9 figure data investment

## What's Known

### Project Go-Big: Large-Scale Data Collection Initiative
- Launched as "YouTube for robot behaviors"
- Addresses robotics field's lack of ImageNet/Wikipedia-scale datasets
- Building massive pretraining dataset for humanoid robots
- First humanoid robot to learn end-to-end from human video alone

### Data Collection Methods

**1. Human Video Data (via Brookfield Partnership)**
- 100% egocentric (first-person perspective) human video
- Passively collected as people perform everyday behaviors
- Recorded in real Brookfield residential homes
- Multiple home environments for diversity
- Continuous scaling program ongoing

**2. Teleoperated Robot Data**
- Approximately 500 hours collected for Helix model
- Multi-robot, multi-operator dataset
- High-quality diverse teleoperated behaviors
- Professional teleoperators controlling Figure robots

**3. Direct Human-to-Robot Transfer**
- No robot-specific data required for initial training
- Learns from human video due to humanoid form factor
- Human kinematics and perspective transfer directly to robot

### Hardware/Methods
- Egocentric video capture systems (likely head-mounted cameras)
- Teleoperation rigs for robot control
- Multi-modal sensors on Figure 01/02 robots
- Stereo cameras on robots for deployment

### Helix: Vision-Language-Action Model
- End-to-end learning from images and language to low-level commands
- Trained on combined human video + teleoperated robot data
- Processes visual input, language instructions, and outputs robot actions
- Demonstrated on Figure 01 and Figure 02 platforms

### Stated Goals
- Create general-purpose humanoid robot for commercial deployment
- Enable robots to learn from watching humans (like humans do)
- Deploy in warehouses, manufacturing, and eventually homes
- Build the "Android for robots" - general-purpose platform

## Industry Impact

### Market Positioning
- Leading humanoid robotics startup by funding ($675M Series B)
- Backed by Microsoft, OpenAI, NVIDIA, Jeff Bezos, Intel Capital
- Commercial deployments with BMW (manufacturing)
- Focus on near-term commercial viability

### Competitive Advantages
1. **Human Video Training Breakthrough:** First to successfully train humanoid from human video alone
2. **Brookfield Partnership:** Unique access to real home environments for data collection
3. **Foundation Model Investors:** Deep partnerships with AI leaders (OpenAI, Microsoft)
4. **Hardware + Software:** Full-stack control from data to deployment
5. **Commercial Traction:** Real customer deployments (BMW)

### Public Demonstrations
- Figure 01 demonstrations: coffee making, object manipulation
- Figure 02 unveiled with improved hardware (2024)
- Helix model technical papers published
- "Project Go-Big" announcement for scaling data collection

### Commercial Deployments
- BMW manufacturing facility partnership
- Multiple pilot programs in warehouse/logistics
- Focus on automating repetitive, physically demanding tasks

## Relevance to DexterData

### Could DexterData Compete/Complement?

**Competitive Challenges:**
- Figure AI's massive funding and partnerships
- Successful human video to robot transfer
- Full-stack vertical integration
- Strong commercial momentum

**Complementary Opportunities:**
- Figure focused on bimanual humanoid tasks, not specialized hand skills
- Egocentric video captures intent but not tactile details
- DexterData could provide higher-fidelity hand manipulation data
- Different target markets: Figure = industrial, DexterData = specialized/research

### Market Opportunities

**What DexterData Could Offer:**

1. **Tactile Data Gap:** Egocentric video shows what humans do, not how hands feel
   - Pressure, grip force, tactile feedback missing from video
   - Critical for delicate manipulation tasks

2. **Specialized Hand Skills:** Figure optimizes for full-body warehouse tasks
   - Medical procedures requiring dexterity
   - Craft/artisan skills
   - Fine assembly tasks
   - Research applications

3. **Data Licensing Model:** Figure won't share their data
   - Academic researchers need alternatives
   - Smaller robotics companies locked out
   - Opportunity for licensed hand-specific dataset

4. **Complementary Modality:** Glove data could augment video approaches
   - Figure's Helix + DexterData's tactile = more robust policies
   - Multi-modal training combining vision and haptics

5. **Faster Iteration for Hand Tasks:**
   - Gloves enable rapid collection of hand-specific skills
   - More efficient than full teleoperation for manipulation-only tasks

### Licensing/Access Gaps

**Figure's Closed Ecosystem Creates Market:**
- Brookfield human video data: proprietary, not licensed
- Teleoperated robot data: internal only
- Helix model: proprietary (not open-sourced like some competitors)
- No third-party access to training infrastructure

**Gap for DexterData:**
- Researchers want hand manipulation data Figure won't provide
- Smaller humanoid companies need training datasets
- Medical/surgical robotics companies need specialized data
- Academic institutions need open alternatives

### Strategic Insights

**Key Observations:**

1. **Human Video Validates Market:** Figure proves learning from human demonstrations works
   - Validates DexterData's approach of collecting human hand data
   - Shows market appetite for human-generated training data

2. **Data Moats Are Real:** Figure's competitive advantage is their unique datasets
   - Brookfield partnership creates exclusive data access
   - Proprietary data = sustainable competitive advantage
   - Supports DexterData's thesis: datasets are valuable assets

3. **Full-Body vs. Hand Specialization:**
   - Figure optimizes for warehouse automation (pick, place, walk)
   - Opens opportunity for hand-dexterity specialists
   - Different applications need different data granularity

4. **Commercial Funding Proves Market:**
   - $675M raise shows enterprise willingness to pay for robotics solutions
   - If companies pay for robots, they'll pay for training data
   - Validates B2B licensing model for robotics datasets

**DexterData Differentiation:**

| Aspect | Figure AI | DexterData Opportunity |
|--------|-----------|----------------------|
| **Data Type** | Egocentric video + teleoperation | Glove sensors with tactile feedback |
| **Focus** | Full-body humanoid tasks | Hand manipulation specialization |
| **Market** | Warehouse/manufacturing | Medical, research, specialized robotics |
| **Access** | Proprietary/closed | Licensed/open to partners |
| **Granularity** | Task-level demonstrations | Fine motor control + haptics |
| **Collection** | Expensive teleoperation + home video | Efficient glove-based capture |

**Recommended Strategy:**
- Position as complementary to video-based approaches
- Target hand-dexterity use cases Figure won't prioritize
- Offer open licensing model vs. Figure's closed ecosystem
- Partner with academic/research institutions Figure ignores
- Focus on tactile/haptic data that cameras can't capture
