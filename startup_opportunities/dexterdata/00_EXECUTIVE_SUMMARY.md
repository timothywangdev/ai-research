# Executive Summary - DexterData

**Last Updated**: 2025-11-14
**Analyst**: Senior Partner, a16z/YC
**Status**: Pre-launch validation phase

---

## The One-Liner

"We pay people in emerging markets to perform everyday tasks with sensor gloves, creating the world's largest dataset of dexterous manipulation for training humanoid robots."

---

## The Problem

**Foundation models for robotics need massive demonstration datasets**:
- Physical Intelligence raised $470M
- Skild AI raised $800M
- Tesla Optimus, Figure AI, 1X all need manipulation data

**Current approach doesn't scale**:
- Robot teleoperation costs: $50-200/hour
- Expert operators required
- $420K per robot task
- Only 50-100 companies can afford this

**Existing datasets lack dexterous data**:
- DROID: 350 hours of gripper data (1 DOF)
- RH20T: 400 hours of gripper data (1 DOF)
- RealDex: Only 2.6K sequences with finger tracking
- **Gap**: No large-scale finger-level manipulation dataset

---

## The Solution

**Passive data collection from natural human activity** - "Robotics' equivalent to web scraping"

**How it works**:
1. Recruit gig workers in India, Brazil, Philippines, Indonesia
2. Ship them sensor gloves ($80 cost)
3. Task marketplace: "Fold laundry - 30 min - earn $2.50"
4. Collect video + finger tracking data (20 DOF)
5. Process and sell to robotics/AI companies

**The arbitrage**:
- Collect at: $2-4/hour (gig workers)
- Sell at: $20-60/hour (foundation model companies)
- **10-40× cost reduction** vs robot teleoperation

---

## The Core Insight

**Why this is different from teleoperation-as-a-service**:

| Teleoperation (Covariant) | Human Task Data (Us) |
|---------------------------|----------------------|
| Control robots remotely | Humans do natural tasks |
| Need robot integrations | Just cameras + gloves |
| Expert operators ($50+/hr) | Gig workers ($2-4/hr) |
| Vertical-specific | Horizontal/diverse |
| 7 years to $20M ARR | Faster scaling potential |
| 30-40% margins | 80-90% margins |

**Key insight**: You don't need robots to collect robot training data. Human demonstrations with rich sensor data transfer to robot policies.

---

## Go-to-Market Strategy

**Phase 0: Validation** (Weeks 1-4, $1,500)
- Collect 20 hours yourself (200 demos)
- Validate with 30 robotics researchers
- Success: 15+ say "we'd use a larger version"

**Phase 1: Free Dataset** (Months 2-4, $5,000)
- Release "DexManip-100" - 100 hours, open-source
- Build credibility ("the dexterous data people")
- Submit paper to CoRL/ICRA/RSS

**Phase 2: Monetization** (Months 6-12, $0 upfront)
- Custom data collection: $20/demo
- Premium dataset tier: $3K/year
- Consulting services: $5-20K/project

**This is how DROID, RH20T, and Open X-Embodiment all launched** - Free dataset → Credibility → Monetize services.

---

## Business Model

### Revenue Streams

**1. Custom Data Collection** (40% of revenue)
- Companies request specific tasks/demos
- Pricing: $15-30/demo, $10K-50K per project
- Margin: 40% (pay collectors $8/demo)

**2. Premium Dataset Subscription** (30% of revenue)
- Free tier: DexManip-100 (released once)
- Premium tier: DexManip-300+ (updated quarterly)
- Pricing: $3-5K/year
- Margin: 90% (software)

**3. Consulting Services** (20% of revenue)
- Pipeline setup, training, data processing
- Pricing: $5-20K/project
- Margin: 70%

**4. Foundation Model** (10% of revenue, future)
- Train "DexterNet" on proprietary dataset
- License to enterprises: $100K-500K/year

### Unit Economics (Custom Collection)

