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
on each company, identify high-leverage decision-makers (founders, co-founders, engineering
directors, talent leads) who can directly facilitate hiring, and produce a comprehensive,
verified outreach report.

---

## ⚠️ ZERO-HALLUCINATION & VERIFICATION DIRECTIVE

This skill enforces a strict **"Verified or Omitted"** standard across all data collection:

1. **Every Data Point Must Be Actively Verified**:
   - Every link, email, person, title, funding amount, and company metric must be verified using the available web browsing, surfing, and search tools in your environment.
   - Do NOT rely on assumptions, guesses, extrapolations, or unverified memory.
2. **Strict Omission Rule**:
   - If a piece of data cannot be 100% verified, **OMIT IT** or set it to `null`.
   - Having fewer, completely accurate entries is infinitely better than having entries with hallucinated, dead, or inaccurate details.
3. **Emails — Absolute Prohibition on Pattern Guessing**:
   - Only record an email address if it is explicitly published in plain text on an authoritative, verified public page (e.g., official website contact/about page, official press release, verified founder profile bio).
   - **NEVER** guess or synthesize email patterns (such as `first@company.com`, `first.last@...`, `contact@...`).
   - If an email is not explicitly found, set `"email": null` in JSON and leave blank (`—`) in reports.
4. **Links — Must Be Live and Working**:
   - Every URL (company website, careers page, LinkedIn profile, job listing) must be navigated to and verified as active and valid.
   - Do NOT guess standard URLs (e.g., assuming `company.com/careers` exists). If a company does not have a dedicated careers page, record `"None — cold outreach recommended"` and set `"careers_page": null`.
5. **People — High-Value Decision-Makers Only**:
   - Only include verified, currently active people who have the direct power or referral influence to hire the candidate or interview them via DM.
   - Do NOT add anyone who cannot help (e.g. unrelated departments, junior staff, inactive profiles, or passive advisors).
6. **Blocked Sources — Never Fabricate**:
   - If a source requires login that is not available, blocks automated access, or returns CAPTCHA/anti-bot challenges: **STOP immediately for that source**.
   - Log it as `"Source blocked — not searched"` in the report's Limitations section.
   - Do NOT fabricate or recall data from memory as a substitute. Move to the next accessible source.

---

## 🚫 WHAT NOT TO DO — Quick Reference

```
❌ NEVER guess emails (first@company.com, first.last@company.com, etc.)
❌ NEVER construct LinkedIn URLs from name patterns (/in/firstname-lastname)
❌ NEVER assume /careers or /jobs exists — visit the page or set null
❌ NEVER include former employees — verify CURRENT employment
❌ NEVER fill roles that don't exist at the company (don't invent an HR person)
❌ NEVER infer tech stack from company name or industry
❌ NEVER fabricate data when a source is blocked — log and move on
❌ NEVER output a startup without visiting its live website first
❌ NEVER write one-liners from memory — copy/paraphrase from their actual site
❌ NEVER write match reasons without citing a verified data point
❌ NEVER reference candidate skills not present in the actual resume
❌ NEVER output raw {{...}} template tokens — replace every one with real data or omit
```

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
3. Summarize the candidate profile in a structured block so all subsequent research
   can reference it accurately.

---

## Phase 1 — Startup Discovery (Multi-Source)

Search the following sources using available web browsing, surfing, and search tools
to navigate and extract real, live results. Build search queries from the candidate's skills,
target roles, and domain interests.

**Target: 10–25 thoroughly verified startups.** Do NOT pad the list beyond what you can
fully verify. It is perfectly acceptable to deliver 5–8 startups if those are the only
ones that pass all verification gates.

### Sources to Search

#### Tier 1 — Primary Discovery (always search these)

| # | Source | URL | What to Look For |
|---|--------|-----|-------------------|
| 1 | **LinkedIn** | linkedin.com | Companies, startup pages, "recently funded" posts, job posts matching skills |
| 2 | **Y Combinator** | ycombinator.com/companies | YC-backed startups filtered by batch, industry, stage |
| 3 | **Work at a Startup (YC)** | workatastartup.com | YC company job board — roles across all YC startups in one place |
| 4 | **Wellfound (AngelList)** | wellfound.com | Startup profiles, open roles, company stage/funding |
| 5 | **Crunchbase** | crunchbase.com | Funding rounds, investors, team size, HQ location |
| 6 | **Web Search** | Various search engines | `"[skill] startup hiring [year]"`, `"[domain] seed round [year]"` |

