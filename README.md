# EditKitz MCP

Make clips with [EditKitz](https://editkitz.com), the free browser clip maker, from your AI assistant. The assistant fills in a Tool (film leader countdown, number counter, search bar typing, bar chart race, notification popup, text message chat) and gives you a link; you open it and press Export. The video is rendered in your browser, with no account.

The MCP server is hosted by EditKitz at:

```
https://editkitz.com/mcp
```

Full docs: https://docs.editkitz.com

## Claude Code

Install the plugin, which adds the server and a skill that picks the right Tool:

```
/plugin marketplace add AshuJojo/editkitz-mcp
/plugin install editkitz --marketplace AshuJojo/editkitz-mcp
```

Or add only the server:

```
claude mcp add --transport http editkitz https://editkitz.com/mcp
```

## Other clients

Add `https://editkitz.com/mcp` as a remote (Streamable HTTP) MCP server or custom connector in ChatGPT, Claude or the OpenAI Agents SDK. No sign-in or API key is needed. See the [connect guide](https://docs.editkitz.com/connect).

This repository holds the Claude Code plugin and marketplace only. The server itself is part of the EditKitz site.
