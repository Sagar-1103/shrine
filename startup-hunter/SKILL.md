---
name: startup-hunter
description: >-
  Use this skill when the user wants to find startups that match their resume/profile,
  discover founder/co-founder/HR contact details, check funding stages, and build a
  comprehensive outreach list. Triggered by requests like "find startups for me",
  "hunt startup jobs", "find companies matching my profile", or "startup outreach list".
  This skill browses LinkedIn, YC, Wellfound, CareerLift, Jack&Jill, BetaList and other
  sources to discover relevant startups — including those without public job postings.
---

# Startup Hunter Skill

Systematically discover startups that match the candidate's resume, gather intelligence
on each company, identify key people (founders, co-founders, HRs), and produce a
comprehensive outreach-ready report.

---

## Phase 0 — Resume Ingestion

1. Locate the candidate's resume. Check the workspace for files named `*resume*`,
   `*cv*`, or ask the user to provide the path.
2. Read the resume (PDF or text). Extract:
   - **Skills & Technologies** (languages, frameworks, tools, domains)
   - **Experience Level** (years, seniority)
   - **Roles Held / Target Roles** (e.g. Full-Stack Engineer, ML Engineer, PM)
   - **Industry Domains** (fintech, healthtech, edtech, SaaS, AI/ML, etc.)
   - **Location Preferences** (remote, city, country)
   - **Education & Certifications**
3. Summarize the candidate profile in a structured block so all subsequent agents
   can reference it.

---

## Phase 1 — Startup Discovery (Multi-Source)

Search **all** of the following sources. For each source, use the browser subagent
to navigate and extract results. Build search queries from the candidate's skills,
target roles, and domain interests.

### Sources to Search

#### Tier 1 — Primary Discovery (always search these)

| # | Source | URL | What to Look For |
|---|--------|-----|-------------------|
| 1 | **LinkedIn** | linkedin.com | Companies, startup pages, "recently funded" posts, job posts matching skills |
| 2 | **Y Combinator** | ycombinator.com/companies | YC-backed startups filtered by batch, industry, stage |
| 3 | **Work at a Startup (YC)** | workatastartup.com | YC company job board — roles across all YC startups in one place |
| 4 | **Wellfound (AngelList)** | wellfound.com | Startup profiles, open roles, company stage/funding |
| 5 | **Crunchbase** | crunchbase.com | Funding rounds, investors, team size, HQ location |
| 6 | **Google Search** | google.com | `"[skill] startup hiring [year]"`, `"[domain] seed round [year]"` |

#### Tier 2 — Specialized Platforms (search all of these)

| # | Source | URL | What to Look For |
|---|--------|-----|-------------------|
| 7 | **CareerLift** | careerlift.in | Indian startup job board — roles, company profiles |
| 8 | **Jack & Jill** | app.jackandjill.ai | AI-powered job matching platform |
| 9 | **BetaList** | betalist.com | Early-stage startups launching soon — pre-seed/seed |
| 10 | **Product Hunt** | producthunt.com | Recently launched products — founding teams, traction |
| 11 | **Indie Hackers** | indiehackers.com | Bootstrapped/profitable startups, founders sharing revenue & hiring |
| 12 | **F6S** | f6s.com | Startup profiles, accelerator programs, founder deals, jobs |
| 13 | **The Org** | theorg.com | Org charts for startups — excellent for finding exact people & roles |
| 14 | **Tracxn** | tracxn.com | Indian & global startup data, funding, sectors, company profiles |
| 15 | **BuiltIn** | builtin.com | Startup jobs by city (NYC, SF, LA, Chicago, etc.), company profiles |
| 16 | **Glassdoor** | glassdoor.com | Company reviews, salaries, job listings, inside look at culture |

#### Tier 3 — Funding & News Intelligence (use to verify and enrich)

| # | Source | URL | What to Look For |
|---|--------|-----|-------------------|
| 17 | **Dealroom** | dealroom.co | European & global startup data, funding, growth signals |
| 18 | **PitchBook** | pitchbook.com | VC deals, funding rounds, investor details (may be paywalled) |
| 19 | **CB Insights** | cbinsights.com | Market maps, top startup lists, funding data |
| 20 | **Fundz** | fundz.net | Real-time funding alerts — recently funded startups |
| 21 | **TechCrunch** | techcrunch.com | Startup funding announcements, launches, news |
| 22 | **YourStory** | yourstory.com | Indian startup ecosystem news, funding, founder stories |
| 23 | **Inc42** | inc42.com | Indian startup news, funding tracker, sector reports |
| 24 | **EU-Startups** | eu-startups.com | European startup news, funding, top lists by sector |
| 25 | **Tech in Asia** | techinasia.com | Southeast Asian startup news and company database |

