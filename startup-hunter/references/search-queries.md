# Startup Hunter — Reference: Search Query Templates

Use these query templates when searching each source. Replace `{skill}`, `{role}`,
`{domain}`, `{location}`, and `{year}` with values extracted from the candidate's resume.

> **Reminder**: These are search queries only. For detailed navigation instructions per
> source, see SKILL.md Phase 1. If a source blocks access or requires unavailable login,
> log the block and move to the next source. Never fabricate results from memory.

---

## Tier 1 — Primary Discovery & People Search

### LinkedIn — Decision-Maker Search
```
site:linkedin.com/in "{company name}" ("Director of Engineering" OR "VP of Engineering" OR "Head of Engineering")
site:linkedin.com/in "{company name}" ("CTO" OR "Chief Technology Officer" OR "Co-Founder & CTO")
site:linkedin.com/in "{company name}" ("Engineering Manager" OR "Lead Engineer" OR "Founding Engineer")
site:linkedin.com/in "{company name}" ("Head of Talent" OR "Head of People" OR "Technical Recruiter" OR "Talent Acquisition")
site:linkedin.com/in "{company name}" ("Founder" OR "Co-Founder" OR "CEO")
```

### LinkedIn — Startup Discovery
```
{role} startup hiring {year}
{skill} engineer startup
"{domain}" startup founded {year}
site:linkedin.com/company {domain} startup
"{domain}" startup "we're hiring" {location}
```

### Y Combinator — Filters
- Industry: `{domain}` | Batch: Recent (W24+) | Status: Active | Region: `{location}` or Remote
- On each company profile, check the **Founders** section for LinkedIn URLs.

### Work at a Startup (YC)
- Role: `{role}` | Skills: `{skill}` | Filter by stage, team size, location

### Wellfound
- Role: `{role}` | Skills: `{skill}` | Stage: Seed, Series A, Series B
- On company profile, check **Team / Culture** for founders and tech leads.

### Crunchbase
```
site:crunchbase.com "{domain}" startup seed {year}
site:crunchbase.com "{skill}" startup series-a
site:crunchbase.com/organization "{company name}"
```

### General Web Search
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
"{domain}" startups series A {year}
```

---

## Tier 2 — Specialized Platforms

### The Org — Org Charts & Decision-Makers
- Search by company name → inspect full org hierarchy
- Locate VP Engineering, Director of Engineering, team leads
- Profile cards link directly to LinkedIn

### BetaList
- Search: `{domain}` or `{skill}` | Topics: `betalist.com/topics/{domain}`

### Product Hunt
- Search: `{domain} {skill}` | Sort by newest
- Review makers/founding team on product pages

### F6S
- Search startups by `{domain}` or `{skill}` | Jobs: `f6s.com/jobs`

### BuiltIn
- By city: `builtin.com/{city}/jobs` | Filter: company size 1-50

### Glassdoor
```
site:glassdoor.com "{domain}" startup "{location}"
site:glassdoor.com "{skill}" startup jobs
```

---

## Tier 3 — Enrichment & Verification

### TechCrunch — Funding Verification
```
site:techcrunch.com "{domain}" startup raises {year}
site:techcrunch.com "{company name}" seed OR "series A" {year}
```

### YourStory (India)
```
site:yourstory.com "{domain}" startup funding {year}
site:yourstory.com startup "{location}" raises
```

### Inc42 (India)
```
site:inc42.com "{domain}" startup funding {year}
site:inc42.com startup "{location}" raises {year}
```

### EU-Startups (Europe)
```
site:eu-startups.com "{domain}" startup funding {year}
```

### Tech in Asia (Southeast Asia)
```
site:techinasia.com "{domain}" startup funding {year}
```

### PitchBook (paywalled — search snippets only)
```
site:pitchbook.com "{company name}" funding
```

### CB Insights
```
site:cbinsights.com "{domain}" startups {year}
site:cbinsights.com market map "{domain}"
```

---

## Tier 4 — Niche & Remote-First

### Hacker News — "Who is Hiring?"
```
site:news.ycombinator.com "Ask HN: Who is hiring" {month} {year}
```

### Twitter/X
```
"{domain}" startup hiring -job_board
"we're hiring" "{role}" startup
"just raised" "{domain}" startup
"founding engineer" "{domain}"
```

### Remote Job Boards
- RemoteOK: Tags `{skill}`, `{role}`
- We Work Remotely: Category Programming / Design / Product
- Himalayas: Role `{role}`, Skills `{skill}`

---

## Verification Queries (Mandatory — Run for Every Company)

### Website & Domain Verification
```
"{Company Name}" official website
site:{companydomain} about OR team OR contact
```

### Decision-Maker Verification
```
site:linkedin.com/in "{Company Name}" ("Director of Engineering" OR "VP Engineering" OR "CTO" OR "Founder" OR "Head of Talent")
"{Person Name}" "{Company Name}" linkedin
site:linkedin.com/in "{Person Name}" "{Company Name}"
```

### Public Email Verification
```
site:{companydomain} contact OR press OR about
"{Person Name}" "{Company Name}" email
```
> Only record an email if found explicitly in text. Never guess patterns.

### Funding Verification
```
"{Company Name}" seed round OR series A TechCrunch OR Crunchbase
"{Company Name}" funding {year}
site:crunchbase.com/organization "{Company Name}"
```

### Careers & Job Listings Verification
```
site:{companydomain} careers OR jobs OR "join us"
"{Company Name}" "open roles" OR "apply"
```
