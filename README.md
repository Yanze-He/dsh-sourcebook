# Sourcebook for DSH
**Keep reusable research, working materials, and notes in Sourcebook across DSH sessions. Bring selected sources into a task, then hand useful work back for review.**
Use the DSH workspace for files in your current project. Use Sourcebook Books for references and materials you want to find again across projects: links, files, and notes stay organized in your local library.
## Who it's for
- Video and visual content creators working from reference images, clips, links, and briefs
- Designers, writers, and researchers who reuse project research and working notes across deliverables
- People who move between DSH sessions or agents and want useful materials and notes to remain available afterward
For example, collect campaign references in a Book, ask DSH to draft a brief from selected sources, then submit the finished brief and its working notes back to Sourcebook for review.
This community bundle connects DSH's built-in MCP client directly to the sourcebook-mcp helper shipped with Sourcebook Desktop. It also enables DSH's built-in sidebar browser. There is no separate adapter service and no copied pairing credential.
> Independent community bundle; not affiliated with or endorsed by DeepSeek. Sourcebook Desktop must be installed and running on the same computer as DSH.
## Bring sources into a task
- Open Sourcebook, check its local service, and choose a Book.
- Search that Book and retrieve the sources relevant to the current task.
- Prepare explicitly selected file sources as temporary context files. DSH can then read them through its normal workspace tools.
- Open HTTP(S) source links in DSH's built-in sidebar browser.
### Copying link-type sources
When Sourcebook is open in DSH's sidebar, it runs inside an iframe on a different origin from DSH. The sidebar currently does not grant that iframe clipboard-write permission, so copying a link-type source with Sourcebook's Copy button may fail with a Clipboard API or Permissions Policy error. To copy the link, open the same Sourcebook HTTP(S) address in a standalone browser tab and use Copy there, or select the URL text and press Command+C (macOS) or Ctrl+C. This is a limitation of the embedded browser's clipboard permissions; the plugin cannot change the iframe permission. File-source copy may use a different path and can continue to work.
## Hand useful work back
When DSH creates something worth keeping, ask it to propose new text, import a named local file, or update source metadata in a Book. The proposals appear in Sourcebook for you to accept or reject; the library changes only after you accept. New text and files can include a note about their origin or intended use, so the next session has context too.
For handoff to another agent, Sourcebook Desktop's **Pack** copies selected materials to the clipboard for pasting into that agent. Ongoing project materials and one-off tasks can stay organized in the same library.
## Try it
- “Open Sourcebook and find the references in my Launch Book for this project.”
- “Use the selected sources to draft a brief, then submit the final text to my Launch Book with a note about its purpose.”
- “Import this local file into my Launch Book and open Sourcebook so I can review the submission.”
## Requirements
- DeepSeek Harness with the built-in @deepseek-ai/dsh-mcp-client
- Sourcebook Desktop installed and running on the same computer as DSH. **[Download Sourcebook Desktop for macOS (Apple silicon)](https://github.com/Yanze-He/sourcebook-for-agents/releases/download/v0.1.1-beta.6/sourcebook-desktop-installer-v0.1.1-beta.6.dmg)**
- macOS; the default helper path in this bundle targets the standard macOS app location
## Install
Install and launch Sourcebook Desktop first, then install this DSH bundle using one of the options below. Keep Sourcebook Desktop running while using the integration.
### DSH Desktop
1. Open DSH Desktop and go to **Settings → Plugins → Add plugin**.
2. Enter the repository URL: https://github.com/Yanze-He/dsh-sourcebook, then complete the Add plugin flow.
3. Restart DSH. Start a new conversation and ask it to open Sourcebook and list your Books.
### DSH Web profile
Run:
dsh plugin --profile web add github:Yanze-He/dsh-sourcebook
For HTTP(S) links returned by Sourcebook to open in the sidebar browser, set DSH's **Link opening method** to **In-app sidebar**. Public and loopback HTTP(S) links are supported. The browser rejects file:, data:, blob:, and DSH's own origin.
## If Sourcebook is installed somewhere else
The bundled patch uses this standard macOS application path:
/Applications/Sourcebook Desktop.app/Contents/Resources/agent-plugin/.agents/plugins/sourcebook/bin/sourcebook-mcp
If your app is installed elsewhere, update the command value in cordis.patch.yml to the actual helper path, then install the local checkout into the DSH profile with:
dsh plugin --profile web add /path/to/dsh-sourcebook-plugin.
