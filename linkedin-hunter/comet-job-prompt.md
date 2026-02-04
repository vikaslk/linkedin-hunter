# LinkedIn Job Hunt - Perplexity Comet Master Prompt

## HOW TO USE THIS PROMPT

1. **Copy the entire prompt** from the section below (starting with "You are a LinkedIn job search specialist...")
2. **Open Perplexity** (perplexity.ai) and select **Comet mode** (the AI agent)
3. **Paste the prompt** and hit enter
4. **Wait 30-60 seconds** while Comet searches LinkedIn and analyzes jobs
5. **Review the results** - Comet will provide 15-20 curated job matches with direct LinkedIn URLs
6. **Click the URLs** to apply directly on LinkedIn
7. **Repeat weekly** - Update the date filter in the prompt to get fresh results

---

## MASTER PROMPT (COPY EVERYTHING BELOW THIS LINE)

```
You are a LinkedIn job search specialist helping Dr. Vikas L Krishna find healthcare opportunities.

CRITICAL EXCLUSIONS (DO NOT INCLUDE):
❌ Roles requiring personal financial investment (co-founder with capital requirement, sweat equity only)
❌ BDS/MDS (dentistry) specific positions - candidate is MBBS (medical), NOT a dentist
❌ Roles explicitly requiring "Big 4 alumni" or "ex-MBB consultant" - he has strategic consulting experience but not formal Big 4/MBB background
❌ Jobs in Delhi, NCR, Mumbai, or North India
❌ Pure clinical practice roles without strategy/leadership component

CANDIDATE PROFILE:
- Name: Dr. Vikas L Krishna
- Education: MBBS (Medical) + MBA (HR/Marketing) - NOT BDS/MDS (Dentistry)
- Experience: 14+ years in healthcare (as of Feb 2026)
- Background: Clinical practice + hospital operations + strategic healthcare consulting + digital health innovation
- Key Achievement: Built USD 6M education business from scratch at GE HealthCare (7 years, Feb 2019 - Dec 2023)
- Leadership: Managed hospitals up to 1800 beds (Sriramachandra Hospital, Chennai)
- Expertise: Healthcare strategy, clinical operations, digital health, P&L management, medical education
- Consulting Experience: Independent strategic consulting (Innov4Sight Health), unlocking special deals at GE HealthCare Education Team - NOT formal Big 4 consultant

TARGET ROLES (Priority Order):
1. STARTUPS WITH EQUITY + SALARY (PRIMARY FOCUS)
   - Chief Medical Officer (CMO)
   - VP of Clinical Operations
   - Medical Director with equity
   - Founding Medical Team Member
   - Head of Medical Affairs
   - VP Clinical Strategy

2. HEALTHCARE CONSULTING
   - Healthcare Strategy Consultant (McKinsey, BCG, Bain)
   - Senior Healthcare Consultant (Deloitte, EY, PwC, KPMG)
   - Practice Lead (ZS Associates, IQVIA, L.E.K.)

3. DIGITAL HEALTH / HEALTH-TECH
   - VP of Clinical Operations
   - Head of Medical Affairs
   - Clinical Director
   - VP of Healthcare Strategy

4. HEALTHCARE LEADERSHIP
   - Chief Medical Officer
   - Medical Director
   - VP of Clinical Operations
   - Director of Medical Services

5. OTHER OPPORTUNITIES
   - Medical Affairs Director
   - Healthcare Strategy Manager
   - Director of Healthcare Partnerships

GEOGRAPHIES (Priority Order):
1. UAE - Dubai, Abu Dhabi, Sharjah (other emirates lower priority)
2. India - Bangalore, Chennai ONLY (explicitly EXCLUDE Delhi, NCR, Mumbai, other cities)
3. Oman - Muscat, Salalah
4. Singapore
5. Malaysia - Kuala Lumpur, Penang
6. Indonesia - Jakarta, Bali

SEARCH TASK:
Search LinkedIn Jobs for opportunities matching the above criteria posted in the LAST 7 DAYS.

Use these search variations:
- "Chief Medical Officer" OR "CMO" healthcare (Dubai OR "Abu Dhabi" OR Bangalore)
- "VP Clinical Operations" OR "Medical Director" startup equity (Dubai OR Bangalore OR Singapore)
- "Healthcare Strategy Consultant" (McKinsey OR BCG OR Bain OR Deloitte OR EY OR PwC) (Dubai OR Singapore OR India)
- "Head of Medical Affairs" OR "VP Medical Affairs" digital health (Dubai OR Bangalore OR Singapore)
- "Clinical Excellence" OR "Clinical Operations" Director healthcare (Chennai OR Dubai OR Singapore)
- "Medical Director" startup (Bangalore OR Dubai OR Singapore) equity
- "Healthcare Consulting" senior (Dubai OR Singapore OR Chennai OR Bangalore)
- telemedicine OR "digital health" CMO (UAE OR India OR Singapore)

FILTERS TO APPLY:
INCLUDE:
- Health-tech, digital health, telemedicine platforms
- Healthcare consulting firms (MBB, Big 4, specialized)
- Hospital management and operations
- Medical education and training
- Healthcare innovation and strategy
- Startups (Series A to Series C preferred) - equity-focused roles
- Director level and above

EXCLUDE:
- Roles requiring personal financial investment or "sweat equity only"
- Pure clinical roles with no strategy/leadership component
- Pharmaceutical sales or medical representative roles
- Medical writing or content creation roles
- Nursing or allied health positions
- Medical coding or billing roles
- BDS/MDS (dentistry) specific roles - candidate is MBBS (medical)
- Delhi, NCR, Mumbai, or other non-target Indian cities
- Roles explicitly requiring Big 4 consulting experience (he has independent consulting background)

PRIORITIZE THESE SIGNALS:
🔥 HIGHEST PRIORITY (Score 90-100):
- Jobs explicitly mentioning "equity" or "stock options" WITH competitive salary
- Startups in Series A, B, or C funding stage (NOT requiring personal investment)
- CMO or VP-level roles at health-tech startups with both equity AND salary
- Healthcare consulting at MBB (McKinsey, BCG, Bain) - roles open to non-traditional consultants
- Dubai or Bangalore locations
- Roles valuing independent consulting/strategic initiatives experience

⭐ HIGH PRIORITY (Score 75-89):
- Digital health or telemedicine companies
- Regional or global healthcare leadership roles
- Healthcare consulting at Big 4
- Singapore or Abu Dhabi locations
- Roles combining clinical + business strategy

✓ MEDIUM PRIORITY (Score 60-74):
- Medical Director roles at hospital chains
- Head of Medical Affairs at pharma/medtech
- Healthcare operations leadership
- Chennai, Oman, or Malaysia locations

⚠️ LOW PRIORITY (Score Below 60):
- Pure corporate hospital roles
- Roles without clear strategy component
- Indonesia or remote-only positions
- Contract or temporary positions

OUTPUT FORMAT:
For each job opportunity found, provide:

**Job #[Number]**
- **Title:** [Exact job title]
- **Company:** [Company name + brief description]
- **Location:** [City, Country]
- **Company Stage:** [Startup Series A/B/C / Consulting / Corporate / Hospital Chain]
- **Salary:** [If mentioned, or "Not disclosed"]
- **Equity:** [Yes/No - if mentioned]
- **Posted:** [Date or "X days ago"]
- **LinkedIn URL:** [Direct link to job posting]
- **Match Score:** [0-100 with brief reasoning]
- **Why It Matches:** [2-3 sentences explaining fit with Dr. Vikas's profile]
- **Key Qualifications Needed:** [Top 3-4 requirements]
- **Action Items:** [What Dr. Vikas should do - e.g., "Apply directly", "Research company first", "Find hiring manager on LinkedIn"]

ORGANIZE OUTPUT:
Group by Geography (UAE → India → Others), then by Priority Score (highest first).
Show TOP 20 MATCHES ONLY.

Also include:
- **Quick Stats:** Total jobs found, avg match score, top geography, top role type
- **Market Insights:** Any trends you notice (e.g., "10 health-tech CMO roles in Dubai this week")
- **Recommendations:** 2-3 actionable next steps for Dr. Vikas

START COMPREHENSIVE LINKEDIN JOB SEARCH NOW.
```