#### Tier 4 — Niche & Remote-First Sources (search when relevant)

| # | Source | URL | What to Look For |
|---|--------|-----|-------------------|
| 26 | **Hacker News — Who is Hiring** | news.ycombinator.com | Monthly "Who is Hiring?" threads — search `Ask HN: Who is hiring?` |
| 27 | **RemoteOK** | remoteok.com | Remote-first startup jobs, salary data, company profiles |
| 28 | **We Work Remotely** | weworkremotely.com | Remote jobs — many early-stage startup postings |
| 29 | **Himalayas** | himalayas.app | Remote startup jobs with company profiles and tech stack info |
| 30 | **Twitter/X** | x.com | Founders announcing hiring, funding rounds |
| 31 | **TopStartups.io** | topstartups.io | Curated lists of top startups by category, funding, batch |
| 32 | **Startup India** | startupindia.gov.in | Government portal — DPIIT-recognized Indian startups |
| 33 | **GrowthList** | growthlist.co | Database of funded startups with contact info |
| 34 | **Instahyre** | instahyre.com | Indian tech hiring platform — startup roles, company profiles |
| 35 | **Cutshort** | cutshort.io | Indian startup jobs — ML-matched roles, company insights |
| 36 | **Hashjob** | hashjob.co | Tech job board with Indian startup focus |
| 37 | **Seedtable** | seedtable.com | European startup database — funding, sector, team data |
| 38 | **Acquire.com** | acquire.com | Startups for sale — reveals what's being built, tech stacks |
| 39 | **GitHub Trending** | github.com/trending | Active open-source projects by startups — signals hiring needs |
| 40 | **StackShare** | stackshare.io | What tech stacks companies use — match to candidate's skills |

### Discovery Strategy

- **Don't require active job postings.** Many startups hire through referrals and
  cold outreach even without listed roles. If a startup's product, tech stack, or
  domain matches the candidate, include it.
- **Check funding status.** Prioritize startups that recently raised (seed, Series A,
  Series B) — they are more likely to be expanding their team.
- **Verify legitimacy.** Confirm the startup has:
  - A real website with a product or landing page
  - Identifiable founders with LinkedIn profiles
  - Some public footprint (press mentions, Product Hunt launch, YC profile, etc.)
  - Skip companies that look like shell entities, affiliate schemes, or scams.

---

## Phase 2 — Company Deep Dive

For each discovered startup, gather:

| Field | Details |
|-------|---------|
| **Company Name** | Official name |
| **One-Liner** | What they build (1 sentence) |
| **Website** | URL |
| **Industry / Domain** | e.g. AI/ML, Fintech, SaaS, Healthtech |
| **Founded** | Year |
| **Location / HQ** | City, Country (or "Remote") |
| **Team Size** | Approximate headcount |
| **Funding Stage** | Pre-seed / Seed / Series A / Series B / Bootstrapped |
| **Total Raised** | Amount if publicly known |
| **Last Funding Date** | When the last round closed |
| **Key Investors** | Notable investors or accelerators |
| **Tech Stack** | Known technologies (from job posts, GitHub, StackShare) |
| **Why It Matches** | Why this startup fits the candidate's profile |
| **Careers Page** | Direct link |
| **LinkedIn Page** | Direct link |
| **Crunchbase / Wellfound** | Direct link |
| **Active Job Listings** | Links if any exist; otherwise "No public listings — cold outreach recommended" |

---

## Phase 3 — People Discovery (Founders / Co-Founders / HRs)

For each startup, identify and collect details for key contacts:

### Who to Find
- **Founders / Co-Founders** — the people who started the company
- **CTO / VP Engineering** — for engineering roles
- **Head of HR / People Ops / Talent** — the hiring decision-makers
- **Hiring Managers** — anyone with "hiring" or relevant department lead titles

### What to Collect Per Person

| Field | Details |
|-------|---------|
| **Full Name** | First and Last |
| **Title / Role** | e.g. "Co-Founder & CEO", "Head of Talent" |
| **Company** | The startup they're at |
| **LinkedIn Profile** | Direct URL |
| **Twitter/X** | If available |
| **Email** | If publicly listed (on company site, LinkedIn, etc.) — never guess emails |
| **Notes** | e.g. "Previously at Google", "Active on Twitter, engages with DMs" |

### How to Find Them
1. **LinkedIn Company Page → People tab** — filter by "Founder", "Co-Founder",
   "CEO", "CTO", "HR", "People", "Talent"
2. **The Org** (theorg.com) — full org charts with LinkedIn links; best source for
   mapping exact roles and reporting structure
