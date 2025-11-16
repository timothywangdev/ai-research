# EPIC-KITCHENS

## Overview
- **Release date**: April 2018 (EPIC-KITCHENS-55), Extended to EPIC-KITCHENS-100 in 2020
- **Organization/Institution**: University of Bristol (UK), University of Toronto (Canada), University of Catania (Italy)
- **Scale**:
  - EPIC-KITCHENS-55: 55 hours of video, 11.5M frames, 39.6K action segments, 454.3K object bounding boxes
  - EPIC-KITCHENS-100: 100 hours of video, 20M frames, 90K actions in 700 variable-length videos, 45 kitchen environments
- **Cost to create**: €50,000 (~£38,000) donation from Nokia Technologies for annotation, plus seed funding from Bristol's Jean Golding Institute (exact total cost not publicly disclosed)
- **License type**: Creative Commons Attribution-NonCommercial 4.0 International License (CC-BY-NC-4.0)

## Dataset Specifications
- **Data captured**:
  - Egocentric video recordings from head-mounted cameras
  - Dense action annotations using "pause-and-talk" narration approach
  - Object bounding boxes
  - Hand-object interactions
  - VISOR extension adds video object segmentation and object relations
- **Tasks/domains covered**: Kitchen activities including cooking, food preparation, cleaning, dishwashing in native home environments
- **Hardware used**:
  - EPIC-KITCHENS-55: GoPro Hero 5, 1080p at 59.94 FPS, linear field of view
  - EPIC-KITCHENS-100: GoPro Hero 7 Black, 50fps with HyperSmooth video stabilization
  - Head-mounted with adjustable mounting
- **Data formats**:
  - RGB video frames
  - Action annotations (verb, noun, action labels)
  - Object bounding boxes
  - Temporal segments
  - Natural language narrations

## Research Community Reception
- **Citation count**:
  - Original 2018 paper: 1,154 citations (Semantic Scholar)
  - 2020 dataset paper: Active citations continuing through 2024
  - Lead author Dima Damen: 10,805 total citations
- **Key papers using this dataset**:
  - LLaVAction (2024): State-of-the-art action recognition, outperforming GPT-4o by 21 points
  - "Extending Video Masked Autoencoders to 128 frames" (NeurIPS 2024)
  - "Towards Training Stronger Video Vision Transformers for EPIC-KITCHENS-100 Action Recognition" (2021)
  - Temporal Action Localization: AdaTAD with VideoMAE-L
  - Multi-modal large language models for action recognition
- **Community sentiment**:
  - **Positive**: Largest egocentric video benchmark, high-quality annotations, real-world natural settings, multi-modal nature, transparent about biases and limitations
  - **Negative**: Domain-specific (kitchen only), acknowledged societal/gender/racial biases, sampling bias and domain gaps, challenges with small objects
- **Benchmark activity**:
  - Active annual challenges since 2018
  - 9 open challenges in 2024 including action recognition, temporal action localization, semi-supervised video object segmentation, hand-object segmentations, audio-based action recognition
  - Multiple active leaderboards on Papers with Code and CodaLab

## Industry Adoption
- **Companies using it**: Not extensively documented in public sources; primarily academic research
- **Commercial applications**:
  - Research foundation for AR smart glasses applications
  - Training data for robotics systems
  - Referenced in discussions of kitchen robotics and smart assistants
- **Deployed products**:
  - No specific deployed products publicly documented
  - University of Bristol working with Meta's Aria Research Kit for egocentric vision applications
  - Potential applications in AR guidance systems, assistive technologies, smart environment interfaces

## Who Uses This Dataset
- **Top 5-10 research groups actively using it**:
  1. University of Bristol, UK (Dima Damen's Computer Vision lab) - Original creators
  2. University of Toronto, Canada (Sanja Fidler's lab)
  3. University of Catania, Italy (Giovanni Maria Farinella, Antonino Furnari)
  4. Various international groups participating in annual challenges
  5. Meta AI/FAIR researchers
  6. Computer vision labs working on action recognition, temporal modeling
  7. Robotics labs exploring egocentric vision for robot learning
- **Notable papers/projects built on it**:
  - Action recognition benchmarks and leaderboards
  - Video understanding with transformers and masked autoencoders
  - Domain adaptation challenges
  - Multi-modal learning combining vision, audio, text
  - Hand-object interaction understanding
  - Temporal action segmentation and anticipation
- **Geographic distribution of users**:
  - Strong presence in UK, Canada, Italy (original consortium)
  - Global research community across North America, Europe, Asia
  - Active participation in annual challenges from worldwide institutions

## Strengths & Weaknesses
### What it does well
- **Scale and quality**: Largest egocentric kitchen dataset with dense, high-quality annotations
- **Natural settings**: Recorded in participants' own homes across multiple countries, providing realistic variation
- **Multi-modal**: Supports visual, audio, and temporal understanding tasks
- **Rich annotations**: Hierarchical action labels (verb-noun), temporal segments, object annotations
- **Active community**: Sustained engagement through annual challenges and benchmarks
- **Transparency**: Openly acknowledges biases and limitations
- **Diverse environments**: 45 different kitchen environments with natural variations

### What it lacks
- **Single domain**: Limited to kitchen activities only
- **Privacy constraints**: Cannot include certain types of real-world interactions
- **Annotation limitations**: "Pause-and-talk" approach still misses some rapid or subtle actions
- **Object size challenges**: Many small objects pose difficulties for detection/tracking
- **Domain gaps**: Temporal gaps between training and test data, location variations

### Common criticisms
- Domain-specific nature limits generalizability to other environments
- Acknowledged biases (societal, gender, racial) in participant selection and activities
- Sampling bias creates domain gaps between different data collection efforts
- Kitchen-centric focus doesn't transfer well to other procedural tasks
- Small object handling remains challenging for many methods

## Relevance to DexterData
- **Competitive overlap**: HIGH
  - Direct overlap in egocentric vision for hand-object manipulation
  - Covers procedural activities and task understanding
  - Focuses on fine-grained action recognition
  - Targets similar end applications (AR guidance, robotics)
- **Complementary opportunities**:
  - DexterData could differentiate by focusing on industrial/manufacturing domains vs. kitchen
  - Multi-environment coverage (not just kitchens) would be valuable
  - More emphasis on dexterous manipulation with haptic/force data
  - Expert skill transfer vs. daily activities
  - Industrial applications have higher commercial value than consumer kitchen applications
- **Key differentiators**:
  - EPIC-KITCHENS is kitchen-only; DexterData should cover diverse industrial/technical domains
  - Non-commercial license limits EPIC-KITCHENS' industry adoption; commercial-friendly licensing would be key differentiator
  - EPIC-KITCHENS lacks haptic/tactile/force sensing data that would be valuable for robotics
  - Focus on hobbyist/consumer activities vs. high-value industrial/professional skills
  - DexterData could emphasize mistake detection, quality control, and expert-novice comparison for industrial training applications