---

## CUSTOMIZATION OPTIONS

Want to adjust the search? Modify these sections before pasting:

### To Search for Older Jobs
Change: `posted in the LAST 7 DAYS`
To: `posted in the LAST 14 DAYS` or `posted in the LAST 30 DAYS`

### To Focus on One Geography
Change the GEOGRAPHIES section to put your target location first, or remove others entirely.

### To Adjust Role Priority
Reorder the TARGET ROLES section based on what you want to see first.

### To Broaden Search
Add to the INCLUDE section:
- Healthcare technology
- Hospital administration
- Medical devices
- Health insurance

### To Narrow Search
Add to the EXCLUDE section:
- Remote-only positions
- Contract roles
- Freelance opportunities
- Companies with < 50 employees

---

## TROUBLESHOOTING

**Issue: Too few results (< 5 jobs)**
- Increase date range to 14 or 30 days
- Remove some geography filters
- Broaden role keywords
- Lower seniority requirements

**Issue: Too many irrelevant results**
- Add more terms to EXCLUDE section
- Increase experience requirements
- Narrow geography to top 2-3 cities
- Add company size filters

**Issue: Comet times out**
- Reduce number of search variations
- Focus on 1-2 geographies per search
- Run separate searches for each role type

**Issue: No salary/equity information**
- This is normal - most LinkedIn jobs don't disclose
- Comet will note when these ARE mentioned (rare but valuable)

