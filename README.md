# Sourcebook for DeepSeek Harness

Use Sourcebook Desktop as a local, Book-scoped research library from DeepSeek Harness (DSH). This bundle connects DSH's built-in MCP client directly to the `sourcebook-mcp` helper shipped with Sourcebook Desktop and enables DSH's built-in sidebar browser in Web profiles. It does not add an adapter service or copy pairing credentials.

> This community bundle is not affiliated with or endorsed by DeepSeek. Sourcebook Desktop must be installed and running on the same computer as DSH.

## What it can do

The Sourcebook MCP server provides nine tools:

- Open Sourcebook and check its local service
- List and select Books
- Search sources and retrieve selected sources
- Prepare explicitly requested file sources as temporary context files
- Propose adding text, importing a local file, or updating source metadata

All `propose_*` operations create pending suggestions. A person must accept them in Sourcebook before a Book is changed. Context-file preparation copies only explicitly requested files into a temporary local task folder. DSH may then read those files through its normal workspace tools, so check your model-provider settings before using sensitive material.

## Requirements

- DeepSeek Harness with the built-in `@deepseek-ai/dsh-mcp-client`
- Sourcebook Desktop installed on the same computer
- macOS (the default helper path in this bundle targets the standard macOS app location)

## Install

```sh
dsh plugin --profile web add github:Yanze-He/dsh-sourcebook
```

For DSH Desktop, use **Settings → Plugins → Add plugin** and enter `https://github.com/Yanze-He/dsh-sourcebook`. For a Web profile managed from the CLI, run the command above. Restart DSH, open a new conversation, then ask the agent to open Sourcebook and list your Books.

## If Sourcebook is installed somewhere else

The bundled patch uses the standard macOS application path:

```text
/Applications/Sourcebook Desktop.app/Contents/Resources/agent-plugin/.agents/plugins/sourcebook/bin/sourcebook-mcp
```

If your app is installed in another location, update the `command` value in `cordis.patch.yml` to the actual helper path, then install the local checkout into the DSH profile:

```sh
dsh plugin --profile web add /path/to/dsh-sourcebook-plugin
```

## Use safely

1. Ask DSH to open Sourcebook and confirm the local service is reachable.
2. List Books, then select the intended Book before searching or retrieving sources.
3. Review each proposed write in Sourcebook and accept it explicitly.

Sourcebook's library remains local. This bundle only registers the MCP client configuration; it does not read the database, copy credentials, or expose the local API to the network. The Sourcebook helper handles its own local API authentication.

## Browser sidebar

The bundle enables the DSH built-in sidebar browser. Set DSH's **Link opening method** to **In-app sidebar** to open HTTP(S) links returned by Sourcebook in that browser. Public and loopback HTTP(S) links are supported. The browser rejects `file:`, `data:`, `blob:`, and DSH's own origin.

## License

MIT. Sourcebook and DeepSeek Harness are separate products with their own licenses and trademarks.