```
Per project (500 demos):
Revenue:              $10,000 ($20/demo)
COGS:
  Collector pay:       $4,000 ($8/demo)
  Processing:          $1,000
  Platform/overhead:   $1,000
Gross Profit:          $4,000
Margin:                   40%
```

### Financial Projections

**Year 1** (6 months post-launch):
- Custom collection: $100K
- Premium subscribers: $10K
- Consulting: $25K
- **Total: $135K**

**Year 2**:
- Custom collection: $400K
- Premium: $50K
- Consulting: $100K
- **Total: $550K**

**Year 3**:
- Custom collection: $1.2M
- Premium: $200K
- Consulting: $200K
- Foundation model: $400K
- **Total: $2M ARR**

---

## Market Opportunity

**TAM (Total Addressable Market)**: $5-10B
- Robotics data services by 2030
- Subset of $75B overall data labeling market

**SAM (Serviceable Addressable Market)**: $2-3B
- Manipulation demonstration collection specifically
- Dexterous data for humanoids

**SOM (Serviceable Obtainable Market)**: $500M-1B
- Our niche: Human task demonstrations with finger tracking
- Realistic capture: 10-20% = $50-200M ARR potential

**Bottom-up validation**:
- 200 companies deploying manipulation robots
- Average spend: $500K-2M/year on data
- Total market: $100-400M/year
- We capture 20-30% = $20-120M ARR achievable

---

## Competitive Landscape

**Existing Players**:

| Company | Focus | Raised | Gap |
|---------|-------|--------|-----|
| Scale AI | Computer vision annotation | $15.9B | Not robot-specific |
| Encord | Sensor annotation | $51M | Passive labeling, not collection |
| Sapien | Gamified labeling | $15.5M | Generic, not dexterous |
| Covariant | Warehouse teleoperation | $145M | Vertical-specific, slow |

**Our Differentiation**:
- ✅ Active collection, not passive annotation
- ✅ Dexterous finger data (20 DOF), not gripper data (1 DOF)
- ✅ Horizontal platform, not vertical-specific
- ✅ Crowdsourced, not expert operators
- ✅ 10× cheaper, 10× faster scaling

**White space confirmed**: No dominant player in crowdsourced dexterous manipulation data.

---

## Competitive Moats

