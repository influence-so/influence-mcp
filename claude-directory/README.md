[![Influence](assets/influence-symbol.svg)](https://influence.so)

# Influence

Draft, review and schedule social posts with saved images and videos, brand guidance and available Insights. Revise posts for your connected accounts and review the exact content before approving publication or a schedule change. Check each destination's delivery status and verified published link.

## Connect

1. In Claude on the web or desktop, open **Customize → Connectors → Add → Custom → Web**.
2. Name the connector **Influence** and enter `https://influence.so/api/mcp/claude`. Choose **Sign in now** and, under **OAuth client**, **Register automatically**.
3. Sign in to Influence, review the workspace, permissions and access duration, then complete consent and return to Claude.

On Team and Enterprise plans, an Owner adds the connector for the organization before members connect their own accounts. See [Claude's custom connector setup](https://support.claude.com/en/articles/11175166-get-started-with-custom-connectors-using-remote-mcp) for current account and administrator requirements.

The remote Streamable HTTP endpoint is `https://influence.so/api/mcp/claude`. The plugin uses OAuth. No API key, environment variable, local server or install script is required. Disconnect or revoke the grant when you no longer want Claude to access your workspace.

### Cowork and Claude Code

Use the connector from the same Claude account in Cowork. Claude Code can also use account connectors when signed in with that Claude subscription; use `/mcp` to inspect the connection. This account reuse is unavailable when Claude Code uses an API key, Bedrock or Vertex AI credentials instead.

If you need to configure the remote connector directly in Claude Code, use its native HTTP setup and complete the OAuth sign-in shown by `/mcp`:

```sh
claude mcp add --transport http influence https://influence.so/api/mcp/claude
```

See [Claude Code's MCP documentation](https://code.claude.com/docs/en/mcp). The separate [community marketplace package](../README.md#claude-code) uses the full Influence endpoint and a scoped API key; its installation is a different connection path.

## Try it

- “Show my connected accounts and their supported post formats.”
- “Prepare an editable draft for the accounts I select, using my saved brand guidance.”
- “Find saved images and videos for this post and show me the review.”
- “Move this scheduled post to tomorrow at 10:00 in Asia/Bangkok, then show me the change for approval.”
- “Show the publishing status and available Insights for my connected accounts.”

This plugin provides the core draft, review, saved-media, brand, Insights and text-planning workflow. Complete exact community, board, channel, messaging recipient/template and other native destination selections in signed-in Influence. Those selections still need a complete review and fresh approval before delivery.

Features follow your granted permissions, connected accounts and their supported formats. Connect accounts and upload new media in Influence. A device or chat attachment is not automatically uploaded by this plugin.

Use images and videos from your Influence media library for galleries, Stories,
Reels and other formats supported by the selected account. TikTok inbox uploads
finish in TikTok; Direct posts finish their posting choices in Influence.

## Review and approval

Claude shows the complete server-derived review before asking you to approve publication or a schedule change. Review text, destination accounts, settings and time before giving a fresh approval. Images and videos require signed-in visual review in Influence. Editing any reviewed field requires a new review and approval.

Accepted or scheduled work is not proof of publication. Delivery can differ by destination; a result that needs review must be reconciled before another send. Missing Insights remain unavailable or unknown rather than zero. Refreshing Insights reads the provider and updates the owned cache; a queued refresh is not a completed refresh.

Text campaign planning uses Influence IQ credits and requires confirmation before spending them. Saved-media selection does not grant publishing approval. Use Influence IQ in signed-in Influence to generate images.

## Account, pricing and help

An Influence account and authorized workspace are required. This connector is free; the hosted Influence service uses a paid subscription. Its seven-day trial requires a payment method and starts the selected subscription after the trial unless you cancel before it ends. Claude subscriptions and Influence IQ credits have their own terms. Review current plans on the [Influence website](https://influence.so).

[How Influence works](https://influence.so/how-it-works) · [Privacy](https://influence.so/privacy) · [Terms](https://influence.so/terms) · [Support](https://influence.so/support)

Contact [hello@influence.so](mailto:hello@influence.so). Influence is operated by Centoria Gate Holdings Limited.

## License and branding

The connection configuration, customer skill and documentation are released under [MIT-0](LICENSE). Files under `assets/`, including the Influence logo, are excluded; see [brand use](BRAND-USAGE.md). The license does not cover the hosted application or grant access to customer data or paid service features.
