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

2. **Gather issue details** - For each issue number, fetch details from GitHub:
   `https://api.github.com/repos/QualityUnit/PostAffiliatePro/issues/{number}`

3. **Organize into sections** following this structure:
   - ## New Features (if any)
   - ## Improvements
   - ## Bug Fixes
   Each section should have subsections grouped by area (e.g., ### Security, ### REST API v3, ### User Interface, ### Banners, ### Integrations, ### Affiliate Panel, ### Network, etc.)

4. **Format each item** as:
   `- **Bold Title** - Brief description (#issue_number)`

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