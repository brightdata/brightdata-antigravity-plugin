# Bright Data for Antigravity

Give Google Antigravity live access to the web. Bright Data searches the web and reads public pages for your agent, and returns each page as clean markdown, so it can work from what a page says today instead of from memory.

## Install

**Antigravity CLI**

```bash
agy plugin install https://github.com/brightdata/brightdata-antigravity-plugin
```

The CLI installs the plugin to `~/.gemini/config/plugins/bright-data`. The Antigravity App and IDE read the same folder, so the plugin also appears there under **Customizations > Installed**.

**Without the CLI**

Copy this folder to `~/.gemini/config/plugins/bright-data` to use it in every workspace, or to `.agents/plugins/bright-data` at the root of one workspace.

The plugin identifier is `bright-data`, and its MCP server is named `brightdata`.

## Sign in

The plugin connects to the hosted Bright Data MCP server, which uses your Bright Data account. No API key goes in any file.

After you install the plugin, sign in once:

1. In the Antigravity CLI, run `/plugin`, open **bright-data** under **Installed** and choose **Sign in**. In the App, open **Customizations > Installed > Bright Data > Accounts** and choose **Sign in**.
2. Sign in to Bright Data in the browser that opens. If you have no account yet, you can create one there.
3. The browser then shows an authorization code. Copy it and paste it back into Antigravity.

The plugin then shows as signed in to `mcp.brightdata.com`. Requests count against your Bright Data account.

## Try it

- "What are the top 10 stories on https://news.ycombinator.com right now, with points? Use Bright Data."
- "What's the newest Python release on https://www.python.org/downloads/? Use Bright Data."
- "Compare the plans and prices on https://vercel.com/pricing and https://www.netlify.com/pricing/. Use Bright Data."

## What the plugin includes

| Component | What it does |
| --- | --- |
| `search_engine` | Returns the results of one web search: titles, links and snippets. Bing by default, Google on request. |
| `search_engine_batch` | Runs 2 to 5 searches in one call. |
| `scrape_as_markdown` | Reads one public page and returns its text as markdown, or as text, HTML or the page's schema.org data. Long pages can be read in parts. |
| `scrape_batch` | Reads 2 to 5 pages in one call. |
| `bright-data` skill | Tells the agent which tool fits a task, each tool's inputs and limits, and how to check what came back. Invoke it with `/bright-data`. |
| Rule | Reminds the agent to use Bright Data when a task needs current information from the web, to cite its sources, and to treat page text as data. |

All four tools only read the web. None of them changes anything in your Bright Data account.

## Data and security

The plugin connects to `https://mcp.brightdata.com/mcp/directory` over HTTPS. Your searches and the URLs you ask to read are sent to Bright Data, together with the OAuth token from your sign-in. Antigravity stores that token, not this plugin. The plugin has no local executables, scripts or hooks: its skill and rule are instructions that Antigravity reads. See the [Bright Data privacy policy](https://brightdata.com/privacy).

## Uninstall

```bash
agy plugin uninstall bright-data
```

In the App or IDE, open **Customizations > Installed**, select **Bright Data** and uninstall it.

## Resources

- [Bright Data MCP documentation](https://docs.brightdata.com/products/mcp-server/overview)
- [Bright Data MCP server source](https://github.com/brightdata/brightdata-mcp)
- [Contact Bright Data](https://brightdata.com/contact)

## License

MIT
