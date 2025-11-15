# Business Model - DexterData

**Last Updated**: 2025-11-14

---

## Revenue Streams

### Stream 1: Custom Data Collection (40% of revenue)

**What it is**:
Companies request specific manipulation tasks, we collect demonstrations on demand.

**Pricing**:
- $15-30 per demonstration
- Minimum order: 100 demos = $1,500-3,000
- Typical project: 500-1,000 demos = $10K-30K

**Example**:
```
Customer: "We need 500 demos of folding different types of fabric"
Timeline: 3-4 weeks
Price: $10,000 ($20/demo)
Delivery: Processed dataset in their preferred format
```

**Unit Economics**:
```
Revenue:              $10,000 (500 demos × $20)
Costs:
  Collector pay:       $4,000 (500 × $8)
  Processing:          $1,000
  Platform/overhead:   $1,000
Gross Profit:          $4,000
Margin:                   40%
```

**Customers**: Foundation model companies, robotics startups, research labs

---

### Stream 2: Premium Dataset Subscription (30% of revenue)

**What it is**:
Two-tier dataset access - Free vs Premium

**Free Tier**:
- DexManip-100 (released once)
- 100 hours, 1,000+ demos
- Research use only
- Community support

**Premium Tier** ($3-5K/year):
- DexManip-300+ (updated quarterly)
- Commercial license
- New task categories added monthly
- Priority feature requests
- Direct support (email/Slack)

**Unit Economics**:
```
Revenue:              $3,000/year per customer
Cost:
  Incremental data:     $200 (amortized)
  Support:              $100
Gross Profit:          $2,700
Margin:                   90%
```

**Customers**: Robotics companies, research labs, manufacturing

---

### Stream 3: Consulting Services (20% of revenue)

**What it is**:
Help companies build their own data collection pipelines or process existing data.

**Services**:
1. **Pipeline setup** ($15-25K)
   - Design data collection workflow
   - Recruit + train collectors
   - Set up QA systems
   - Deliver turnkey solution

2. **Data processing** ($5-15K)
   - Clean + annotate their existing dataset
   - Retargeting to their robot
   - Quality validation

3. **Training workshops** ($2-5K)
   - Half-day to full-day
   - Best practices for data collection
   - Hands-on with our tools

**Unit Economics**:
```
Revenue:              $20,000 per project
Costs:
  Your time (40 hrs):  $4,000 (@$100/hr opportunity cost)
  Tools/travel:        $2,000
Gross Profit:         $14,000
Margin:                   70%
```

**Customers**: Mid-sized robotics companies, manufacturing firms

---

### Stream 4: Foundation Model (10% of revenue, future)

**What it is**:
Train "DexterNet" - manipulation foundation model on proprietary dataset (1M+ hours).

**Timeline**: Year 3-5 (after collecting 1M hours)

**Pricing**:
- API access: $0.01-0.10 per inference
- Enterprise license: $100K-500K/year
- Fine-tuning service: $50-200K per project

**Moat**: Trained on largest dexterous dataset (proprietary data after free 100hrs)

**Customers**: Companies building manipulation products

---

## Pricing Matrix

| Product | Customer | Price | Margin |
|---------|----------|-------|--------|
| Free dataset (DexManip-100) | Anyone | $0 | N/A (marketing) |
| Custom collection (small) | Research lab | $1.5-3K | 40% |
| Custom collection (medium) | Robotics startup | $10-30K | 40% |
| Custom collection (large) | Foundation model co | $50-200K | 35% |
| Premium subscription | Commercial user | $3-5K/year | 90% |
| Consulting - workshop | Any company | $2-5K | 70% |
| Consulting - pipeline | Mid-size company | $15-25K | 70% |
| Foundation model API | Developers | $0.01-0.10/call | 80% |
| Foundation model license | Enterprise | $100-500K/year | 90% |

---

## Financial Projections

### Year 1 (Months 6-12, Post-Launch)

**Custom Collection**:
- 10 projects × $10K avg = $100K
- Margin: 40% = $40K profit

**Premium Subscriptions**:
- 5 customers × $2K avg = $10K
- Margin: 90% = $9K profit

**Consulting**:
- 2 projects × $12.5K = $25K
- Margin: 70% = $17.5K profit

**Total Year 1**: $135K revenue, $66.5K profit (49% margin)

---

### Year 2

**Custom Collection**:
- 40 projects × $10K avg = $400K
- Margin: 40% = $160K

**Premium Subscriptions**:
- 15 customers × $3.5K avg = $52.5K
- Margin: 90% = $47K

**Consulting**:
- 8 projects × $12.5K = $100K
- Margin: 70% = $70K

**Total Year 2**: $552.5K revenue, $277K profit (50% margin)

---

### Year 3

**Custom Collection**:
- 80 projects × $15K avg = $1.2M
- Margin: 40% = $480K

**Premium Subscriptions**:
- 50 customers × $4K avg = $200K
- Margin: 90% = $180K

**Consulting**:
- 15 projects × $15K = $225K
- Margin: 70% = $157.5K

**Foundation Model** (early stage):
- 10 enterprise licenses × $40K = $400K
- Margin: 90% = $360K

**Total Year 3**: $2.025M revenue, $1.18M profit (58% margin)

---

## Unit Economics Deep Dive

### Custom Data Collection

