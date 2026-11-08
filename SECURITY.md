# Security

This private repository contains a sanitized workflow export. Access should be limited to project maintainers.

- The committed JSON replaces four embedded API key locations with `REPLACE_WITH_API_KEY` and clears pinned execution data.
- Restore keys only inside n8n. Prefer managed credentials or supported secret expressions when editing the live workflow.
- Do not commit lead records, webhook secrets, provider tokens, or execution logs.
- If a secret is accidentally committed, rotate it at the provider and remove it from repository history; deleting the latest line alone is insufficient.
- Keep the repository private unless the complete workflow has been reviewed for public release.
