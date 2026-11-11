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

**2026-11-11 — engine checked against the live connector tools.** Findings, all now
reflected in `project-instructions.md` and the session walkthrough:

- Search is one tool: a plain-language description plus two filters, BPM range and
  loop/one-shot. Key, duration and dry/wet go in the description and get checked at triage.
- Splice requires every search result to be shown, numbered, unfiltered and unreordered.
  Triage now marks each result likely-yes / maybe / ruled-out instead of hiding any.
- First download of a sound costs one credit; re-downloads are free. So duplicates cost
  library space, not credits, and the commit-boundary cost is the count of new sounds.
- Splice can't report what you already own. Duplicate checks depend on your own manifest.
- A download returns a quickly expiring link, not a saved file. Saving to disk depends
  on the client; otherwise links are shown at once with filenames.
- Stack tools exist (multi-layer arrangements). The engine keeps them off unless asked,
  since they lean toward finished-sounding combinations.

## Source of truth

- Splice MCP server setup: https://splice.com/tools/mcp-server
- Splice MCP announcement: https://splice.com/blog/splice-sounds-in-claude-mcp/
- How credits work: https://support.splice.com/en/articles/8652639-how-do-credits-work