#### Tier 2 — Specialized Platforms (search all accessible)

| # | Source | URL | What to Look For |
|---|--------|-----|-------------------|
| 7 | **The Org** | theorg.com | Org charts — best source for finding exact current titles & roles |
| 8 | **CareerLift** | careerlift.in | Indian startup job board — roles, company profiles |
| 9 | **Jack & Jill** | app.jackandjill.ai | AI-powered job matching platform |
| 10 | **BetaList** | betalist.com | Early-stage startups launching soon — pre-seed/seed |
| 11 | **Product Hunt** | producthunt.com | Recently launched products — founding teams, traction |
| 12 | **F6S** | f6s.com | Startup profiles, accelerator programs, founder deals, jobs |
| 13 | **BuiltIn** | builtin.com | Startup jobs by city, company profiles with tech stack |
| 14 | **Indie Hackers** | indiehackers.com | Bootstrapped/profitable startups, founders sharing revenue & hiring |

#### Tier 3 — Enrichment & Verification (use to cross-check and fill gaps, not primary discovery)

These sources are used to **verify** data found in Tiers 1–2, not for primary discovery.
Many are paywalled or have limited free access. Use public snippets and search results.
If blocked, log the block and move on — never fabricate.

| # | Source | URL | Use |
|---|--------|-----|-----|
| 15 | **Tracxn** | tracxn.com | Cross-check funding, investor, team data |
| 16 | **Glassdoor** | glassdoor.com | Verify company culture, salary data (may require login) |
| 17 | **TechCrunch** | techcrunch.com | Verify funding announcements via press coverage |
| 18 | **YourStory** | yourstory.com | Verify Indian startup funding & news |
| 19 | **Inc42** | inc42.com | Verify Indian startup funding & sector reports |
| 20 | **Dealroom** | dealroom.co | European & global startup enrichment |
| 21 | **Fundz** | fundz.net | Real-time funding alerts |
| 22 | **EU-Startups** | eu-startups.com | European startup news & lists |
| 23 | **Tech in Asia** | techinasia.com | Southeast Asian startup data |
| 24 | **CB Insights** | cbinsights.com | Market maps & sector lists |
| 25 | **PitchBook** | pitchbook.com | VC deals (mostly paywalled — use search snippets only) |

#### Tier 4 — Niche & Remote-First (search when relevant to candidate profile)

| # | Source | URL | Use |
|---|--------|-----|-----|
| 26 | **Hacker News — Who is Hiring** | news.ycombinator.com | Monthly hiring threads — founders post with direct contact info |
| 27 | **RemoteOK** | remoteok.com | Remote-first startup jobs |
| 28 | **We Work Remotely** | weworkremotely.com | Remote jobs — many early-stage startup postings |
| 29 | **Himalayas** | himalayas.app | Remote startup jobs with tech stack info |
| 30 | **Twitter/X** | x.com | Founders announcing hiring, funding rounds |
| 31 | **TopStartups.io** | topstartups.io | Curated lists by category, funding, batch |
| 32 | **Startup India** | startupindia.gov.in | DPIIT-recognized Indian startups |
| 33 | **Instahyre** | instahyre.com | Indian tech hiring platform |
| 34 | **Cutshort** | cutshort.io | Indian startup jobs — ML-matched roles |
| 35 | **StackShare** | stackshare.io | Verify tech stacks companies use |
| 36 | **GitHub Trending** | github.com/trending | Active open-source projects by startups |

### Discovery Strategy

