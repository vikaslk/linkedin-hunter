# Major Updates - February 5, 2026

## 🎯 What Changed & Why

### Context
After Dr. Vikas ran the initial Comet prompt (v1.0) and applied to 2 jobs (HAI Health, Google), we received valuable feedback and made significant refinements.

---

## Key Updates

### 1. **NEW: Comet Prompt v2.0** (Multi-Phase Deep Search)

**File:** `/linkedin-hunter/comet-job-prompt-v2.md`

**What's New:**
- ✅ **3-Phase Approach:**
  - Phase 1: Broad scan (48 search combinations: 8 roles × 6 geographies)
  - Phase 2: Deep analysis of **top 25 matches** with 0-100 scoring
  - Phase 3: Actionable intelligence (immediate action plan, networking targets, tracking table)
- ✅ **Past 10 days** filter (changed from 7 days - better balance of freshness + volume)
- ✅ **Enhanced scoring system:** Role (40pts) + Geography (30pts) + Equity (20pts) + Other (10pts)
- ✅ **Direct LinkedIn URLs** for every match
- ✅ **Application strategy** for each job (apply immediately vs. research first vs. network intro)

**Why:**
- Comet v1.0 identified limitations (incomplete coverage, missing data)
- Multi-phase approach overcomes Comet's natural constraints
- 25 matches (vs. 15-20) provides more options without overwhelming
- 10-day window balances recency with sufficient volume

---

### 2. **Achievement Refinement** (Critical Update)

**BEFORE (Inaccurate):**
> "I built a $6M education business from scratch at GE HealthCare"

**AFTER (Accurate & Honest):**
> "As part of GE HealthCare's 40-person Education team, I helped scale quarterly revenue from $80K → $250K (2019-2023). My personal contributions: KOL network scaling (8X), global partnerships ($150K quarterly), program design."

**Why This Matters:**
- ✅ **Honesty:** Acknowledges team effort and leadership (Padmaja Sajja led the team)
- ✅ **Credibility:** Verifiable numbers ($80K → $250K is documented)
- ✅ **Impactful:** 3X growth story still compelling
- ✅ **Differentiating:** Shows ability to contribute to AND lead within high-performing teams
- ✅ **Startup-relevant:** Demonstrates team collaboration + individual initiative

**Updated in:**
- `profile-summary.md` (elevator pitches, quick stats, new "Team Acknowledgments" section)
- `comet-job-prompt-v2.md` (candidate profile)
- All application templates

---

### 3. **Critical Exclusions** (Prevent Wasted Applications)

Added explicit filters for roles to AVOID:
- ❌ **Investment-required roles** ("invest ₹10L to join as co-founder")
- ❌ **Sweat equity only** (no salary component)
- ❌ **BDS/MDS dentistry-specific** (Dr. Vikas is MBBS medical, NOT dentist)
- ❌ **"Big 4 alumni required" or "Ex-MBB only"** (he has strategic consulting skills, not formal Big 4/MBB)
- ❌ **Pure clinical practice** (no strategy/leadership)
- ❌ **Delhi/NCR/Mumbai** (outside target geography)

**Why:**
- Saves time on applications that won't succeed
- Focuses energy on high-probability opportunities
- Prevents frustration from mismatched roles

**Updated in:**
- `comet-job-prompt-v2.md` (CRITICAL EXCLUSIONS section at top)
- `profile-summary.md` (new "Roles to AVOID" section)
- `README.md` (warning in Quick Start section)

---

### 4. **Experience Update** (14+ Years)

**Changed throughout all documents:**
- 12+ years → **14+ years** (as of February 2026)

**Based on:** Updated CV (`Dr Vikas L Krishna - CV - February 2026.pdf`)

**Updated in:**
- All profile summaries
- Comet prompts
- Target roles documentation
- Quick stats

---

### 5. **Consulting Background Clarification**

**Challenge:** Dr. Vikas has consulting skills but NOT formal Big 4/MBB experience

**Solution:** Reframed as "independent strategic consulting + deal-making"

**Evidence:**
- Innov4Sight Health (strategic consultant, health-tech startup)
- GE HealthCare (deal-making, global partnerships $150K quarterly)
- ₹50L research grants secured (consultative selling)

