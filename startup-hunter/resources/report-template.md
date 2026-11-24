# Startup Hunter — Report Template

Use this template to generate the final output artifact and report file.

> **Critical**: The placeholders below (marked with `[DESCRIPTION]` brackets) show the
> report structure. Replace EVERY placeholder with actual verified data. Never output
> raw placeholder text, template tokens, or `{{...}}` syntax in the final report.
> If a field has no verified data, render `—` (em-dash) or omit the row entirely.

**Strictly adhere to the Zero-Hallucination & Verification Directive**:
- Only include verified, active companies and working links.
- Only include high-leverage decision-makers who can directly facilitate hiring.
- If a contact's email is not publicly published, render `—` (em-dash).
- If a company has no dedicated careers page, render `None (Cold outreach recommended)`.
- Never insert speculative, guessed, or unhelpful contacts.

---

```markdown
# 🚀 Startup Outreach List for [Candidate Name]

> **Generated**: [Date]
> **Based on**: [Resume file path]
> **Data Integrity**: All companies, contacts, and links verified via live web inspection. Unverified fields are omitted.
> **Targeting**: Contacts strictly filtered for high-leverage hiring decision-makers.

---

## 📋 Candidate Profile Summary

| Field | Details |
|-------|---------|
| **Target Roles** | [Roles from resume] |
| **Key Skills** | [Skills from resume] |
| **Experience** | [X] years |
| **Domains** | [Domains from resume] |
| **Location Pref** | [Location from resume] |
| **Education** | [Education from resume] |

---

## 📊 Discovery Summary

| Metric | Count |
|--------|-------|
| Total verified startups | [X] |
| With active job listings | [X] |
| Cold outreach targets | [X] |
| Pre-Seed | [X] |
| Seed | [X] |
| Series A | [X] |
| Series B+ | [X] |
| Bootstrapped | [X] |

---

## 🏢 Startup Details

[Repeat this block for each verified startup]

### [Number]. [Company Name] | Confidence: [High/Medium]

- [ ] **Outreach done**

> [One-liner copied/paraphrased from company's live homepage]

| Field | Details |
|-------|---------|
| **Website** | [Verified live link] |
| **Industry** | [From company's own description] |
| **Founded** | [Verified year or —] |
| **Location** | [Verified location or —] |
| **Team Size** | [Verified count or —] |
| **Funding Stage** | [Verified stage or —] |
| **Total Raised** | [Verified amount or —] |
| **Last Funded** | [Verified date or —] |
| **Key Investors** | [Verified investors or —] |
| **Tech Stack** | [From careers/jobs/GitHub only, or —] |
| **Why It Matches** | [Must cite specific verified source] |
| **Careers Page** | [Verified link or None (Cold outreach recommended)] |
| **LinkedIn** | [Verified link or —] |
| **Crunchbase** | [Verified link or —] |
| **Job Listings** | [Verified links or No public listings — cold outreach recommended] |
| **Verified Via** | [Primary source: e.g. "YC directory + Crunchbase"] |

#### 👥 High-Leverage Outreach Targets (Decision-Makers)

| Done | Name | Title | DM / Outreach Angle | LinkedIn | Twitter/X | Email | Verified Via |
|:---:|------|-------|---------------------|----------|-----------|-------|-------------|
[Repeat for each verified decision-maker]
| [ ] | [Verified name] | [Current title from live profile] | [References person's title + candidate's resume skills only] | [Verified profile link] | [Verified handle or —] | [Publicly listed email or —] | [Source: e.g. "LinkedIn", "Company /team page"] |

---

[End repeat block]

## 📇 Quick Reference — All High-Value Contacts

| Done | # | Name | Title | Company | DM / Outreach Angle | LinkedIn | Email |
|:---:|---|------|-------|---------|---------------------|----------|-------|
[Flat table of ALL contacts across all startups]
| [ ] | [Number] | [Name] | [Title] | [Company] | [Angle] | [Profile link] | [Email or —] |

---

## 🔗 All Verified Links

| Company | Website | Careers Page | LinkedIn |
|---------|---------|-------------|----------|
[One row per startup]
| [Company] | [Website link] | [Careers link or None] | [LinkedIn link or —] |

---

## ⚠️ Limitations & Gaps

[Always include this section. Be transparent about what could not be verified.]

- **Sources blocked / requiring login**: [List any sources that could not be accessed]
- **Data points unverified**: [List specific fields where data could not be confirmed]
- **Startups excluded**: [Number of startups discovered but excluded due to failed verification]
- **Known gaps**: [Any other limitations the user should be aware of]

---

> **DM & Outreach Strategy**:
> - **Who is Included**: All verified decision-makers discovered at the company (Founders, CTO, VP Engineering, Director of Engineering, Tech Leads, Head of Talent/Recruiters). At early startups without an HR/VP layer, only verified founders and core technical leads are listed; at larger startups, specialized engineering heads and recruiters are also included. Never hallucinate missing roles.
> - **Whom to DM First**:
>   - **Founders & CTO**: Highest impact for early-stage startups and small teams — send a concise DM highlighting how your skills solve a specific product problem.
>   - **Director / VP of Engineering / Tech Leads**: Highest impact for growth-stage startups — message them directly with relevant technical contributions and code samples.
>   - **Head of Talent / Technical Recruiters**: Message them to get your resume fast-tracked through the applicant tracking pipeline.
> - **Outreach Channels**:
>   - **If Email is Available**: Send a concise, 3-sentence cold email with links to GitHub/portfolio.
>   - **If Email is `—`**: Connect on LinkedIn with a personalized note referencing their recent engineering achievements.
> - Update `"status": "done"` in `findings/startup-outreach-data.json` as outreach progresses.
```
