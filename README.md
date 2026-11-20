<p align="center">
  <a href="https://pomerado.ai"><img src="assets/logo.png" alt="Pomerado logo" width="96" height="96"></a>
</p>

<h1 align="center"><a href="https://pomerado.ai">Pomerado</a> for Antigravity</h1>

<p align="center">Connect your agents to any website. The cheaper, faster, and more reliable alternative to browser use.</p>

<p align="center">
  <a href="LICENSE"><img src="https://img.shields.io/badge/license-MIT-blue?style=for-the-badge" alt="License MIT"></a>
  <a href="https://antigravity.google/docs/plugins"><img src="https://img.shields.io/badge/Antigravity-plugin-4285F4?style=for-the-badge&amp;logo=google&amp;logoColor=white" alt="Antigravity plugin"></a>
  <a href="https://docs.pomerado.ai/guides/connect/client-setup"><img src="https://img.shields.io/badge/MCP-Streamable%20HTTP-0A0A0A?style=for-the-badge" alt="MCP over Streamable HTTP"></a>
  <a href="https://github.com/Pomerado/pomerado"><img src="https://img.shields.io/github/stars/Pomerado/pomerado?style=for-the-badge&amp;logo=github" alt="Pomerado core on GitHub"></a>
  <img src="https://img.shields.io/badge/Backed%20by-Y%20Combinator-F26522?style=for-the-badge&amp;logo=ycombinator&amp;logoColor=white" alt="Backed by Y Combinator">
</p>

<p align="center">
  <a href="#install">Install</a> ·
  <a href="#sign-in">Sign in</a> ·
  <a href="#example-prompts">Example prompts</a> ·
  <a href="#whats-in-the-plugin">What's in the plugin</a> ·
  <a href="https://docs.pomerado.ai">Docs</a> ·
  <a href="https://discord.gg/QCwQFydAym">Discord</a>
</p>

---

## What Pomerado does

Give your agents tools for the websites you use. Pomerado turns any website into an API or MCP, so it's cheaper, faster and more reliable than driving a browser. Use it whenever a task involves a website or web app, such as looking things up, filling in forms and automating web workflows.

- Pomerado finds a ready-made tool for your site and task, or builds one in minutes
- Tools are deterministic APIs that run in seconds, so your agent doesn't reason through every page
- Pomerado signs in for you, including on sites that ask for a two-factor code
- It works on sites with no API, from consumer sites to legacy portals and internal tools
- When a site changes, Pomerado repairs the tool and finishes the call

## Install

### From GitHub

Run this in your terminal with the Antigravity CLI.

```sh
agy plugin install https://github.com/Pomerado/antigravity-plugin
```

Pomerado then shows up under **Customizations** and **Installed** in the Antigravity App, and in `/plugin` in the CLI.

### As a local plugin

Clone this repository into Antigravity's global plugin folder to use Pomerado in every workspace.

```sh
git clone https://github.com/Pomerado/antigravity-plugin ~/.gemini/config/plugins/pomerado
```

To use it in one workspace only, clone it into `.agents/plugins/pomerado` at the workspace root instead.

### Manual setup

Add this entry to `~/.gemini/config/mcp_config.json` to use Pomerado in every workspace, or to `.agents/mcp_config.json` to use it in one workspace.

```json
{
  "mcpServers": {
    "pomerado": {
      "serverUrl": "https://mcp.pomerado.ai/mcp"
    }
  }
}
```

## Sign in

Pomerado signs you in with OAuth, so there's no API key to copy.

1. Add Pomerado with any of the steps above
2. When Antigravity asks, open Pomerado's sign-in page in your browser
3. Sign in with Google, GitHub or email, then approve Antigravity. Your first sign-in creates a free account
4. If Antigravity asks for an authorization code, paste the code from your browser and click **Submit**
5. Antigravity lists the Pomerado tools once sign-in succeeds

To sign in again later, open **Customizations** and then **Installed** in the Antigravity App. Click **Authenticate** next to Pomerado under **MCP Servers**. In the CLI, open `/plugin`, expand Pomerado under **Installed** and choose **Sign in**.

To disconnect Antigravity, open **Settings** and then **Connected apps** in the [Pomerado Dashboard](https://app.pomerado.ai). To connect with an API key instead, see [client setup](https://docs.pomerado.ai/guides/connect/client-setup).

## Example prompts

> Use Pomerado to get the 7-day forecast for Yosemite Valley on weather.gov.

> Use Pomerado to get the top 10 stories on Hacker News right now.

> Use Pomerado to find the cheapest nonstop flights from SFO to JFK on March 12, 2027 for one adult in economy on Google Flights.

Pomerado looks for a tool for the site first. If none exists yet, it builds one and reuses it after that.

Pomerado works best when your instructions say to prefer it. Add this line to your workspace `AGENTS.md`, or to `~/.gemini/AGENTS.md` to use it in every workspace.

```text
For tasks on websites, use the Pomerado MCP before a browser.
```

## What's in the plugin

This plugin adds one MCP server to Antigravity. It has no rules, skills, agents, hooks or scripts, and it runs no code on your machine.

| File | What it does |
| --- | --- |
| `plugin.json` | Names the plugin and its publisher, and sets the starter prompts |
| `mcp_config.json` | Connects Antigravity to the hosted Pomerado MCP at `https://mcp.pomerado.ai/mcp` over Streamable HTTP |
| `assets/logo.png` | The Pomerado logo |

The server gives your agent these main tools.

| Tool | What it does |
| --- | --- |
| `find_website_tool` | Finds a ready-made tool for a task on a website |
| `run_read_only_website_tool` | Runs a tool that only reads a website |
| `run_website_tool` | Runs a tool that changes something on a website, such as submitting a form |
| `build_website_tool` | Builds a new tool when none exists yet |
| `get_job` | Follows a run or build until it finishes |
| `answer_job` | Answers a question a run or build asks |
| `cancel_job` | Stops a run or build |

Once you sign in, the server also has tools for saved logins, file uploads and the rest of the Pomerado API.

## Your data

- Task results are erased once delivered, or within 60 minutes if never read
- Pomerado stores a website login only if you choose to save it
- Your agent can use a saved login in a job but never sees its password

Read the [privacy policy](https://pomerado.ai/privacy-policy), the [terms of service](https://pomerado.ai/terms-of-service) and the [trust center](https://trust.pomerado.ai) for details.

## Open source

Pomerado's core is open source under the MIT license at [Pomerado/pomerado](https://github.com/Pomerado/pomerado). It builds integrations in a real browser and runs them on your own machine.

This plugin connects Antigravity to Pomerado Cloud, which runs the same core as a hosted service. Cloud adds hosting, sign-in, saved logins and automatic repair when a site changes.

## Links

- [Documentation](https://docs.pomerado.ai)
- [Set up an MCP client](https://docs.pomerado.ai/guides/connect/client-setup)
- [Open-source core](https://github.com/Pomerado/pomerado)
- [Privacy policy](https://pomerado.ai/privacy-policy)
- [Terms of service](https://pomerado.ai/terms-of-service)
- [Trust center](https://trust.pomerado.ai)
- [Discord](https://discord.gg/QCwQFydAym)
- Support at [founders@pomerado.ai](mailto:founders@pomerado.ai)

## License

Copyright (c) 2026 Pomerado AI, Inc. Licensed under the MIT License. See [LICENSE](LICENSE).