**Cost structure** (per 500-demo project):
```
Revenue:                          $10,000

Variable costs:
  Collector payments (500×$8):     $4,000
  Processing (automated):            $500
  QA/review (manual):                $300
  Storage/bandwidth:                 $100
  Payment processing (3%):           $300
Total variable costs:              $5,200

Contribution margin:               $4,800 (48%)

Fixed costs (allocated):
  Platform development:              $500
  Sales/marketing:                   $300
  General overhead:                  $200
Total fixed costs:                 $1,000

Net profit per project:            $3,800 (38%)
```

**Key drivers**:
- Collector cost ($8/demo): Largest variable cost
- Processing automation: Reduces manual QA cost
- Scale: Fixed costs amortize over more projects

**Improving margins**:
- Automate QA: 90% → 95% automation = +$200/project
- Offshore processing: India team = -$150/project
- Volume discounts: Loyal customers = higher retention
- Premium pricing: Specialized tasks = $30/demo

---

### Premium Subscriptions

**LTV calculation** (per customer):
```
Annual subscription:               $4,000
Average retention:                 3 years
Gross LTV:                        $12,000

Costs:
  Incremental data collection:       $600 (200 hrs × $3/hr amortized)
  Support (3 years):                 $300
  Platform/overhead:                 $200
Total costs:                       $1,100

Net LTV:                          $10,900

CAC (from free dataset):              $0 (organic)
LTV/CAC:                          Infinite (organic channel)
```

**Retention drivers**:
- Dataset keeps growing (quarterly updates = ongoing value)
- Switching cost (models trained on our format)
- Commercial license (legal dependency)

---

## Business Model Evolution

### Stage 1: Services Business (Year 1-2)
- Focus: Custom data collection
- Model: High-touch, manual sales
- Margins: 40%
- Scale limit: ~$1M ARR (labor-intensive)

### Stage 2: Platform Business (Year 2-3)
- Focus: Premium subscriptions + API
- Model: Self-service, automated
- Margins: 80%+
- Scale: $5-10M ARR potential

### Stage 3: Product Business (Year 3-5)
- Focus: Foundation model (DexterNet)
- Model: License + API
- Margins: 90%+
- Scale: $50M+ ARR potential

**Goal**: Transition from services → platform → product as dataset scale increases.

---

## Comparison to Analogous Companies

### Scale AI

| Metric | Scale AI | DexterData (Target) |
|--------|----------|---------------------|
| Business model | Data labeling BPO | Data collection BPO |
| Gross margin | 50%+ | 40-50% (custom), 80%+ (premium) |
| ARR | $1.5B | $2M (Year 3) |
| Customers | 300+ | 50 (Year 3) |
| Valuation | $13.8B | $300M-1B (exit target) |

**Key difference**: We focus on collection (higher value) vs annotation (commodity).

### Covariant

| Metric | Covariant | DexterData (Target) |
|--------|-----------|---------------------|
| Business model | Vertical deployment | Horizontal data platform |
| Timeline to $20M ARR | 7 years | 4-5 years (target) |
| Margins | 30-40% | 50-60% (blended) |
| Valuation | $380M (down round) | $300M-500M (exit target) |

**Key difference**: We sell data, they sell deployment. Lower infrastructure cost.

---

## Strategic Considerations

### Build vs Buy

**Customers will ask**: "Should we build this in-house?"

**Our answer**:
```
In-house data collection costs:
- Hire 2 FTEs for data ops:           $200K/year
- Glove hardware (10 pairs):           $18K
- Platform development:               $150K
- Time to first data:                 6 months
Total Year 1:                        $368K for ~20K demos

With DexterData:
- 20K demos × $20:                   $400K
- But:
  ✓ Immediate (no 6-month delay)
  ✓ Higher quality (our expertise)
  ✓ No headcount
  ✓ Flexible (scale up/down)

ROI: For <100K demos/year, outsource to us is cheaper.
```

**When they should build**: >100K demos/year → break-even on in-house.

**Our response**: Offer hybrid (train their team, provide tools, ongoing support at $10K/month).

---

### Moat & Defensibility

**What IS our moat**:
1. **Data flywheel** (18-24 months to build)
   - More data → Better QA → Higher quality → More customers → More data
   
2. **Reputation** (12-18 months)
   - 100+ paper citations
   - Default source for dexterous data
   
3. **User network** (12-24 months)
   - 1,000 trained collectors globally
   - Competitor needs to recruit/train from scratch
   
4. **Customer lock-in** (12-24+ months)
   - Models trained on our format
   - Switching cost high

**What is NOT our moat**:
- Technology (gloves are commodity)
- Patents (data not patentable)
- First mover alone (copyable)

**Defensibility**: MODERATE. This is an execution game. Move fast, build reputation, lock in customers.

---

## Key Metrics to Track

### Leading Indicators (Months 1-6)
- Dataset downloads
- GitHub stars
- Paper citations
- Inbound demo requests

### Revenue Metrics (Months 6+)
- MRR (premium subscriptions)
- Custom project pipeline ($ value)
- Average deal size
- Customer acquisition cost

### Efficiency Metrics
- Cost per demo collected
- Gross margin by product line
- LTV/CAC ratio
- Payback period

### Growth Metrics
- Month-over-month revenue growth
- Customer count
- Retention rate (premium subs)
- Dataset size (hours collected)

**Target metrics (Year 1)**:
- 100+ downloads (DexManip-100)
- $135K revenue
- 15-20 customers
- 50% gross margin

---

[← Back to README](README.md) | [Next: Execution Plan →](04_EXECUTION_PLAN.md)
