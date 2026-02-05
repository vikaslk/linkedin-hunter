# LinkedIn Hunter - Phase 2 MCP Agent Handoff

## Context Summary

**Date:** February 5, 2026
**Current Status:** Phase 1 COMPLETE ✅ - Dr. Vikas is using Comet prompt for immediate job hunting
**Next Phase:** Build MCP Agent with Proxycurl API integration

---

## What's Been Completed (Phase 1)

### ✅ Comet Prompt System (Ready to Use)
- **File:** `/linkedin-hunter/comet-job-prompt-v2.md`
- **Status:** Ready for immediate use
- **Features:**
  - 3-phase comprehensive search (48 combinations: 8 roles × 6 geographies)
  - Top 25 matches with 0-100 scoring
  - Past 10 days filter
  - Critical exclusions (investment-required, BDS/MDS, Big 4 only)
  - Direct LinkedIn URLs
  - Application strategy for each job

### ✅ Profile Documentation (Corrected & Updated)
- **File:** `/linkedin-hunter/profile-summary.md`
- **Key Correction:** GE HealthCare story updated
  - NEVER worked WITH Padmaja Sajja (she had left before he joined)
  - Inherited her foundation, drove execution
  - Lean 3-12 person team (down from 40)
  - Manager scope: 9 people (not 40)
  - "Do more with less" narrative for startups
- **Experience:** 14+ years (updated from 12+)

### ✅ Supporting Documents
- `target-companies.md` - 103 companies by geography
- `target-roles.md` - Role descriptions, keywords, salary expectations
- `geography-notes.md` - Market insights for 6 target geographies
- `tracking-template.csv` - Application tracking spreadsheet
- `conversation-log.md` - Session documentation
- `README.md` - Master guide

### ✅ Research & Architecture Decisions
- **LinkedIn API Research:** Complete (see `/phase-2-mcp-agent.md`)
- **Decision:** Proxycurl API (NOT Chrome extension)
- **Why:** Chrome extensions get banned by LinkedIn, Proxycurl is legal/compliant
- **Cost:** ~$10/month (pay-as-you-go)
- **Architecture:** Python MCP Server + Proxycurl API + SQLite Database

---

## Phase 2: MCP Agent Implementation Plan

### Objective
Build a Python MCP server that uses Proxycurl API to search LinkedIn jobs, score matches 0-100, and track applications locally.

### Architecture Overview

```
┌─────────────────────────────┐
│   Claude Desktop (UI)       │
└──────────┬──────────────────┘
           │
           ▼
┌─────────────────────────────┐
│  Python MCP Server          │
│  - Proxycurl API calls      │
│  - Profile matching (0-100) │
│  - SQLite tracking          │
└──────────┬──────────────────┘
           │
    ┌──────┴──────┐
    ▼             ▼
┌─────────┐  ┌─────────┐
│Proxycurl│  │ SQLite  │
│   API   │  │Database │
└─────────┘  └─────────┘
```

### Implementation Approach: 3 Steps

#### STEP 1: Proof of Concept (2-3 hours)
**Goal:** Validate Proxycurl API + basic MCP server works

**Build:**
1. Simple Python MCP server (`poc-server.py`)
2. Proxycurl API client wrapper
3. Single tool: `search_jobs_by_company(company_name, location)`
4. Test with 5-10 companies
5. Validate: Can we get jobs? Are they relevant? What's the cost?

**Success Criteria:**
- MCP server runs and Claude can call it
- Proxycurl returns job data
- Cost is <$1 for 50 company searches
- Data quality is good (job titles, descriptions, URLs)

#### STEP 2: Iterate Based on POC (1-2 hours)
**Goal:** Fix issues, refine approach

**Adjust:**
- API response format (if needed)
- Error handling
- Rate limiting strategy
- Cost optimization (caching?)

#### STEP 3: Full Agent Build (10-15 hours)
**Goal:** Production-ready MCP agent

**Complete:**
- All MCP tools (search, track, analyze, report)
- SQLite database with schema
- Profile matching algorithm (0-100 scoring)
- One-click installer (`install-agent.bat`)
- GUI configuration (`configure-preferences.html`)
- Setup documentation

---

## Critical Files & Specifications

### 1. Proxycurl API Integration

**Endpoint:** `https://nubela.co/proxycurl/api/v2/linkedin/company/job`

**Authentication:**
```python
headers = {"X-Api-Key": os.getenv("PROXYCURL_API_KEY")}
```

