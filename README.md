# LeaseLineage integration

[![M8ven Score](https://m8ven.ai/badge/mcp/kyl3kan3-leaselineage-mcp-nzqtsh)](https://m8ven.ai/mcp/kyl3kan3-leaselineage-mcp-nzqtsh?s=readme)

This configuration-only package connects an assistant to LeaseLineage's read-only commercial real
estate tools and includes a workflow for reviewing prospects, inventory, and
campaign performance. It is prepared for directory review. A package file or
successful upload does not mean it has been submitted, approved, or published.

## Connect

Use `https://leaselineage.com/mcp` with Streamable HTTP and OAuth. Client
registration is automatic; no API key or client secret belongs in this package.
Sign in to LeaseLineage and approve the requested read scopes. See the
[connection guide](https://leaselineage.com/mcp#connect) and
[authentication guide](https://leaselineage.com/auth.md).

`mcp.read` enables public listing search, broker search, and the educational
resource index. `mcp.account.read` enables your saved prospects, owned listings,
campaigns, and reporting. Existing role, plan, account-status, and ownership
checks apply. Account tokens expire after one hour; authenticate again when
prompted. The server does not issue refresh tokens.

## Available operations

- `list_my_prospects`, `list_my_listings`, `list_my_campaigns`, `get_my_reporting`
- `search_cre_listings`, `search_cre_brokers`, `get_cre_resources`

The tools cannot send email, launch campaigns, edit records, read connected
mailbox contents, or manage billing and account settings. Public search can
return no matches. Prospect results cover at most the 500 most recent matches;
page totals describe that window. Account lists default to 25 items and allow
at most 100 per page; public searches allow at most 50.

## Client setup

The public configuration source is
[kyl3kan3/leaselineage-mcp](https://github.com/kyl3kan3/leaselineage-mcp).
Repository availability and directory listing are separate: installing directly
from the repository does not indicate provider review or endorsement.

For Gemini CLI:

```sh
gemini extensions install https://github.com/kyl3kan3/leaselineage-mcp
```

Start Gemini CLI and run `/mcp auth leaselineage` to authorize your account.
See the [Gemini CLI extensions guide](https://geminicli.com/docs/extensions/).

For Claude Code, load a local checkout with `claude --plugin-dir ./<checkout>`
and authenticate from `/mcp`, or add the remote server directly:

```sh
claude mcp add --transport http leaselineage https://leaselineage.com/mcp
```

Then use `/mcp` to authenticate. The `.claude-plugin/plugin.json` and `.mcp.json`
files describe the Claude bundle. Its public directory submission is separate
from the URL-only remote connector submission. See the
[Claude Code MCP guide](https://code.claude.com/docs/en/mcp).

Cursor's current plugin format accepts the root Agent Plugins manifest and
MCP configuration. Follow the [Cursor plugin instructions](https://cursor.com/docs/reference/plugins)
for installation; do not assume the repository is already in its marketplace.

## Package and review status

`plugin.json` uses the portable Agent Plugins format. OpenAI presentation and
review cases are under `extensions.com.openai`; `mcp.json` declares the hosted
server and OAuth registration method. Skills are discovered under `skills/`.
The icon is copied from LeaseLineage's existing 512 by 512 brand asset.

The five positive and three negative cases are proposed acceptance criteria,
not completed test results. Public submission still needs the publisher's
verified identity, portal domain challenge, a fully populated review account,
client testing, and a reviewer-accessible demonstration recording. Reviewer
credentials and the video URL are intentionally absent from public package
files. Enter credentials only in the provider's private review form.

The OpenAI auth extension follows OpenAI's current packaging documentation.
The public Agent Plugins 1.0.0 MCP base schema currently rejects that documented
per-server extension, so OpenAI portal validation remains necessary. The root
plugin manifest passes its published schema. Do not describe this preparation
as a successful portal upload or complete vendor validation.

For Claude, the direct MCP connector submission uses the server URL and does
not require this package or a public repository. Additional vendor manifests
can share these connection settings and workflows after client validation.
The configuration files and workflow documentation use the [MIT license](LICENSE);
the name and brand artwork are excluded from that license. The companion source
contains only connection settings, documentation,
workflows, and the brand icon; it does not include the LeaseLineage application,
database, customer data, or server implementation. Keep application source
private when publishing the separate integration repository.

## Data and support

Tools process task-specific filters and return public records or account data
authorized by the signed-in user. The chosen AI client receives the tool
results in the conversation. This package contains no account credentials,
customer records, or executable scripts.

- [Privacy policy](https://leaselineage.com/privacy)
- [Terms of service](https://leaselineage.com/terms)
- [Customer support](https://leaselineage.com/support)

## Format sources

- [OpenAI package format](https://developers.openai.com/plugins/build/plugins)
- [OpenAI submission requirements](https://developers.openai.com/plugins/deploy/submission)
- [Claude directory submission](https://claude.com/docs/directory/publish)