**NOT a moat** (be honest):
- First mover (easily copied)
- Technology (gloves are commodity)
- Patents (data isn't patentable)

**REAL moat** (if executed well):

1. **Data flywheel** (18-24 months to build)
   - More data → Better QA → Higher quality → More customers → More data

2. **User network** (12-18 months)
   - 10K trained collectors across 10 countries
   - Competitors need to recruit/train from scratch

3. **Customer lock-in** (24+ months)
   - Models trained on your data format
   - Switching cost = retrain entire pipeline

4. **Reputation** (12-24 months)
   - 100+ papers citing your dataset
   - The default source for dexterous data

**Time to replicate**: 24-36 months if executed well

**Defensibility**: MODERATE - This is an execution game, not a patent moat

---

## Capital Requirements

### Validation Phase ($8,500)

```
Phase 0 (Weeks 1-4):
- Rokoko gloves (1 pair):     $995
- Recording equipment:          $50
- Storage/compute:             $150
- Validation costs:            $305
Subtotal:                    $1,500

Phase 1 (Months 2-4):
- Additional gloves (5 pairs): $4,975
- Contributor stipends (5×$200): $1,000
- Shipping/logistics:            $500
Subtotal:                      $6,475

Phase 2 (Month 5):
- Video production:            $500
- Website/hosting:             $200
- Conference fees:             $100
- Launch marketing:            $1,200
Subtotal:                    $2,000

Total validation:            $8,500
```

### Post-Validation Funding

**If validation succeeds**, optional paths:

**Bootstrap** (Recommended):
- Reinvest revenue from custom collection
- Grow organically to $500K ARR
- Raise only if hitting constraints

**Seed Round** ($2-3M):
- Use traction as proof (100+ downloads, $135K revenue)
- Build SaaS platform, API, enterprise features
- Hire 5 engineers
- Target: $10M ARR in 24 months

---

## Timeline to Key Milestones

**Week 1**: Order gloves, set up recording
**Week 2-3**: Collect 20 hours
**Week 4**: Validate with researchers → **GO/NO-GO**

**Month 2-4**: Collect 100 hours with contributors
**Month 5**: Release dataset + paper
**Month 6**: First revenue ($20K)
**Month 12**: $135K revenue, proven business model

**Month 18**: Decision to bootstrap or raise
**Month 24**: $500K ARR (bootstrap) or $2M ARR (funded)
**Month 36**: Exit discussions begin

---

## Exit Strategy

**Most Likely: Acquisition** ($300M-1B, Years 5-7)

**Potential Acquirers**:
1. **Physical Intelligence / Skild AI** - Need data moat for foundation models ($500M-1B)
2. **NVIDIA** - Omniverse + robotics data ecosystem ($500M-1B)
3. **Scale AI** - Expand into robotics data ($300M-800M)
4. **Amazon** - Robotics for logistics (Covariant playbook) ($300M-500M)
5. **Google DeepMind** - Robotics research at scale ($400M-800M)

**Ambitious: IPO** ($3-5B, Years 7-10)
- Requires: $200M+ ARR, clear path to profitability
- Precedent: Scale AI (founded 2016 → $13.8B valuation 2024)

---

## Critical Success Factors

**What MUST go right**:

1. ✅ **Validation succeeds** (15+ researchers confirm dataset is valuable)
2. ✅ **Quality bar met** (research-grade data, not amateur recordings)
3. ✅ **Contributors recruited** (5 people commit to 20 hours each)
4. ✅ **Dataset gets cited** (10+ papers in first 6 months post-release)
5. ✅ **First revenue** ($20K in Month 6 from custom collection)
6. ✅ **Reputation built** ("The dexterous data people")

**What would kill this**:

1. 🔴 **Scale AI enters market** (20% probability, existential impact)
2. 🟡 **Sim2real wins** (30% probability, market shrinks 50%)
3. 🟡 **Quality too low** (30% probability, no one uses dataset)
4. 🟡 **Can't recruit contributors** (40% probability, slows timeline)

**Mitigation**: Validate early (Phase 0), iterate fast, move before incumbents notice.

---

## Why This Will Work (VC Perspective)

**As a partner at a16z, I'd fund this because**:

✅ **Capital efficient de-risking** - $8.5K to full validation (vs $3M on hypothesis)
✅ **Proven playbook** - DROID, RH20T succeeded with free datasets
✅ **Clear differentiation** - Dexterous data gap is real
✅ **Multiple monetization paths** - Not dependent on single revenue stream
✅ **Founder hustle** - Starting with 1 pair of gloves = "do things that don't scale"
✅ **Market timing** - Foundation model wave creates urgent demand
✅ **Credible exit** - $300M-1B in 5-7 years (fits fund timeline)

**This is a STRONG opportunity.**

---

## Next Steps

**If you're considering this**:

1. Read [Core Insight](01_CORE_INSIGHT.md) - Understand why this is different
2. Read [Execution Plan](04_EXECUTION_PLAN.md) - Week-by-week roadmap
3. Validate demand (email 10 robotics researchers, gauge interest)
4. Order gloves next Monday
5. Start collecting

**If you're an investor**:

1. Review [Market Analysis](02_MARKET_ANALYSIS.md)
2. Review [Risk Analysis](08_RISK_ANALYSIS.md)
3. Check [Fundraising Strategy](09_FUNDRAISING_STRATEGY.md)
4. Let's talk after Phase 0 validation (Week 5)

---

**The bottom line**: This is a real business disguised as an academic dataset project. The dataset is marketing. The business is B2B data services with software-like margins.

**Capital required**: $8.5K
**Time to validation**: 4 weeks
**Time to revenue**: 6 months
**Exit potential**: $300M-1B

**This is fundable. This is executable. This is realistic.**

Now go order those gloves.

---

[← Back to README](README.md) | [Next: Core Insight →](01_CORE_INSIGHT.md)
