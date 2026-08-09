# Compatibility notes

The Splice MCP connector is officially provided by Splice and is currently in **beta**.
That means its exact set of tools, their names, and their behavior may change without
notice.

This framework is deliberately written around **intent** rather than specific tool
mechanics:

> search by feel → triage → audition → confirm at a commit boundary → download

As long as the connector can search the catalog by natural language and download with
credits, the framework holds. If a specific tool behaves differently than expected, fall
back to the intent of the relevant beat and tell the user what changed.

## Change log

Add dated entries here as you notice connector changes.

```
YYYY-MM-DD — (what changed, and how the framework adapts)
```

## Source of truth

- Splice MCP server setup: https://splice.com/tools/mcp-server
- Splice MCP announcement: https://splice.com/blog/splice-sounds-in-claude-mcp/
- How credits work: https://support.splice.com/en/articles/8652639-how-do-credits-work
