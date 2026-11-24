# Startup Hunter — Reference: JSON Schema & Field Documentation

This file defines the complete JSON output schema for `findings/startup-outreach-data.json`.

> **Anti-Hallucination Note**: The field descriptions below define what goes in each field.
> Every value must come from live verification. If a field cannot be verified, set it to
> `null` (for strings/objects), `[]` (for arrays), or omit it. Never fill in plausible-
> sounding data from memory.

---

## Full Schema

```json
{
  "generated_at": "ISO 8601 timestamp of when this report was generated",
  "summary": {
    "total_startups": 0,
    "with_active_listings": 0,
    "cold_outreach_targets": 0,
    "funding_breakdown": {
      "pre_seed": 0,
      "seed": 0,
      "series_a": 0,
      "series_b_plus": 0,
      "bootstrapped": 0
    }
  },
  "limitations": [
    "List of sources that were blocked, logins unavailable, or data gaps"
  ],
  "startups": [
    {
      "company_name": "Official company name verified on live website",
      "one_liner": "Copied or closely paraphrased from company's live homepage/about page",
      "website": "Verified live URL — must have been visited and confirmed active",
      "verified_via": "Primary source where company was discovered/verified (e.g. 'YC directory', 'Crunchbase')",
      "confidence": "high or medium — high = 2+ sources confirm, medium = single source",
      "industry": "Industry from company's own description, not inferred",
      "founded": null,
      "location": "Verified city, country or 'Remote' — null if unconfirmed",
      "team_size": null,
      "funding_stage": "Verified stage or null if unconfirmed",
      "total_raised": "Verified amount or null if unconfirmed",
      "last_funded": "Verified date or null if unconfirmed",
      "key_investors": [],
      "tech_stack": [],
      "match_reason": "Must cite a specific verified data point. E.g. 'Uses React per their careers page listing' — NOT inferred from company name",
      "careers_page": null,
      "linkedin_url": null,
      "crunchbase_url": null,
      "wellfound_url": null,
      "active_job_listings": [],
      "has_public_listings": false,
      "status": "pending",
      "contacts": [
        {
          "name": "Verified full name of a current decision-maker",
          "title": "Exact current title verified on live profile or team page",
          "outreach_angle": "Must reference only: (a) person's verified title, (b) skills from candidate's actual resume. Never introduce skills not in the resume.",
          "verified_via": "Source where current role was confirmed (e.g. 'LinkedIn profile', 'Company /team page', 'The Org')",
          "linkedin": "Verified live LinkedIn profile URL — null if not found",
          "twitter": null,
          "email": null,
          "email_source": "Where the email was found (e.g. 'Company contact page', 'Press release') — null if no email",
          "notes": "Verified background info or null",
          "status": "pending"
        }
      ]
    }
  ]
}
```

---

## Field Rules Quick Reference

| Field | Required | Nullable | Anti-Hallucination Rule |
|-------|----------|----------|------------------------|
| `company_name` | Yes | No | Must match official name on live website |
| `one_liner` | Yes | No | Copy/paraphrase from live homepage — never from memory |
| `website` | Yes | No | Must have been visited and confirmed live. Dead site = exclude company |
| `verified_via` | Yes | No | Name the source. If you can't name a source, the data is from memory — omit it |
| `confidence` | Yes | No | `"high"` = 2+ sources agree; `"medium"` = single source only |
| `industry` | Yes | No | From company's own description, not inferred from name |
| `founded` | No | Yes | Verified year or `null` |
| `location` | No | Yes | Verified location or `null` |
| `team_size` | No | Yes | Verified count or `null` |
| `funding_stage` | No | Yes | Verified stage or `null` |
| `total_raised` | No | Yes | Verified amount or `null` |
| `last_funded` | No | Yes | Verified date or `null` |
| `key_investors` | No | — | Verified list or `[]` |
| `tech_stack` | No | — | Only from careers page, job posts, GitHub, StackShare. Never inferred. `[]` if unconfirmed |
| `match_reason` | Yes | No | Must cite specific verified source — not "seems like a good fit" |
| `careers_page` | No | Yes | Verified live URL or `null` — never guess `/careers` |
| `linkedin_url` | No | Yes | Verified live URL or `null` — never construct from name |
| `contacts[].name` | Yes | No | Verified current decision-maker |
| `contacts[].title` | Yes | No | Exact current title from live profile |
| `contacts[].outreach_angle` | Yes | No | Only reference verified title + resume skills |
| `contacts[].verified_via` | Yes | No | Name the source where you confirmed current role |
| `contacts[].linkedin` | No | Yes | Verified live URL or `null` |
| `contacts[].email` | No | Yes | Explicitly published in plain text or `null` — **NEVER GUESS** |
| `contacts[].email_source` | No | Yes | Where email was found, or `null` |
| `status` | Yes | No | Always `"pending"` on initial generation |
