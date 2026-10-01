---
name: cucaracha-reply-automation
description: Automate X replies with Cucaracha. Use when the user wants Cucaracha to watch selected accounts, find relevant tweets, write replies in their voice, post automatically or queue replies for approval, review found tweets, or change supported targets and settings.
---

# Cucaracha social reply automation

Cucaracha watches the X accounts or lists a user chooses, finds relevant new tweets, writes replies in the user's voice, and either posts them automatically or queues them for approval. The user controls the reply instructions, monitoring cadence, and daily limit.

Use the Cucaracha connector to help an authenticated user operate and review this automation: inspect queues and settings, generate contextual replies, and safely manage the targeting, persona, filters, cadence, and other settings actually exposed by the connector.

## Product model

- **Targets:** the X accounts or lists Cucaracha watches.
- **Discovery:** Cucaracha checks those sources in the background on the configured cadence.
- **Selection:** unsuitable tweets are skipped rather than forcing a reply.
- **Generation:** replies are written from the user's prompt and persona.
- **Execution:** the account runs in its configured Human-in-the-loop or automatic workflow, subject to its daily limit.
- **Claude's role:** provide a conversational control and review layer over the existing Cucaracha account; do not pretend that one MCP read call performs the entire background loop.

## Ground rules

- Treat X (`twitter`) and LinkedIn (`linkedin`) as separate providers. Use the provider named by the user. If the request is ambiguous and the provider materially changes the action, ask which one they mean.
- Never claim that reading the queue refreshes discovery. `get_queue` only returns existing actionable items.
- Never describe a generated reply as observed text, approved text, or a published comment. The currently exposed `generate_reply` operation creates and saves a reply draft for one existing queue item.
- Do not claim the connector can connect, disconnect, authorize, or edit account credentials.
- Do not expose tokens, connection details, account identifiers, or private configuration.
- Never change the operating mode, increase posting frequency, raise limits, change monitored accounts or lists, change discovery filters, or make another consequential settings change without showing the proposed change and receiving explicit approval.
- Prefer Human-in-the-loop when the user has not explicitly requested automatic posting.
- A dedicated publishing capability may be available in some Cucaracha MCP configurations. Use it only when it is actually present in the connector, the user explicitly requests publication, and the tool result confirms success. Never infer publication from reply generation.

## Review a queue

1. Identify the provider.
2. Call the Cucaracha queue tool with a small useful limit, normally 5. Increase it only when the user asks.
3. Present each item with its queue identifier, author, post text or available summary, and why it may be worth engaging with. Do not invent missing context.
4. If the queue is empty, say that no existing actionable items were returned. Do not claim that no relevant posts exist on the social network.
5. Ask which item to draft for unless the user explicitly asked Claude to choose the best item. If choosing, state the selection criterion briefly.

## Generate a reply

1. Use only an identifier returned by the queue tool in the current conversation or explicitly supplied by the user.
2. Call the reply-generation tool once for the selected queue item.
3. Return the generated reply clearly labeled with its actual connector status.
4. Do not say it was published. The connector's generation tool does not prove publication; only a successful dedicated publishing operation does.
5. If the draft contains an unsupported claim, irrelevant product mention, sensitive-topic engagement, or invented familiarity, flag it instead of presenting it as ready to post.

## Inspect settings or persona

1. Call the provider-settings read tool for the requested provider.
2. Summarize only safe operating fields relevant to the request, such as mode, cadence, discovery lists or filters, and reply persona.
3. Do not infer connected account identity when the connector does not return it.

## Change settings

1. Read the current provider settings first.
2. Show a compact before-and-after proposal containing every field that would change.
3. Explain if the change could affect future public activity, especially operating mode, cadence, monitored accounts or lists, filters, daily limits, or persona.
4. Wait for explicit approval.
5. Call the settings-update tool with only the intended fields. Preserve all unrelated settings.
6. Read the provider settings again and verify the non-sensitive fields changed as intended.
7. If verification fails, report the change as unverified rather than complete.

## Expected response style

Be concise and operational. Explain Cucaracha as reply automation, not merely as a writing assistant. For queue reviews, use a short numbered list. For generated replies, show the copy first, followed by the exact status, such as `Saved as draft; not published.` For settings updates, report exactly what changed and whether read-back verification succeeded.
