# Assembly101

## Overview
- **Release date**: March 28, 2022 (CVPR 2022)
- **Organization/Institution**: Meta Reality Labs Research + National University of Singapore
  - **Meta Reality Labs**: Fadime Sener, Daniel Shelepov, Kun He, Robert Wang
  - **NUS**: Dibyadip Chatterjee, Dipika Singhania, Angela Yao
- **Scale**:
  - 4,321 videos
  - 513 hours of footage
  - 101 different "take-apart" toy vehicles
  - 100K+ coarse action segments
  - 1M+ fine-grained action segments (1,380 fine-grained classes, 202 coarse classes)
  - 18M 3D hand poses
  - 328 sequences with mistake annotations
- **Cost to create**: Not publicly disclosed; Meta Reality Labs funded
- **License type**: Creative Commons Attribution-NonCommercial 4.0 International License (CC-BY-NC-4.0)

## Dataset Specifications
- **Data captured**:
  - **Multi-view video**: First dataset with simultaneous egocentric (4 cameras) + static exocentric (8 cameras) = 12 synchronized camera views
  - **Action annotations**: Hierarchical coarse and fine-grained action labels
  - **3D hand poses**: 18M hand pose annotations
  - **Mistake annotations**: 4 mistake types (wrong order, previous one is mistake, shouldn't have happened, wrong position)
  - **Natural variations**: Participants work without fixed instructions, creating realistic variations in action ordering, mistakes, corrections
- **Tasks/domains covered**:
  - Assembly and disassembly of 101 toy vehicles
  - Procedural activity understanding
  - Action recognition, anticipation, temporal segmentation
  - Mistake detection (novel task)
  - Cross-view transfer learning
- **Hardware used**:
  - 8 static cameras (third-person viewpoint)
  - 4 egocentric cameras (first-person viewpoint)
  - All cameras synchronized
  - Motion capture setup for 3D hand pose
- **Data formats**:
  - Multi-view synchronized video
  - Temporal action annotations (start/end times, labels)
  - 3D hand pose keypoints
  - Mistake labels and timestamps
  - Metadata (toy ID, participant ID, assembly/disassembly)

## Research Community Reception
- **Citation count**: 234 citations (Semantic Scholar, as of search date)
- **Key papers using this dataset**:
  - Original Assembly101 paper (CVPR 2022)
  - Temporal action segmentation papers
  - Unseen view action segmentation
  - Mistake detection in procedural activities
  - Cross-view learning and transfer
  - Long-tailed action recognition
  - Hand-object interaction papers
- **Community sentiment**:
  - **Positive**: First multi-view procedural dataset, rich annotations, mistake detection capability, realistic task variations, natural unscripted sequences, comprehensive 3D hand poses
  - **Negative**: Limited to toy assembly (not real-world manufacturing), non-commercial license, relatively new dataset, domain-specific (may not generalize)
- **Benchmark activity**:
  - Active benchmarks on Papers with Code
  - GitHub repositories for action recognition, temporal segmentation, mistake detection
  - Distinguished Paper Award at EgoVis 2022/2023
  - Used in multiple workshops and challenges

## Industry Adoption
- **Companies using it**: Limited public information; primarily academic research
- **Commercial applications**:
  - Research foundation for AR-guided assembly
  - Training data for robotic assembly systems
  - Mistake detection for quality control
  - Worker training and performance support
  - Human-robot collaboration research
- **Deployed products**:
  - No specific deployed commercial products documented
  - Research prototype systems for assembly assistance
  - Foundation for future AR/VR assembly guidance tools

## Who Uses This Dataset
- **Top 5-10 research groups actively using it**:
  1. Meta Reality Labs Research (creators)
  2. National University of Singapore - Angela Yao's Computer Vision & Machine Learning lab (co-creators)
  3. Computer vision labs working on procedural activity understanding
  4. Robotics groups exploring human-robot collaboration
  5. Action recognition and temporal modeling researchers
  6. Egocentric vision research groups
  7. AR/VR application developers in academia
  8. Hand-object interaction researchers
- **Notable papers/projects built on it**:
  - Temporal action segmentation benchmarks
  - Cross-view action recognition
  - Mistake detection algorithms
  - Procedural activity anticipation
  - Hand pose estimation from egocentric views
  - Long-tailed distribution learning
  - Generalization to unseen toys/viewpoints
- **Geographic distribution of users**:
  - **Singapore**: Strong presence (co-creators at NUS)
  - **North America**: Meta Reality Labs, various universities
  - **Europe**: Computer vision research groups
  - **Global**: International computer vision and robotics community

## Strengths & Weaknesses
### What it does well
- **Multi-view innovation**: First dataset with synchronized ego+exo views for procedural tasks
- **Rich annotations**: 1M+ action segments with hierarchical labels, 18M hand poses
- **Mistake detection**: Novel task with realistic error annotations
- **Natural variations**: Unscripted assembly creates realistic task variations
- **Comprehensive coverage**: 101 different toys provide diversity
- **Cross-view learning**: Enables unique research on viewpoint transfer
- **Hand poses**: Extensive 3D hand tracking data
- **Award recognition**: Distinguished Paper Award demonstrates quality

### What it lacks
- **Real-world relevance**: Toy assembly doesn't directly translate to industrial manufacturing
- **Commercial license**: Non-commercial restriction limits industry adoption
- **Domain specificity**: Limited to one type of procedural task (toy assembly)
- **Scalability**: Collecting 12 synchronized camera views is resource-intensive
- **Object complexity**: Toys are simpler than real industrial components
- **Generalization**: Unclear how well methods transfer to real assembly tasks

### Common criticisms
- "Toy dataset" both literally and figuratively - may not represent real industrial complexity
- Limited practical applicability beyond research setting
- High resource requirements for multi-view capture discourage follow-up data collection
- Non-commercial license prevents direct industrial use
- Toys are standardized products vs. varied real-world components
- Missing haptic/force feedback that would be present in real assembly

## Relevance to DexterData
- **Competitive overlap**: MEDIUM
  - Covers procedural activities and assembly tasks
  - Multi-view egocentric+exocentric setup
  - Mistake detection capability
  - Hand-object interaction focus
  - However, toy domain vs. real industrial applications
- **Complementary opportunities**:
  - **Real industrial tasks**: DexterData could focus on actual manufacturing/assembly vs. toys
  - **Commercial licensing**: Offer commercial-friendly terms vs. NC restriction
  - **Haptic data**: Add force/pressure sensing missing from Assembly101
  - **Expert training**: Focus on skill transfer vs. just task completion
  - **Simplified capture**: More practical camera setups than 12-view system
  - **Quality control**: Emphasize defect detection in real products vs. toy mistakes
  - **Domain diversity**: Cover multiple industrial domains vs. just assembly
- **Key differentiators**:
  - **Application domain**: Real manufacturing/industrial vs. toy assembly
  - **Commercial viability**: Assembly101's NC license prevents industry use; DexterData should enable it
  - **Practical complexity**: Real components, materials, tools vs. simplified toys
  - **Business value**: Industrial tasks have clear ROI; toy assembly is primarily academic
  - **Sensing modality**: Add tactile/force data critical for real assembly
  - **Expert knowledge**: Capture professional techniques vs. anyone can assemble toys
  - **Scalability**: Assembly101's 12-camera setup is impractical; DexterData should use accessible hardware
  - **Generalization**: Focus on transferable skills across real tasks vs. toy-specific procedures
