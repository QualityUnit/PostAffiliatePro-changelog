Create a changelog MD file for Post Affiliate Pro release version: $ARGUMENTS

## Steps

1. **Create the file** `_posts/{today's date}-{version}.md` with frontmatter:
   ```
   ---
   layout: post
   title: {version}
   author: mkendera
   tags: [pap,Post Affiliate Pro,{version}]
   ---
   ```

2. **Fetch issues for the milestone** using the GitHub Search API via `gh`:
   ```
   gh api "search/issues?q=repo:QualityUnit/PostAffiliatePro+is:closed+milestone:{version}+-project:qualityunit/38&per_page=100&page={page}" --jq '.items[] | {number, title, labels: [.labels[].name]}'
   ```
   - Paginate: keep incrementing `page` until fewer than 100 results are returned
   - Exclude issues belonging to GitHub project `qualityunit/38` (the `-project:qualityunit/38` filter)

3. **Categorize each issue by its first matching label** (check in this order):
   - `type: security` → Security (**special handling**, see Security Rules below)
   - `type: feature` → New Feature
   - `type: improvement` → Improvement
   - `type: plugin` → Plugin
   - `type: styling` → Style
   - `type: performance` or `type:performance` → Performance
   - `type: refactoring` or `type: technical` → **Skip** (these are internal infrastructure/code changes not relevant to customers; only include if the change has clear customer-facing impact)
   - No matching label → Bug Fix

4. **Organize into sections** following this structure:
   - ## New Features (if any)
   - ## Improvements
   - ## Bug Fixes
   Each section should have subsections grouped by area (e.g., ### Security, ### REST API v3, ### User Interface, ### Banners, ### Integrations, ### Affiliate Panel, ### Network, etc.)
   
   Map categories to sections:
   - Security, New Feature → ## New Features (or ## Security if only security items)
   - Improvement, Performance, Style → ## Improvements
   - Bug Fix, Plugin → ## Bug Fixes (unless they clearly fit elsewhere)

5. **Format each item** as:
   `- **Bold Title** - Brief description (#issue_number)`

## Security Rules

Security issues require careful handling — **never disclose vulnerability details publicly**.

- **Theoretical / internal hardening** (e.g., upgrading a library, adding input validation where no exploit was known): **Skip entirely** — these are internal improvements, not customer-facing changes.
- **Real vulnerability that was fixed**: Include, but use only vague, general language. Do NOT reveal:
  - The attack vector or how it could be exploited
  - Specific endpoints, parameters, or components affected
  - CVE numbers or severity scores
  - Technical details of the fix
  
  Good example: `- **Security Improvement** - Improved input sanitization in the merchant panel (#1234)`
  Bad example: `- **XSS Fix** - Fixed stored XSS vulnerability in the campaign name field that allowed script injection via the REST API (#1234)`

- **When unsure** whether a security issue is theoretical or real, **ask before including it**.

## Writing Rules

- 1-2 sentences max per item (one sentence is best)
- Focus on WHAT changed and customer impact, not HOW it was implemented
- Avoid technical implementation details

### DO NOT include:
- Class names (e.g., Pap_Signup_SetParentToAffiliate)
- CSS classes (e.g., IconObjectBlock3, flexPanel)
- Database table names
- Variable names
- Method names
- HTTP status codes
- Redundant phrases like "making it easier to", "providing complete", "ensuring better"

### Good vs Bad examples:

BAD: "The system now properly logs when the background task `Pap_Signup_SetParentToAffiliate` recognizes and assigns a parent affiliate from visitor data, providing complete audit trail for affiliate relationships"

GOOD: "Fixed missing audit log entries when parent affiliates are automatically assigned from cookies after signup"

## Reference

Use the most recent changelog file in `_posts/` as a style reference for formatting and tone.

## After creating

- If you are not sure about any issue, ask before finalizing
- Present the result for review before committing