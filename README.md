# Goalz plugins

This repository contains reviewed, portable connection packages for Goalz. They connect to the hosted
Goalz MCP endpoint; they do not contain a local server, backend source, or account credentials.

## Packages

- `packages/openai/` contains the OpenAI Agent Plugins manifest and OAuth configuration. It asks the
  browser consent flow for all seven reviewed gameplay scopes because Goalz filters the available
  tools to the scopes the host actually requests and receives. Read-only setup is documented in the
  package README.
- `packages/grok-build/` follows the xAI plugin layout. The `source.path` for an xAI catalog entry
  must point to this directory. xAI category metadata is optional; no category is selected by
  default.
- `packages/cursor-grokbot/` contains the documented Cursor plugin format. The Grok Bot Connect apps
  flow is a separate catalog; a Cursor package or listing does not establish Grok Bot availability.
- `server.json` describes one remote-only Streamable HTTP MCP endpoint for registry discovery. It
  adds no local executable or package runtime.

Each package directory is self-contained for its platform's current source/import workflow. Preserve
hidden manifest files when copying or archiving a package. Platform requirements and submission
flows can change; consult the linked official documentation before import or submission.

## Authentication and permissions

The endpoint is `https://www.goalz.de/mcp/apps`. Authentication is OAuth in the provider's browser
flow. The OpenAI package explicitly requests `manager:read`, `manager:manage`, `club:read`,
`club:manage`, `transfers:write`, `messages:read`, and `messages:write` so the complete reviewed
gameplay tool set can be exposed after the user approves those rights. Goalz requires `manager:read`;
if another client omits a scope request, Goalz grants only that read scope. For Grok Build and Cursor,
the endpoint manifest does not itself request OAuth scopes: check the scopes the host actually asks
for and the browser consent screen. Do not assume write access from a connection URL alone.

The server checks account, resource, and effective scopes on every tool call. Passwords, email codes,
and newly issued manual API credentials remain in Goalz's normal browser account flows. Account
controls such as viewing and revoking this account's own sessions or existing connections remain
subject to the granted account-management permission.

Wappen generation remains available when the necessary rights are granted. It can consume quota or
incur cost and sends the documented generation inputs to an image provider. It creates a private
preview; it does not activate or publish the result. The manager chooses separately whether to accept
or discard the preview. See the Goalz privacy information before using it.

## Publication state

These are source files for review and platform import. This repository does not itself mean that a
provider listing has been approved, that Grok Bot lists Goalz, or that the production endpoint is
active. OpenAI portal verification, provider categories and review materials, Grok Build/Cursor
catalog approval, MCP Registry namespace publication, and production domain/endpoint activation are
separate steps. The MCP Registry `server.json` is metadata only and has not been submitted.

Grok Bot's documented Connect apps user flow is described at
<https://cursor.com/help/grok-bot/connect-apps>; it does not document a plugin-source submission
route. Do not treat a Cursor listing as a Grok Bot listing.

## Help and source terms

- Setup: <https://www.goalz.de/agenten.php#einrichten>
- Support: <https://www.goalz.de/agenten.php#support>
- Privacy: <https://www.goalz.de/agenten.php#datenschutz>
- Use terms: <https://www.goalz.de/agenten.php#nutzung>
- Publisher: Daniel Gebauer, <mailto:danielgebauer@gmail.com>

The authored plugin configuration, skills, and documentation are licensed under MIT. The Goalz name,
logo, icon, and game artwork are reserved and excluded from that license. See `LICENSE` and
`NOTICE.md`.

## Official platform documentation

- OpenAI package format: <https://developers.openai.com/plugins/build/plugins>
- OpenAI authentication: <https://developers.openai.com/plugins/build/auth>
- OpenAI submission: <https://developers.openai.com/plugins/deploy/submission>
- xAI plugin catalog: <https://github.com/xai-org/plugin-marketplace>
- Cursor plugins: <https://cursor.com/docs/reference/plugins>
- MCP Registry remote servers: <https://github.com/modelcontextprotocol/registry/blob/main/docs/modelcontextprotocol-io/remote-servers.mdx>
