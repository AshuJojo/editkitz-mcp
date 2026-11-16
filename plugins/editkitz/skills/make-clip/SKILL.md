---
name: make-clip
description: "Make a small custom clip with EditKitz: a film leader countdown, number counter, search bar typing animation, bar chart race or notification popup. Use when the user asks for one of these clips or an animation like them."
---

# Make a clip with EditKitz

EditKitz renders clips in the user's own browser. You cannot produce the video file: you prefill a Tool and give the user a link.

1. Pick the Tool that matches the request. Each is an MCP tool from the `editkitz` server:
   - `create_film_leader_countdown`: old film countdown with grain and scratches.
   - `create_number_counter_animation`: a number counting from one value to another.
   - `create_search_bar_typing_animation`: a query typed into a search bar.
   - `create_bar_chart_race`: bars racing over time.
   - `create_notification_popup_animation`: a phone-style notification sliding in.
2. Call it with only the options the user asked for. Every option is optional and has a default; read the tool's input schema for names and ranges.
3. If the call returns an "Invalid options" error, fix the named option using the range in the message and call again.
4. Reply with the returned link and tell the user to open it, check the preview and press **Export** to download the MP4.

Do not promise a finished video, and do not invent options the schema does not list. Icons and images that need an upload are not available through this server.
