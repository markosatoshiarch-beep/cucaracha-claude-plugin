# Cucaracha: Automated Replies

Cucaracha automates replies on X and LinkedIn.

The Claude plugin lets you check and control that automation from a conversation: review what Cucaracha found, generate a reply, inspect your setup, and change supported targets and settings.

## Current status

The plugin bundle is built, publicly available, and passes Claude's official local validator. The remote Cucaracha MCP endpoint is configured, but public Claude account connection is not live yet: Cucaracha still needs Claude-compatible per-user OAuth. Existing personal MCP keys must not be committed to this repository or shared with Marketplace users.

## How it works

1. Choose X accounts or lists, or configure LinkedIn topics and author filters.
2. Tell Cucaracha how your replies should sound.
3. Cucaracha finds relevant posts, skips poor fits, and writes replies in your voice.
4. Review generated replies or use the supported X automation configured in your Cucaracha account.

## What you can ask Claude

- “What relevant tweets did Cucaracha find?”
- “Write a reply to the best one in my voice.”
- “Which accounts and lists am I monitoring?”
- “Show the newest LinkedIn posts in my queue and draft a reply to the best one.”
- “Show my current reply prompt, cadence, and daily limit.”
- “Change this setting after I approve the update.”

## Important limitations

Reading the queue does not itself run or refresh discovery; Cucaracha's background automation performs monitoring according to the account's configuration. A reply-generation result is not proof of publication. Claude must report a reply as published only when a dedicated connector result explicitly confirms publication. The connector can read the authenticated user's supported workflow settings, but it cannot connect or disconnect social accounts, authorize credentials, or expose account credentials, OAuth tokens, or connection secrets.

## Install and connect

After Cucaracha's OAuth flow is implemented and the plugin and connector are approved in Claude Directory, add the plugin in Claude, open its **Connectors** tab, and connect Cucaracha. Authentication will be handled by the hosted Cucaracha service. Do not put API keys or access tokens into the plugin files.

Example requests:

- “Show me how my Cucaracha X reply automation is configured.”
- “Show the five newest items Cucaracha found in my X queue.”
- “Choose the best item and generate a reply in my voice.”
- “Show which accounts and lists Cucaracha is monitoring.”
- “Propose a 30-minute Human-in-the-loop setup, but do not change anything yet.”

## Safety

The plugin requires explicit confirmation before consequential settings changes such as increasing posting frequency, changing discovery targets, or changing the operating mode. It never treats generated content as published unless the connector explicitly confirms the public action. MCP keys and account credentials must remain private.

## Links

- Product: https://cucaracha.ai
- Privacy: https://cucaracha.ai/privacy
- Terms: https://cucaracha.ai/terms
- Safety: https://cucaracha.ai/safety
- Support: mailto:hello@cucaracha.ai