**Application Strategy:**
- Apply to consulting firms (don't self-reject)
- Frame as: "client-side strategic problem-solving + business development"
- Emphasize: "I've RUN the operations consulting firms advise on"

**Updated in:**
- `profile-summary.md` ("Red Flags to Address" section)
- `comet-job-prompt-v2.md` (candidate profile + exclusions)

---

### 6. **NEW: Conversation Log** (`conversation-log.md`)

**Purpose:** Track our discussions, decisions, and learnings over time

**Contents:**
- Session summaries (user inputs, actions taken, insights)
- Patterns & meta-learnings (as they emerge)
- Quick reference of key decisions
- Post-Comet run review templates
- Application response tracking templates
- Monthly reflection prompts

**Why:**
- Helps Dr. Vikas refine job search strategy iteratively
- Documents what works vs. what doesn't
- Enables prompt optimization based on actual results
- Creates institutional knowledge

---

## Files Updated

### New Files:
1. `/linkedin-hunter/comet-job-prompt-v2.md` - ⭐ **USE THIS FOR NEXT RUN**
2. `/linkedin-hunter/conversation-log.md` - Track discussions and learnings
3. `/linkedin-hunter/applications-log.md` - Simple application tracker
4. `/linkedin-hunter/UPDATES-FEB-5-2026.md` - This file

### Modified Files:
1. `/linkedin-hunter/profile-summary.md` - Achievement refinement, team acknowledgments, experience update
2. `/linkedin-hunter/comet-job-prompt.md` - Added critical exclusions, updated profile
3. `/linkedin-hunter/README.md` - Added exclusions warning

---

## Comparison: v1.0 vs v2.0

| Feature | v1.0 (Feb 4) | v2.0 (Feb 5) |
|---------|-------------|-------------|
| **Approach** | Single-phase | 3-phase comprehensive |
| **Results** | 15-20 matches | Top 25 matches |
| **Date Range** | Past 7 days | Past 10 days |
| **Scoring** | Qualitative | 0-100 quantitative |
| **Coverage** | Limited combinations | 48 search combinations |
| **Output** | List of jobs | Jobs + strategy + tracking + networking |
| **Exclusions** | Basic | Comprehensive (6 specific filters) |
| **URLs** | Some | All (direct LinkedIn links) |
| **Action Plan** | None | Immediate next steps provided |
| **Tracking** | Manual | Copy-paste table included |

**Recommendation:** Use v2.0 for comprehensive bi-weekly scans, v1.0 for quick mid-week checks

---

## What to Do Next

### Immediate (Tonight/Tomorrow):
1. **Run Comet v2.0**
   - Open `/linkedin-hunter/comet-job-prompt-v2.md`
   - Copy the full prompt (starts "PHASE 1: BROAD SCAN")
   - Paste into Perplexity Comet
   - Wait 90-120 seconds for results

2. **Review Top 25 Matches**
   - Focus on 90-100 score jobs first
   - Check for any exclusion violations (investment-required, BDS/MDS, etc.)
   - Copy tracking table to Excel or Google Sheets

3. **Apply to 90+ Score Jobs**
   - Same day application for highest matches
   - Use team-achievement framing from updated profile
   - Log in `/linkedin-hunter/applications-log.md`

### This Week:
1. Apply to 20-30 total jobs from Comet results
2. Connect with 10+ hiring managers on LinkedIn
3. Track response rates and patterns
4. Update `conversation-log.md` with post-Comet review

### After 2-3 Comet Runs:
**Decision Point:** Validate approach effectiveness, then proceed to Phase 2 (MCP Agent build) if desired

---

## Key Learnings from This Session

### What Worked:
- ✅ Initial Comet prompt structure was solid foundation
- ✅ Found relevant jobs quickly (HAI Health, Google)
- ✅ Clear geographies and role priorities

### What Needed Refinement:
- 🔧 Achievement framing (solo claim → team-based with personal contributions)
- 🔧 Exclusion criteria (needed explicit filters)
- 🔧 Search comprehensiveness (single-phase → multi-phase)
- 🔧 Date range (7 days too narrow → 10 days better)

### Insights:
1. **Honest framing builds credibility:** Team context + personal contributions > solo credit claims
2. **Explicit exclusions save time:** Clear filters prevent wasted applications
3. **Multi-phase beats single pass:** Structured approach overcomes Comet limitations
4. **Verifiable numbers matter:** "$80K → $250K" with team context > "$6M built from zero"
5. **Consulting framing matters:** "Independent strategic consulting" bridges gap without claiming Big 4/MBB

---

## Questions Addressed

**Q: "Can we use a multi-phased approach?"**
✅ Yes - Comet v2.0 now uses 3 phases for comprehensive coverage

**Q: "Can we shortlist 25 roles?"**
✅ Yes - Phase 2 identifies and scores top 25 matches

**Q: "Can we consider past 10 days?"**
✅ Yes - Updated default to past 10 days (adjustable if needed)

**Q: "How do we downplay the $6M achievement?"**
✅ Reframed as team achievement ($80K → $250K quarterly) with personal contributions clarified

**Q: "Can we exclude BDS/MDS roles?"**
✅ Yes - Added to CRITICAL EXCLUSIONS at top of prompt

**Q: "Can we maintain a log of our conversations?"**
✅ Yes - Created `conversation-log.md` to track discussions, decisions, learnings

---

## Status: Phase 1 ENHANCED ✅

- ✅ Comet prompt v2.0 ready for use
- ✅ Profile documentation updated with accurate achievements
- ✅ Exclusion filters comprehensive and explicit
- ✅ Conversation log system in place
- ✅ Application tracking templates ready
- ⏳ Phase 2 (MCP Agent) ready to start on your signal

---

**Next Major Milestone:** Run Comet v2.0 and apply to 20-30 jobs this week

**Last Updated:** February 5, 2026, 4:30 AM IST
