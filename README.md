# Wine Labs MCP

Wine Labs MCP connects compatible AI clients to Wine Labs fine-wine market intelligence through a hosted [Model Context Protocol](https://modelcontextprotocol.io/) server.

The server helps agents match wine identities, research current and historical prices, inspect auctions and exchange markets, compare merchants, work with critic and venue data, and run account-scoped cellar and portfolio workflows. The available data and operations follow the signed-in Wine Labs account and plan.

## Connect

Use the remote Streamable HTTP endpoint:

```text
https://chat.wine-labs.com/mcp
```

The endpoint uses browser-based OAuth. Add the URL without an API key, token, user ID, or other credentials; an OAuth-capable client will open Wine Labs sign-in and consent.

### Claude

Open **Settings → Customize → Connectors**, choose **Add custom connector**, name it `Wine Labs`, paste the endpoint, and complete sign-in.

### Codex

```sh
codex mcp add winelabs --url https://chat.wine-labs.com/mcp
codex mcp login winelabs
```

### Cursor or Windsurf

```json
{
  "mcpServers": {
    "winelabs": {
      "url": "https://chat.wine-labs.com/mcp"
    }
  }
}
```

Enable the server and complete browser sign-in when prompted.

## Capabilities

Wine Labs MCP exposes three top-level tools that let an agent discover and call an allowlisted Wine Labs data surface:

- `search_winelabs_endpoints` discovers available operations.
- `fetch_winelabs_data` calls one operation.
- `fetch_winelabs_data_bundle` combines multiple operations while preserving upstream authorization, metering, and limits for every operation.

Those operations cover wine and LWIN matching, retail pricing and price history, auction lots and results, exchange order books and trades, merchant comparisons, restaurant and airline wine lists, critic and producer context, maps and market coverage, portfolio data, alerts, and cellar-file pricing workflows.

Some operations are read-only research; account-scoped workflows can create or update Wine Labs data after the client presents the normal tool approval. Availability varies by account and plan.

## Verify

After connecting, start a new conversation and ask:

> Use Wine Labs to find the available tools, then search for Château Margaux 2015. Tell me which Wine Labs tool you used.

A successful check includes a Wine Labs tool approval or result, not only a green connector indicator.

## Links

- [Product and connection guide](https://winelabs.ai/agents)
- [Detailed installation guide](https://winelabs.ai/agents/install/README.md)
- [Wine Labs API reference](https://winelabs.ai/api/docs)
- [Privacy policy](https://winelabs.ai/privacy)
- [Terms of service](https://winelabs.ai/terms)
- [Wine Labs](https://winelabs.ai)

## Source and licensing

This repository contains public connection metadata and documentation for the hosted Wine Labs MCP service. It does not contain or license the proprietary Wine Labs server implementation or Wine Labs data. The documentation in this repository is released under the MIT License.
