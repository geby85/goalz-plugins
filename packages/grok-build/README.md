# Goalz for Grok Build

This package follows the xAI plugin layout and connects to the hosted Goalz MCP server at `https://www.goalz.de/mcp/apps`. Its `.mcp.json` declares the remote endpoint only; it does not have a documented field for requesting OAuth scopes. The OAuth client must include the desired scopes in its authorization request. Goalz requires `manager:read`; when `scope` is omitted it grants only `manager:read`, so the visible tool catalog will be limited. Full gameplay requires the client to request and receive the needed scopes in its browser consent flow. Check the actual requested scopes before claiming that write tools are available. No incremental authorization is promised. The package does not contain an API key, bearer token, OAuth client secret, local executable, hook, or Goalz backend code.

Use the included `goalz-manager` skill for account setup and game workflows. The skill starts from read access, checks the currently visible tools and scopes, and treats public messages and costly or difficult-to-reverse actions carefully. Wappen generation remains enabled and creates a private preview; the manager must separately accept it.

For Grok.com custom MCP connectors, use the custom connector flow in Grok's connector settings and enter the same endpoint. Do not confuse that direct connection with the Grok Build marketplace: the official xAI marketplace is a separate catalog of plugin repositories.

The intended public repository is `https://github.com/geby85/goalz-plugins`. An xAI marketplace entry must use `source.path: "packages/grok-build"` for this plugin directory and a full reachable 40-character lowercase commit SHA. The current xAI format treats `category` as optional free-form metadata; this package leaves it out unless the publisher deliberately supplies a value. No fabricated SHA or category is included here. The repository and production endpoint still require separate publication/activation checks.

Read <https://www.goalz.de/agenten.php#einrichten> for setup, <https://www.goalz.de/agenten.php#datenschutz> for privacy, and <https://www.goalz.de/agenten.php#nutzung> for use terms. Public user support is available at <mailto:support@goalz.de> or <https://www.goalz.de/agenten.php#support>. Publisher and marketplace contact: <mailto:apps@goalz.de>.

The Goalz logo and marks are reserved; see `NOTICE.md`.
