# Claudius

Chat with Claude, ChatGPT, or Grok in your vault on iPhone and desktop. The agent can read, write, and search notes. No desktop CLI.

Plugin id: `obsidinect` · `isDesktopOnly`: **false** (loads on iPhone) · MIT

This is meant for **other people** to install, not a private sideload. After you publish a public GitHub repo and a release, strangers can use A, then B, then C.

## Install on iPhone

Claudius is not in Browse yet. Use BRAT.

1. Settings → Community plugins → turn **Restricted mode** off.
2. Browse → install **[BRAT](https://github.com/TfTHacker/obsidian42-brat)** → enable it.
3. Settings → BRAT → **Add beta plugin**.
4. Paste `thisisntartificial/obsidinect` (or https://github.com/thisisntartificial/obsidinect).
5. Enable **Claudius**.
6. Settings → Claudius → paste your Claude / ChatGPT / Grok API key.

Open the robot icon and chat. Same steps work on desktop.

## Other install paths

Turn **Restricted mode** off first: Settings → Community plugins.

### A. Official directory (once listed)

Settings → Community plugins → Browse → search **Claudius** → Install.

Each person pastes their own API key in Settings → Claudius. No keys ship in the plugin.

### B. BRAT

Same as **Install on iPhone** above. Repo: [thisisntartificial/obsidinect](https://github.com/thisisntartificial/obsidinect).

### C. Manual (GitHub Release files)

Download **exactly** these three assets from the GitHub Release named after the version (for example `1.0.0`):

- `main.js`
- `manifest.json`
- `styles.css`

Put them here:

```text
<vault>/.obsidian/plugins/obsidinect/
```

Then: reload / wait for Sync → enable **Claudius** → paste an API key.

Phone walkthrough: [IPHONE.md](IPHONE.md).  
Developer copy from a local build: [INSTALL-FROM-BUILD.md](INSTALL-FROM-BUILD.md).  
How Robert publishes this for strangers: [SHARE.md](SHARE.md).

## What it does

1. Open **Claudius chat** from the ribbon or the command palette.
2. Type a request. The plugin sends the thread (and any attached notes) to your provider over HTTPS with Obsidian’s `requestUrl` — not `fetch`.
3. The model can call vault tools. The plugin runs them locally:
   - `list_notes` · `read_note` · `search_notes`
   - `write_note` · `append_note` · `replace_in_note`
4. Type `@` in the composer to attach markdown notes (or tap the `@` button).
5. **Inline edit**: select text or use the whole note, preview before/after, then Apply.

Tap **Stop** on the send button while a reply is in flight.

## Why this is not Claudian

[Claudian](https://github.com/YishenTu/claudian) (`realclaudian`) is desktop-only. It embeds Claude Code, Codex, Grok Build, OpenCode, and Pi by **spawning those CLIs**.

iOS Obsidian **cannot spawn processes**. Claudius is a smaller, mobile-first plugin inspired by that UX only. It does not clone Claudian and does not require those CLIs.

## Privacy

There is **no telemetry**. The plugin does not phone home.

**What is sent:** the current chat (your prompt, earlier turns in this session, `@`-attached note text, and later vault-tool results such as note contents the model just read). Inline edit sends the selection or current note plus your instruction.

**To whom:** only the provider **you** chose in settings:

| You picked | Destination |
| --- | --- |
| Anthropic (Claude) | `https://api.anthropic.com` (or your custom base URL) |
| OpenAI / compatible | `https://api.openai.com/v1` (or your custom base URL) |
| xAI (Grok) | `https://api.x.ai/v1` (or your custom base URL) |

No other host is contacted. A custom base URL is the only way to point somewhere else, and only you set that.

**What stays on the device:** your API key (plugin `data.json`, never logged, never written into notes), the vault files, and tool execution via the Obsidian vault API.

Each user pastes their own key. This repository does not contain API keys.

## Safety

- Only `.md` paths inside the vault. `..` and absolute paths are rejected.
- Overwriting an existing note asks for confirmation unless this turn already named that file.
- No Node, `child_process`, `fs`, `exec`, Electron, or `require('os')` in the plugin.

## Providers

| Provider | API | Default model |
| --- | --- | --- |
| Anthropic (default) | Messages API, `x-api-key` + `anthropic-version` | `claude-sonnet-4-5` |
| OpenAI / compatible | Chat Completions `tools[]` | `gpt-4o` |
| xAI Grok | OpenAI-compatible chat completions | `grok-3` |

Use **Test connection** after pasting a key.

## Develop

```bash
npm install
npm run build
```

`main.js` is bundled with esbuild but **not minified**, so community review can still read it. `npm run package` also writes `obsidinect-<version>.zip`. Tag a version (for example `1.0.0`) to publish a GitHub Release that attaches `main.js`, `manifest.json`, and `styles.css`.

Requires Obsidian 1.4.0 or later.

## License

MIT
