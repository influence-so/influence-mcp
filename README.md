# Influence MCP connector

Connect an AI assistant to [Influence](https://influence.so) to create social drafts, review and schedule posts for connected accounts, and read available Insights.

This repository contains customer connection settings and instructions for the hosted service. The Influence application, backend, provider integrations and customer data are maintained separately.

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

For OpenClaw, follow its [MCP connection guide](https://docs.openclaw.ai/tools/mcp). The same skill can be distributed through [ClawHub](https://docs.openclaw.ai/clawhub/publishing). The native Claude plugin layout is also accepted by the [xAI plugin marketplace](https://github.com/xai-org/plugin-marketplace/blob/main/CONTRIBUTING.md). Directory inclusion and complete host behavior are separate from package format support.

## Use and approval

Read the [customer skill](skills/influence/SKILL.md) for the complete workflow. Display the exact review and wait for a fresh approval before publishing or changing a schedule. Image posts require signed-in visual review in Influence. Scheduled or accepted work is not a published post; preserve the same request ID after an uncertain result.

IQ planning and image generation spend credits only through their explicitly confirmed service actions. A quote or queued job is not completed content. Service pricing and client subscriptions are separate from this free connector.

See [how Influence works](https://influence.so/how-it-works), [publishing from ChatGPT](https://influence.so/publish-from-chatgpt), [privacy](https://influence.so/privacy), [terms](https://influence.so/terms) and [support](https://influence.so/support).

## License and branding

The connection configuration, customer skill and documentation are released under [MIT-0](LICENSE). Files under `assets/`, including the Influence logo, are excluded; see [brand use](BRAND-USAGE.md). The license does not cover the hosted application or grant access to customer data or paid service features.