- **Verify Legitimacy Upfront**: Confirm the startup has an active website, an actual product or real service, and identifiable founders. Skip empty shells or parked domains.
- **Don't require active job postings**: Many early-stage startups hire through direct founder reachout even before listing jobs.
- **Check funding status**: Prioritize startups that recently raised capital (pre-seed, seed, Series A, Series B) within the last 6–12 months.
- **Blocked source protocol**: If a site blocks access, requires login you don't have, or shows CAPTCHA — log it in the Limitations section and move to the next source. Never recall data from memory as a substitute.

---

## Phase 2 — Company Deep Dive & Data Verification

For each discovered startup, verify and gather the following details using your available
web browsing and search tools. **If any field cannot be verified, omit it or set it to `null`.**

**Source Conflict Rule**: When two sources disagree on a data point (e.g., Crunchbase says
"Seed" but a TechCrunch article says "Series A"), prefer the most recent authoritative
source in this order: **official company page > Crunchbase/YC directory > press articles > LinkedIn**.
If a conflict cannot be resolved, note the discrepancy and use the most conservative figure.

| Field | Verification Requirement | Action if Unverified |
|-------|--------------------------|----------------------|
| **Company Name** | Official legal or operating name | Exclude startup if name cannot be verified |
| **One-Liner** | **Copy or closely paraphrase real text from the company's live homepage or About page.** Do NOT write this from memory or general knowledge. | Must be based on text visible on their actual site |
| **Website URL** | Must navigate to it and confirm it is live, active, and belongs to the company | Exclude startup if website is dead/parked |
| **Industry / Domain** | Verified industry from company's own description | Record only verified domains |
| **Founded Year** | Verified year from Crunchbase, LinkedIn, or About page | Set `null` if unconfirmed |
| **Location / HQ** | Verified city, country or "Remote" | Set `null` if unconfirmed |
| **Team Size** | Approximate headcount from LinkedIn/Crunchbase | Set `null` if unconfirmed |
| **Funding Stage** | Pre-seed / Seed / Series A / Series B / Bootstrapped | Set `null` / `"Not disclosed"` if unconfirmed |
| **Total Raised** | Amount confirmed via Crunchbase or verified press | Set `null` / `"Not disclosed"` if unconfirmed |
| **Last Funding Date** | Verified date of last funding round | Set `null` / `"Not disclosed"` if unconfirmed |
| **Key Investors** | Notable verified investors or accelerators | Set `[]` if unconfirmed |
| **Tech Stack** | **Only list technologies explicitly mentioned on their careers page, job listings, GitHub repos, or StackShare profile.** Do NOT infer tech stack from the company's industry, product category, or name. | Set `[]` if not confirmed |
| **Why It Matches** | **Must cite a specific verified data point** (e.g., "Uses React per their careers page listing for Senior Frontend Engineer" or "AI/ML company per YC S24 profile"). Do NOT infer match from company name alone. | Must reference a concrete source |
| **Careers Page** | Direct link navigated to and verified as live | Set `null` / `"None"` if no page exists |
| **LinkedIn Page** | Direct URL to verified company page | Set `null` if not found |
| **Crunchbase / Wellfound** | Direct verified URL | Set `null` if not found |
| **Active Job Listings** | Verified direct links to specific open positions | `"No public listings — cold outreach recommended"` if none |

For every data point, internally track the **source** where you found it (e.g., "Crunchbase",
"Company /about page", "YC directory"). You will record this in the `"verified_via"` field
in the JSON output.

---

## Phase 3 — High-Leverage People Discovery (DM & Outreach Targets)

Inspect the company's LinkedIn Company Page (People tab), The Org, team pages, and verified
leadership records. Identify **all** high-leverage individuals who can directly evaluate
the candidate, open doors, make hiring decisions, or sponsor an interview via DM.

### 1. The Core Decision-Maker Target Pool (Search for these across ALL startups)

Regardless of startup stage or headcount, search for and include any verified individuals
currently holding these roles:
1. **Founders & Executive Leadership**:
   - Founders, Co-Founders, CEO, CTO.
   - Always highest leverage for company vision, technical direction, and direct hiring authority.
2. **Engineering Leadership & Technical Hiring Managers**:
   - VP of Engineering (VPE), Director of Engineering, Head of Engineering.
   - Engineering Managers (EMs), Tech Leads, Principal Engineers, Founding Engineers.
   - Directly own team headcount, set technical requirements, and make offer recommendations.
