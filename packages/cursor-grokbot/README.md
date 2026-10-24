# Goalz for Cursor, with Grok Bot Connect apps notes

This package uses Cursor's documented `.cursor-plugin/plugin.json` format and connects to the hosted Goalz OAuth MCP endpoint at `https://www.goalz.de/mcp/apps`. The manifest declares the endpoint only; no scope-request field is documented for this file. The OAuth client must include desired scopes in its authorization request. Goalz requires `manager:read`; if the request omits `scope`, only that scope is granted and the visible tools are limited. Full gameplay requires the client to request and receive the needed scopes in its browser consent flow. Check the actual requested scopes before claiming that write tools are available. No incremental authorization is promised. The plugin contains no static credentials, local executable, or hooks.

Grok Bot's Connect apps help documents how users browse for an app, add it, finish provider sign-in in a browser, and confirm it under Installed. It does not document a plugin-source upload or marketplace-submission route. A Cursor plugin ZIP or public GitHub repository alone does not place Goalz in Grok Bot's catalog. The official Cursor marketplace separately distributes reviewed Git repositories; Cursor listing approval does not establish Grok Bot availability.

For a user, the documented Grok Bot steps are:

1. Open Connect apps in Grok Bot and search for Goalz.
2. If Goalz is listed, choose Add and complete the Goalz login and consent in the browser.
3. Confirm Goalz appears under Installed, then attach it in chat with the app picker.
4. Grant only the requested permissions that match the intended use. Reconnect through the provider if the required permission is absent.

If Goalz is not in the catalog, this package does not provide a supported manual endpoint-import workflow for Grok Bot. The Goalz listing route for Grok Bot remains to be verified. Do not paste a password or access token into chat.

Read <https://www.goalz.de/agenten.php#einrichten> for setup, <https://www.goalz.de/agenten.php#support> for support, <https://www.goalz.de/agenten.php#datenschutz> for privacy, and <https://www.goalz.de/agenten.php#nutzung> for use terms. The publisher contact is <mailto:danielgebauer@gmail.com>.

The Goalz logo and marks are reserved; see `NOTICE.md`.
