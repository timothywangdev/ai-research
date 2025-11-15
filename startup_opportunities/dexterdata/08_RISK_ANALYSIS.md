# Risk Analysis - DexterData

**Last Updated**: 2025-11-14

---

## Risk Matrix

| Risk | Probability | Impact | Mitigation | Status |
|------|-------------|--------|------------|--------|
| Scale AI enters market | 20% | EXISTENTIAL | Move fast, 18-month head start | ⚠️ Monitor |
| Sim2real wins | 30% | HIGH | Position as validation service | 🟡 Hedge |
| Quality too low | 30% | HIGH | Validate in Phase 0 | ✅ Addressable |
| Can't recruit contributors | 40% | MEDIUM | Start solo, recruit parallel | ✅ Mitigated |
| Dataset not used | 20% | HIGH | Pre-validate with 30 researchers | ✅ Addressable |
| Market too small | 40% | MEDIUM | Bootstrap-friendly economics | 🟢 Acceptable |

---

## Critical Risks (Detailed Analysis)

### Risk 1: Scale AI Enters Market 🔴

**Probability**: 20% (in next 24 months)
**Impact**: EXISTENTIAL - They win on brand/capital

**Why it could happen**:
- Adjacent to their core business (data services)
- They have $15.9B raised (massive capital advantage)
- Brand recognition + existing customer relationships
- Could acquire us or build competitor overnight

**Why it might NOT happen**:
- Different business (annotation vs active collection)
- Robotics is complex, requires domain expertise
- Lower margins than their core (50%+ vs our 40%)
- Focused on bigger markets (LLMs, autonomous vehicles)

**Our defense**:
1. **Speed** - 18-month head start before they notice
2. **Specialization** - Deep robotics expertise they don't have
3. **Hardware** - Proprietary glove designs, trained collector network
4. **Relationships** - Lock in foundation model customers (multi-year contracts)

**Mitigation plan**:
- Move aggressively: 100-hour dataset in 4 months (not 12)
- Build proprietary tools they'd have to rebuild
- Sign 2-3 year contracts with key customers
- If they enter: Position as specialized premium vs their commodity

**Worst case**: Acquisition target ($50-100M) instead of independent exit

---

### Risk 2: Simulation Wins (Sim2Real Gap Closes) 🟡

**Probability**: 30%
**Impact**: HIGH - Market shrinks 50-70%

**The scenario**:
- Genesis AI's 430,000× faster simulation becomes standard
- Sim2real gap narrows from 30% → 5%
- Real-world data needed only for final validation (not training)
- Market for training data shrinks dramatically

**Why it could happen**:
- Simulation improving rapidly (NVIDIA Isaac, MuJoCo, Genesis)
- Research trend toward sim2real
- Way cheaper than real data collection
- Infinite data generation possible

**Why real data still matters**:
- Sim2real gap unlikely to fully close (physics complexity)
- Long-tail edge cases can't be simulated
- Final validation always needs real world
- Regulatory requirements (FDA, ISO) require real testing

**Our pivot if this happens**:
1. **Sim2real validation service** - Companies test sim policies on our real-world data
2. **Hybrid offering** - Sim data + real validation bundle
3. **Partnership** - Work WITH sim companies (complementary)
4. **Specialize** - Focus on tasks sim can't handle (deformables, liquids)

**Mitigation plan**:
- Monitor sim2real research closely
- Build relationships with Genesis, NVIDIA Isaac teams
- Offer "sim grounding" service (map sim to real)
- Diversify: Don't depend 100% on training data sales

**Hedge**: Even if market shrinks 50%, still $50-75M TAM (acceptable)

---

### Risk 3: Dataset Quality Below Bar 🟡

**Probability**: 30%
**Impact**: HIGH - No one uses dataset, reputation damaged

**The failure mode**:
- Collect 100 hours but quality insufficient for research
- Glove tracking drift >10° (unusable)
- Video quality poor (lighting, occlusion issues)
- Researchers say "can't train policies on this"