3. **Talent & Hiring Gatekeepers**:
   - Head of Talent, VP / Director of People, Lead Technical Recruiter, Talent Acquisition Lead.
   - Actively scouting candidates, screening resumes, and fast-tracking qualified profiles.
4. **Domain Leadership (matching candidate profile)**:
   - For Product: VP Product, Head of Product, Chief Product Officer (CPO).
   - For Design: VP Design, Head of Design, Design Director.

### 2. Critical Anti-Hallucination Rule: Stage Realities & No Forced Filling
- **Include whoever actually exists**: If an early-stage startup has a Founder, a VP of
  Engineering, a Tech Lead, and a Recruiter, **include all of them**.
- **Do NOT force-fill missing titles**: In early-stage startups (e.g. <25–50 people),
  specialized roles like a dedicated "VP of Engineering" or dedicated "HR / Recruiter"
  often DO NOT exist yet; founders and founding engineers handle hiring directly.
  - **NEVER** hallucinate an HR person or VP if the company doesn't have one.
  - **NEVER** pick an unrelated person (e.g. an intern, administrative assistant, or
    sales rep) and pretend they are a hiring manager just to fill a role slot.
  - If only the founders exist, include only the verified founders. If an early startup
    *does* have a VP of Eng, a Tech Lead, or an HR lead, **include them**.

### 3. Strict Negative Filter: Who NOT to Add ("Don't Add Anyone Who Can't Help")

**DO NOT include any contact who falls into these categories**:
- ❌ **Unrelated Departments**: Never add Sales Reps (BDRs/SDRs/AEs), Customer Support
  reps, Finance/Accounting staff, or Office Managers if the candidate is applying for
  engineering or technical roles.
- ❌ **Junior Staff & Interns**: Do not add interns, junior associates, or contractors
  who lack hiring influence or context to sponsor an interview.
- ❌ **Passive Advisors & Board Members**: External board members, advisory board members,
  and non-operational investors do not hire for specific teams.
- ❌ **Former Employees**: Double-check current employment. If the person's LinkedIn shows
  a different current company, or their end date at this startup has passed, do NOT include them.
  Having an older profile photo is NOT grounds for exclusion if the current employment is verified.
- ❌ **Unreachable Profiles**: Do not include profiles where the person's LinkedIn shows
  no current role listed at this company, or the profile clearly belongs to a different person.

### 4. Contact Data Requirements & Outreach Angle

| Field | Verification Requirement | Strict Rule |
|-------|--------------------------|-------------|
| **Full Name** | Verified first and last name | Must currently hold an active hiring/decision-making role |
| **Title / Role** | Exact current title verified on live profile or team page | e.g. "Director of Engineering", "Co-Founder & CTO" |
| **Company** | Confirm current active employment | Discard if they have transitioned to another company |
| **LinkedIn Profile** | Direct URL navigated to and verified | Must be the actual person's profile for direct connection/DM |
| **Twitter/X** | Direct URL to active handle | Set `null` if unconfirmed or inactive |
| **Email** | **MUST BE PUBLICLY LISTED** in plain text on official site, press release, or verified bio | **NEVER GUESS.** If not found, strictly set to `null` |
| **Why DM / Outreach Angle** | Must only reference: (a) the person's verified title/role, and (b) skills explicitly listed in the candidate's resume from Phase 0 | Do NOT introduce skills, technologies, or experiences not present in the resume |
| **Verified Via** | The source where you confirmed this person's current role | e.g. "LinkedIn People tab", "Company /team page", "The Org" |

---

## Phase 3.5 — Strict Data Verification & Omission Gate

**Before generating any report or JSON output, run every discovered entity through the
complete verification protocol documented in `references/verification-checklist.md`.**

That file defines 5 mandatory gates:
1. **Gate 1**: URL & Link Live Check — visit every URL, discard 404s and dead links.
2. **Gate 2**: Contact Authenticity — confirm current employment.
3. **Gate 3**: Hiring Leverage & DM Relevance — discard anyone who can't help.
4. **Gate 4**: Email Provenance — strip any guessed/unverified emails.
5. **Gate 5**: Company Metrics — replace unverified numbers with `null`.