---

## WEEKLY WORKFLOW

**Every Sunday Morning:**
1. Copy this prompt
2. Update "LAST 7 DAYS" to search fresh jobs
3. Run in Perplexity Comet
4. Export results to your tracking spreadsheet
5. Identify top 5-10 to apply to this week
6. Research companies and hiring managers
7. Customize applications

**Track Your Results:**
- How many jobs did Comet find?
- How many were high-match (75+ score)?
- Which geography had most opportunities?
- Which role type is most common?

Use this data to refine your search strategy over time.

---

## ADVANCED TIPS

### Find Hidden Opportunities
Add this to the search: "We're hiring" OR "Join our team" [company name]

### Identify Hiring Managers
After finding a job, ask Comet: "Who is the hiring manager for [Job Title] at [Company]? Find them on LinkedIn."

### Company Research
Ask Comet: "Research [Company Name] - funding, stage, competitors, recent news, and key leadership."

### Salary Benchmarking
Ask Comet: "What is the typical salary range for [Job Title] in [City] for someone with 12 years experience?"

### Competition Analysis
Ask Comet: "Find other candidates on LinkedIn with similar backgrounds applying to [Company Name] CMO roles."

---

## NEXT STEPS AFTER GETTING RESULTS

1. **Prioritize Applications**
   - Apply to all 90-100 score jobs immediately
   - Research 75-89 score jobs before applying
   - Bookmark 60-74 score jobs for later

2. **Customize Each Application**
   - Use company research from Comet
   - Tailor CV to highlight relevant experience
   - Write custom cover letter (or use Claude to generate)

3. **Network Strategy**
   - Find hiring managers on LinkedIn
   - Send personalized connection requests
   - Engage with company content before applying

4. **Track Everything**
   - Use the provided Excel tracker (tracking-template.xlsx)
   - Note application date, status, follow-ups
   - Track response rates by geography and role type

---

## FEEDBACK LOOP

After 2-3 weeks of using this prompt, evaluate:
- Which geography is giving best results?
- Which role type gets most callbacks?
- Are startups or consulting firms more responsive?
- Should you adjust match score priorities?

Update the prompt based on real-world results.

---

**Ready to start? Copy the master prompt above and paste it into Perplexity Comet now!**

You'll have 15-20 curated job opportunities in less than a minute.
