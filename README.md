# Sourcebook for DSH

**Keep reusable research, working materials, and notes in Sourcebook across DSH sessions. Bring selected sources into a task, then hand useful work back for review.**

Use the DSH workspace for files in your current project. Use Sourcebook Books for references and materials you want to find again across projects: links, files, and notes stay organized in your local library.

This community bundle connects DSH's built-in MCP client directly to the sourcebook-mcp helper shipped with Sourcebook Desktop. It also enables DSH's built-in sidebar browser. There is no separate adapter service and no copied pairing credential.

> Independent community bundle; not affiliated with or endorsed by DeepSeek. Sourcebook Desktop must be installed and running on the same computer as DSH.

## Bring sources into a task

- Open Sourcebook, check its local service, and choose a Book.
- Search that Book and retrieve the sources relevant to the current task.
- Prepare explicitly selected file sources as temporary context files. DSH can then read them through its normal workspace tools.
- Open HTTP(S) source links in DSH's built-in sidebar browser.

## Hand useful work back

When DSH creates something worth keeping, ask it to propose new text, import a named local file, or update source metadata in a Book. The proposals appear in Sourcebook for you to accept or reject; the library changes only after you accept. New text and files can include a note about their origin or intended use, so the next session has context too.

For handoff to another agent, Sourcebook Desktop's **Pack** copies selected materials to the clipboard for pasting into that agent. Ongoing project materials and one-off tasks can stay organized in the same library.

## Try it

- “Open Sourcebook and find the references in my Launch Book for this project.”
- “Use the selected sources to draft a brief, then submit the final text to my Launch Book with a note about its purpose.”
- “Import this local file into my Launch Book and open Sourcebook so I can review the submission.”

## Requirements

- DeepSeek Harness with the built-in @deepseek-ai/dsh-mcp-client
- Sourcebook Desktop installed and running on the same computer
- macOS; the default helper path in this bundle targets the standard macOS app location

## Install

Run: dsh plugin --profile web add github:Yanze-He/dsh-sourcebook

For DSH Desktop, use Settings → Plugins → Add plugin and enter https://github.com/Yanze-He/dsh-sourcebook. Restart DSH, open a new conversation, and ask it to open Sourcebook.

Set DSH's Link opening method to In-app sidebar to open HTTP(S) links returned by Sourcebook in the sidebar browser. Public and loopback HTTP(S) links are supported. The browser rejects file:, data:, blob:, and DSH's own origin.

## If Sourcebook is installed somewhere else

The bundled patch uses this standard macOS application path:

/Applications/Sourcebook Desktop.app/Contents/Resources/agent-plugin/.agents/plugins/sourcebook/bin/sourcebook-mcp

If your app is installed elsewhere, update the command value in cordis.patch.yml to the actual helper path, then install the local checkout into the DSH profile with dsh plugin --profile web add /path/to/dsh-sourcebook-plugin.

## Local-first and data handling

Sourcebook's Books and files stay on your computer. This bundle registers the MCP client; it does not read the database, copy credentials, or expose the local API to the network. The Sourcebook helper handles local API authentication. Context files are prepared only when explicitly requested, but DSH may read them through its normal tools and send their contents to the model provider configured for DSH. Check that provider's data settings before using sensitive material.

## License

MIT. Sourcebook and DeepSeek Harness are separate products with their own licenses and trademarks.
