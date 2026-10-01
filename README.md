# Cucaracha: X Reply Automation for Claude

Cucaracha watches the X accounts you choose, finds relevant new tweets, writes replies in your voice, and either posts them automatically or lets you approve them first.

The Claude plugin lets you check and control that automation from a conversation: review what Cucaracha found, generate a reply, inspect your setup, and change supported targets and settings.

## How it works

1. Pick the X accounts or lists you want to engage with.
2. Tell Cucaracha how your replies should sound.
3. Cucaracha checks for new tweets, skips poor fits, and writes relevant replies.
4. Approve replies yourself or let Cucaracha post them automatically, within your daily limit.

## What you can ask Claude

- “What relevant tweets did Cucaracha find?”
- “Write a reply to the best one in my voice.”
- “Which accounts and lists am I monitoring?”
- “Show my current reply prompt, cadence, and daily limit.”
- “Change this setting after I approve the update.”

## Important limitations

Reading the queue does not itself run or refresh discovery; Cucaracha's background automation performs monitoring according to the account's configuration. A reply-generation result is not proof of publication. Claude must report a reply as published only when a dedicated connector result explicitly confirms publication. The connector cannot connect or disconnect social accounts, authorize credentials, or expose tokens and private account data.

## Install and connect

After adding the plugin in Claude, open its **Connectors** tab and connect Cucaracha. Authentication is handled by the hosted Cucaracha service. Do not put API keys or access tokens into the plugin files.

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
