# Operations

## Flow

The webhook routes requests into a web-search path or an Apollo path. Both paths gather lead data, remove duplicates, validate details, write records to Airtable, and return a response to the caller.

## Routine checks

- Inspect recent n8n executions for Firecrawl, Reoon, Apollo, and Airtable failures.
- Compare reported counts with Airtable records; check both valid and invalid branches.
- Watch API quotas, rate limits, and paid-credit usage before increasing batch sizes.
- Check that the deduplication nodes still use the intended identifiers after schema changes.
- Validate webhook responses after edits to any branch.

## Common issues

| Symptom | Check |
| --- | --- |
| Search returns no leads | Search variations, Firecrawl credential, and source-site responses. |
| Apollo branch fails | Both Apollo API header placeholders, request limits, and account credits. |
| Email verification fails | Reoon key in **Verify Email1** and service quota. |
| Duplicate or missing records | Deduplication nodes, Airtable table mappings, and field names. |
| Webhook times out | Long-running loops, wait nodes, and response routing. |

When refreshing this repository, export the current workflow, remove secret values and pinned execution data, then commit the new JSON with a concise change note.
