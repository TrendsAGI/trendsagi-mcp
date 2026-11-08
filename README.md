# TrendsAGI MCP Server

Live trend intelligence for AI agents. TrendsAGI measures what is trending across
social platforms in real time — volume, velocity and growth — and turns it into
AI insights, source-backed dossiers, evidence-backed recommendations and crisis
alerts for paid media, growth and marketing teams.

- **Hosted MCP endpoint:** `https://api.trendsagi.com/mcp`
- **Transport:** Streamable HTTP
- **Auth:** OAuth 2.1 sign-in, or a TrendsAGI API key as a Bearer token
- **Tools:** 15 read-only tools
- **Website:** [trendsagi.com/mcp](https://trendsagi.com/mcp)
- **Create an account:** [app.trendsagi.com/register](https://app.trendsagi.com/register)
- **API documentation:** [trendsagi.com/api-docs](https://trendsagi.com/api-docs)

## What agents can do

- Find topics accelerating in a category, or around a brand, product or competitor.
- Check whether a trend is still rising, flat or fading over 24 hours, 7 days or 30 days.
- Read the AI insight for a trend: themes, sentiment, audience and marketing angles.
- Read the source-backed dossier: resolved subject, dated timeline, channels, brands and products.
- Review prioritised recommendations with the evidence behind each one.
- Check reputation and crisis events before recommending more spend.
- Query the account's data with read-only SQL.

TrendsAGI measures trend volume and growth. It does not measure ad performance or
conversion lift, and a recommendation's confidence score reflects how complete its
evidence is — not the probability that an action will succeed.

## Connect

### Claude Code

```bash
claude mcp add --transport http trendsagi https://api.trendsagi.com/mcp
```

Or add the plugin marketplace and install the plugin:

```bash
/plugin marketplace add TrendsAGI/TrendsAGI
/plugin install trendsagi@trendsagi
```

### Claude, ChatGPT, Cursor and other MCP clients

Add a remote MCP server named `trendsagi` with the URL:

```text
https://api.trendsagi.com/mcp
```

The client opens the TrendsAGI consent page on first use. Approve the connection;
TrendsAGI creates a dedicated API key for that client under **Profile → API Keys**,
where you can revoke it at any time.

### Cursor

```json
{
  "mcpServers": {
    "trendsagi": {
      "url": "https://api.trendsagi.com/mcp"
    }
  }
}
```

### GitHub Copilot

```bash
copilot mcp add --transport http trendsagi https://api.trendsagi.com/mcp
```

### Snowflake Cortex Code (CoCo)

```bash
cortex mcp add trendsagi https://api.trendsagi.com/mcp --type http
```

### API key instead of OAuth

Send the key as `Authorization: Bearer <TRENDSAGI_API_KEY>` or `X-API-Key:
<TRENDSAGI_API_KEY>`. An API key works for MCP clients that cannot complete a
browser OAuth flow, including some cloud coding agents.

## Tools

| Tool | What it returns |
| --- | --- |
| `list_trends` | Trending topics with measured volume, velocity and growth; filter by category, phrase, period and sort order. |
| `list_trend_categories` | The category names `list_trends` accepts. |
| `search_trend_insights` | Trends and insights matching a theme or phrase. |
| `get_trend` | One trend's current snapshot: volume, velocity, growth and category. |
| `get_trend_ai_insights` | Summary, key themes, sentiment, audience and marketing angles for one trend. |
| `get_trend_dossier` | The source-backed dossier: subject, timeline, channels, content landscape, brands and products. |
| `list_web_trends` | Labels found in an external trend list, including labels not yet in the measured table. Discovery evidence only. |
| `get_trend_analytics` | A trend's volume time series over 24h, 7d or 30d. |
| `list_recommendations` | Prioritised, evidence-backed recommendations with decision briefs. |
| `list_crisis_events` | Reputation and crisis events on monitored topics. |
| `list_watchlist` | The topics the account watches and their alert conditions. |
| `get_api_usage` | The API key's usage against its daily limit. |
| `read_data_schema` | Tables, columns, rules and example queries for `execute_sql`. |
| `execute_sql` | One read-only PostgreSQL `SELECT` over the account's TrendsAGI data. |
| `find_capability` | Whether TrendsAGI can do a task, and which tool or app page does it. |

Every tool is read-only. The connection cannot change an ad campaign, edit a
watchlist or spend money.

## Example prompts

- "Which Technology topics are accelerating fastest right now?"
- "Is the OpenAI trend still rising, or is it fading this week?"
- "What audience and ad angles does TrendsAGI suggest for this trend?"
- "What is the story behind this trend, and where is the conversation happening?"
- "Show my highest-priority TrendsAGI recommendations."
- "Which of my watched topics are trending this week?"

## Plans and limits

Any TrendsAGI plan can read trends, trajectories, insights, recommendations and the
watchlist. Insight search needs Advantage or higher; crisis events need Scale or
higher. Each tool call counts as one API request against the plan's daily limit.
See [pricing](https://trendsagi.com/pricing) for the current plans.

## Data and privacy

- The assistant calls `https://api.trendsagi.com` only. No code runs on your machine.
- TrendsAGI receives the tool requests the assistant sends — a category, a search
  phrase or a trend id — never your conversation.
- Each connection gets its own API key named for the client. Revoke it under
  **Profile → API Keys** to disconnect immediately.
- [Privacy policy](https://trendsagi.com/privacy) · [Terms](https://trendsagi.com/terms)

## Links

- [TrendsAGI homepage](https://trendsagi.com)
- [Create a free account](https://app.trendsagi.com/register)
- [MCP setup guide](https://trendsagi.com/mcp)
- [API reference](https://trendsagi.com/api-docs/reference)
- [Python SDK and CLI](https://pypi.org/project/trendsagi/)
- [npm CLI](https://www.npmjs.com/package/trendsagi)
- [Source and plugins](https://github.com/TrendsAGI/TrendsAGI)
- [Support](https://trendsagi.com/contact)

## License

MIT © TrendsAGI
