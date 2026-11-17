# Startup Hunter — Reference: Search Query Templates

Use these query templates when searching each source. Replace `{skill}`, `{role}`,
`{domain}`, `{location}`, and `{year}` with values extracted from the candidate's resume.

---

## Tier 1 — Primary Discovery

### LinkedIn Search Queries
```
{role} startup hiring {year}
{skill} engineer startup
"{domain}" startup founded {year}
site:linkedin.com/company {domain} startup
"{domain}" startup "we're hiring" {location}
```

### Y Combinator Company Directory
Navigate to `https://www.ycombinator.com/companies` and use filters:
- **Industry**: Match to candidate's domain (e.g., "B2B", "Fintech", "AI")
- **Batch**: Recent batches (W25, S25, W26, S26, etc.)
- **Status**: Active
- **Region**: Match candidate's location preference, or "Remote"

### Work at a Startup (YC Job Board)
Navigate to `https://www.workatastartup.com/jobs` and search:
- Role: `{role}`
- Skills: `{skill}`
- Filter by company stage, team size, location
- This aggregates jobs from ALL YC companies — very high signal

### Wellfound Search
Navigate to `https://wellfound.com/jobs` and search:
- Role: `{role}`
- Skills: `{skill}`
- Stage: Seed, Series A, Series B
- Also browse `https://wellfound.com/startups` filtered by domain

### Crunchbase Search
```
site:crunchbase.com "{domain}" startup seed {year}
site:crunchbase.com "{skill}" startup series-a
```
Or navigate to `https://www.crunchbase.com/discover/organization.companies` with filters.

### Google Search Queries
```
"{skill}" startup hiring {year}
"{domain}" startups recently funded {year}
"{role}" startup job remote {year}
site:wellfound.com "{skill}" startup
site:ycombinator.com/companies "{domain}"
"{domain}" startup seed round {year} hiring
"{skill}" "{role}" startup careers
YC {batch} startups {domain}
"{domain}" startup "{location}" hiring {year}
"{skill}" startup "open position" {year}
best "{domain}" startups to work for {year}
"{domain}" startups series A {year} India
```

---

## Tier 2 — Specialized Platforms

### CareerLift
Navigate to `https://careerlift.in` and search:
- Role keywords: `{role}`
- Filter by startups, tech companies
- Look at company profiles for funding info

### Jack & Jill
Navigate to `https://app.jackandjill.ai` and:
- Create/import profile or search manually
- Browse recommended startups by skill match
- Check company details and team info

### BetaList
Navigate to `https://betalist.com` and search `{domain}` or `{skill}`.
- Browse by topic: `https://betalist.com/topics/{domain}`
- Look at recently listed startups — these are pre-launch or early stage
- Founding team info is often listed on startup profiles

### Product Hunt
Navigate to `https://www.producthunt.com` and search `{domain} {skill}`.
- Sort by newest
- Look at the founding team listed on each product page
- Filter by topics matching candidate's domain

### Indie Hackers
Navigate to `https://www.indiehackers.com` and:
- Browse products: `https://www.indiehackers.com/products`
- Filter by revenue range (funded or profitable = more likely hiring)
- Search forum posts for `{domain} hiring` or `{role} looking`
- Many bootstrapped founders post hiring needs in community

### F6S
Navigate to `https://www.f6s.com` and:
- Search startups by `{domain}` or `{skill}`
- Browse startup profiles — includes funding, team, location
- Check jobs section: `https://www.f6s.com/jobs`
- Many accelerator-backed startups list here

### The Org
Navigate to `https://theorg.com` and search for startups by `{domain}`.
- **This is gold for people discovery** — shows full org charts
- Find exact titles: CEO, CTO, VP Eng, Head of HR, etc.
- LinkedIn profiles are linked directly from org chart cards

### Tracxn
Navigate to `https://tracxn.com` and search:
- Sector: `{domain}`
- Stage: Seed, Series A, Series B
- Location: `{location}` or India / US / Global
- Provides comprehensive funding, investor, and team data

### BuiltIn
Navigate to `https://builtin.com` and search:
- Browse by city: `https://builtin.com/{city}/jobs`
- Filter by company size (1-50 = startup territory)
- Tech stack filters available — match to candidate skills
- Company profiles include perks, culture, tech stack

### Glassdoor
```
site:glassdoor.com "{domain}" startup "{location}" reviews
site:glassdoor.com "{skill}" startup jobs
```
Navigate to `https://www.glassdoor.com` and search company names found elsewhere
to get reviews, salary data, and interview process info.

---

## Tier 3 — Funding & News Intelligence

### Dealroom
Navigate to `https://dealroom.co` and search:
- Filter by sector, stage, HQ location
- Sort by most recently funded
- Provides team size growth signals (growing = hiring)