3. **Company About/Team page** — many startups list their team with photos & bios
4. **Crunchbase People tab** — founders and key executives listed
5. **YC Company Page** — founders listed with LinkedIn links
6. **Wellfound Company Page** — team members and founders listed
7. **F6S Startup Profile** — founders and team listed
8. **Twitter/X bios** — founders often mention their company and role
9. **GitHub Org Members** — engineering team members visible on org page
10. **Tracxn Company Page** — founders and key management listed
11. **Google Search**: `"{company name}" founder OR co-founder OR CTO linkedin`

---

## Phase 4 — Output Generation

Generate a comprehensive artifact report with the following sections:

### Report Structure

```
# 🚀 Startup Outreach List for [Candidate Name]

> Generated on [date]. Based on resume analysis of [resume file].

## 📋 Candidate Profile Summary
[Extracted profile from Phase 0]

## 📊 Discovery Summary
- Total startups found: X
- With active job listings: Y
- Cold outreach targets (no listings): Z
- Funding breakdown: N pre-seed, N seed, N Series A, ...

## 🏢 Startup Details

### 1. [Company Name]
[Full company details table from Phase 2]

#### Key Contacts
[People details table from Phase 3]

---
(Repeat for each startup)

## 📇 Quick Reference — All Contacts
[Flat table of ALL people across all startups for easy copy-paste outreach]

## 🔗 All Links
[Consolidated list of all career pages, LinkedIn profiles, etc.]
```

### Output Formats

Generate **two** output files:

#### 1. Markdown Report (human-readable)
- Create as a **markdown artifact** so the user can view it inline in chat.
- Also save a copy to `findings/startup-outreach-report.md` in the workspace.

#### 2. JSON Data File (machine-readable)
- Save to `findings/startup-outreach-data.json` in the workspace.
- Structure:

```json
{
  "generated_at": "2026-11-17T22:50:00+05:30",
  "resume_file": "resume/sagar-resume.pdf",
  "candidate_profile": {
    "name": "...",
    "target_roles": ["..."],
    "skills": ["..."],
    "experience_years": 0,
    "domains": ["..."],
    "location_preference": "...",
    "education": "..."
  },
  "summary": {
    "total_startups": 0,
    "with_active_listings": 0,
    "cold_outreach_targets": 0,
    "funding_breakdown": {
      "pre_seed": 0, "seed": 0, "series_a": 0,
      "series_b_plus": 0, "bootstrapped": 0
    }
  },
  "startups": [
    {
      "company_name": "...",
      "one_liner": "...",
      "website": "...",
      "industry": "...",
      "founded": 2024,
      "location": "...",
      "team_size": 0,
      "funding_stage": "Seed",
      "total_raised": "$2M",
      "last_funded": "2026-06",
      "key_investors": ["..."],
      "tech_stack": ["..."],
      "match_reason": "...",
      "careers_page": "...",
      "linkedin_url": "...",
      "crunchbase_url": "...",
      "wellfound_url": "...",
      "active_job_listings": ["..."],
      "has_public_listings": false,
      "status": "pending",
      "contacts": [
        {
          "name": "...",
          "title": "Co-Founder & CEO",
          "linkedin": "...",
          "twitter": "...",
          "email": "...",
          "notes": "...",
          "status": "pending"
        }
      ]
    }
  ]
}
```

#### Status Field Rules
- Every startup and every contact **must** have a `"status"` field.
- Only two values: `"pending"` (not yet reached out) or `"done"` (outreach completed).
- When generating the report for the first time, set **all** statuses to `"pending"`.
- An outreach agent or cold-mail platform can later read the JSON, process only
  `"pending"` entries, and flip them to `"done"` after sending.

The JSON file enables the user to:
- Import into Notion, Airtable, Google Sheets, or any CRM
- Filter `"pending"` entries for outreach, skip `"done"` entries
- Feed into cold-mail automation — agent reads JSON, emails pending contacts, marks done
- Avoid duplicate outreach across multiple runs

---

## Execution Notes

- **Use the browser subagent** for all web browsing (LinkedIn, YC, Wellfound, etc.).
  Delegate browsing tasks clearly with specific URLs and extraction instructions.
- **Use search_web** for quick factual lookups (funding data, company info).
- **Fan out work** using multiple browser subagents or a workflow when searching
  multiple sources in parallel.
- **Rate limit awareness**: Space out LinkedIn browsing to avoid rate limits.
  If blocked, note it and move to the next source.
- **Be transparent**: If a source blocks access or requires login the user hasn't
  provided, report it and continue with other sources.
- **Quality over quantity**: 15-25 high-quality, well-researched matches are better
  than 50 shallow ones.
- **Prioritize recency**: Favor startups with recent activity (funding, hiring,
  product launches) in the last 6-12 months.
