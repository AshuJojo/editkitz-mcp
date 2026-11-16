# EditKitz plugin for Claude Code

Make short custom clips with [EditKitz](https://editkitz.com), the free clip maker that runs in your browser. This plugin connects Claude to the EditKitz MCP server and adds a skill that picks the right tool for your request. Claude fills in the tool and gives you a link. You open the link, check the preview and press Export to download the MP4. The clip is made in your own browser, so nothing is uploaded and no account is needed.

## What you get

- **The EditKitz MCP server**, a remote server at `https://editkitz.com/mcp` with one tool for each EditKitz clip maker: film leader countdown, number counter, search bar typing, bar chart race and notification popup.
- **The `make-clip` skill**, which maps what you ask for to the right tool and its options, and returns the prefilled link.

## Install

```
/plugin marketplace add AshuJojo/editkitz-mcp
/plugin install editkitz --marketplace AshuJojo/editkitz-mcp
```

## Try it

Ask: "Make a 10 second film leader countdown with heavy grain." Claude answers with a link to the Film Leader Countdown Maker, already set up. Open it and press Export.

## Privacy and limits

The server only builds a link from the options Claude sends. It needs no sign-in, stores nothing and keeps no sessions. Options that need a file upload, such as custom icons or images, are not available. See the [privacy policy](https://editkitz.com/privacy) and the [documentation](https://docs.editkitz.com).
