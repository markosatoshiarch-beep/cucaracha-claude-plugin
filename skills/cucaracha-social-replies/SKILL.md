---
name: cucaracha-social-replies
description: Review and draft replies for a user's Cucaracha X or LinkedIn queue, inspect the reply persona, or safely change Cucaracha provider settings. Use when the user mentions Cucaracha, their social reply queue, drafting replies to queued posts, reply persona, target lists, discovery filters, cadence, Human-in-the-loop, or Autopilot.
---

# Cucaracha social replies

Use the Cucaracha connector to help an authenticated user review existing queue items, generate contextual reply drafts, and manage provider settings safely.

## Ground rules

- Treat X (`twitter`) and LinkedIn (`linkedin`) as separate providers. Use the provider named by the user. If the request is ambiguous and the provider materially changes the action, ask which one they mean.
- Never claim that reading the queue refreshes discovery. `get_queue` only returns existing actionable items.
- Never describe a generated reply as observed text, approved text, or a published comment. `generate_reply` creates and saves a draft for one existing queue item.
- Do not claim the connector can connect, disconnect, authorize, or edit account credentials.
- Do not expose tokens, connection details, account identifiers, or private configuration.
- Never enable Autopilot, increase posting frequency, raise limits, change discovery targets, or make another consequential settings change without showing the proposed change and receiving explicit approval.
- Prefer Human-in-the-loop when the user has not explicitly requested automatic posting.

## Review a queue

1. Identify the provider.
2. Call the Cucaracha queue tool with a small useful limit, normally 5. Increase it only when the user asks.
3. Present each item with its queue identifier, author, post text or available summary, and why it may be worth engaging with. Do not invent missing context.
4. If the queue is empty, say that no existing actionable items were returned. Do not claim that no relevant posts exist on the social network.
5. Ask which item to draft for unless the user explicitly asked Claude to choose the best item. If choosing, state the selection criterion briefly.

## Generate a reply draft

1. Use only an identifier returned by the queue tool in the current conversation or explicitly supplied by the user.
2. Call the reply-generation tool once for the selected queue item.
3. Return the saved draft clearly labeled as a draft.
4. Do not say it was published. The connector's generation tool does not prove publication.
5. If the draft contains an unsupported claim, irrelevant product mention, sensitive-topic engagement, or invented familiarity, flag it instead of presenting it as ready to post.

## Inspect settings or persona

1. Call the provider-settings read tool for the requested provider.
2. Summarize only safe operating fields relevant to the request, such as mode, cadence, discovery lists or filters, and reply persona.
3. Do not infer connected account identity when the connector does not return it.

## Change settings

1. Read the current provider settings first.
2. Show a compact before-and-after proposal containing every field that would change.
3. Explain if the change could affect future public activity, especially Autopilot, cadence, targets, filters, or persona.
4. Wait for explicit approval.
5. Call the settings-update tool with only the intended fields. Preserve all unrelated settings.
6. Read the provider settings again and verify the non-sensitive fields changed as intended.
7. If verification fails, report the change as unverified rather than complete.

## Expected response style

Be concise and operational. For queue reviews, use a short numbered list. For generated replies, show the draft first, followed by a one-line status such as `Saved as draft; not published.` For settings updates, report exactly what changed and whether read-back verification succeeded.
