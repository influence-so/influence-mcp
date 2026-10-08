<a href="https://influence.so"><img src="assets/influence-symbol.svg" alt="Influence" width="96" height="96"></a>

# Influence

Influence is a social media management tool for planning campaigns, writing posts and scheduling content across your connected accounts. Its hosted MCP server lets compatible AI assistants use your saved brand voice to prepare drafts, schedule approved posts and read saved results in Insights. Review the exact post and attached media before approving publication or a schedule change.

[Website](https://influence.so) · [How it works](https://influence.so/how-it-works) · [ChatGPT guide](https://influence.so/publish-from-chatgpt) · [Support](https://influence.so/support)

This repository contains customer connection settings and instructions for the hosted service. The Influence application, backend, provider integrations and customer data are maintained separately.

## What you can do

| Work                | How Influence helps                                                                                                                                                                   |
| ------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Plan a campaign     | Use saved brand context to develop campaign ideas and revise a plan for your connected accounts.                                                                                      |
| Prepare content     | Save and revise social drafts. Create image ideas and generate images through Influence IQ with a confirmed credit quote.                                                             |
| Review and schedule | Review the exact text, account, settings and time before approving a post or changing its schedule. Attach saved images and videos in the right order, then review them in Influence. |
| Schedule a set      | Prepare up to 10 posts and 50 account or recipient deliveries in one batch. Review every exact post before scheduling; image approval stays in Influence.                             |
| Follow delivery     | Check each destination's publishing status and the verified post link when available.                                                                                                 |
| Read Insights       | Read available connected-account and post metrics, and refresh supported reporting.                                                                                                   |

Try asking your connected assistant:

- “Plan a campaign for our new product using our saved brand context.”
- “Prepare a draft for LinkedIn and Instagram, then show me the review.”
- “Show the status and published links for that campaign.”
- “Summarize the available Insights for our connected accounts.”

Use images and videos from your Influence media library for galleries, Stories,
Reels and other formats supported by the selected account. The full connection
can import supported images when the assistant can supply the file and has media
write access; other files use Influence upload. Importing an image does not
approve publication. TikTok inbox uploads finish in TikTok; Direct posts finish their
posting choices in Influence.

For bulk scheduling, the assistant can read your calendar and prepare a set of
posts with individual reviews. Calendar reads do not reserve times or enforce
spacing, and bulk scheduling does not change the web-app experience. Tools and
file transfer depend on the installed client's support; a package update alone
does not verify that a client has loaded the new tools.

## Workflow in Influence

Prepare and edit a draft, choose its accounts, and review how it will appear on each channel.

![Influence composer with an editable draft and connected-account previews](https://influence.so/images/influence-composer.jpg)

Use the calendar to see approved scheduled campaigns by date and account.

![Influence calendar showing scheduled campaigns in a weekly view](https://influence.so/images/influence-calendar.jpg)

Both images show an example workspace in the current Influence UI.

## Connections

Influence brings your channels into one workspace:

| Channels                  | Connections                                                                                         |
| ------------------------- | --------------------------------------------------------------------------------------------------- |
| Social and video          | X, LinkedIn profiles and Pages, Instagram, Facebook, Threads, YouTube, TikTok, Pinterest and Twitch |
| Communities and messaging | Discord, Slack, Telegram and WhatsApp Business                                                      |
| Open networks             | Mastodon, Bluesky, Nostr and Pixelfed                                                               |
| Blogs and email           | DEV.to, Hashnode, WordPress, listmonk and Tumblr                                                    |

Choose your connected accounts when preparing a draft. Account permissions, content formats and available Insights follow each channel's supported features.

## Claude

Use [Connect to Claude](https://influence.so/claude) for the primary OAuth connection. No API key is needed. Follow the [Cowork guide](https://influence.so/claude-cowork) or [Claude Code guide](https://influence.so/claude-code) to use the same Claude-account connection where available.

The Claude Code marketplace plugin below uses the full Influence endpoint and a scoped API key. Choose it when you need the additional tools.

## Connection

The Streamable HTTP endpoint is `https://influence.so/api/mcp`. An Influence account and authorized workspace are required. Available tools depend on your permissions, connected accounts and enabled features.

For the bearer-key setups below, create a scoped API key in [Influence Settings → Apps and automations → API keys](https://influence.so/sign-in?next=%2Fapp%2Fsettings%2Faccount%23settings-developer). Choose only the permissions you need and set an expiry. Save the shown-once key in your local secret store as `INFLUENCE_MCP_TOKEN`, available to the process that starts your assistant. Never commit the key, paste it into chat or place it in a URL. Revoke it in Influence when no longer needed.

The root `.mcp.json` reads the bearer key from that environment variable. No key is included in this repository. ChatGPT, Claude and the [Kimi Work plugin](#kimi-work) use Influence sign-in through their native OAuth connection.

## Claude Code

Add this marketplace and install its plugin:

```text
/plugin marketplace add influence-so/influence-mcp
/plugin install influence@influence-mcp
```

Start Claude Code with `INFLUENCE_MCP_TOKEN` available, then use `/mcp` to inspect the connection. This package has no local server, install script or hook. See [Claude Code MCP setup](https://code.claude.com/docs/en/mcp).

## Gemini CLI

Before your first Influence request, set up [Gemini CLI model access](https://geminicli.com/docs/get-started/authentication/) with a Gemini API key or supported enterprise authentication. Your Influence key only connects Influence.

Install the extension:

```text
gemini extensions install https://github.com/influence-so/influence-mcp
```

When prompted, enter your scoped Influence API key. Gemini stores it as a sensitive extension setting and uses it for the hosted MCP connection. The extension includes the same Influence customer skill and review workflow. See [Gemini CLI extensions](https://geminicli.com/docs/extensions/reference/).

If Influence is already installed but `/influence` is missing, update the
extension once:

```text
gemini extensions update influence
```

Restart Gemini CLI after installing or updating. In later conversations, use
`/influence` to check your connected accounts, or `/influence` followed by your
request. This native command activates the included skill; it does not grant
publishing approval. See [custom commands](https://geminicli.com/docs/cli/custom-commands/).

If your Influence key expires or is revoked, create a replacement in Influence
Settings and run:

```text
gemini extensions config influence
```

Confirm replacing the saved setting and enter the new key only in Gemini's
protected terminal prompt, then restart Gemini CLI. Keep the extension installed;
the key does not go in the command, chat or extension files.

This extension connects Gemini CLI. Gemini web and Google Workspace have separate integration options. For manual configuration, use the [Influence Gemini guide](https://influence.so/gemini).

## Kimi Work

Use an account with Kimi Work and K3 access. Select **K3** before starting a new
task. In **Plugins → Custom Plugin**, open **PluginBuilder** and ask it to import
the Influence plugin from
`https://github.com/influence-so/influence-mcp/tree/main/kimi-work`, preserving
its included skill and connection settings.

In **Personal**, choose **Install**. Kimi opens Influence's sign-in and permission
review in your browser; select only the permissions your workflow needs. Wait
until installation completes, then start a new K3 task and ask Influence to list
your connected accounts without creating or publishing anything. Check the
result before creating a draft. Review and approve an exact post in signed-in
Influence before publishing.

The `kimi-work/` plugin uses Kimi's native OAuth connection and the same Influence
customer skill. In later K3 tasks, select the installed Influence plugin from
Plugins; no import is needed for each task. Reconnect only when Kimi requests it
or your Influence connection has expired or been revoked. No API key goes in
chat, plugin files or a model prompt. Work
availability depends on your account and region; this setup does not connect
Kimi web, Claw or ordinary Plus chats. See the [Influence Kimi guide](https://influence.so/kimi).

## Kimi Code

Check your [Kimi Code model access](https://www.kimi.com/code/docs/en/kimi-code-cli/configuration/providers.html): you need eligible Kimi access with available quota, or your own model-provider credentials. Your Influence key only connects Influence.

Start Kimi Code with `INFLUENCE_MCP_TOKEN` available from your local secret manager, then install the plugin:

```text
/plugins install https://github.com/influence-so/influence-mcp/tree/main
```

After installation finishes, enter `/reload` as a separate command.

The native `kimi.plugin.json` loads the same Influence skill and connects the hosted HTTP MCP server using `bearerTokenEnvVar`. Use `/mcp` to check that Influence tools are available. The skill loads when a session starts or resumes; use `/skill:influence` to select it explicitly in a later conversation. Keep the key available when starting Code and replace it when it expires or is revoked. No local server or hook is installed. See [Kimi Code plugins](https://www.kimi.com/code/docs/en/kimi-code-cli/customization/plugins.html) and the [Influence Kimi guide](https://influence.so/kimi).

The root plugin targets Kimi Code. Installing it does not install the separate
Work plugin or connect Kimi web.

## DeepSeek Harness

With DeepSeek Harness **0.2.0-rc.2** and pnpm installed, add the native Influence bundle to the web profile. If you already use manual setup, remove only its `mcp-influence` entry from `~/.dsh/cordis.patch.yml` or `~/.dsh/profiles/web/cordis.patch.yml` before installing; keep your other settings:

```text
dsh plugin --profile web add github:influence-so/influence-mcp
```

Start the Harness with `INFLUENCE_MCP_TOKEN` available from your local secret manager:

```text
dsh web
```

In Web Harness, open **Settings → Models**, add your DeepSeek Platform API key and select **Apply**, then choose a model in your conversation. The API account needs available credit. DeepSeek Chat sign-in does not configure Web Harness, and the model key is separate from `INFLUENCE_MCP_TOKEN`. See [Harness model access](https://github.com/deepseek-ai/deepseek-harness/blob/dsh-v0.2.0-rc.2/docs/user/guide/providers.md).

The config-only bundle connects to `https://influence.so/api/mcp` using the native Streamable HTTP client and includes the canonical Influence skill. It has no runtime dependencies, install script or wrapper server. If you use another existing profile, use that profile for both installation and startup.

For a different Influence address, use standalone manual setup instead of the bundle. If you already installed the bundle in the web profile, remove it first with `dsh plugin --profile web remove influence`. Add the following entry to `~/.dsh/profiles/web/cordis.patch.yml` and change its URL. If an Influence entry exists in the home-level `~/.dsh/cordis.patch.yml`, move only that entry into the profile patch. Preserve your other settings and replace an existing `mcp-influence` entry rather than adding it twice. If you set `DSH_HOME`, use that home instead of `~/.dsh`; for another profile, replace `web` with that profile in the path:

```yaml
- insert:
    - id: mcp-influence
      name: "@deepseek-ai/dsh-mcp-client"
      config:
        serverName: influence
        transport: streamable-http
        url: https://influence.so/api/mcp
        headers:
          Authorization: !!js "`Bearer ${process.env.INFLUENCE_MCP_TOKEN}`"
```

For manual setup, save the [customer skill](skills/influence/SKILL.md) as `~/.dsh/skills/influence/SKILL.md`; the native bundle already includes it. Restart the Harness and check that Influence tools are available before starting a conversation. To remove the native bundle, run:

```text
dsh plugin --profile web remove influence
```

See [DeepSeek native bundles](https://deepseek-harness.github.io/deepseek-harness/en/develop/basic/publish), [native MCP setup](https://github.com/deepseek-ai/deepseek-harness/blob/dsh-v0.2.0-rc.2/packages/mcp/mcp-client/README.md) and the [Influence DeepSeek guide](https://influence.so/deepseek).

This setup connects DeepSeek Harness. The model API and regular DeepSeek chat app are separate products; this configuration does not add tools to them.

## Manus

Open [Influence Settings → Manus](https://influence.so/sign-in?next=%2Fapp%2Fsettings%2Faccount%23settings-developer-manus) to create an expiring scoped key and copy the credential-free MCP configuration. In Manus, open **+ Add connectors → Create → Import MCP by JSON** and paste that configuration. Keep the connector private.

Open **Manage → Edit configuration → Custom headers → Add custom header**. Set the header name to `Authorization` and its value to `Bearer` followed by one space and your scoped key. This field displays the key. Keep it out of chat and shared exports, and do not choose **Publish to Projects**.

Choose **Try it out** and ask Influence to list your connected accounts and summarize your saved Brand Guidelines without creating, publishing or scheduling anything. Check those results before creating a draft. Review and approve the exact post while signed in to Influence.

Download the [Influence skill ZIP](https://influence.so/downloads/influence-skill.zip). In Manus, open **Skills** and choose the option to upload a skill. The archive contains `SKILL.md` at its root. In later tasks, type `/` and select Influence from your installed skills. For a project, select it in that project's skill library too. Keep the private MCP connector configured and replace its key when it expires or is revoked. The skill adds workflow instructions; the MCP connection must be configured separately. See [Manus skill installation and use](https://help.manus.im/en/articles/14753565-how-to-share-and-use-skills-in-manus).

This uses Manus’s native remote MCP client and does not require a local server or a separate plugin manifest. See the [Influence Manus guide](https://influence.so/manus) for the setup flow and [Manus Custom MCP Servers](https://manus.im/docs/integrations/custom-mcp) for provider help.

## OpenClaw

These instructions use OpenClaw **2026.9.8** and a
[supported Node.js version](https://docs.openclaw.ai/install).
Keep your scoped key in your private `~/.openclaw/.env` file as
`INFLUENCE_MCP_TOKEN`, or make it available in the environment that starts
OpenClaw. Save Influence's native connection before installing the plugin:

```sh
openclaw mcp set influence '{"url":"https://influence.so/api/mcp","transport":"streamable-http","headers":{"Authorization":"Bearer ${INFLUENCE_MCP_TOKEN}"}}'
```

This saves the key reference, without connecting. OpenClaw resolves it from your
private environment and uses this saved definition instead of the plugin's
connection settings. See [native MCP configuration](https://docs.openclaw.ai/cli/mcp/registry).

Download this repository and install its existing Claude-format bundle:

```sh
git clone https://github.com/influence-so/influence-mcp influence
openclaw plugins install ./influence
```

Review and accept OpenClaw's source and plugin capability prompts, then start or
restart your Gateway. The native installer includes the Influence skill and
icon without a local server, hook or wrapper. In later conversations, use
`/influence` followed by your request. Keep the installation; update your private
key when it expires or is revoked. Installing the plugin does not approve a
post. See [plugin bundles](https://docs.openclaw.ai/plugins/bundles) and the
[Influence OpenClaw guide](https://influence.so/openclaw).

## Other assistants

The `skills/influence/` directory contains the customer skill in standard `SKILL.md` format. Installing a skill provides instructions; it does not connect a server or issue credentials. Configure your assistant's supported remote MCP client separately with the endpoint and scoped bearer key.

The native Claude plugin layout is also accepted by the [Grok Build plugin marketplace](https://github.com/xai-org/plugin-marketplace/blob/main/CONTRIBUTING.md), subject to its separate publication review.

## Use and approval

Read the [customer skill](skills/influence/SKILL.md) for the complete workflow. Display the exact review and wait for a fresh approval before publishing or changing a schedule. Review attached images and videos before approving the post. Scheduled or accepted work is not a published post; preserve the same request ID after an uncertain result.

IQ planning and image generation spend credits only through their explicitly confirmed service actions. A quote or queued job is not completed content.

## Pricing and help

This connector is free. The hosted Influence service uses a paid subscription. Its seven-day trial requires a payment method and automatically starts the selected subscription after the trial unless you cancel before it ends. Review current plans on the [Influence website](https://influence.so). Assistant subscriptions and Influence IQ credits have their own terms.

See [how Influence works](https://influence.so/how-it-works), [publishing from ChatGPT](https://influence.so/publish-from-chatgpt), [privacy](https://influence.so/privacy), [terms](https://influence.so/terms) and [support](https://influence.so/support).

## Registry metadata

`server.json` describes the hosted endpoint for the official MCP Registry under `io.github.influence-so/influence-mcp`. It does not identify this customer connector as the service implementation source.

Authorized maintainers can manually run the **Publish to MCP Registry** GitHub workflow on this repository's `main` branch. It validates the manifest and uses the official publisher with GitHub OIDC, without a dedicated registry secret. Published Registry metadata is immutable; a metadata update needs a new unique server version. Check the workflow result and public registry record after publication. See the [official publishing guide](https://modelcontextprotocol.io/registry/github-actions) and [versioning guide](https://modelcontextprotocol.io/registry/versioning).

## License and branding

The connection configuration, customer skill and documentation are released under [MIT-0](LICENSE). Files under `assets/` and `kimi-work/icon.svg`, including the Influence logos, are excluded; see [brand use](BRAND-USAGE.md). The license does not cover the hosted application or grant access to customer data or paid service features.
