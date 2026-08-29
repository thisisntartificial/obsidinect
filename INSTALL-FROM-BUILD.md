# Install from a local build

For **other people**, use a GitHub Release or BRAT — see [README.md](README.md) and [SHARE.md](SHARE.md). This page is only for a developer machine.

```bash
npm install
npm run build
```

That leaves these files at the repository root:

- `manifest.json`
- `main.js`
- `styles.css`

Copy them into:

```text
<vault>/.obsidian/plugins/obsidinect/
```

Example:

```bash
VAULT="$HOME/path/to/your-vault"
mkdir -p "$VAULT/.obsidian/plugins/obsidinect"
cp manifest.json main.js styles.css "$VAULT/.obsidian/plugins/obsidinect/"
```

Then on the phone (or desktop Obsidian):

1. Reload the vault or wait for iCloud / Obsidian Sync.
2. Settings → Community plugins → Restricted mode off.
3. Enable **Obsidi Connect**.
4. Paste an API key in Settings → Obsidi Connect.

Do not copy `src/`, `node_modules/`, or `main.js.map`. Only the three files above are loaded.

`manifest.json` must keep `"isDesktopOnly": false`. If that flag is true, iPhone Obsidian will not load the plugin.

To share a zip instead of loose files: `npm run package` writes `obsidinect-<version>.zip`. See [SHARE.md](SHARE.md).
