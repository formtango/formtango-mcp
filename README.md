# formtango-mcp

An MCP server that lets an AI assistant add a working form to a website and read what people submit.

[FormTango](https://formtango.com) is a form backend: a form posts to one address, and every submission is stored, checked for spam and emailed to you. No server code.

**Works with no setup.** Without an account or key, the assistant can create a live form endpoint and hand you a link to claim it.

## Install

Add to your MCP settings (Claude Desktop, Cursor, Windsurf, VS Code and others):

```json
{
  "mcpServers": {
    "formtango": { "command": "npx", "args": ["-y", "formtango-mcp"] }
  }
}
```

Claude Code:

```bash
claude mcp add formtango -- npx -y formtango-mcp
```

Then ask: "Add a contact form to this site."

### With your account (optional)

To list your forms and read submissions, create an API key under Account at https://formtango.com and add it:

```json
{
  "mcpServers": {
    "formtango": { "command": "npx", "args": ["-y", "formtango-mcp"], "env": { "FORMTANGO_API_KEY": "ft_..." } }
  }
}
```

A read-only key is enough for everything except `create_form`.

## Tools

| Tool | Needs a key | What it does |
| --- | --- | --- |
| `create_form_without_account` | no | Creates a working form endpoint and a link to claim it |
| `get_form_snippet` | yes | Code for HTML, fetch, React, Next.js, Astro, Vue or Svelte |
| `list_forms` | yes | Your forms |
| `create_form` | yes (write) | Creates a form in your account |
| `list_submissions` | yes | Recent submissions of a form |
| `get_account` | yes | Plan and usage |

## Prefer nothing to install?

There is also a hosted server with sign-in at `https://formtango.com/mcp`. See https://github.com/formtango/mcp.

## Privacy

This server talks only to formtango.com. Your API key stays on your machine and is sent only to FormTango. Privacy policy: https://formtango.com/privacy

## License

MIT