**Request:**
```python
params = {
    "url": "https://www.linkedin.com/company/okadoc",  # Company LinkedIn URL
    "search_id": "0"  # Start from beginning
}
```

**Response Format:**
```json
{
  "jobs": [
    {
      "job_title": "Chief Medical Officer",
      "company_name": "Okadoc",
      "location": "Dubai, UAE",
      "job_url": "https://www.linkedin.com/jobs/view/...",
      "description": "...",
      "posted_date": "2 days ago",
      "applicant_count": "50 applicants"
    }
  ]
}
```

**Rate Limit:** 300 requests/minute
**Cost:** ~$0.01-0.05 per company search

### 2. Profile Matching Algorithm (0-100 Scoring)

**Scoring System:**

```python
def calculate_match_score(job: dict) -> tuple[int, str]:
    score = 0

    # Role Alignment (40 points)
    if "cmo" in title or "chief medical" in title:
        if "equity" in description:
            score += 40  # Tier 1 with equity
        else:
            score += 35  # Tier 1 without equity
    elif "consultant" in title:
        score += 30  # Tier 2 consulting
    # ... more role scoring

    # Geography (30 points)
    if "dubai" in location or "abu dhabi" in location:
        score += 30  # UAE (priority #1)
    elif "bangalore" in location:
        score += 28  # Bangalore (priority #2)
    # ... more geography scoring

    # Equity Mention (20 points)
    if "equity" in description or "stock option" in description:
        score += 20
    elif "startup" in description:
        score += 10

    # Other Factors (10 points)
    if "clinical + business" in description:
        score += 5
    if "scale" in description or "build" in description:
        score += 3
    if posted within 3 days:
        score += 2

    return score, "reasoning..."
```

**Exclusion Filters (Auto-reject):**
```python
def should_exclude(job: dict) -> bool:
    desc = job["description"].lower()
    title = job["job_title"].lower()

    # Exclude if requires investment
    if "invest" in desc and ("co-founder" in title or "founder" in title):
        return True

    # Exclude if dentistry-specific
    if "bds" in desc or "mds" in desc or "dentist" in title:
        return True

    # Exclude if Big 4 alumni only (strict requirement)
    if "big 4 alumni required" in desc or "ex-mbb only" in desc:
        return True

    return False
```

### 3. Database Schema

**File:** `/linkedin-hunter/database/schema.sql`

```sql
CREATE TABLE jobs (
    id INTEGER PRIMARY KEY,
    job_url TEXT UNIQUE,
    title TEXT,
    company TEXT,
    location TEXT,
    description TEXT,
    posted_date TEXT,
    discovered_date DATETIME DEFAULT CURRENT_TIMESTAMP,
    match_score INTEGER,
    equity_mentioned BOOLEAN,
    salary_range TEXT,
    source TEXT DEFAULT 'proxycurl'
);

CREATE TABLE applications (
    id INTEGER PRIMARY KEY,
    job_id INTEGER,
    applied_date DATETIME DEFAULT CURRENT_TIMESTAMP,
    status TEXT DEFAULT 'applied',
    notes TEXT,
    follow_up_date DATE,
    FOREIGN KEY (job_id) REFERENCES jobs(id)
);

CREATE INDEX idx_match_score ON jobs(match_score DESC);
```

### 4. MCP Tools to Implement

```python
# MUST HAVE (POC)
@mcp.tool()
async def search_jobs_by_company(company_name: str, location: str = "Dubai") -> dict:
    """Search LinkedIn jobs at specific company via Proxycurl"""

# SHOULD HAVE (Full Agent)
@mcp.tool()
async def track_application(job_url: str, company: str, title: str, status: str = "applied") -> dict:
    """Log application to SQLite database"""

@mcp.tool()
async def get_daily_report(date: str = "today") -> dict:
    """Generate daily summary of new job matches"""

@mcp.tool()
async def analyze_job_fit(job_description: str, criteria: dict) -> dict:
    """Score job 0-100 based on Dr. Vikas's profile"""

# NICE TO HAVE (Phase 3)
@mcp.tool()
async def find_hiring_manager(company_name: str, role: str) -> dict:
    """Find hiring manager on LinkedIn (if Proxycurl supports)"""
```

---

## Dr. Vikas's Profile (For Matching Logic)

