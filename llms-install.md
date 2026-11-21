# Installing formtango-mcp (for AI agents)

formtango-mcp is a local MCP server for FormTango, a form backend. It runs with `npx` and needs Node.js 18 or later. Nothing has to be cloned or built.

## 1. Add the server to the MCP settings

```json
{
  "mcpServers": {
    "formtango": {
      "command": "npx",
      "args": ["-y", "formtango-mcp"]
    }
  }
}
```

That is the whole install. No API key is required to start.

## 2. Check that it works

The server should list six tools. Call `create_form_without_account` with a name, for example `{"name": "Install check"}`. It returns a working form `endpoint` and a `claimUrl`. No account or key is involved.

## 3. Optional: connect an account

To list an existing account's forms and read submissions, the user creates an API key at https://formtango.com/app/account and it is passed as an environment variable. Ask the user for the key; do not invent one.

```json
{
  "mcpServers": {
    "formtango": {
      "command": "npx",
      "args": ["-y", "formtango-mcp"],
      "env": { "FORMTANGO_API_KEY": "<the user's key>" }
    }
  }
}
```

Without a key, `create_form_without_account` still works. The other tools (`list_forms`, `create_form`, `get_form_snippet`, `list_submissions`, `get_account`) return a message asking for a key.

## Troubleshooting

- `npx` not found: install Node.js from https://nodejs.org.
- "No matching version found": clear the npm cache with `npm cache clean --force` and try again.
- More: https://formtango.com/ai.md
