[![Influence](assets/influence-symbol.svg)](https://influence.so)

# Influence

Draft, review and schedule social posts through your Influence workspace. Use saved brand guidance, revise posts for your connected accounts, choose saved images, and review the exact content before approving publication or a schedule change. Check each destination's delivery status and verified published link, and read available account and post Insights.

## Connect

1. Add the Influence plugin in Claude, then open its **Connectors** tab.
2. Add or connect the Influence connector and sign in to Influence through the OAuth window.
3. Choose the workspace and permissions you want to grant. Return to Claude after completing consent.

On Team and Enterprise plans, an Owner adds the connector for the organization before members connect their own accounts. Adding the plugin loads its instructions; account access begins only after you connect and authorize Influence.

The remote Streamable HTTP endpoint is `https://influence.so/api/mcp/claude`. The plugin uses OAuth. No API key, environment variable, local server or install script is required. Disconnect or revoke the grant when you no longer want Claude to access your workspace.

## Try it

- “Show my connected accounts and which can publish text or an image.”
- “Prepare an editable draft for the accounts I select, using my saved brand guidance.”
- “Find a saved image for this post and show me the review.”
- “Move this scheduled post to tomorrow at 10:00 in Asia/Bangkok, then show me the change for approval.”
- “Show the publishing status and available Insights for my connected accounts.”

Features follow your granted permissions, connected accounts and their supported formats. Connect accounts and upload new media in Influence. A device or chat attachment is not automatically uploaded by this plugin.

## Review and approval

Claude shows the complete server-derived review before asking you to approve publication or a schedule change. Review text, destination accounts, settings and time before giving a fresh approval. Image posts require signed-in visual review in Influence. Editing any reviewed field requires a new review and approval.

Accepted or scheduled work is not proof of publication. Delivery can differ by destination; a result that needs review must be reconciled before another send. Missing Insights remain unavailable or unknown rather than zero.

Text campaign planning uses Influence IQ credits and requires confirmation before spending them. Saved-image selection does not grant publishing approval. This directory package does not offer image or video generation.

## Account, pricing and help

An Influence account and authorized workspace are required. This connector is free; the hosted Influence service uses a paid subscription. Its seven-day trial requires a payment method and starts the selected subscription after the trial unless you cancel before it ends. Claude subscriptions and Influence IQ credits have their own terms. Review current plans on the [Influence website](https://influence.so).

[How Influence works](https://influence.so/how-it-works) · [Privacy](https://influence.so/privacy) · [Terms](https://influence.so/terms) · [Support](https://influence.so/support)

Contact [hello@influence.so](mailto:hello@influence.so). Influence is operated by Centoria Gate Holdings Limited.

## License and branding

The connection configuration, customer skill and documentation are released under [MIT-0](LICENSE). Files under `assets/`, including the Influence logo, are excluded; see [brand use](BRAND-USAGE.md). The license does not cover the hosted application or grant access to customer data or paid service features.
