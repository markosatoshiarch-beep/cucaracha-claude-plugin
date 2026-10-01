# Cucaracha for Claude

Cucaracha helps founders and teams engage with relevant conversations on X and LinkedIn. This Claude plugin connects to the hosted Cucaracha MCP server so an authenticated user can review existing actionable queue items, generate and save contextual reply drafts, inspect their reply persona, and safely manage supported provider settings from a conversation.

## What the plugin does

- Reads existing actionable X or LinkedIn queue items.
- Generates and saves one contextual reply draft for a selected queue item.
- Reads safe provider operating settings, including the reply persona.
- Updates supported provider settings only after the user reviews and approves the proposed change.

## Important limitations

Reading the queue does not run or refresh discovery. Generating a reply saves a draft and does not by itself prove that anything was published. The connector cannot connect or disconnect social accounts, authorize credentials, or expose tokens and private account data.

## Install and connect

After adding the plugin in Claude, open its **Connectors** tab and connect Cucaracha. Authentication is handled by the hosted Cucaracha service. Do not put API keys or access tokens into the plugin files.

Example requests:

- “Show me the five newest items in my Cucaracha X queue.”
- “Choose the best item from my X queue and draft a relevant reply.”
- “Show my current LinkedIn reply persona.”
- “Propose a safer Human-in-the-loop configuration, but do not change anything yet.”

## Safety

The plugin requires explicit confirmation before consequential settings changes such as enabling Autopilot, increasing posting frequency, or changing discovery targets. The default workflow treats generated content as a draft until publication is independently confirmed.

## Links

- Product: https://cucaracha.ai
- Privacy: https://cucaracha.ai/privacy
- Terms: https://cucaracha.ai/terms
- Safety: https://cucaracha.ai/safety
- Support: mailto:hello@cucaracha.ai
