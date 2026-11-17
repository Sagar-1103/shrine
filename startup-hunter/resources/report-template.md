# Startup Hunter — Report Template

Use this template to generate the final output artifact. Every startup and
every contact has a checkbox for outreach tracking.

---

```markdown
# 🚀 Startup Outreach List for {{CANDIDATE_NAME}}

> **Generated**: {{DATE}}
> **Based on**: {{RESUME_FILE}}
> **Sources searched**: LinkedIn, YC, Work at a Startup, Wellfound, CareerLift,
> Jack&Jill, BetaList, Crunchbase, Product Hunt, Indie Hackers, F6S, The Org,
> Tracxn, BuiltIn, Glassdoor, Dealroom, Fundz, TechCrunch, YourStory, Inc42,
> Hacker News, RemoteOK, We Work Remotely, Himalayas, Twitter/X, and more

---

## 📋 Candidate Profile Summary

| Field | Details |
|-------|---------|
| **Target Roles** | {{ROLES}} |
| **Key Skills** | {{SKILLS}} |
| **Experience** | {{EXPERIENCE_YEARS}} years |
| **Domains** | {{DOMAINS}} |
| **Location Pref** | {{LOCATION}} |
| **Education** | {{EDUCATION}} |

---

## 📊 Discovery Summary

| Metric | Count |
|--------|-------|
| Total startups found | {{TOTAL}} |
| With active job listings | {{WITH_LISTINGS}} |
| Cold outreach targets | {{COLD_OUTREACH}} |
| Pre-Seed | {{PRE_SEED}} |
| Seed | {{SEED}} |
| Series A | {{SERIES_A}} |
| Series B+ | {{SERIES_B_PLUS}} |
| Bootstrapped | {{BOOTSTRAPPED}} |

---

## 🏢 Startup Details

{{#EACH STARTUP}}

### {{INDEX}}. {{COMPANY_NAME}}

- [ ] **Outreach done**

> {{ONE_LINER}}

| Field | Details |
|-------|---------|
| **Website** | [{{WEBSITE}}]({{WEBSITE}}) |
| **Industry** | {{INDUSTRY}} |
| **Founded** | {{FOUNDED}} |
| **Location** | {{LOCATION}} |
| **Team Size** | ~{{TEAM_SIZE}} |
| **Funding Stage** | {{FUNDING_STAGE}} |
| **Total Raised** | {{TOTAL_RAISED}} |
| **Last Funded** | {{LAST_FUNDED}} |
| **Key Investors** | {{INVESTORS}} |
| **Tech Stack** | {{TECH_STACK}} |
| **Why It Matches** | {{MATCH_REASON}} |
| **Careers Page** | [Link]({{CAREERS_URL}}) |
| **LinkedIn** | [Link]({{LINKEDIN_URL}}) |
| **Crunchbase** | [Link]({{CRUNCHBASE_URL}}) |
| **Job Listings** | {{JOB_LISTINGS_OR_COLD_OUTREACH}} |

#### 👥 Key Contacts

| Done | Name | Title | LinkedIn | Twitter/X | Email | Notes |
|------|------|-------|----------|-----------|-------|-------|
| [ ] | {{PERSON_NAME}} | {{PERSON_TITLE}} | [Profile]({{PERSON_LINKEDIN}}) | {{PERSON_TWITTER}} | {{PERSON_EMAIL}} | {{PERSON_NOTES}} |

---

{{/EACH}}

## 📇 Quick Reference — All Contacts

| Done | # | Name | Title | Company | LinkedIn | Email |
|------|---|------|-------|---------|----------|-------|
{{#EACH PERSON}}
| [ ] | {{INDEX}} | {{NAME}} | {{TITLE}} | {{COMPANY}} | [Profile]({{LINKEDIN}}) | {{EMAIL}} |
{{/EACH}}

---

## 🔗 All Career Pages

| Done | Company | Careers Page | LinkedIn |
|------|---------|-------------|----------|
{{#EACH STARTUP}}
| [ ] | {{COMPANY_NAME}} | [Careers]({{CAREERS_URL}}) | [LinkedIn]({{LINKEDIN_URL}}) |
{{/EACH}}

---

> **Next Steps**: Filter by `pending` in the JSON file to find who hasn't been
> contacted yet. Prioritize startups that recently raised funding. Personalize
> each outreach message referencing the company's product and why your skills
> are relevant. Connect with founders on LinkedIn before cold-emailing.
```