**Key Facts:**
- **Experience:** 14+ years in healthcare
- **Education:** MBBS (medical, NOT dentist) + MBA (HR/Marketing)
- **Achievement:** Scaled GE HealthCare Education revenue $80K → $250K with lean 3-12 person team (after founder left)
- **Expertise:** Clinical operations, healthcare strategy, digital health, P&L management
- **Hospital Leadership:** Managed 1800-bed hospital (Sriramachandra)
- **Consulting:** Independent strategic consulting (Innov4Sight, GE deal-making), NOT formal Big 4/MBB

**Target Roles (Priority):**
1. Startups with equity + salary (CMO, VP Clinical Ops, Medical Director)
2. Healthcare consulting (MBB, Big 4, specialized) - open to non-traditional backgrounds
3. Digital health leadership (VP Clinical Strategy, Head of Medical Affairs)
4. Hospital leadership (CMO, Medical Director)

**Target Geographies (Priority):**
1. UAE (Dubai, Abu Dhabi, Sharjah)
2. India (Bangalore, Chennai ONLY - exclude Delhi/Mumbai)
3. Oman, Singapore, Malaysia, Indonesia

**Critical Exclusions:**
- ❌ Requires personal investment
- ❌ Sweat equity only (no salary)
- ❌ BDS/MDS dentistry roles
- ❌ "Big 4 alumni required" or "Ex-MBB only" (strict requirement)
- ❌ Pure clinical roles (no strategy)

---

## POC Implementation Guide

### Step 1: Setup (15 minutes)

**Create POC folder structure:**
```
/linkedin-hunter/poc/
  ├── server.py (MCP server)
  ├── proxycurl_client.py (API wrapper)
  ├── requirements.txt
  ├── .env.template
  └── test_companies.txt (list of 10 companies to test)
```

**Install dependencies:**
```bash
pip install fastmcp httpx python-dotenv
```

**Get Proxycurl API key:**
1. Visit https://nubela.co/proxycurl
2. Sign up for free trial OR buy $1.99 for 100 credits
3. Copy API key

### Step 2: Build POC Server (1 hour)

**File: `poc/server.py`**
```python
from fastmcp import FastMCP
from proxycurl_client import ProxycurlClient
import os

mcp = FastMCP("LinkedIn Hunter POC")
client = ProxycurlClient(os.getenv("PROXYCURL_API_KEY"))

@mcp.tool()
async def search_jobs(company_name: str, location: str = "Dubai") -> dict:
    """Search LinkedIn jobs at a company (POC)"""

    # For POC: Use hardcoded company LinkedIn URL
    # In full version: would lookup company URL first
    company_urls = {
        "okadoc": "https://www.linkedin.com/company/okadoc",
        "vezeeta": "https://www.linkedin.com/company/vezeeta",
        "altibbi": "https://www.linkedin.com/company/altibbi",
        # ... more companies
    }

    company_url = company_urls.get(company_name.lower())
    if not company_url:
        return {"error": f"Company {company_name} not in POC list"}

    try:
        jobs = await client.search_company_jobs(company_url)

        # Simple filtering for POC
        filtered_jobs = []
        for job in jobs.get("jobs", []):
            # Basic match score (simplified for POC)
            score = calculate_simple_score(job)
            if score >= 60:  # Only return decent matches
                filtered_jobs.append({
                    "title": job["job_title"],
                    "company": job["company_name"],
                    "location": job["location"],
                    "score": score,
                    "url": job["job_url"],
                    "posted": job.get("posted_date", "Unknown")
                })

        return {
            "company": company_name,
            "total_jobs": len(jobs.get("jobs", [])),
            "matched_jobs": filtered_jobs,
            "api_cost_estimate": "$0.02"
        }

    except Exception as e:
        return {"error": str(e)}

def calculate_simple_score(job: dict) -> int:
    """Simplified scoring for POC"""
    score = 50  # Base score
    title = job["job_title"].lower()

    # Role boost
    if "cmo" in title or "chief medical" in title:
        score += 30
    elif "director" in title or "vp" in title:
        score += 20

    # Location boost
    location = job["location"].lower()
    if "dubai" in location or "abu dhabi" in location:
        score += 20

    return min(score, 100)

if __name__ == "__main__":
    mcp.run()
```

