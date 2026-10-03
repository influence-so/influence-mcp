<a href="https://influence.so"><img src="assets/influence-symbol.svg" alt="Influence" width="96" height="96"></a>

# Influence

Plan, review and publish social campaigns with AI. Connect your assistant to [Influence](https://influence.so) to turn ideas into drafts, schedule approved posts for connected accounts, and read available Insights.

[Website](https://influence.so) · [How it works](https://influence.so/how-it-works) · [ChatGPT guide](https://influence.so/publish-from-chatgpt) · [Support](https://influence.so/support)

This repository contains customer connection settings and instructions for the hosted service. The Influence application, backend, provider integrations and customer data are maintained separately.

## What you can do

| Work | How Influence helps |
| --- | --- |
| Plan a campaign | Use saved brand context to develop campaign ideas and revise a plan for your connected accounts. |
| Prepare content | Save and revise social drafts. Create image ideas and generate images through Influence IQ with a confirmed credit quote. |
| Review and schedule | Review the exact text, account, settings and time before approving a post or changing its schedule. Review image posts in Influence. |
| Follow delivery | Check each destination's publishing status and the verified post link when available. |
| Read Insights | Read available connected-account and post metrics, and refresh supported reporting. |

Try asking your connected assistant:

- “Plan a campaign for our new product using our saved brand context.”
- “Prepare a draft for LinkedIn and Instagram, then show me the review.”
- “Show the status and published links for that campaign.”
- “Summarize the available Insights for our connected accounts.”

## Connections

Influence brings your channels into one workspace:

| Channels | Connections |
| --- | --- |
| Social and video | X, LinkedIn profiles and Pages, Instagram, Facebook, Threads, YouTube, TikTok, Pinterest and Twitch |
| Communities and messaging | Discord, Slack, Telegram and WhatsApp Business |
| Open networks | Mastodon, Bluesky, Nostr and Pixelfed |
| Blogs and email | DEV.to, Hashnode, WordPress, listmonk and Tumblr |

Choose your connected accounts when preparing a draft. Account permissions, content formats and available Insights follow each channel's supported features.

## Connection

The Streamable HTTP endpoint is `https://influence.so/api/mcp`. An Influence account and authorized workspace are required. Available tools depend on your permissions, connected accounts and enabled features.

Create a scoped API key in [Influence Settings → Developer](https://influence.so/app/settings/account#settings-developer). Choose only the permissions you need and set an expiry. Save the shown-once key in your local secret store as `INFLUENCE_MCP_TOKEN`, available to the process that starts your assistant. Never commit the key, paste it into chat or place it in a URL. Revoke it in Influence when no longer needed.

The included `.mcp.json` reads the bearer key from that environment variable. No key is included in this repository. ChatGPT web and Claude web can use the existing Influence OAuth connection; this package uses a scoped key and does not add an OAuth callback.

## Claude Code

Add this marketplace and install its plugin:

```text
/plugin marketplace add influence-so/influence-mcp
/plugin install influence@influence-mcp
```

Start Claude Code with `INFLUENCE_MCP_TOKEN` available, then use `/mcp` to inspect the connection. This package has no local server, install script or hook. See [Claude Code MCP setup](https://code.claude.com/docs/en/mcp).

## Other assistants

The `skills/influence/` directory contains the customer skill in standard `SKILL.md` format. Installing a skill provides instructions; it does not connect a server or issue credentials. Configure your assistant's supported remote MCP client separately with the endpoint and scoped bearer key.

For OpenClaw, follow its [MCP connection guide](https://docs.openclaw.ai/tools/mcp). The same skill can be distributed through [ClawHub](https://docs.openclaw.ai/clawhub/publishing). The native Claude plugin layout is also accepted by the [xAI plugin marketplace](https://github.com/xai-org/plugin-marketplace/blob/main/CONTRIBUTING.md).

## Use and approval

Read the [customer skill](skills/influence/SKILL.md) for the complete workflow. Display the exact review and wait for a fresh approval before publishing or changing a schedule. Image posts require signed-in visual review in Influence. Scheduled or accepted work is not a published post; preserve the same request ID after an uncertain result.

IQ planning and image generation spend credits only through their explicitly confirmed service actions. A quote or queued job is not completed content.

## Pricing and help

This connector is free. The hosted Influence service uses a paid subscription. Its seven-day trial requires a payment method and automatically starts the selected subscription after the trial unless you cancel before it ends. Review current plans on the [Influence website](https://influence.so). Assistant subscriptions and Influence IQ credits have their own terms.

See [how Influence works](https://influence.so/how-it-works), [publishing from ChatGPT](https://influence.so/publish-from-chatgpt), [privacy](https://influence.so/privacy), [terms](https://influence.so/terms) and [support](https://influence.so/support).

## Registry metadata

`server.json` describes the hosted endpoint for the official MCP Registry under `io.github.influence-so/influence-mcp`. It does not identify this customer connector as the service implementation source.

Authorized maintainers can manually run the **Publish to MCP Registry** GitHub workflow on this repository's `main` branch. It validates the manifest and uses the official publisher with GitHub OIDC, without a dedicated registry secret. Published Registry metadata is immutable; a metadata update needs a new unique server version. Check the workflow result and public registry record after publication. See the [official publishing guide](https://modelcontextprotocol.io/registry/github-actions) and [versioning guide](https://modelcontextprotocol.io/registry/versioning).

## License and branding

The connection configuration, customer skill and documentation are released under [MIT-0](LICENSE). Files under `assets/`, including the Influence logo, are excluded; see [brand use](BRAND-USAGE.md). The license does not cover the hosted application or grant access to customer data or paid service features.
