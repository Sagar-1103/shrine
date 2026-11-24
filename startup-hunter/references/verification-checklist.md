# Startup Hunter — Reference: Verification Checklist & Omission Protocol

This is the **single source of truth** for all verification rules. SKILL.md Phase 3.5
points here. Every startup, contact, link, and metric must pass these gates before
appearing in the final output.

---

## 🚫 The Golden Rule: "Verified or Omitted"

- **Zero Guessing**: Never deduce or extrapolate data (e.g., predicting an email format or assuming a careers URL exists).
- **Zero Placeholders**: Never invent placeholder links or filler text. If an email is not publicly listed, set `"email": null` and render `—` in tables.
- **High-Leverage Contacts Only**: Do NOT include anyone who cannot help the candidate get hired.
- **Precision Over Quantity**: 10 fully verified records with direct hiring managers are vastly superior to 50 records with dead links or unhelpful contacts.

---

## 🛡️ Mandatory Verification Gates

### Gate 1: URL & Link Live Check
Every link included in the output must be actively verified using available web surfing/browsing tools:
- [ ] **Company Website**: The site must be active, render real product/service content, and not be a parked domain, expired site, or placeholder. **If the website is dead, discard the entire company.**
- [ ] **Careers Page**: Must be a verified live jobs board or careers page. If the company does not have a careers page, record `"None — cold outreach recommended"` and set `"careers_page": null`. Do NOT guess URLs like `/careers` or `/jobs`.
- [ ] **LinkedIn URL**: Must navigate to the real, active company or person page. Do NOT construct URLs from name patterns.
- [ ] **Job Post URLs**: Must link directly to an active, valid role listing.

### Gate 2: Contact Authenticity & Current Affiliation Check
Every person included must be confirmed as an active team member:
- [ ] **Current Role**: The person currently works at the startup in the specified role (verified on their live profile or official company team page).
- [ ] **Not Former Staff**: If the person's LinkedIn shows a different current company, or their end date at this startup has passed, do NOT include them.
- [ ] **Reachable Profile**: The profile must have enough information to identify the right person and be contactable via LinkedIn DM or connection request.
- [ ] **Dormant Profile Clarification**: Having an older profile photo is NOT grounds for exclusion if current employment is verified. "Dormant" means the person's LinkedIn shows a different current company, or has no current role listed at this startup.

### Gate 3: Hiring Leverage & DM Relevance Check
Every person included **must pass this value-add test**:
- [ ] **Can this person hire, screen, or sponsor the candidate?**
  - **YES (Pass)**: Founder, Co-Founder, CEO, CTO, VP of Engineering, Director of Engineering, Head of Engineering, Engineering Manager, Tech Lead, Founding Engineer, Head of Talent, Technical Recruiter, or department head matching the candidate's field.
  - **NO (Disqualify / Do Not Add)**:
    - ❌ Unrelated departments (e.g., Sales SDR/AE, Customer Support, Accounting, Office Management).
    - ❌ Junior staff, entry-level contributors, interns without hiring authority.
    - ❌ Non-operating board members, passive advisors, external angels.
- [ ] **Anti-Hallucination on Missing Roles**:
  - Include any of the above roles that **actually exist** at the startup.
  - If a role does NOT exist (e.g. an early-stage startup has no HR person or no VP of Engineering), **DO NOT FORCE-FIT OR HALLUCINATE ONE**. Only list the people who genuinely exist and hold those titles.
- [ ] **Clear Outreach Angle**: Can you write a 1-sentence actionable reason explaining why DMing this person adds value, using only: (a) their verified title, and (b) skills from the candidate's actual resume? If not, discard the contact.

### Gate 4: Email Provenance & Non-Guessing Protocol
Every recorded email address must pass strict provenance verification:
- [ ] **Explicit Public Source**: The email must be visible in plain text on an official public page (company website contact/about page, official press release, SEC/regulatory filing, or verified profile bio).
- [ ] **Source Attribution**: Record where the email was found in the `"email_source"` JSON field.
- [ ] **Strict Prohibition on Pattern Synthesis**: NEVER generate an email using common conventions (such as `first@company.com`, `first.last@...`, `hello@...`, `info@...`, etc.) without explicit public confirmation.
- [ ] **Fallback**: If an email is not publicly published, set `"email": null` and `"email_source": null` in JSON and `—` in markdown reports. Direct the candidate to outreach via verified LinkedIn or Twitter/X instead.

### Gate 5: Company Metrics & Funding Fact-Check
Every metric reported must be backed by verifiable sources:
- [ ] **Funding Stage & Amount**: Must be confirmed via Crunchbase, PitchBook/Dealroom public snippets, YC directory, or trusted tech press (TechCrunch, Inc42, YourStory).
- [ ] **Headcount**: Approximate headcount must be verified against LinkedIn Company Page or official disclosures.
- [ ] **Source Conflict**: When two sources disagree, prefer the most recent authoritative source: official company page > Crunchbase/YC > press articles > LinkedIn. Note discrepancies.
- [ ] **Fallback**: If a metric is undisclosed or cannot be verified, record `"Not publicly disclosed"` and set the JSON value to `null`.

---

## 📋 Field-by-Field Omission & Relevance Protocol

| Field | Verification Requirement | When to Omit / Set Null | Strictly Prohibited Actions |
|-------|--------------------------|-------------------------|------------------------------|
| **Company Website** | Live site with real product/content | Discard entire company if dead | Guessing domain or using parked links |
| **One-Liner** | Copied/paraphrased from live site | Omit company if site inaccessible | Writing from memory or general knowledge |
| **Careers Page** | Direct link verified live | Set `null` / `"None"` if absent | Inventing `/careers` or `/jobs` URLs |
| **Job Listings** | Verified active job posting URLs | Set `[]` / `"No public listings"` | Guessing listing URLs |
| **LinkedIn Page** | Verified active company profile | Set `null` / omit from table | Constructing URL from company name |
| **Contact Name** | Verified high-leverage decision-maker | **Exclude completely if non-decision-maker** | Adding anyone who can't help |
| **Contact Title** | Current title on live profile/site | Omit contact if title unconfirmed | Guessing promotions or roles |
| **Outreach Angle** | References verified title + resume skills | Omit contact if no hiring relevance | Referencing skills not in the resume |
| **Contact Email** | Plain text on official public source | **Set `null` / render `—`** | **Pattern guessing (e.g. `first@`)** |
| **Contact LinkedIn** | Live, active personal profile | Set `null` / omit if not found | Constructing URL from person's name |
| **Contact Twitter/X** | Live, active handle | Set `null` / omit if not found | Guessing twitter handle |
| **Tech Stack** | From careers page, jobs, GitHub, StackShare | Set `[]` / omit if unconfirmed | Inferring from industry or company name |
| **Match Reason** | Cites specific verified data point | Must have concrete source | Vague "seems like a good fit" language |
| **Funding / Total Raised** | Primary/secondary press or DB | Set `null` / `"Not disclosed"` | Guessing round size or stage |

---

## 🚩 Automatic Disqualification (Exclude Entire Company)

Exclude a startup immediately if any of the following are true:
- 🚩 Company website is dead, parked, returns 404, or has an expired SSL error.
- 🚩 Website is an unedited generic template with stock photos, lorem ipsum, or fake testimonials.
- 🚩 Zero real humans identifiable as founders or active leaders.
- 🚩 Founder profiles show no real history or have identical duplicates across multiple unrelated entities.
- 🚩 Startup claims major funding rounds with zero press coverage, no Crunchbase presence, and no accelerator records.
- 🚩 Suspicious business models: multi-level marketing, pay-to-apply schemes, or known scams.