### PitchBook
```
site:pitchbook.com "{domain}" startup
site:pitchbook.com "{company name}" funding
```
Note: May be paywalled. Use search results snippets for data.

### CB Insights
```
site:cbinsights.com "{domain}" startups {year}
site:cbinsights.com market map "{domain}"
```
Good for sector-wide company lists (market maps).

### Fundz
Navigate to `https://fundz.net` and:
- Browse recent funding rounds
- Filter by industry and stage
- Real-time alerts — recently funded = actively hiring

### TechCrunch
```
site:techcrunch.com "{domain}" startup raises {year}
site:techcrunch.com "{domain}" seed round {year}
site:techcrunch.com "{domain}" series A {year}
```
Great for discovering recently funded startups with press coverage.

### YourStory (India Focus)
```
site:yourstory.com "{domain}" startup funding {year}
site:yourstory.com "{domain}" startup hiring
site:yourstory.com startup "{location}" raises
```

### Inc42 (India Focus)
```
site:inc42.com "{domain}" startup funding {year}
site:inc42.com startup "{location}" raises {year}
```
Also check: `https://inc42.com/startup-funding-tracker/` for latest rounds.

### EU-Startups (Europe Focus)
```
site:eu-startups.com "{domain}" startup funding {year}
site:eu-startups.com top "{domain}" startups
```

### Tech in Asia (Southeast Asia Focus)
```
site:techinasia.com "{domain}" startup funding {year}
site:techinasia.com startup "{location}" raises
```

---

## Tier 4 — Niche & Remote-First

### Hacker News — "Who is Hiring?" Threads
Search on Google:
```
site:news.ycombinator.com "Ask HN: Who is hiring" {month} {year}
```
Then search within the thread for `{skill}`, `{role}`, `{domain}`.
These are monthly threads with high-quality startup postings.

### RemoteOK
Navigate to `https://remoteok.com` and search:
- Tags: `{skill}`, `{role}`
- Filter by salary range
- Company profiles include tech stack and team size

### We Work Remotely
Navigate to `https://weworkremotely.com` and search:
- Category: Programming, Design, Product, etc.
- Many early-stage startup postings
- Company profiles link to websites and careers pages

### Himalayas
Navigate to `https://himalayas.app` and search:
- Role: `{role}`
- Skills: `{skill}`
- Shows tech stack, company size, benefits
- Good remote-first startup coverage

### Twitter/X Search
```
"{domain}" startup hiring -job_board
"we're hiring" "{role}" startup
"just raised" "{domain}" startup
"seed round" "{domain}" {year}
"join our team" "{skill}" startup
"founding engineer" "{domain}"
"first hire" "{domain}" startup
"looking for" "{role}" startup
```

### TopStartups.io
Navigate to `https://topstartups.io` and browse:
- Curated lists by category, funding, YC batch
- Company profiles with key metrics

### Startup India
Navigate to `https://www.startupindia.gov.in` and:
- Search recognized startups by sector
- Filter by location, industry
- DPIIT-recognized = verified legitimate

### GrowthList
Navigate to `https://growthlist.co` and:
- Browse funded startups with contact info
- Filter by industry and funding stage
- Some provide founder email addresses

### Instahyre (India Focus)
Navigate to `https://www.instahyre.com` and search:
- Role: `{role}`
- Skills: `{skill}`
- Many Indian startups hire exclusively here
- Company profiles include funding and team info

### Cutshort (India Focus)
Navigate to `https://cutshort.io` and search:
- ML-matched roles based on skills
- Company profiles with funding info
- Filter by startup stage

### Hashjob
Navigate to `https://hashjob.co` and browse:
- Tech-focused job board
- Many Indian startup listings

### Seedtable (Europe Focus)
Navigate to `https://seedtable.com` and:
- Browse European startups by sector, stage, country
- Funding data, team size, investor info

### Acquire.com
Navigate to `https://acquire.com` and browse:
- Startups listed for sale reveal what's being built
- Shows SaaS metrics, tech stacks, revenue
- Useful for understanding the landscape in `{domain}`

### GitHub Trending
Navigate to `https://github.com/trending` and:
- Browse by language matching candidate's skills
- Look at org profiles — many startups have GitHub orgs
- Active repos = active engineering team = potential hiring

### StackShare
Navigate to `https://stackshare.io` and search:
- Companies using `{skill}` or `{framework}`
- Match tech stack to candidate's expertise
- Company profiles link to websites and careers pages

---

## Meta-Search (Combine Sources)

For maximum coverage, also run these combined Google queries:
```
"{company name from any source}" hiring {year}
"{company name}" "careers" OR "jobs" OR "join us"
"{company name}" founder linkedin
"{company name}" funding crunchbase OR tracxn OR dealroom
"{company name}" "{role}" OR "{skill}"
```
