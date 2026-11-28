---
name: make-clip
description: "Make a small custom clip with EditKitz: a film leader countdown, number counter, search bar typing animation, bar chart race, notification popup or text message chat. Use when the user asks for one of these clips or an animation like them."
---

# Make a clip with EditKitz

EditKitz renders clips in the user's own browser. You cannot produce the video file: you prefill a Tool and give the user a link.

1. Pick the Tool that matches the request. Each is an MCP tool from the `editkitz` server:
   - `create_film_leader_countdown`: old film countdown with grain and scratches.
   - `create_number_counter_animation`: a number counting from one value to another.
   - `create_search_bar_typing_animation`: a query (or several) typed into a search bar, with key and click sounds and an optional results page.
   - `create_bar_chart_race`: bars racing over time, with rank numbers, an axis, logos, bar styles and step sounds.
   - `create_notification_popup_animation`: a phone-style notification sliding in.
   - `create_text_message_chat_maker`: a one-on-one or group text conversation appearing bubble by bubble, with typing dots, voice notes, pictures, reactions, read receipts and sounds.
2. Before calling, load that tool's input schema so you know the exact option names, types and ranges. Map every detail the user gave to an option: "a 10 second countdown with heavy grain" means `start` 10 and `grain` "high". Never call a tool with empty arguments when the user asked for anything specific, because the link would open with the defaults. Leave out only the options the user did not mention; each has a default.
3. If the call returns an "Invalid options" error, fix the named option using the range in the message and call again.
4. Reply with the returned link on a line of its own, or as a short markdown link such as `[Open the countdown](url)`. A long URL inside a sentence wraps in a terminal and then only part of it is clickable. Tell the user to open it, check the preview and press **Export** to download the MP4.

For a text message chat, pass the whole conversation in the `chat` option: one line per message, each starting with `<` for the left speaker or `>` for the right speaker (the user, "You"), then the text. It is for story content, so write the conversation the user asked for.

- **Group chat:** pass the other people's names in `group`, separated by `|` (up to 3, for example `Ben|Cara`). Put a digit 1 to 3 before `<` to pick who says a line: `2<Hi!` is the second member. No digit means the main speaker (`left`).
- **Tokens** go after the marker and before the text: `[v:7]` a voice note of 7 seconds, `[img]` a picture, `[r:👍]` a reaction (one of ❤️ 👍 😂 😮 😢 🔥), `[d:2.5]` seconds to wait before the message (0 to 10). A voice note or picture has no text. A text that starts with `[` or `\` needs a `\` in front.
- Example: `<Are you there?` then `2<[v:5]` then `>[r:👍][d:1]Yes, what's up?`
- Other options: `receipts` (Delivered then Read, on by default), `send` and `receive` (sound ids, or `off`), `look` (light, dark, blush, ocean, forest), `shape`, `frame` and `status` (phone frame and status bar).
- The chat can run up to 5 minutes.

For a bar chart race, the link sets the look, timing and text. It carries **no data**: the page shows the user's own saved table, or sample data about video editing apps. So set `title` to match the user's subject, and tell them to add their data on the page (type it, paste it, or import CSV or Excel).

- **Chart:** `bars` (how many show), `order` (`largest`, `smallest` or `table`), `ranks` and `axis` (true or false), `max` (a fixed full-width value, 0 to follow the leader), `ease`.
- **Words and numbers:** `title`, `sub` (a second line), `src` (a source credit), `pre`, `suf`, `dec`, `sep`, `abbr` (true shows 1.2M).
- **Look:** `shape` (`soft`, `square`, `pill`), `fill` (`solid`, `gradient`), `names` (`side`, `above`, `inside`), `pal` (`contrast` is color-safe, `mono` is slate grays, `neon` suits dark backgrounds).
- **Highlight:** `hl` takes one item's name. Use it only when you know the name is in the user's table, or the sample data if they want a demo.
- **Sound:** `tick` (`off`, `tick`, `pop`, `blip`) plays each time the step changes.
- **Only on the page:** the table itself, a color or logo for each item, seconds for a single step, the user's own step sound and music, and undo, reordering and CSV export. Negative values work in the table.

Do not promise a finished video, and do not invent options the schema does not list. Icons, images and audio that need an upload are not available through this server. For the text message chat that means pictures in messages, avatar pictures, own sounds and the audio of voice notes; for the search bar typing it means own key and click sounds; for the bar chart race, logos, the user's own step sound and music. A picture message in a link shows a stand-in, and a voice note is silent until the user uploads the audio on the page (it stays in their browser). For the film leader countdown that means a background image (one, or one per count) and the user's own audio: set the background color and the built-in sound through the options, and tell the user to open the link and upload their own image or audio on the page (it stays in their browser). The countdown also has `num`, `cross` and `circles` options to hide the big number, the crosshair and the two circles.