**File: `poc/proxycurl_client.py`**
```python
import httpx
from typing import Dict

class ProxycurlClient:
    BASE_URL = "https://nubela.co/proxycurl/api/v2"

    def __init__(self, api_key: str):
        self.api_key = api_key
        self.client = httpx.AsyncClient(
            headers={"X-Api-Key": api_key},
            timeout=30.0
        )

    async def search_company_jobs(self, company_url: str) -> Dict:
        """Get jobs posted by a LinkedIn company"""
        endpoint = f"{self.BASE_URL}/linkedin/company/job"
        params = {
            "url": company_url,
            "search_id": "0"
        }

        response = await self.client.get(endpoint, params=params)
        response.raise_for_status()
        return response.json()

    async def close(self):
        await self.client.aclose()
```

**File: `poc/requirements.txt`**
```
fastmcp>=0.2.0
httpx>=0.27.0
python-dotenv>=1.0.0
```

**File: `poc/.env.template`**
```
PROXYCURL_API_KEY=your_api_key_here
```

**File: `poc/test_companies.txt`**
```
okadoc (Dubai)
vezeeta (Dubai)
altibbi (Dubai)
practo (Bangalore)
mfine (Bangalore)
medibuddy (Bangalore)
doctor-anywhere (Singapore)
mydoc (Singapore)
halodoc (Jakarta)
alodokter (Jakarta)
```

### Step 3: Test POC (30 minutes)

**Run server:**
```bash
cd /linkedin-hunter/poc
python server.py
```

**Configure Claude Desktop:**
Add to `claude_desktop_config.json`:
```json
{
  "mcpServers": {
    "linkedin-hunter-poc": {
      "command": "python",
      "args": ["D:/LinkedIn-Hunter/linkedin-hunter/poc/server.py"]
    }
  }
}
```

**Test in Claude Desktop:**
```
User: "Search for CMO jobs at Okadoc in Dubai"
Claude: [Calls search_jobs tool]
        [Returns top matches with scores]
```

**Validate:**
- Does Proxycurl return real job data?
- Are job titles, descriptions, URLs present?
- Is scoring reasonable (60-100 for good matches)?
- How much did 10 company searches cost? (~$0.20?)
- Any rate limiting issues?

### Step 4: Iterate (1-2 hours)

Based on POC results, fix:
- API response parsing (if format differs)
- Error handling (rate limits, invalid companies)
- Scoring logic (too many/few matches?)
- Cost optimization (caching? batch requests?)

---

## Full Agent Build (After POC Validation)

Once POC works and Dr. Vikas approves the approach:

### Phase 2B: Complete Implementation (10-15 hours)

**Expand POC to full agent:**

1. **Add all MCP tools** (track application, get report, analyze fit)
2. **Implement SQLite database** (jobs table, applications table, indices)
3. **Enhance matching algorithm** (full 0-100 scoring with reasoning)
4. **Add company lookup** (map company name → LinkedIn URL automatically)
5. **Create installer** (`install-agent.bat` - one-click setup)
6. **Build GUI config** (`configure-preferences.html` - simple form)
7. **Write documentation** (setup guide with screenshots, troubleshooting)
8. **Add error handling** (rate limits, network issues, bad API responses)
9. **Implement caching** (avoid re-searching same companies)
10. **Create daily/weekly reports** (HTML output, analytics)

**Estimated Development Time:**
- POC: 2-3 hours
- Iteration: 1-2 hours
- Full Agent: 10-15 hours
- **Total: 13-20 hours**

---

## Success Criteria

### POC Success:
- ✅ MCP server runs, Claude can call tools
- ✅ Proxycurl returns job data (5-10 companies tested)
- ✅ Data quality good (titles, descriptions, URLs present)
- ✅ Cost reasonable (<$1 for 50 searches)
- ✅ Scoring makes sense (high scores for relevant jobs)
- ✅ No major technical blockers

