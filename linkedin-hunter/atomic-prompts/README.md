# UAE Atomic Prompts - Runner's Guide

## What Are These?

12 focused, copy-paste-ready Perplexity Comet prompts for UAE job searching. Each targets a specific role type + geography combination, so Comet can search deeply instead of trying to cover everything at once.

**vs. the Mega Prompt:** The mega prompt (`comet-job-prompt-v2.md`) runs 48 search combinations across 6 geographies in one session. These atomic prompts each focus on ONE slice, yielding better results per search.

---

## The 12 Prompts

| # | File | Focus | Priority | Frequency |
|---|------|-------|----------|-----------|
| 1 | `uae-01-startup-cmo-dubai.md` | CMO / VP at Dubai startups | HIGH | Weekly |
| 2 | `uae-02-startup-cmo-abudhabi.md` | CMO / VP at Abu Dhabi startups | Medium | Bi-weekly |
| 3 | `uae-03-startup-meddir-dubai.md` | Medical Director at Dubai startups | HIGH | Weekly |
| 4 | `uae-04-startup-meddir-abudhabi.md` | Medical Director in Abu Dhabi | Low | Monthly |
| 5 | `uae-05-consulting-mbb-dubai.md` | MBB consulting Dubai | HIGH | Weekly |
| 6 | `uae-06-consulting-big4-dubai.md` | Big 4 + specialized consulting Dubai | Medium | Bi-weekly |
| 7 | `uae-07-consulting-abudhabi.md` | All consulting Abu Dhabi | Low | Monthly |
| 8 | `uae-08-digital-health-dubai.md` | Digital health VP roles Dubai | Medium | Bi-weekly |
| 9 | `uae-09-digital-health-abudhabi.md` | Digital health leadership Abu Dhabi | Low | Monthly |
| 10 | `uae-10-hospital-leadership.md` | Hospital chain CMO/Director all UAE | Medium | Bi-weekly |
| 11 | `uae-11-medtech.md` | MedTech medical affairs all UAE | Low | Monthly |
| 12 | `uae-12-named-startups.md` | Any role at 10 named startups | HIGH | Weekly |

---

## How to Run Each Prompt

1. Open the `.md` file
2. Select and copy everything inside the code fence (between the ``` marks)
3. Go to [perplexity.ai](https://perplexity.ai), select **Comet** mode
4. Paste the full prompt and press Enter
5. Wait 30-60 seconds
6. Review the Top 8 results
7. Apply immediately to any 90+ score matches
8. Copy the CSV summary row at the bottom to your master tracking spreadsheet

---

## Weekly Cadence

### Sunday Morning (30 min) - Run the 4 highest priority prompts:
1. `uae-01` - Startup CMO/VP Dubai
2. `uae-12` - Named startups (all UAE)
3. `uae-05` - MBB consulting Dubai
4. `uae-03` - Startup Medical Director Dubai

### Wednesday Evening (15 min) - Run 2 medium priority prompts:
5. `uae-08` - Digital health Dubai
6. `uae-06` - Big 4 consulting Dubai

### First of the Month (45 min) - Comprehensive run of all 12:
Run all prompts for full UAE coverage. This catches opportunities in Abu Dhabi, hospital chains, MedTech, and lower-priority segments.

---

## Consolidating Results

After running multiple prompts:

1. **Collect:** Copy the CSV summary row from each prompt's output
2. **Paste:** Add all rows to a single tracking spreadsheet
3. **Sort:** Sort by Score descending
4. **Deduplicate:** Same company + role appearing in multiple results? Keep the entry with the highest score
5. **Act:** Apply to 90+ immediately, research 75-89, bookmark 60-74

---

## Expected Results

| Per Prompt | Per Weekly Run (4 prompts) | Per Monthly Run (12 prompts) |
|-----------|---------------------------|------------------------------|
| 3-8 matches | 12-32 matches | 36-96 matches |
| ~2 at 90+ | ~5-8 at 90+ | ~10-20 at 90+ |

After deduplication, expect **20-50 unique opportunities per monthly run**.

---

## Updating Your Profile

When profile details change:

1. **First:** Update `_profile-block.md` (the source of truth)
2. **Then:** In each of the 12 prompt files, find the `CANDIDATE PROFILE` section and replace it with the updated block from `_profile-block.md`
3. **Also update:** Any role-specific context sections (e.g., HOSPITAL OPERATIONS CONTEXT in prompt 10, MEDTECH CONTEXT in prompt 11)

---

## Adding New Companies

To add a new UAE startup to track:
1. Add it to `uae-12-named-startups.md` in the SEARCH THESE SPECIFIC COMPANIES list
2. If it fits a specific category, also add it to COMPANIES TO WATCH in the relevant prompt (e.g., a new telehealth startup goes in prompts 1, 3, and 8)

---

## Troubleshooting

**Comet returns 0 results for a prompt:**
- Broaden date range from "past 10 days" to "past 14 days" or "past 21 days"
- Abu Dhabi prompts (2, 4, 7, 9) are naturally thinner markets - this is expected

**Too many irrelevant results:**
- Check if exclusions are being respected
- If not, add the specific exclusion to the prompt's CRITICAL EXCLUSIONS section

**Same job appearing in multiple prompts:**
- This is expected (e.g., a CMO role at Altibbi could appear in prompts 1, 8, and 12)
- Deduplicate when consolidating into your spreadsheet

**Prompt too long for Comet:**
- Each prompt is ~80-100 lines, well within Comet's limits
- If Comet truncates, try splitting the search strings across two runs

---

## File Reference

| File | Purpose |
|------|---------|
| `_profile-block.md` | Source of truth for candidate profile + exclusions |
| `uae-01` through `uae-12` | The 12 atomic prompts (copy-paste ready) |
| `README.md` | This guide |

**Related files (parent directory):**
| File | Purpose |
|------|---------|
| `comet-job-prompt-v2.md` | Original mega prompt (all geographies) |
| `comet-job-prompt-v2-mod.md` | Modified mega prompt (most accurate profile) |
| `target-companies.md` | Full list of 103 target companies |
| `target-roles.md` | 15 role types with keywords |
| `geography-notes.md` | Market insights per geography |

---

*Created: Feb 9, 2026*
*Prompts: 12 (UAE-focused)*
*Next: India atomic prompts (when ready)*