**Why it could happen**:
- Rokoko gloves less accurate than expected
- Contributors don't follow protocols
- QA processes inadequate
- Our quality bar doesn't match research needs

**How we prevent this**:
1. **Phase 0 validation** (Week 1-4)
   - Collect 20 hours yourself FIRST
   - Get 30 researchers to review BEFORE scaling
   - Iterate on quality based on feedback

2. **Rigorous QA**
   - Automated drift detection (<10° threshold)
   - Manual review of random 10% sample
   - Reject/redo any demos with issues

3. **Contributor training**
   - 1-hour onboarding call (hands-on)
   - Quality checklist for every demo
   - Weekly quality reviews + feedback

4. **Benchmark validation**
   - Train baseline policy on our data
   - Measure robot success rates
   - Compare to DROID/RH20T quality

**Mitigation if quality issues arise**:
- Upgrade hardware (Manus gloves $3,500 if needed)
- Re-collect problematic demos
- Be transparent: "v1.0 had issues, v1.1 fixes them"
- Academic community forgives iteration if you're honest

**Decision point**: If Phase 0 validation fails quality bar, STOP and iterate (don't proceed to 100 hours).

---

### Risk 4: Can't Recruit Contributors 🟢

**Probability**: 40%
**Impact**: MEDIUM - Slows timeline but not fatal

**The problem**:
- Can't find 5 people willing to record 20 hours each
- Contributors drop out mid-project
- Quality varies too much across contributors

**Why it could happen**:
- $200 stipend not attractive enough
- Time commitment too high (20 hours)
- Gloves uncomfortable / technical issues
- People flake (gig economy problem)

**Backup plans**:
1. **Collect solo** (100 hours yourself over 6 months)
   - Slower but viable
   - Ensures consistent quality
   - Still achieves dataset goal

2. **Reduce target** (50 hours instead of 100)
   - Still valuable (2× RealDex)
   - Faster to market
   - Can expand later

3. **Increase incentives**
   - Raise stipend to $400
   - Let them keep gloves after 10 hours (not 20)
   - Find intrinsically motivated contributors (students, hobbyists)

4. **Alternative labor sources**
   - University research assistants (paid through grants)
   - VR enthusiasts (interested in glove tech)
   - Mechanical Turk / Upwork (pay per demo)

**Mitigation plan**:
- Start recruiting during Phase 0 (parallel track)
- Over-recruit: Target 8 people to get 5 who complete
- Weekly check-ins to catch dropouts early
- Have replacement pipeline ready

**Acceptable outcome**: Even with 0 contributors, solo collection of 50 hours in 6 months = still valuable dataset.

---

### Risk 5: No One Uses Dataset 🟡

**Probability**: 20%
**Impact**: HIGH - Credibility not established, no inbound customers

**The scenario**:
- Release DexManip-100, get 10 downloads total
- No papers cite it
- Community ignores it
- Revenue plan (based on inbound) fails

**Why it could happen**:
- Wrong tasks (not what researchers need)
- Format incompatible with common tools
- Marketing/launch poorly executed
- Timing bad (conference deadlines, etc.)

**How we prevent this**:
1. **Pre-validation** (Week 4 of Phase 0)
   - 30 researchers confirm "we'd use this"
   - If <15 say yes, we STOP and pivot

2. **Task selection based on demand**
   - Ask researchers: "What tasks do you need?"
   - Collect exactly what they requested
   - Not what we think is cool

3. **Format compatibility**
   - PyTorch DataLoader (standard)
   - ROS bag export option
   - Match DROID format where possible
   - Extensive documentation + examples

4. **Strong launch**
   - Submit paper to top conference
   - Coordinate with publication date
   - Twitter, Reddit, Hacker News
   - Email all 30 validation researchers

5. **Academic partnerships**
   - Co-author with respected professor
   - Present at top conferences
   - Guest lectures at universities

**Mitigation if it happens**:
- Direct outreach (not just passive)
- Offer free custom data to key labs ("try it, we'll collect what you need")
- Pivot to pure B2B (skip open dataset, go straight to services)
- Accept failure fast, cut losses at $13.5K

**Key metric**: 100+ downloads in first month = success, <20 = failure

---

## Operational Risks

### Risk: Data Security / Privacy

**Issue**: Collecting data in people's homes, potential privacy concerns

**Mitigation**:
- Terms of service: Contributors consent to data being released publicly
- Face blurring: Automatically blur any faces in video
- PII removal: No audio, no personal items in frame
- Data review: Manual check before public release
- Opt-out: Contributors can request specific demos deleted

---

### Risk: Glove Hardware Failures

**Issue**: Gloves break, malfunction, lost in shipping

**Mitigation**:
- Buy 6 pairs (not 5) - 1 spare for replacements
- Shipping insurance
- Require deposits from contributors ($500 refundable)
- Rokoko warranty (1 year)
- Budget 20% for breakage/loss

---

### Risk: Platform/Infrastructure

**Issue**: Data loss, website downtime, scaling issues

**Mitigation**:
- Triple backup (local + Google Drive + AWS S3)
- Use proven infrastructure (GitHub Pages, Hugging Face)
- Start small, scale gradually
- Have technical advisor (robotics professor with infra experience)

---

## Market Timing Risks

### Risk: Too Early

**Scenario**: Dexterous robots don't go mainstream for 5-10 years, market not ready

**Likelihood**: 20%

**Mitigation**:
- Current demand exists (foundation models need data NOW)
- Even if dexterous robots delayed, gripper robots can benefit
- Pivot to other use cases (VR training, task understanding, etc.)

---

### Risk: Too Late

**Scenario**: Someone else launches similar dataset before us

**Likelihood**: 15%

**Mitigation**:
- Move FAST (5 months to launch, not 12)
- Monitor arXiv, RSS, ICRA for competing datasets
- If someone launches first: Differentiate on quality, task diversity, or go premium-only

---

## Financial Risks

### Risk: Burn Rate Too High

**Issue**: Spend $13.5K but can't monetize, run out of capital

**Mitigation**:
- Phase 0 is only $2,300 - STOP if validation fails
- Bootstrap-friendly (no employees, minimal overhead)
- Can pause/slow at any point
- Revenue starts Month 6 (only 6 months cash needed)

---

### Risk: Customer Concentration

**Issue**: 1-2 customers = 80% of revenue, they churn

**Mitigation**:
- Diversify customer base (10+ customers target)
- Multi-year contracts (lock-in)
- Don't depend on any single customer >30% revenue
- Build platform business (less customer-dependent)

---

## Competitive Risks

### Risk: Incumbent Pivots

**Scenario**: Encord, Sapien, or Segments.ai add dexterous data collection

**Likelihood**: 30%

**Mitigation**:
- They focus on annotation (different skill set)
- 12-18 month head start
- We have deeper robotics expertise
- Partner instead of compete (white-label our collection to them)

---

## Summary: Risk Management Strategy

**Accept**:
- Market size uncertainty (40% risk, acceptable if bootstrap works)
- Simulation competition (30% risk, can pivot)
- Contributor recruitment (40% risk, can do solo)

**Mitigate**:
- Quality issues (Phase 0 validation catches this early)
- Dataset not used (Pre-validate demand with 30 researchers)
- Operational issues (backups, insurance, processes)

**Transfer**:
- Hardware failures (insurance, deposits, warranties)
- Legal/privacy (lawyer review terms of service)

**Avoid**:
- Don't commit $13.5K until Phase 0 succeeds
- Don't scale before validating quality
- Don't depend on single customer or technology

---

**Overall Risk Assessment**: MODERATE - Acceptable for $13.5K investment with $300M-1B upside.

Key insight: Most risks are **early detectable** (Phase 0 validation). If we pass Week 4, risks drop dramatically.

---

[← Back to README](README.md) | [Next: Fundraising Strategy →](09_FUNDRAISING_STRATEGY.md)