### Full Agent Success:
- ✅ One-click installation (non-technical user)
- ✅ Finds 50+ relevant jobs per week
- ✅ Match scores accurate (validated manually on 20 jobs)
- ✅ Zero false positives (no BDS/MDS, no investment-required)
- ✅ Application tracking works (SQLite database)
- ✅ Daily reports generate correctly
- ✅ Cost < $15/month
- ✅ Zero LinkedIn account issues (Proxycurl doesn't touch account)

---

## Files Reference

**Already Created (Phase 1):**
- `/linkedin-hunter/comet-job-prompt-v2.md` - Use NOW for job hunting
- `/linkedin-hunter/profile-summary.md` - Corrected profile
- `/linkedin-hunter/target-companies.md` - 103 companies
- `/linkedin-hunter/target-roles.md` - Role strategies
- `/linkedin-hunter/geography-notes.md` - Market insights
- `/linkedin-hunter/README.md` - Master guide
- `/linkedin-hunter/PROFILE-CORRECTION-FEB-5-2026.md` - GE story correction
- `C:\Users\vikas\.claude\plans\phase-2-mcp-agent.md` - Detailed Phase 2 plan

**To Create (Phase 2 POC):**
- `/linkedin-hunter/poc/server.py`
- `/linkedin-hunter/poc/proxycurl_client.py`
- `/linkedin-hunter/poc/requirements.txt`
- `/linkedin-hunter/poc/.env.template`
- `/linkedin-hunter/poc/test_companies.txt`

**To Create (Phase 2 Full):**
- `/linkedin-hunter/mcp-server/server.py`
- `/linkedin-hunter/mcp-server/proxycurl_client.py`
- `/linkedin-hunter/mcp-server/tools/profile_matcher.py`
- `/linkedin-hunter/database/schema.sql`
- `/linkedin-hunter/database/init_db.py`
- `/linkedin-hunter/config/config.json`
- `/linkedin-hunter/install-agent.bat`
- `/linkedin-hunter/configure-preferences.html`
- `/linkedin-hunter/SETUP-GUIDE.md`

---

## Key Decisions & Rationale

### Why Proxycurl (NOT Chrome Extension)?
- **Legal:** Proxycurl is compliant, Chrome extensions violate LinkedIn ToS
- **Safety:** Zero account ban risk vs. HIGH risk with extensions
- **Cost:** $10/month vs. free but account suspension
- **Maintenance:** API is stable vs. extensions break frequently

### Why Python MCP Server (NOT Composio)?
- **Job Search:** Composio lacks LinkedIn job search capability
- **Control:** Full control over API calls, caching, error handling
- **Cost:** Pay-as-you-go vs. $30/month subscription
- **Flexibility:** Can add Apify as backup provider easily

### Why SQLite (NOT Cloud Database)?
- **Privacy:** All data local, nothing leaves Dr. Vikas's computer
- **Cost:** Free vs. cloud database fees
- **Simplicity:** No server management, just a file
- **Backup:** Easy to backup (copy one file)

---

## Questions for Dr. Vikas (Before POC)

1. **Proxycurl Budget:** Is $10-20/month acceptable for API usage?

2. **POC Timeline:** When do you want to test POC? (Suggest: within next 2-3 days)

3. **Company List:** Should I pre-load 100 target companies or let you add them as needed?

4. **Manual Application OK:** Confirm you're okay with agent FINDING jobs but YOU applying manually? (Safest approach)

5. **Backup Provider:** If Proxycurl doesn't meet needs, should I have Apify POC ready as backup?

---

## Next Steps in New Context

1. **Start with POC:**
   ```
   User: "Let's build the Proxycurl POC first"
   Claude: [Creates poc/ folder, builds server.py, proxycurl_client.py]
   ```

2. **Test POC:**
   ```
   User: "Test with Okadoc, Vezeeta, Practo"
   Claude: [Runs searches, validates results, reports costs]
   ```

3. **Iterate:**
   ```
   User: "Scoring is too loose, tighten filters"
   Claude: [Adjusts algorithm, retests]
   ```

4. **Full Agent:**
   ```
   User: "POC looks good, build full agent"
   Claude: [Expands to complete implementation over 10-15 hours]
   ```

---

## Important Notes

### About GE HealthCare Story (CRITICAL)
- **NEVER say:** "worked with Padmaja Sajja"
- **ALWAYS say:** "joined after Padmaja Sajja left, inherited her foundation"
- **Team size:** 3-12 people (not 40)
- **Manager scope:** 9 people (not 40)
- **Narrative:** "Do more with less" - 3X revenue with 1/4 team size
- **See:** `/linkedin-hunter/PROFILE-CORRECTION-FEB-5-2026.md` for details

### About Consulting Background
- Independent strategic consulting (Innov4Sight, GE deal-making)
- NOT formal Big 4/MBB consultant
- Can apply to consulting firms (don't self-reject)
- Frame as: "client-side strategic problem-solving"

### About Exclusions
Must filter out:
- Investment-required roles
- Sweat equity only
- BDS/MDS dentistry
- "Big 4 alumni required" (strict)
- Pure clinical roles

---

**Last Updated:** February 5, 2026, 5:00 AM IST
**Status:** Ready for Phase 2 POC
**Contact:** Dr. Vikas L Krishna | vikaslk@hotmail.com | +91 96864 55450