Any entity that fails a gate must be corrected (field set to `null`) or removed entirely.
See the full checklist for detailed criteria and the Field-by-Field Omission Protocol table.

---

## Phase 4 — Output Generation

Generate **two** synchronized output files containing only verified, high-leverage data.

### 1. Markdown Report (Human-Readable)
- Create as a **markdown artifact** so the user can inspect it in the chat interface.
- Also save a copy to `findings/startup-outreach-report.md` in the workspace.
- **Formatting Rule for Missing Data**:
  - If a contact has no verified email, leave the email column as `—` (em-dash).
  - If a company has no dedicated careers page, write `None (Cold outreach recommended)`.
  - Highlight the **DM / Outreach Angle** so the user knows exactly how to approach each contact.

#### Report Structure (Structural Guide):

> The structure below shows the layout. Replace every field description with actual
> verified data. Never output placeholder text or template tokens in the final report.

**Sections to include in order**:
1. **Title**: `🚀 Startup Outreach List for [Candidate Name]`
2. **Header block**: Generated date, resume file, data integrity note, targeting note.
3. **📋 Candidate Profile Summary**: Table with Target Roles, Key Skills, Experience, Domains, Location Pref, Education.
4. **📊 Discovery Summary**: Table with Total verified startups, With active listings, Cold outreach targets, Funding breakdown.
5. **🏢 Startup Details** (repeat per startup):
   - Company name as heading, outreach done checkbox, one-liner quote.
   - Company details table (all verified fields; omit or mark `—` for unverified).
   - **👥 High-Leverage Outreach Targets** table: Done checkbox, Name, Title, DM / Outreach Angle, LinkedIn, Twitter/X, Email.
6. **📇 Quick Reference — All High-Value Contacts**: Flat table of ALL contacts across all startups.
7. **🔗 All Verified Links**: Company, Website, Careers Page, LinkedIn.
8. **⚠️ Limitations & Gaps**: List of sources that were blocked, logins unavailable, data points that could not be verified, and any known gaps.
9. **DM & Outreach Strategy**: Guidance on whom to DM first and how.

See `resources/report-template.md` for the full markdown template.

### 2. JSON Data File (Machine-Readable)
- Save to `findings/startup-outreach-data.json` in the workspace.
- Do NOT include user-specific details (candidate name, resume path, skills, education, etc.) in the JSON — those belong only in the markdown report.
- Include `"outreach_angle"` and `"verified_via"` for every contact and key company fields.
- Include `"confidence"` tag: `"high"` = confirmed by 2+ independent sources; `"medium"` = single source only.
- See `references/json-schema.md` for the complete schema definition and field documentation.

#### Status Field Rules
- Every startup and contact **must** have `"status": "pending"` on initial generation.
- Cold outreach automation can process `"pending"` records and flip to `"done"` once sent.

---

## Execution Guidelines

- **Use Available Browsing & Surfing Tools**: Navigate to live pages, inspect the real DOM, verify responses, and confirm content authenticity. Never rely on unverified guesses.
- **Deep LinkedIn & Org Navigation**: Review the company's People tab on LinkedIn, org charts, and leadership directories to locate true decision-makers.
- **Ruthless Relevance Filtering**: Only list people who can actually open a door or hire the candidate. Skip junior employees, unrelated departments, and inactive accounts.
- **Strict Verification Before Inclusion**: Every link must be tested. Every contact must currently work there. Every email must have public provenance.
- **Quality Over Quantity**: 10 completely accurate, verified startups with validated, high-leverage decision-maker contacts provide 100x more value than 40 entries filled with broken links, former employees, and junior non-hiring staff.
- **Omission is Correctness**: Leaving an unverified email or missing careers link as `null`/blank is the correct, professional behavior.
- **Source Attribution**: For every key data point, track where you found it. Record this in the `"verified_via"` field.
- **Transparency on Gaps**: Always include a Limitations section listing what you could not access or verify.
