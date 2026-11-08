# Setup

## Requirements

- n8n with Airtable and Firecrawl nodes available.
- Airtable credential with access to the Example Brand base. The export points to base `appWzgzC0MmOvHTg8`; its web and Apollo branches use tables `tblYPo5OmMZYRy1y8` and `tblnlqNdqg0tfwdhF`.
- Firecrawl, Reoon email verification, and Apollo credentials.

## Import

1. Create an inactive workflow in n8n and import [`../workflow.json`](../workflow.json).
2. Reconnect the Airtable credentials on all Airtable nodes and the Firecrawl credential on **Search the web and scrape results**.
3. Replace each `REPLACE_WITH_API_KEY` placeholder inside n8n:

| Node | Field | Service |
| --- | --- | --- |
| Extract Lead Info1 | `Authorization` request header | Firecrawl |
| Verify Email1 | `key` URL parameter | Reoon |
| Apollo People Search | `X-Api-Key` request header | Apollo |
| Apollo Reveal Person | `X-Api-Key` request header | Apollo |

4. Check webhook paths, response nodes, Airtable table and field mappings, Firecrawl limits, and Apollo request settings for the target environment.
5. Test each branch with a small controlled query. Confirm deduplication and inspect valid/invalid Airtable records before activation.

Never put real API keys back into a committed JSON export. Prefer n8n credentials or supported secret expressions when changing the workflow.

The exported `active` field reflects the source workflow. Do not activate an imported copy alongside the original without checking for duplicate processing.
